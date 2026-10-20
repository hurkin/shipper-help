# Email Attachments into Shipper

Anyone can add attachments to Shipper by email: drivers, inspectors, suppliers or
your own staff from a phone. Older versions of ShipperXL Mobile's
[Send Pictures](../context/M09.md) use this too.

## Send an email

1. Send it to your database's inbound email address (see *Set it up* below).
2. Set the subject to the record to attach to:

   | Record | Subject |
   |---|---|
   | Cargo | The cargo number, such as `ABCD1234567` |
   | SKU | The SKU, such as `A789` |
   | Booking (shipment) | The booking number, such as `567890123` |
   | Sales order | `Sales Order 123456` |
   | Purchase order | `Purchase Order 789012` |
   | Sales contract | `Sales Contract 345678` |
   | Purchase contract | `Purchase Contract 901234` |

   Agreements need their words, such as "Sales Order", before the number.
3. Attach the pictures, documents and so on. The body can be blank. Nothing in the
   body is attached.

Shipper checks the mailbox every few minutes and attaches the files. If it can't
find the record, it replies to tell you.

Work orders don't have attachments. Link the work order to a cargo and send to the
cargo instead.

## Set it up

You need a mailbox that supports IMAP, with OAuth2 or a password. **Shipper reads
and deletes all email in it,** so use a mailbox just for this. It can't be the
mailbox Shipper sends from.

| Provider | Server | Notes |
|---|---|---|
| Microsoft 365 (preferred) | `outlook.office365.com` | A [shared mailbox](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-a-shared-mailbox) or an individual one. Sign in with **Set credentials**. If you have Send As permission to another mailbox, enter it in **Other Mailbox**. |
| Outlook.com | `outlook.office.com` | [Turn on IMAP](https://support.microsoft.com/en-us/office/pop-imap-and-smtp-settings-for-outlook-com-d088b986-291d-42b8-9564-9c414e2aa040) and allow apps to delete items. Sign in with **Set credentials**. |
| Gmail and Google Workspace | `imap.gmail.com` | Works for now, but may not for much longer. Turn on two-step verification, create an [app password](https://support.google.com/mail/answer/185833), and enter the user and app password directly. |

An administrator enters these in **Admin > Settings**, **Email** tab. Click **Test
connection** to check them. See [Settings](../context/settings.md).

## Sending email

Shipper sends email, such as invoices and [scheduled job](../context/G014.md)
emails, through the **outbound** server in **Admin > Settings**. You need a mailbox
that supports authenticated SMTP, with OAuth2 or a password.

| Provider | Server | Notes |
|---|---|---|
| Microsoft 365 (preferred) | `smtp.office365.com` | A shared mailbox is usually best, so its members see what was sent. The mailbox must allow [Authenticated SMTP](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission) (in the Exchange admin center: the user's **Manage email apps**). The signed-in user needs **Send As** permission on it, not Send on Behalf. Sign in with **Set credentials**. |
| Gmail and Google Workspace | `smtp.gmail.com` | Works for now, but may not for much longer. Use an app password, as for inbound. |
| SendGrid | `smtp.sendgrid.net` | Complete [sender authentication](https://www.twilio.com/docs/sendgrid/glossary/sender-authentication) and [create an API key](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/api-keys). The user is `apikey`, the password is the API key, and **Send As Address** is your approved from address. |
| Outlook.com, Live.com and other free Microsoft mail | | Don't work for sending. |

![[email-o365-email-apps.png|400]]

**Send a test email** sends one to you with what is on screen.

## Related

[Settings](../context/settings.md) · [Scheduled Jobs](../context/G014.md) ·
[Send Pictures](../context/M09.md)
