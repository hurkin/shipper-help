# Scheduled Job: Payment Posted

When a payment on an invoice (or a bill, credit memo or letter of credit) is posted,
Shipper can run a scheduled job, for example to email the customer a receipt.

The job runs when the payment's **Posted** date is set, not when the payment is first
entered. With accounting integration, payments recorded in your accounting system
come back to Shipper already posted.

## Setting it up

1. Go to **Admin > Scheduled Jobs** and click **Add**.
2. Set **When this event occurs** to *Invoice Payment Posted* (or the bill, credit
   memo or letter of credit version).
3. Choose the action, for example *Send Email Notification*, and fill in its
   settings.
4. To include the payment's details, put this in **Iteration SQL**:

```sql
SELECT TOP 1 p.Reference1 AS PaymentReference,
       pm.Description AS PaymentMethod,
       p.Amount AS PaymentAmount,
       p.Posted AS PaymentPosted
FROM dbo.Payment p
JOIN dbo.PaymentMethod pm ON pm.PaymentMethodId = p.PaymentMethodId
WHERE p.BillId = @BillId
ORDER BY p.Posted DESC
```

You can then use `@PaymentReference`, `@PaymentMethod`, `@PaymentAmount` and
`@PaymentPosted` in the subject and body. These names are case-sensitive.

> **Screenshot placeholder:** a Payment Posted scheduled job with its event, action and Iteration SQL filled in. (save as `images/payment-posted-job.png`)

See also: [Scheduled Jobs](../context/G014.md).
