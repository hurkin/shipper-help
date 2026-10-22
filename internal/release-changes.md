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
| Medium | **Notes: delete and visibility flags** | Clicking a note opens it for editing on agreement, bill, booking and party pages for anyone who may write the record, and agreement notes can be deleted at Delete level. Still open: bill, booking and party notes can't be deleted (WinForms had Remove). Visibility flags are lost: agreement notes are always saved with `ShowBuyer/ShowSeller/ShowShipTo = false`, booking notes with `IsPublic = false`, `IsProcessor = false`. Only bill notes keep `IsPublic`. |

---

## 2. Agreements (PO, PC, SO, SC, Quote)

### 2.1 Agreement related data and actions

| Sev | Change | Detail |
|---|---|---|
| Medium | **Child-orders grid on a contract is gone** (`gridRelated`) | WinForms listed the orders drawn from a contract. The web has no view of a contract's call-off orders. |
| Low | Line-item grid | WinForms edited Ordered, Non-Inv SKU, Price, Reference, Cust/Sup Ref and Completed inline and showed Assigned, Fulfilled, Price Per, Processor/Internal/Buyer-Seller memos. The web grid is read-only (edits go through the dialog) and shows none of Assigned, Fulfilled, Price Per or the memos. |

### 2.2 Agreement line (`AgreementItem`)

| Sev | Field / action | Detail |
|---|---|---|
| Medium | **Line notes** | WinForms added and edited notes on a line. The web adds header notes only (it does display existing line notes). |
| Low | Copy price components from line 1 (`btnCopyEstimates`) | Gone. |
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
| Medium | Origin/destination free-time memos under the contract rate | Shown | Not shown. The Estimated Freight Rate on the Freight tab otherwise covers the rate lookup |
| Low | Fulfillment grid | Gone: External Processor (`Processor_PartyId`), agreement number and type, processor/internal/buyer-seller memos | |

### 4.2 Screens not ported

| Sev | Screen | Detail |
|---|---|---|
| Medium | **Carrier Service Contracts** (`ucCarrierContract(s)`, `ucCarrierContractRate`) | Contracts, rates by container class/type and port pair, fees, minimum TEU, free time. Not in the web. Bookings can pick a rate (Estimated Freight Rate), but contracts and rates can't be maintained. Freight Classes exist in Admin. |

---

## 5. Cargo

### 5.1 Cargo fields

| Sev | Field | WinForms | Web |
|---|---|---|---|
| Medium | `Cargo.Processor_PartyId` (External Processor) | Editable | Set only when the cargo is created. Not editable afterwards |

### 5.2 Cargo related data

| Sev | Change | Detail |
|---|---|---|
| Low | Fulfillment: assign a whole agreement | WinForms "choose/create a [type] Number → Make Assignment" assigned every line of an agreement at 0. The web adds one line at a time from a search. |
| Low | Fulfillment grid | Gone: External Processor, agreement type and number, Buyer and Seller together, the three memos. |

---

## 6. SKUs

| Sev | Field / action | WinForms | Web |
|---|---|---|---|
| Medium | **Inventory adjustment** from the SKU (I012, new `ItemInventory` row) and **edit an existing ledger row** (`ucItemInventory`: barcode, note, location, cargo, work order, date, quantities, sequence) | Present | Gone. The ledger is read-only, and inventory changes only through Receive/Return/Move/Ship/Process and Physical Inventory. Feature `I012` is defined but unused |
| Low | SKU search | SKU, item, manufacturer, supplier, description, active | One search box plus Active/Inactive/All. Manufacturer and Description columns are gone. |

---

## 7. Inventory

| Sev | Change | Detail |
|---|---|---|
| Medium | **Move: no memo** | WinForms Move Inventory set `Note` from a memo. The web Move writes no note. (Backdating is done: Move has a Transaction Date.) |
| Medium | No single-transaction editor | See SKUs: `ucItemInventory` (edit or adjust one `ItemInventory` row) isn't ported. |
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
| No Clone/Copy for bills | WinForms `OnClone` copied a bill (`CopyBill`). The web clones agreements and bookings only. |

### 8.2 Agreements

