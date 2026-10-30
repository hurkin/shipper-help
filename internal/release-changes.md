# Release changes: shipper-windows client → shipper-ui

This compares the WinForms client (`shipper-windows/Client/Hurkin.Shipper.Client`) with this SPA for **agreements, bills, bookings/shipments, cargo, SKUs and inventory**. It covers fields that are missing or no longer editable, screens and actions that are gone, and changes in which records a user can find or open. It leaves out layout and cosmetic changes, and it doesn't list things the web adds unless they change what data is written.

**Sources.** WinForms: designer bindings and grid columns (`*.Designer.cs`), plus each form's `BindData`/`SaveData` and event handlers. Web: the pages under `src/pages/*` and the `report.*` procs behind the grids (`shipper-db/report/Stored Procedures`). The findings come from reading the code. None of them was reproduced against a database.

**Severity**
- **High:** data is written differently, a record can't be found or opened, or a security boundary changed.
- **Medium:** a field or action that users relied on can't be read or edited in the web.
- **Low:** a column, filter or convenience is gone, but the data can still be reached another way.

**Status.** Sections 1–7 list only the differences that are still open. Rows the web has caught up on, matching WinForms, have been removed. Differences that are deliberate gaps or exclusions are in section 8. Open items and decisions noted during development sessions, which aren't differences from the WinForms client, are collected in section 9.

---

## 1. Cross-cutting

| Sev | Change | Detail |
|---|---|---|
| Medium | **Notes: visibility flags** | Notes on agreement, bill, booking, party and carrier contract pages can be edited by anyone who may write the record and deleted with Delete on it. Still open: agreement notes are always saved with `ShowBuyer/ShowSeller/ShowShipTo = false` and booking notes with `IsProcessor = false`. `IsPublic` is deliberately gone (see 8.1). |

---

## 2. Agreements (PO, PC, SO, SC, Quote)

### 2.1 Agreement line (`AgreementItem`)

| Sev | Field / action | Detail |
|---|---|---|
| Medium | **Line notes** | WinForms added and edited notes on a line. The web adds header notes only (it does display existing line notes). |
| Low | `ContainerClassId` | WinForms picked a container class directly. The web derives it from the Container Type. A class is kept only when a saved type doesn't resolve one. |
| Low | Fulfillment tab | Gone: Work Order, Work Zone, Work Center, External Processor. Added: Scale Ticket and date. |
| Low | `AgreementId` (move a line to another agreement) | WinForms ddlAgreement was editable on a stand-alone line. The web can't move a line. |

---

## 3. Bills (Bills, Invoices, Credit Memos, Letters of Credit)

### 3.1 Bill header

| Sev | Field | WinForms | Web |
|---|---|---|---|
| Medium | `BillNumber` | Editable | Read-only after create |
| Medium | **Applies To links** (`BillLink` to agreements and shipments) | Added and removed on the bill | Read-only Related tab. Links are made only when an invoice is created or an LC is chosen on an agreement or booking |
| Low | LC "Notify" party | Labelled Notify Party | Labelled **Advising Bank**. Same column (`Notify_PartyId`) |

---

## 4. Bookings / Shipments

### 4.1 Booking fields

| Sev | Field | WinForms | Web |
|---|---|---|---|
| Low | Fulfillment grid | Gone: External Processor (`Processor_PartyId`), agreement number and type, processor/internal/buyer-seller memos | |

### 4.2 Screens not ported

None. Carrier Service Contracts are in the web under **Lists > Carrier Contracts** (2026-10-24).

---

## 5. Cargo

### 5.1 Cargo fields

None. External Processor is on General, under Tare Pounds (2026-10-27).

### 5.2 Cargo related data

| Sev | Change | Detail |
|---|---|---|
| Low | Fulfillment: assign a whole agreement | WinForms "choose/create a [type] Number → Make Assignment" assigned every line of an agreement at 0. The web adds one line at a time from a search. |
| Low | Fulfillment grid | Gone: agreement type and number, Buyer and Seller together, the three memos. |

---

## 6. SKUs

| Sev | Field / action | WinForms | Web |
|---|---|---|---|
| Low | SKU search | SKU, item, manufacturer, supplier, description, active | One search box plus Active/Inactive/All. Manufacturer and Description columns are gone. |

---

## 7. Inventory

| Sev | Change | Detail |
|---|---|---|
| Medium | **Move: no memo** | WinForms Move Inventory set `Note` from a memo. The web Move writes no note. (Backdating is done: Move has a Transaction Date.) |
| Low | Partial-barcode lookup | WinForms "Item Inventory by Partial Barcode" searched barcodes by fragment. The web ledger and balance look a tag up by exact barcode only. |

---

## Not compared in depth

Scale tickets, inspections, attachments, queues, documentation tasks and auto (template) work orders are present on both sides and were checked only at the field level. No material gaps showed. Traffic Center, work orders and parties are out of scope.

---

## 8. Deliberate gaps and exclusions

Differences from WinForms that are intended. They're listed so they can be explained to users, not fixed.

### 8.1 Cross-cutting

