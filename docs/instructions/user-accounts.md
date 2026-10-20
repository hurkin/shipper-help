# User Accounts

Each user signs in with their own ShipperXL account, tied to a contact in your
database. What they see depends on the company that contact belongs to and the
roles you give them.

## Add a user

1. An administrator opens the right company in
   [Companies and Contacts](../context/G008.md) (see *Which company* below) and
   uses **Add contact** to add the user as a **contact** (a person, not a company),
   with the email address they will sign in with.
2. Then set up their account:
   - **[Create User Account](https://secure.hurkin.com/haal/signup)** if the person
     has no account yet. They create a password (within 30 minutes), and you are
     then emailed a link to grant them roles in your database.
   - **[Manage User Account](https://secure.hurkin.com/haal/request-access)** if the
     account already exists. Grant them roles in your database.

## Which company

**A user can see every record for the company their contact belongs to.**

- Relate your own staff to your own company. Being one of its contacts lets a
  person see everything.
- Relate a vendor's, customer's or other party's people to *their own* company.
  They then see only the records that involve that company.

## Troubleshooting

*"You do not have permission to Shipment XXXXXX because your user account is not
affiliated with this record in any way."* Make sure the user's contact belongs to
the booking's shipper, its forwarder, or your own company.

## Related

[Companies and Contacts](../context/G008.md) ·
[Install ShipperXL Mobile](install-mobile.md) for mobile roles ·
[Implementation Checklist](implementation-checklist.md)
