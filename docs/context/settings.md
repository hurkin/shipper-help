# Settings

Settings is your database's own configuration: your company, its default currency
and weight unit, its logo, its email servers and text messaging, and its
accounting and payment integrations. It is the
web version of ShipperXL Desktop's options, and only database and application owners
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
  the database. Without one, the button is unavailable.

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

### Twilio

Twilio sends Shipper's text messages (SMS): Stripe payment and autopay links, and
scheduled jobs that send a text. Find all three values in the
[Twilio Console](https://console.twilio.com), under **Account Info**.

- **Account** is the Account SID, starting `AC`.
- **Secret** is the Auth Token.
- **Sender** is the Twilio phone number texts come from, written with its country
  code, such as `+15035550100`.

Leave them blank and Shipper sends no texts.

## Accounting

Shipper copies invoices and bills to one accounting package, QuickBooks Online or
Zoho Books, and payments back from it. Stripe can collect invoice payments with
either. See [Accounting Integration](../instructions/accounting-integration.md) for
what is copied. Support can set these up with you.

Changes reach the integrations within a few minutes of saving.

### Integrations

The top of the tab shows whether each of QuickBooks Online, Zoho Books and Stripe is
set up, and what it still needs. It follows the fields as you type, before you save.

- An integration is on as soon as it is set up, and off when it isn't. There is no
  separate switch. Zoho Books and Stripe are set up by filling in their credentials;
  QuickBooks Online by connecting your QuickBooks company (below).
- If both QuickBooks Online and Zoho Books are set up, only QuickBooks Online is used.
  To use Zoho Books instead, ask support to disconnect QuickBooks Online.

### Sending invoices

**Send invoices by email when they are posted** emails each invoice to the customer
once it is posted to the accounting integration, with its Stripe payment link if
Stripe is on. Unticked, Shipper doesn't contact customers about invoices at all, by
email or text, and Stripe starts no new charges. Invoices are still posted.

### QuickBooks Online

Item and account fields hold **names** as they appear in QuickBooks. A name
QuickBooks doesn't have falls back to its first account of that type. An item's own
external income or expense account in Shipper wins over these defaults.

- **Default Item Code** is the QuickBooks item used on an invoice line that has no
  Shipper item, or whose item can't be copied. Blank, the item is named after the
  **Income Account**, or `Services`. It is created in QuickBooks if missing.
- **AR Account for Invoices** is the accounts receivable account on every invoice.
  Blank uses QuickBooks' default.
- **Expense Account** goes on items Shipper copies and on every bill line.
- **Income Account** goes on items Shipper copies, and on the default item.

**Connect to QuickBooks** links Shipper to your QuickBooks company:

1. Save any changes first. The button waits until there are none.
2. Select **Connect to QuickBooks**. QuickBooks opens in a new window.
3. Sign in to QuickBooks, choose your company and allow the connection. The window
   says when it is connected, and you can close it.

Back in Settings, the section shows the company it is connected to (QuickBooks'
company ID). Finish signing in within five minutes. If your browser blocks the new
window, allow pop-ups for Shipper and try again.

Use **Reconnect to QuickBooks** to connect a different company, or if QuickBooks
stops accepting Shipper's connection, for example after a long time unused or after
the connection was removed in QuickBooks. Only one company is connected at a time.

### Zoho Books

Zoho Books needs no separate connection step: the Organization Id, Data Center,
Client Id and Client Secret are all it takes.

- **Organization Id** is in Zoho Books under **Settings > Organization Profile**, and
  in the address bar when you are signed in to Zoho Books.
- **Data Center** is where your Zoho account lives: `com` for zoho.com, `eu` for
  zoho.eu, and so on. Blank means `com`.
- **Client Id** and **Client Secret** come from a **Self Client** made in the Zoho
  API Console for the same data center (api-console.zoho.com, api-console.zoho.eu
  ...), on its **Client Secret** tab. Choose Self Client, not Server-based.
- **Payments Account** is the bank account customer payments are deposited to, such
  as `Checking`. Blank, or a name Zoho Books doesn't have, deposits to Undeposited
  Funds.
- **Income Account** goes on items Shipper creates in Zoho Books. An item that
  already exists keeps its own.
- **Expense Account** goes on every bill line.
- **Webhook Signing Secret** and **Webhook URL Slug** let Zoho Books tell Shipper
  about a payment as soon as it is made. Without them, payments still come across on
  the hourly check. To set it up:
  1. Generate a slug with the button in **Webhook URL Slug**, then copy the webhook
     URL shown under it.
  2. In Zoho Books, open **Settings > Automation > Webhooks** and add a webhook to
     that URL for payments created and updated. Send it as **parameters**, not a raw
     JSON body.
  3. Copy Zoho's signing secret into **Webhook Signing Secret**, and save.

### Stripe

Stripe collects invoice payments by bank debit (ACH in the US, pre-authorized debit
in Canada) or card, and records them in whichever accounting package is set up.

- **Secret API Key** is in the Stripe Dashboard under **Developers > API keys**. It
  starts `sk_live_` (or `sk_test_` for a test account). Blank turns Stripe off.
- **Webhook URL Slug** and **Webhook Signing Secret** let Stripe tell Shipper when a
  payment succeeds, fails or is returned. To set them up:
  1. Generate a slug with the button in **Webhook URL Slug**, then copy the webhook
     URL shown under it.
  2. In the Stripe Dashboard, open **Developers > Webhooks**, add an endpoint at that
     URL, and choose these events: `payment_intent.succeeded`,
     `payment_intent.payment_failed`, `invoice_payment.paid` (or `invoice.paid`),
     `payment_method.attached`, `payment_method.detached`, `charge.refunded`,
     `charge.dispute.created` and `radar.early_fraud_warning.created`.
  3. Copy the endpoint's signing secret, which starts `whsec_`, into **Webhook
     Signing Secret**, and save.
- In Stripe, turn on ACH Direct Debit (USD), Pre-authorized debit (CAD) and cards
  under **Settings > Payment methods**. If a Stripe-to-QuickBooks sync app is
  installed, turn off its payment creation, so only Shipper closes invoices.

## Related

[Companies and Contacts](G008.md) · [Scheduled Jobs](G014.md) ·
[Units of Measure](G007.md)