| Change | Detail |
|---|---|
| **Record-level permissions moved to the database; `RecordUser` grants are no longer honoured** | WinForms checked in the client (`DataUtils.GetObjectPermissions`). Now shipper-api tags each party-scoped user's connection (`include/caller_parties.py`, `caller_tag.py` → `security.GetCallerScope`), and the row-level security policy `security.PartyVisibility` filters Agreement, Bill, Shipment, Cargo, WorkOrder and ScaleTicket. Staff (anyone related to party 1) and owners see everything, as before. What's different: (1) `RecordUser` rows are ignored. WinForms used them to grant a party access to a record, or to set its level to Read/Write/Delete, and the web can't view or edit them either. (2) Visibility is all-or-nothing. A visible record gets the user's feature level; WinForms could cap it per record. (3) The rules are wider. A user also sees records they created, bookings where their party is carrier or forwarder, cargo they own or process, and work orders and scale tickets linked to visible records. (4) `ItemSKU` is deliberately unfiltered, where WinForms limited outside users to SKUs they supply or manufacture. If no instance uses `RecordUser`, (1) and (2) don't matter in practice. |
| Posted locking changed | Agreements: WinForms locked a posted agreement for everyone. The web lets an owner change Posted (and so unpost), and only an owner may set Posted. Bills: WinForms let an owner edit a posted bill in full. The web lets the owner change only Posted. |
| Notes are always public | The web no longer offers `IsPublic` on any note (WinForms offered it on bill and booking notes). shipper-api sets `IsPublic = 1` on every new BillNote, BookingNote, CarrierServiceContractNote, PartyNote and ShipmentNote unless the caller sends it; existing notes keep their flag. Decided 10-24. |
| Bill Clone saves at once | WinForms `OnClone` (`CopyBill`) opened an unsaved copy with a blank number. The web's **Clone** creates the bill (next number, or one typed), its lines and notes, and puts it in its type's starting queues; line Posted dates are cleared too. A letter of credit's clone also copies its `BillLC` row, which `CopyBill` didn't. |
| Fumigation Tool replaced | The Calaway custom plug-in (fumigated, opened, Cu plate, ready to ship on many containers) has no web form. Cargo **Bulk Edit** sets Container Type, Movement Type, Location, Carrier Status, Ready to Ship, Fumigated, Opened, Tested and Memo; it doesn't set the copper plate. |
| F3 search | WinForms F3 searched everything (`dbo.GetSearchResults`). The web's is **Search everything** in the header, on `/api/search/full`, from 3 characters. |
| Emailing attachments | WinForms `ucAttachments` **Send** wrote the ticked files into an unsent `.eml` (`Framework.Helpers.Email.Send`, X-Unsent, subject the form's title, body "TBD") and opened it in the user's mail client. The web's **Email Attachments** sends through Shipper: shipper-api `POST /api/email/outbound` with `attachmentIds` queues the stored files for shipper-svc (`keep: true`), from the instance mailbox (`MAILSENDSA`) with Reply-To and a Bcc to the user, HTML body cleaned with nh3, 25 MB in all. **Download .eml** (`POST /api/attachments/eml`) keeps the old way, with To, CC, subject and message filled in, and is the only choice when the instance has no outbound mail. Each file is checked as `/api/attachment/<id>/url` checks it. |

### 8.2 Agreements

| Change | Detail |
|---|---|
| Search filters removed | WinForms `GetAgreements3` filtered by number, reference, order date ±range, completion date ±range, buyer, seller, ship-to, buyer contact, seller contact, Approved only, Incomplete only, **SKU**, **Shipment**, cancellation date or Canceled only, expiration date or Expired only. The web has one search box (number, Reference 1/2, buyer or seller name), Fulfilled/Not Fulfilled, an Ordered (or Fulfilled) date range and Include completed. Searching by SKU, shipment, ship-to, contact, canceled, expired or approved is no longer possible. |
| `AgreementNumber` | Editable and required in WinForms. Assigned from the number scheme on create, then read-only. |
| `Currency_UnitTypeId` | Editable in WinForms. Set to the default currency on create. Not shown, not editable. |
| Own-side party (Seller on a sale, Buyer on a purchase) and its address | Any party and address in WinForms. Fixed to the company (CO_DEFAULT/CO_ADDRESS). Only the agent contact can be changed. |
| `ParentAgreementId` on a **Sales Contract** | Editable in WinForms (txtParentAgreementId visible for SC). The parent picker exists only for PO and SO. |
| Completed date permission | WinForms needed **Delete** level. Write level is enough. |
| Parent-contract consistency warnings | WinForms warned when a line's parent contract or line didn't match the header's. No warning. |
| Documentation tasks | WinForms: Sales Orders only (`SalesOrderDocumentationTasks`). Web: every sales-side type (SO, SC, Quote), gated by D001. |
| Shipments grid on a Sales Order | WinForms listed every shipment the order's lines were assigned or fulfilled to, with dates and Posted. The web Related tab lists bills only. |
| Line notes toggle | WinForms could hide line notes (`chkShowItemNotes`). The web always shows header and line notes together. |
| Line `Completed` | Editable in WinForms at Delete level. Not shown or editable. |
| **Other SKUs** on a line (`AgreementItemSkus`: SKU, Sequence, Quantity, Memo) | Whole grid gone. Existing rows are neither shown nor maintained. |
| **Quick Sale / Quick Sales** (`ucQuickSale`, `ucQuickSales`) | One-step sales order + line + optional matching purchase contract + optional cargo + invoice, and the list of quick sales. Not in the web. |

### 8.3 Bills

| Change | Detail |
|---|---|
| Bill line price lookup | A vendor bill (BILL) line takes its amount from the cost list (supplier, bill date), an invoice line from the price list (customer, bill date, currency, incoterm), when the item or Per changes. Credit memos and LCs look nothing up. WinForms used the price list for every bill type. |
| `Printed` isn't stamped or shown | WinForms set `Bill.Printed` the first time the Invoice or Commercial Invoice report was opened, and it was editable. The web never sets `Printed` and doesn't show it. |
| `ShipDate`, `Confirmed` | Editable in WinForms. Not shown, not editable. |
| Own-side party (Buyer on a bill, Seller on invoice/credit/LC) | Editable in WinForms. Fixed to the company. |
| Line `Posted` | Editable in WinForms. Not shown. |
| LC lines and `CommodityId` | WinForms showed commodity on LC lines. The web gives an LC no lines at all, so existing LC lines and their commodity can't be reached. |
| Search filters removed | WinForms `GetBills4` filtered by number, reference/advice no., buyer, seller, ship-to, bill/ship/printed/posted/completed/paid/due dates ±range, Not Posted, Not Printed, Not Completed, Not Paid, Agreement, Shipment and Pro Forma. The web has Open/Completed/Paid, a date range on the Completed and Paid views, and one search box (number, buyer, seller, references, LC reference/advice). |
| Default date window | Completed and Paid start six months back. |

### 8.4 Bookings / Shipments

| Change | Detail |
|---|---|
| ShipsGo updates are applied on arrival, without the IPI/DLV legs | WinForms `ucShipment.CheckNotes` read the sync's JSON `BookingNote`, asked the user, then applied the changes. Now `api.BookingUpdated` (called from `POST /api/bookings/<n>/notes`) applies them right away: carrier, POL/POD ports and dates, carrier status, vessel, voyage, and each container's type, status and carrier dates. It logs the change list as a `ShipmentNote` and no longer writes `BookingNote`. The IPI and DLV port and date updates are commented out in the proc, because ShipsGo misreports load and discharge. |
| `Shipment.Origin_PartyId` + address, `Shipment.Destination_PartyId` + address (place of receipt and delivery parties) | Editable in WinForms. Not shown, not editable. |
| Cargo grid on the booking | Gone: Delivered to Carrier, Ready to Ship, Unloaded. |
| Search filters removed | WinForms `GetBookings4` filtered by shipment number, booking number, origin port, destination port, shipper, carrier, forwarder, booking class, agreement, vessel, voyage, cargo/docs due, planned departure/arrival ±days, Not Departed, Not Arrived, booked/Not Booked, canceled/Not Canceled, completed/Not Completed, posted/Not Posted. The web has Loading/Departing/Arriving/Completed with a date range, Include canceled, and a search on number, carrier, vessel, voyage, release no. and B/L no. You can no longer search by shipper, forwarder, port, agreement or posted state. |
| Default windows | Arriving defaults to the last 30 days. A delivered booking that isn't completed and arrived earlier drops out of every default view until the user widens the dates. |

### 8.5 Cargo

| Change | Detail |
|---|---|
| `CargoContainer.Chassis` | Editable in WinForms. Not shown, not editable. |
| `CargoRailcar` row | WinForms created it when the container class is rail. Never created. |
| Search filters removed | WinForms `GetCargos2` filtered by shipment number, **booking number**, cargo number, scale ticket, manifest, **chassis**, **seal**, **Cu plate**, container type, **location**, available/loaded/unloaded/shipped/completed dates ±range, and Not Available, Not Unloaded, Not Loaded, Not Shipped, Not Completed. The web has Received/Incomplete/Finished, Include completed, a date range, work zone, work center, and a search on cargo number, shipment number, manifest, ticket, SKU and work order. You can no longer search by booking, chassis, seal, Cu plate, location or container type. |

### 8.6 SKUs

| Change | Detail |
|---|---|
| `Manufacturer_PartyId`, `Quantity2_UnitTypeId` (processed unit), `OrderLeadDays` | Editable in WinForms. Not shown, not editable. Left unchanged on save. |
| `Barcode` | Editable in WinForms. Read-only; generated on save. |
| **Recalculate inventory** (`RecalculateInventory`) | Button gone. |

---

## 9. Open notes from development sessions

These aren't differences from the WinForms client. They're the caveats, choices and suggestions raised at the end of Claude Code sessions (2026-10-09 to 2026-10-30, every repo under `hurkin/`), kept here because the session transcripts are the only other place they're written down. Items later fixed have been left out. Each says when it was raised; "decide" marks a choice that is yours to make.

### 9.1 Choices made in the web app that you may want changed

| Area | Note | Raised |
|---|---|---|
| Carrier contracts | Rates and Fees are one grid: a row per rate, a column per fee name, base rate and fees typed in place, Set Fee and Remove on ticked rates. Fees take Per Container, Rate %, Per Booking and Booking %, on the contract and on a rate (in the rate dialog; cells typed in the grid and Set Fee are amounts only). A rate fee's Memo isn't shown (no rows on CALTEST). A fee with no amount isn't stored, a fee name is once per rate, and freight classes are saved once each; existing duplicates and zero-amount rows are left as they are until that rate's fees change. Removing a rate needs Write on B009, as in WinForms. | 10-24 |
| Carrier contract amendments | **New Amendment** puts the copy under the chain's master (the root), not under the contract it was made from, so no new grandchildren (281 on CALTEST). It copies rates, their fees with an amount and their freight classes once each, and the contract's fees; not notes, attachments, Minimum TEUs or Memo, as WinForms. **Master Contract** on General offers the same carrier's contracts; shipper-api refuses the contract itself or one of its amendments. *Decide* whether a contract that has amendments may be given a master (its amendments then sit two levels down). | 10-24 |
| Carrier contract delete | Refused while a booking uses one of its rates (WinForms deleted it and those bookings lost their rate) or while it has amendments. Decided 10-24: keep refusing. There's no Related > Add Child Contract; use New and pick the Master Contract. | 10-24 |
| Carrier contract SQL | The list, detail, save, amend and delete SQL is constant text in shipper-api (`include/carrier_contracts.py`), as Assets is, not shipper-db procs. There's no reports button on the contract page yet. | 10-24 |
| SKU ledger lines | Add and edit need I004 at Delete; others open a line read only. The SKU, unit and total weights (the trigger recalculates them), the bill line and the moved-from line can't be changed. There's no Delete on a line. *Decide* whether the bill line and moved-from line should be editable, and whether to offer Delete. | 10-24 |
| Agreement Related tab | Lists the agreements drawn from this one by their header or by any line naming it (many sales orders name their contract on lines only), one level down: a contract copied into another contract shows, but that contract's orders don't. The line dialog's Fulfilment tab is the same, one level down. | 10-24 |
| Booking class | A booking in a class other than ocean shows no sea details, and saving it deletes its `BookingSea` row (shipper-api, in the save's transaction). Existing non-ocean bookings that still have one (175 Land on CALTEST, booking S0032481 as Air) show a warning and lose it on their next save from the web. The rate lookup runs only for ocean bookings; another class keeps its saved rate and free time. Watch Shipline stays offered, but the ShipsGo procs (`api.BookingUpdated`, `api.UpsertSchedule`) inner-join `BookingSea`, so they skip non-ocean bookings. New Booking offers the class, starting at Ocean Vessel each time. General shows only IPI and DLV for such a booking: POL and POD and their dates are hidden but kept, and POL's cutoff (`Booking.CargoDue`) shows under IPI, above Departs, as Cargo Due. On every booking each cutoff now sits above its departure, though the Bookings grid still shows them and its Loading view still goes by the POL departure. **Open:** the IPI cutoff is `BookingSea.RampDue`, so a non-ocean booking has only Cargo Due (none of the 177 non-ocean bookings with a `BookingSea` row on CALTEST has a RampDue); to be solved in a later session. | 10-24 |
| Booking free time | Shown on General beside Receiving only while a freight rate is chosen: the rate's origin and destination memo, else its contract's, "None on the rate or its contract" when neither has one. | 10-24 |
| Booking freight rate | The rate lookup matches on the shipment's IPI and DLV locations and the POL departure, as WinForms `ucShipment` did, not on the POL and POD ports. | 10-22 |
| Booking freight rate | Without a freight class the lookup still runs, but finds only rates not limited to particular classes. WinForms refused to look up without one. | 10-22 |
| Agreement delete | Refused in more cases than "a line has fulfillments": also posted, cargo contents loaded against a line, orders drawn from it, linked bills or invoices, generated documents (as booking and bill deletes do). | 10-22 |
| Bill line lookups | The Agreement Line lookup offers purchase orders and contracts on a vendor bill and sales orders and contracts on an invoice or credit memo; sales quotes aren't offered. The Cargo lookup searches cargo, booking, manifest, ticket, SKU and work order numbers, completed cargo included, and shows the first 250 matches. | 10-22 |
| Bill line amounts | A found cost or price replaces the amount whenever the item or Per changes, even a typed amount; opening a saved line never re-prices it. | 10-22 |
| Booking Status | The carrier Status on the General tab is free text. The mockup showed a dropdown; it needs a fixed list of values. *Decide.* | 10-20 |
| Custom characteristics | Inactive fields are hidden but keep their saved values. Cloning an item or SKU doesn't copy them. A blank number is stored as NULL (WinForms stored 0). | 10-12 |
| Assets | The asset pickers on work orders, agreement lines, bill lines and SKUs show only with T001 read; without it a line's existing asset is left as is on save. | 10-15 |
| M08 Inbound Inspection | Mobile M08 is treated as I008 at Write: it reads and saves inspections but can't delete them. *Decide* whether it should delete. | 10-15 |
| Work order movement button | No button on Transfer work orders (no screen for them); hidden on posted ones; disabled while the work order has unsaved changes. | 10-10 |
| Auto Work Orders | A process work order that later gets a cargo creates that cargo's Auto Work Orders. | 10-17 |
| Auto Work Orders movement | A template is created only on cargo of its own movement type (Inbound on inbound, Outbound on outbound, Outbound from Supplier on direct-ship, Process on process-only); Create Work Orders on a line asks for the movement type and offers only those templates. Before, every template went on every cargo, and a Process one took the cargo's movement. Templates set up as Process (including any made in Windows without a movement) now go only on process-only cargo, so check existing agreements' templates when shipper-db is deployed. | 10-27 |
| Error messages | 57 places still show a fixed message ("Save failed") instead of the server's sentence. Switching them changes what users see. | 10-10 |
| UI conventions | The consistency pass of 10-24 made every screen follow one pattern, written down in shipper-ui `AGENTS.md` ("UI conventions"). Choices in it you may want changed: dialogs that only stage a change until the page's Save (the contract rate, document type field and lookup translation dialogs) now say **Save**, not OK (*decide* whether Apply reads better); the RateList and Contract Rates row removals keep their confirmation, since one deletes at once and the other warns which bookings lose their rate; lists choose their page size from the window, so it differs between screens and users. Agreement **Copy** is now **Clone** (Copy To in WinForms). | 10-24 |
| Parties | A party has an **Active** box on General, and the Companies and Contacts lists show Active / Inactive / All. `api.GetParties` still returns active parties only unless `@Active` is passed, so the pickers and the Windows and mobile clients don't offer an inactive party; a record that names one still shows it (`/api/party/<id>?Active=all`). | 10-24 |
| Bill Clone | Same type only. Lines keep their agreement line and cargo, as WinForms did, so a cloned cargo bill can bill twice; the dialog warns. A letter of credit's clone copies its bank parties and details but clears ReferenceNumber, AdviceNumber and NumberOfAmendments. *Decide* whether lines should drop those links. | 10-26 |
| Agreement parties | Our side (Buyer on a purchase, Seller on a sale) is the first Parties row: the party fixed, its address and the agent. An agreement saved without our side's party or address takes CO_DEFAULT (else party 1) and CO_ADDRESS as it opens, which marks the page as unsaved until Save. Ship To's **Same as buyer** on a purchase copies our side. | 10-26 |
| Party column | Fulfillment and agreement-line rows (booking and cargo Fulfillment, SKU and asset Related) show one **Party**, the counterparty by agreement type, instead of Buyer and Seller. Bill item rows on asset Related still show both. | 10-26 |
| Search everything | Results come in `dbo.GetSearchResults`' order, once per record. Rows with no web page are left out: `dbo.Booking` rows (B002) and documents (D001). The term is sent as a prefix (`"text*"`), as BookingPicker does. Work orders (W001) need shipper-db `c12cd29`; without it they aren't found. | 10-27 |
| Cargo Bulk Edit | Fumigated, Opened and Tested go only to cargo whose container type is a container's, and Ready to Ship only to outbound and process cargo, judged by the type and movement set in the same edit. Cargo on a posted shipment is skipped, owners included (as the cargo page). No queue or note, unlike bookings; Memo replaces. | 10-26 |
| Party Tax ID and opt-ins | Tax ID, Transactions Opt-In and Marketing Opt-In are `dbo.Party` columns, so contacts have them too; a new party is opted in to both, as the column defaults. | 10-26 |
| Reports | The Reports nav entry shows for everyone, even with no report features. `List.ashx` caches each session's list for 5 minutes. | 10-15 |
| Custom reports | The web ignores CUSTREPS (Desktop still needs it to show any custom report): a custom report needs only the feature in its Description, and one with no Description is open to everyone. One whose Description is a standard report's mnemonic (spaces and case ignored) replaces it and takes its feature name, with a **Custom** chip. Every hand-off passes `p:WEBURL` (origin + `/shipper`). | 10-27 |
| Work order Assigned Inventory | The tab holds the work order's `ItemInventory` rows with no transaction date (ucWorkOrder's assigned SKUs). They stay the work order's when it goes on a cargo, so the tab stays editable there, and they no longer show on the Inventory tab of a work order with no cargo. | 10-27 |
| Booking queues | A booking queue lists `report.BookingGrid @QueueId` rows in the Bookings grid's columns, so cutoffs show with their time and departure and arrival are actual else planned. ERD (Earliest Receiving), Pickup, Ramp Due, LRD, Forwarder, Memo and Notes are hidden at first; Receipt, Delivery and Planned Arrival are gone (POL, POD and DLV replace them). WinForms keeps `dbo.GetQueueBookings`. | 10-27 |
| External Processor | Edited in place on the cargo, work order and booking Fulfillment grids, with Work Zone and Work Center, and written to both the assignment and fulfilment of a row. The cargo's own is on General, under Tare Pounds; saving the cargo's grid after a processor edit there resets it, as WinForms did: the first row that differs from the cargo's, a fulfilment over an assignment. The line dialog's Fulfilment tab shows it read-only. | 10-27 |
| Email Attachments | On every Attachments tab (agreement, asset, booking, cargo, carrier contract, bill, inspection, item, party, SKU). Anyone who can see the tab may email its files; there's no feature of its own. Subject starts as the record's title. To and CC take typed addresses or a company's contact (the company's own email when it has none). The From line comes from `GET /api/email/sender`. A file that can't be read fails the send (shipper-svc) rather than going out without it. | 10-27 |
| Session sharing between tabs | A tab opened from a link in the app takes the session of the tab it came from over a BroadcastChannel; a bookmark or typed address lists the open sessions as **Continue as** on the login page. Logging off signs out every tab on that session. | 10-27 |
| Staff parties | A party related to PartyId 1 either way is staff. shipper-api (`9d6744f`) lets only an owner change Email or Active on one (and a contact's Other Email), and refuses a non-owner staff member any change to another staff member's party, its addresses, categories, notes and relations. shipper-ui follows it: Email and Active greyed with "A staff sign-in - only an owner changes it", no Convert, another staff member's party read-only ("Staff member - owners only"), no Remove on a relation to the company or (for staff) another staff member, and Add Relation / Add Contact refuse those before saving. Documentation tasks and attachment uploads on a staff party stay open, as shipper-api allows them. Whether a party is staff comes from its own relations; for staff users also from the company's contacts list, read once per sign-in. | 10-27 |
| Document type SQL | Only an owner writes `DocumentType.Sql` (shipper-api `9d6744f`); Admin > Document Types shows it read-only to others, who can still save the rest. Fill Fields runs it under the user's row-level security on a connection that is rolled back and dropped. | 10-27 |
| Agreement own side | The Buyer on a purchase and Seller on a sale start as the company. Someone with Delete on the agreement (and write, not posted) can name another party; that clears its address and agent, and clearing the party puts the company back at its default address. shipper-api doesn't check this; any writer could set it through the API. | 10-28 |
| System message | `SYSMSG`'s three values run together without a separator, as WinForms does, in an amber bar under the app bar; not shown in embedded tabs. Closing it hides that text on that device (localStorage) until the text changes. The session is re-read every 30 minutes, and only replaced when it changed. | 10-28 |
| Admin > Settings, Accounting | Integrations status follows the form as typed. QuickBooks is configured once `AI_ACCESS` has a refresh token and realm, which **Connect to QuickBooks** sets through shipper-svc (`/svc/qbo/connect` and `/svc/qbo/callback`, svc da910ff, ui 1e0c633). The page no longer shows `AI_APP` (Environment, Client Id, Client Secret) or `AI_DSN`'s Base URL; `AI_APP` is assumed to exist on every instance and the redirect URI to be registered on its Intuit app. Another svc replica's cached session (up to 120s) can write the old tokens back after a connect; connect again if it happens. Data Center blank means `com`. Webhook slugs have a Generate button and show the full `/svc/webhook/{zoho,stripe}/{INSTANCE}/{slug}` URL. `AI_ITEM` is item code, expense, income everywhere, shipper-svc included from `fc4363f` (it read Setting1 as the income account before). Check that no QBO tenant's `AI_ITEM` was entered in the old svc layout, with an account name in Setting1. | 10-28 |
| Agreement line Variable Costs | As ucAgreementItem: Amount (required), per (blank is a flat amount), Item, Company, Note, Auto Bill on every agreement type and Auto Invoice on all but purchases; a sale's costs used to be saved with Auto Bill cleared. A line's cost carries `AgreementItemId` alone (CC_PriceComponent1). The cost per unit and total estimated cost follow `gridPriceComponents_DataBindingComplete`, converting through `dbo.UnitTypeConversion`; a cost in a unit outside the Per unit's class and not the line's Unit Type is left out. **Copy From Other Line Items** copies from any saved line (btnCopyEstimates copied line 1's) and skips costs the line already has (ui 73caafa, b89f03b). | 10-29 |
| Dashboard | A card per menu section, a 100% bar per grid under its statuses, a segment opening the grid on that status. Queue counts are each node's Queues page's for the user, and Overdue is within Queued now; when `/api/queues` fails the card says the counts are unavailable. The Inventory card is hidden for now (`hidden: true` in `dashboardConfig.js`) (ui 73caafa, 5a63b9c). | 10-29 |
| Search everything | Also offers the queues on the user's Queues pages, each once, opening on its first node; dropped when the session or Q001 level changes (ui 73caafa, b89f03b). | 10-29 |
| Sign-in machine name | The web sign-in sends the page's host as `machineName` and the email as `networkName`, so HAAL's sessions and license authorizations name the deployment and a new IP or browser isn't counted as another device (MaxMachines) or user (MaxUsers with UseNetworkUser) (ui 73caafa). | 10-29 |
| Cargo warnings | ucCargo's checks as warnings on the cargo page: a warning icon on the tab, and the tab lists them; none blocks a save. Rules as tmrValidation_Tick, except Incomplete weight shows until both weights and dates are in (Windows only with neither), the contents check sums each ticket's net (Windows' `Gross ?? 0 - Tare ?? 0` summed the gross) and "No contents" for a non-outbound cargo goes on General. After a save, api.ValidateCargo's shared numbers and, for a ticket weighed and changed in the last 20 minutes, dbo.GetItemWeightStats by the OPT1 setting. The scale ticket checks are skipped for a user who can't read scale tickets. Unassigned Work Order needs shipper-db `2054750` (`report.CargoWorkOrders` IsWorkerRequired); until it is deployed only a work order with no item counts (ui, not yet pushed). | 10-30 |
| Vehicle tare | Choosing a vehicle whose Reference 1 is TARE and Reference 2 a whole weight fills in an empty or 0 tare, Tare Weighed now, and appends " manual tare <weight>" to Driver / Memo, as ucMiniScaleTicket. Unlike Windows, choosing another vehicle (or none, or another drayman) before saving takes back the tare it filled in, unless the tare was weighed or typed since, and the vehicle no longer sets the drayman. Needs shipper-db `b11e1f2` (`dbo.GetAssets` returns Reference1/2) deployed; until then no vehicle carries a tare (ui, not yet pushed). | 10-30 |
| Dashboard access line | "Database: X" sits beside the help icon; beneath the welcome, a party-scoped user reads "You have access to A and B." or "You aren't linked to any company." plus "You see the records you created and those that name you". `/api/me/access` tells a company from a person by its class, since a company converted from a contact in Windows keeps its PartyPerson row (Sprint Forwarders on CALTEST) (api 7d0d61a). | 10-30 |
| Terminology | The web app says "database" for the HAAL instance everywhere a user reads it, including the sign-in's Database field. | 10-30 |
| Caller scope age | shipper-api calls `security.GetCallerScope` with `@MaxAgeSeconds 360`, so a record linked to or unlinked from a party-scoped caller's parties can take up to 6 minutes to show or hide for them (api fdffb6d, ee46d8d). Documented in the user accounts guide. | 10-29 |

### 9.2 Loose ends and things to check

| Area | Note | Raised |
|---|---|---|
| shipper-ui | `/inbound/workorder/:id` (`InboundCargoDetailPage`) is an unlinked prototype whose Inspections tab shows two made-up inspections from `api/stubs.js`. Remove it or point it at the work order's cargo. | 10-15 |
| shipper-db | `f6ebd7f` (`api.GetParties @Active` and IsActive, `api.GetItems @Active`, audit columns on `report.BookingGrid`, `AgreementGrid`, `CargoGrid`, `BillGrid`) is deployed on CALTEST only. shipper-ui from 211f066 on needs it on every instance before it ships: without it every party lookup by id fails. | 10-24 |
| shipper-db | `d311988` (`api.GetActiveSkus` finds a SKU containing the search text; before, exact only) is pushed to dev, not yet deployed. | 10-26 |
| shipper-db | `c12cd29` (full-text index on `dbo.WorkOrder.WorkOrderNumber`, `dbo.GetSearchResults` returns W001 rows) and `13fe5a1` (`report.AgreementGrid`: a contract fulfilled through its orders is on Fulfilled, and every agreement is on exactly one of Not Fulfilled and Fulfilled) are pushed to dev, not yet deployed. | 10-27 |
| shipper-db | `bfc635d` (`report.BookingGrid @QueueId`; External Processor on `report.CargoFulfillment`, `ShipmentFulfillment` and `AgreementItemFulfillment`) is pushed to dev, not yet deployed. shipper-ui's booking queues read `report.BookingGrid @QueueId`, so they fail to load until it is deployed; the External Processor column stays blank until then. | 10-27 |
| shipper-db | `33cd258` (a deactivated user with no other active contact gets an empty scope instead of coming back as staff; `api.DeleteAgreement` also deletes the agreement's unworked Auto Work Order template work orders) and `0066ba6` (dashboard tiles count what their grids show) are pushed to dev; check they are deployed with 2026.4. | 10-27 |
| shipper-ui | `5d73ccf` (Email Attachments) needs shipper-api `f554d35` and shipper-svc `6cc0815` (html_body, reply_to, bcc, `keep` attachments, percent-encoded blob names) deployed with it; until then Send fails, though Download .eml needs only shipper-api. | 10-27 |
| shipper-api | `fdffb6d`/`ee46d8d` (one connection pool per database, no ping per checkout, orjson responses) want shipper-db `f8be4e6` (`security.GetCallerScope` seeks and rewrites only what changed) for the cheaper scope refresh; it runs against the older proc too. `f8be4e6` is pushed to dev, not yet deployed. | 10-29 |
| shipper-ui | Recent items: records that open only in a dialog (a line item) can't be reopened from the list. | 10-20 |
| shipper-ui | In a tab left open across a deploy, Excel export does nothing and shows no message (its chunk is gone). | 10-22 |
| shipper-ui | Per-route lazy loading wasn't done; it's the largest remaining startup saving, but needs reload-on-chunk-error handling. Only worth it if first loads are reported slow. | 10-22 |
| shipper-db | `security.GetCallerScope` decides a matched party is a person by a PartyPerson row, not its class. A company converted from a contact in Windows keeps that row (Sprint Forwarders, 1316, and SPRINT FORWARDERS, INC. - CA, 1317, on CALTEST), so a sign-in email on such a company would be widened to every party related to it. Suggested: test the PERSON class, as `/api/me/access` now does. *Decide.* | 10-30 |
| shipper-db | `b11e1f2` (`dbo.GetAssets` returns Reference1 and Reference2, for the vehicle tare) and `2054750` (`report.CargoWorkOrders` IsWorkerRequired, for the cargo warnings) are pushed to dev, not yet deployed. | 10-30 |
| shipper-ui | `src/auth/shp-features.tsv` still lists D002, I007 and G009 as HIDDEN. Once the table is re-dumped, `features.test.js` fails until they move to UI. | 10-09 |
| Editions | Owners are trimmed to their edition. Not verified: whether HAAL sends an owner the edition's full feature list; if it sends few, owners lose features. | 10-15 |
| Row-level security | Reports go through the WCF/SSRS path, so they still show every record to party-scoped users. Every instance is scoped since shipper-api `8dc36ef` (`PARTY_SCOPED_INSTANCES` is gone), owners included: an owner who isn't one of the company's contacts sees only their parties' records. | 10-09, 10-27 |
| shipper-api | The ORM caches its table model in a file named after `dbo.DBVersion` only, so a schema deploy that adds a column without a version bump leaves the API on the old model (`model_<version>.pkl` has to be deleted). Suggested: key the file on the version plus `max(modify_date)` from `sys.tables`. | 10-17 |
| shipper-api / cluster | Intermittent 503s from `istio-envoy` when gunicorn closes idle keep-alive connections. Suggested: gunicorn `--keep-alive 75`, a DestinationRule with `idleTimeout: 60s` for `shipper-api-service`, optionally CORS `max_age=600`. | 10-10 |
| Performance | `dbo.ReportShipmentInventoryCost` couldn't return 200 rows within 10 minutes on CALTEST. History tables have no index on the parent's key, so the History dialog scans them (2.4 s for a busy shipment). | 10-15 |
| `dbo.Archive` | The loop meant to unlink related bills clears the wrong bill's `Related_BillId`, so old bills another bill points at are never archived. Not fixed when raised. | 10-17 |
| Schedule sync (`api.UpsertSchedule`) | Bookings with neither a planned departure nor a voyage still match on the vessel name alone. shipper-svc doesn't pass the file's date, so an old schedule file can overwrite a cut-off a user corrected later. The job writes only with `mode=apply`, and says nothing when no queue has the flags set. The schedule file should be regenerated daily. | 10-19 |
| Sign-in log | After a dev deploy, check a web sign-in row in HAAL: a `MachineName` of "Internal/External-Unknown" means the ingress isn't forwarding the client IP (`X-Real-Ip`). | 10-22 |
| HAAL | `dbo.GetUserData` returns the row for a key from every user (an `or` branch), and `GET /api/user/<UserId>/data/<Key>` needs no authentication; with Recent items stored under a guessable key, anyone could read others' lists. Suggested: serve only GUID-shaped keys on that route. *Decide.* | 10-20 |
| HAAL | Forgot-password, request-access and signup pages don't read `?email=`, so users retype the address shipper-ui already has. | 10-13 |
| HAAL instance create | shipper-api's refusal reaches the user as "Creating a new database failed." rather than the real reason; a timeout or connection failure leaves the HAAL instance behind; dev still has the `custom.CreateInstance` stub. | 10-16 |
| HAAL SQL Server | The prod SQL Server pod was preempted by an istiod rollout. The maintenance window only moves the restart; a dedicated database node (taint + toleration) prevents it, and haal-api could retry `08001` with a short backoff. Dev lacks the `aksManagedAutoUpgradeSchedule` window. | 10-19 |
| shipper-windows | The `FeatureExpansion` changes (2026.4g, 4h, 4i: D002, I007, G009, G010, I009, G014, G007, W003 kept as records; S030 from G010; G007B for everyone) were never compiled. Build on Windows before shipping. | 10-09, 10-10 |
| shipper-help | Six reports have only a stub (R112, R134, R198, R199, SQL-AGR, SQL-SHP). There's no mobile app source, so the mobile pages are inferred; M09 may no longer need inbound email. No pages for reports, flags, other mobile features or retired line-item features. Hardware page settings are for the TLP 2824 Plus, not the recommended ZD411t. Retiring support.hurkin.com needs Desktop's `HELPURL` changed to `https://hurkin.github.io/shipper-help/#/context/{mnemonic}`. | 10-12 to 10-20 |