| Change | Detail |
|---|---|
| Default date window | The grids start at six months back on Ordered (or on Last Fulfilled in the Fulfilled view). WinForms applied no date filter by default. Older open agreements are hidden until the user changes the date. |
| Search filters removed | WinForms `GetAgreements3` filtered by number, reference, order date ±range, completion date ±range, buyer, seller, ship-to, buyer contact, seller contact, Approved only, Incomplete only, **SKU**, **Shipment**, cancellation date or Canceled only, expiration date or Expired only. The web has one search box (number, Reference 1/2, buyer or seller name), Fulfilled/Not Fulfilled, an Ordered (or Fulfilled) date range and Include completed. Searching by SKU, shipment, ship-to, contact, canceled, expired or approved is no longer possible. |
| Grid columns | Gone: Ship To, Effective, Expires, Completed, Canceled, Posted, Reference 1/2, contacts, Approved?. Added: Ordered/Assigned/Fulfilled quantities, Last Fulfilled, Total Amount. |
| `AgreementNumber` | Editable and required in WinForms. Assigned from the number scheme on create, then read-only. |
| `Currency_UnitTypeId` | Editable in WinForms. Set to the default currency on create. Not shown, not editable. |
| Own-side party (Seller on a sale, Buyer on a purchase) and its address | Any party and address in WinForms. Fixed to the company (CO_DEFAULT/CO_ADDRESS). Only the agent contact can be changed. |
| `PlannedDelivery`, `ActualDelivery`, `DocumentDelivery`, `Printed`, `PaymentDue` | Editable dates in WinForms. Not shown, not editable. Still copied by Copy Agreement. Some appear read-only in queue grids. |
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
| Grid columns | Gone: Ship To, Ship Date, Printed, Posted, Reference 1/2. Added: Balance, and Credit Amount and Expires for LCs. |

### 8.4 Bookings / Shipments

| Change | Detail |
|---|---|
| Ocean-only | The web creates and edits SEA bookings only. |
| ShipsGo updates are applied on arrival, without the IPI/DLV legs | WinForms `ucShipment.CheckNotes` read the sync's JSON `BookingNote`, asked the user, then applied the changes. Now `api.BookingUpdated` (called from `POST /api/bookings/<n>/notes`) applies them right away: carrier, POL/POD ports and dates, carrier status, vessel, voyage, and each container's type, status and carrier dates. It logs the change list as a `ShipmentNote` and no longer writes `BookingNote`. The IPI and DLV port and date updates are commented out in the proc, because ShipsGo misreports load and discharge. |
| `Shipment.Origin_PartyId` + address, `Shipment.Destination_PartyId` + address (place of receipt and delivery parties) | Editable in WinForms. Not shown, not editable. |
| Cargo grid on the booking | Gone: Delivered to Carrier, Ready to Ship, Unloaded. |
| Search filters removed | WinForms `GetBookings4` filtered by shipment number, booking number, origin port, destination port, shipper, carrier, forwarder, booking class, agreement, vessel, voyage, cargo/docs due, planned departure/arrival ±days, Not Departed, Not Arrived, booked/Not Booked, canceled/Not Canceled, completed/Not Completed, posted/Not Posted. The web has Loading/Departing/Arriving/Completed with a date range, Include canceled, and a search on number, carrier, vessel, voyage, release no. and B/L no. You can no longer search by shipper, forwarder, port, agreement or posted state. |
| Default windows | Arriving defaults to the last 30 days. A delivered booking that isn't completed and arrived earlier drops out of every default view until the user widens the dates. |
| Grid columns | Gone: Class, Forwarder, Shipper, ERD, Ramp Due, LRD, Receipt (IPI), Contract and Expires, Posted. |
| **Shipments Bulk Edit** (`ucShipmentBulkEdit`) | Mass update of vessel, voyage, carrier, every cutoff and date, queue and an added note across selected bookings. Not in the web. |

### 8.5 Cargo

| Change | Detail |
|---|---|
| `CargoContainer.Chassis` | Editable in WinForms. Not shown, not editable. |
| `CargoRailcar` row | WinForms created it when the container class is rail. Never created. |
| Search filters removed | WinForms `GetCargos2` filtered by shipment number, **booking number**, cargo number, scale ticket, manifest, **chassis**, **seal**, **Cu plate**, container type, **location**, available/loaded/unloaded/shipped/completed dates ±range, and Not Available, Not Unloaded, Not Loaded, Not Shipped, Not Completed. The web has Received/Incomplete/Finished, Include completed, a date range, work zone, work center, and a search on cargo number, shipment number, manifest, ticket, SKU and work order. You can no longer search by booking, chassis, seal, Cu plate, location or container type. |
| Grid columns | Gone: Booking, Scale Ticket, Location, Chassis, Manifest, Seal, Cu Plate, Ready to Ship, Delivered to Carrier, External Processor, Completed. Added: Work Order, SKU, Work Zone. |

### 8.6 SKUs

| Change | Detail |
|---|---|
| `Manufacturer_PartyId`, `Quantity2_UnitTypeId` (processed unit), `OrderLeadDays` | Editable in WinForms. Not shown, not editable. Left unchanged on save. |
| `Barcode` | Editable in WinForms. Read-only; generated on save. |
| **Recalculate inventory** (`RecalculateInventory`) | Button gone. |
| Physical inventory grid on the SKU | Gone (Inventory > Physical Inventory remains). |

---

## 9. Open notes from development sessions

