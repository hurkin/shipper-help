# MailChimp Integration

[MailChimp](https://mailchimp.com/) is an email marketing service for keeping in
regular touch with your customers. Shipper can upload your companies and contacts
to a MailChimp list, and MailChimp takes it from there.

## Before you start

- A MailChimp account.
- A MailChimp [API key](https://mailchimp.com/help/about-api-keys/).
- Enter the key once in **Admin > Settings**, **Email** tab, **MailChimp API Key**,
  or ask support@shipperxl.com to do it.

## Set it up

1. Write a SQL query that returns the subscribers you want. Don't worry, we'll
   help. There is an example below.
   - It needs a unique column named `Email`.
   - Every column is merged into MailChimp, and each email address is subscribed to
     the list.
2. Create a list in MailChimp, and note its exact name. It is case-sensitive.
3. Create a [scheduled job](../context/G014.md) with the action *Update MailChimp
   Subscribers*, on a schedule:
   - **Parameter 1:** the SQL query.
   - **Parameter 2:** the list name, exactly.
4. Let it run, and check the results in the job's log.

## Example query

Companies and their contacts who have opted in to marketing and transaction email,
with their last purchase, sale and shipment in the past three years:

```sql
declare @YearsAgo int = 3
select
    p1.Name Company,
    isnull(p2.Name,p1.Name) FNAME,
    ISNULL(p2.Email,p1.Email) Email,
    b.LastPurchase,
    s.LastSale,
    sh.LastShip,
    case when nullif(isnull(p2.PortalPassword,p1.PortalPassword),'') is not null then 1 else 0 end PortalUser
from
    dbo.Party p1
    join dbo.PartyClass pc1 on pc1.PartyClassId = p1.PartyClassId and pc1.Mnemonic = 'COMPANY'
    left outer join dbo.PartyRelation pr
        join dbo.Party p2 on p2.PartyId = pr.ToPartyId
            and p2.IsActive = 1
            and p2.IsMarketingOptedIn = 1
            and p2.IsTransactionOptedIn = 1
        join dbo.PartyClass pc2 on pc2.PartyClassId = p2.PartyClassId and pc2.Mnemonic = 'PERSON'
    on pr.FromPartyId = p1.PartyId
    left outer join (select max(CreatedDate) LastPurchase, Buyer_PartyId
    from dbo.Agreement
    where CreatedDate > DATEADD(year, -@YearsAgo, getutcdate())
    group by Buyer_Partyid) b on b.Buyer_PartyId = p1.PartyId
    left outer join (select max(CreatedDate) LastSale, Seller_PartyId
    from dbo.Agreement
    where CreatedDate > DATEADD(year, -@YearsAgo, getutcdate())
    group by Seller_PartyId) s on s.Seller_PartyId = p1.PartyId
    left outer join (select max(CreatedDate) LastShip, ShipTo_PartyId
    from dbo.Agreement
    where CreatedDate > DATEADD(year, -@YearsAgo, getutcdate())
    group by ShipTo_PartyId) sh on sh.ShipTo_PartyId = p1.PartyId
where
    p1.IsActive = 1
    and p1.IsMarketingOptedIn = 1
    and p1.IsTransactionOptedIn = 1
    and NULLIF(ISNULL(p2.Email,p1.Email),'') is not null
    and (b.LastPurchase is not null or s.LastSale is not null or sh.LastShip is not null)
order by
    1, 2, 3
```

## Related

[Scheduled Jobs](../context/G014.md) · [Settings](../context/settings.md)
