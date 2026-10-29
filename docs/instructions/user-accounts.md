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
- Owners are no exception: an owner sees every record only as one of your
  company's contacts.

Only an owner can make someone staff or change a staff member's sign-in: relating a
person to your company, and changing **Email** or **Active** on one of its contacts.
See [Your own company](../context/G008.md?id=your-own-company).

## Remove a user

An owner unticks **Active** on the user's contact. With no active contact for their
sign-in email, they no longer see your company's records, even if the HAAL account
still has roles. To stop them signing in at all, remove their roles in your
database as well.

Give each person **one active contact** with their sign-in email. If their email is
on more than one, the dashboard warns them and links each contact so the extras can
be deactivated, keeping the one that belongs to the right company.

## What the dashboard shows

A user from another company sees which companies' records they can reach on the
dashboard, under the title: *Instance: TEST. You have access to Acme.* Your own
staff see only the instance.

If a user's email isn't on an active contact of any company, the dashboard says
they see only the records they created. Add their email to a contact of their
company (see *Add a user*).

## Troubleshooting

A record newly linked to a user's company, for example a booking whose forwarder
was just set, can take up to 6 minutes to appear for that user. Removing a link
takes as long to hide the record.

*"You do not have permission to Shipment XXXXXX because your user account is not
affiliated with this record in any way."* Make sure the user's contact belongs to
the booking's shipper, its forwarder, or your own company.

## Related

[Companies and Contacts](../context/G008.md) ·
[Install ShipperXL Mobile](install-mobile.md) for mobile roles ·
[Implementation Checklist](implementation-checklist.md)