These aren't differences from the WinForms client. They're the caveats, choices and suggestions raised at the end of Claude Code sessions (2026-10-09 to 2026-10-22, every repo under `hurkin/`), kept here because the session transcripts are the only other place they're written down. Items later fixed have been left out. Each says when it was raised; "decide" marks a choice that is yours to make.

### 9.1 Choices made in the web app that you may want changed

| Area | Note | Raised |
|---|---|---|
| Booking freight rate | The rate lookup matches on the shipment's IPI and DLV locations and the POL departure, as WinForms `ucShipment` did, not on the POL and POD ports. | 10-22 |
| Booking freight rate | Without a freight class the lookup still runs, but finds only rates not limited to particular classes. WinForms refused to look up without one. | 10-22 |
| Booking freight rate | The origin and destination free-time memos WinForms showed under the rate aren't shown. | 10-22 |
| Agreement delete | Refused in more cases than "a line has fulfillments": also posted, cargo contents loaded against a line, orders drawn from it, linked bills or invoices, generated documents (as booking and bill deletes do). | 10-22 |
| Bill line lookups | The Agreement Line lookup offers purchase orders and contracts on a vendor bill and sales orders and contracts on an invoice or credit memo; sales quotes aren't offered. The Cargo lookup searches cargo, booking, manifest, ticket, SKU and work order numbers, completed cargo included, and shows the first 250 matches. | 10-22 |
| Bill line amounts | A found cost or price replaces the amount whenever the item or Per changes, even a typed amount; opening a saved line never re-prices it. | 10-22 |
| Booking Status | The carrier Status on the General tab is free text. The mockup showed a dropdown; it needs a fixed list of values. *Decide.* | 10-20 |
| Custom characteristics | Inactive fields are hidden but keep their saved values. Cloning an item or SKU doesn't copy them. A blank number is stored as NULL (WinForms stored 0). | 10-12 |
| Assets | The asset pickers on work orders, agreement lines, bill lines and SKUs show only with T001 read; without it a line's existing asset is left as is on save. | 10-15 |
| M08 Inbound Inspection | Mobile M08 is treated as I008 at Write: it reads and saves inspections but can't delete them. *Decide* whether it should delete. | 10-15 |
| Work order movement button | No button on Transfer work orders (no screen for them); hidden on posted ones; disabled while the work order has unsaved changes. | 10-10 |
| Auto Work Orders | A template's movement type is copied onto the work order, not used as a filter, so an inbound template also fires on an outbound cargo for the same line. A process work order that later gets a cargo creates that cargo's Auto Work Orders. *Decide* whether movement should decide when a template applies. | 10-17 |
| Error messages | 57 places still show a fixed message ("Save failed") instead of the server's sentence. Switching them changes what users see. | 10-10 |
| Reports | The Reports nav entry shows for everyone, even with no report features. `List.ashx` caches each session's list for 5 minutes. | 10-15 |

### 9.2 Loose ends and things to check

| Area | Note | Raised |
|---|---|---|
| shipper-ui | `/inbound/workorder/:id` (`InboundCargoDetailPage`) is an unlinked prototype whose Inspections tab shows two made-up inspections from `api/stubs.js`. Remove it or point it at the work order's cargo. | 10-15 |
| shipper-ui | Recent items: records that open only in a dialog (a line item) can't be reopened from the list. | 10-20 |
| shipper-ui | In a tab left open across a deploy, Excel export does nothing and shows no message (its chunk is gone). | 10-22 |
| shipper-ui | Per-route lazy loading wasn't done; it's the largest remaining startup saving, but needs reload-on-chunk-error handling. Only worth it if first loads are reported slow. | 10-22 |
| shipper-ui | `src/auth/shp-features.tsv` still lists D002, I007 and G009 as HIDDEN. Once the table is re-dumped, `features.test.js` fails until they move to UI. | 10-09 |
| Editions | Owners are trimmed to their edition. Not verified: whether HAAL sends an owner the edition's full feature list; if it sends few, owners lose features. | 10-15 |
| Row-level security | Reports go through the WCF/SSRS path, so they still show every record to party-scoped users. Scoping is switched on per instance with `PARTY_SCOPED_INSTANCES`. | 10-09 |
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
| shipper-help | Six reports have only a stub (R112, R134, R198, R199, SQL-AGR, SQL-SHP). There's no mobile app source, so the mobile pages are inferred; M09 may no longer need inbound email. No pages for reports, flags, other mobile features or retired line-item features. Hardware page settings are for the TLP 2824 Plus, not the recommended ZD411t. `booking-general.png` shows the old General tab, and the Freight tab has changed since. Retiring support.hurkin.com needs Desktop's `HELPURL` changed to `https://hurkin.github.io/shipper-help/#/context/{mnemonic}`. | 10-12 to 10-20 |
