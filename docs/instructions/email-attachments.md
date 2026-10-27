# Email Attachments

Email works both ways for attachments. Anyone can add attachments to Shipper by
email, and you can email a record's attachments to anyone from Shipper.

## Email attachments into Shipper

Drivers, inspectors, suppliers or your own staff from a phone can add attachments
by email. Older versions of ShipperXL Mobile's [Send Pictures](../context/M09.md)
use this too.

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

## Email attachments from a record

Every **Attachments** tab in the web app can email its files: on agreements, bills,
bookings, cargo, carrier contracts, companies and contacts, items, SKUs, assets and
inspections.

1. Tick the attachments to send, or tick **Select All**.
2. Click **Email Attachments**.
3. Fill in **To** and, if you like, **CC**. Type or paste addresses (separate them
   with commas, semicolons or spaces), or click the contacts button beside the field
   to choose a company and one of its contacts. A company with no contacts uses its
   own email address. An address that isn't valid shows in red.
4. **Subject** starts as the record, such as *Cargo ABCD1234567* or
   *Sales Order 123456*. Change it if you like.
5. Write the message. It can have bold, italic, underline, lists and links.
6. Click **Send**. Shipper says how many people it was sent to.

- **It comes from Shipper's mailbox,** the outbound address set up in
  [Sending email](email-attachments.md?id=sending-email) below, not your own.
  Replies go to you, and you get a copy (Bcc), so the email is in your own mailbox
  too.
- The attachments can come to 25 MB at most.
- **Download .eml** gives an unsent email with the attachments, To, CC, subject and
  message filled in. Open it in Outlook (classic Outlook opens it as a draft), check
  it and send it from your own mailbox, as ShipperXL Desktop's **Send** did. If
  outbound email isn't set up for your database, this is the only choice.

## Sending email

Shipper sends email, such as invoices, [scheduled job](../context/G014.md) emails
and [attachments emailed from a record](email-attachments.md?id=email-attachments-from-a-record),
through the **outbound** server in **Admin > Settings**. You need a mailbox that
supports authenticated SMTP, with OAuth2 or a password.

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
