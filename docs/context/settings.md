# Settings

Settings is your instance's own configuration: your company, its default currency
and weight unit, its logo, its email servers and its accounting defaults. It is the
web version of ShipperXL Desktop's options, and only instance and application owners
see it. It comes first under **Admin**.

## Things to know

- **One Save** writes every change on every tab. **Unsaved changes** shows until you
  save. If a save fails partway, what was saved before the failure stays saved.
- Only this database's own settings are read and written. A setting this database
  doesn't have uses the application's.
- Saving also removes this database's own company contact, origin port, help site
  and home site settings, so the application's apply.
- Your signature isn't here. It is on your own contact: see
  [Companies and Contacts](G008.md).

## General

- **Company** is always your own company. **Open the company** goes to it, to change
  its name, addresses or contacts.
- **Default Address** is the company address used on documents. Pick one, or add
  one from the picker.
- **Default Currency** is the currency new agreements take.
- **Default Weight Unit** is pounds or kilograms. Weights show in this unit across
  the app.
- **Company Logo** is printed on documents. Use a PNG or JPEG of about 250 x 75
  pixels. **Upload** stages it and **Remove** clears it, both kept when you save.
  With no logo, documents use the application's. Uploading needs a file store for
  the instance. Without one, the button is unavailable.

## Email

Shipper reads email from the **inbound** server (IMAP) and sends it through the
**outbound** server (SMTP).

- **Server:Port** is the server and its port, such as `outlook.office365.com:993`
  inbound or `smtp.office365.com:587` outbound.
- **Set credentials** signs in with Microsoft or Google in a new window, and fills
  in the user and an access token that renews itself. Finish signing in within two
  minutes. To use a password instead, remove the **OAuth2 sign-in** chip.
- **Other Mailbox** (inbound) is optional. **All email in it is processed and
  deleted.**
- **Send As Address** (outbound) is optional. A shared mailbox lets its members see
  what was sent.
- The inbound mailbox can never be the one outbound email is sent from, because its
  email is deleted. Shipper won't save settings where they match.
- **Test connection** and **Send a test email** try what is on screen, before you
  save.
- **MailChimp API Key** connects your MailChimp account for scheduled jobs that
  update MailChimp.

## Accounting

- **Default Item Code**, **AR Account for Invoices**, **Default Expense Account**
  and **Default Income Account** are the codes your accounting system uses when
  Shipper posts to it.
- **Send invoices by email when they are posted** emails each invoice once it is
  posted to the accounting integration, if one is set up.
- **Integrations** shows which of QuickBooks Online, Zoho Books and Stripe are set up
  for this instance. Support sets them up.

## Related

[Companies and Contacts](G008.md) · [Scheduled Jobs](G014.md) ·
[Units of Measure](G007.md)
