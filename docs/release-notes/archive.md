# Archived Release Notes

Releases from 2020.2 to 2025.5, before these notes moved here. For newer
releases, see [Release Notes](./).

## Version 2025.5

**Deployment:** October  31, 2025 17:00 PDT

There will be no disruption of service for this release. The apps will prompt you to update once you restart them, or when you first log in. This applies to [ShipperXL for Windows](../instructions/install-desktop.md) and [ShipperXL Mobile](../instructions/install-mobile.md). The mobile apps will release on their own timelines according to the approval processes from Google and Apple, potentially as early as October 23rd.

**Updates**

- Mobile: Compliance updates to stay published on the App Stores
- Extended Daylight Savings dates for USA/CAN from 2025 thru 2035
- Desktop: Locking SKU unit types once there is any inventory against that SKU
- Desktop: Updated internal packages.

## Version 2025.4

**Deployment:** September 1, 2025 08:00 PDT

There will be no disruption of service for this release. The apps will prompt you to update once you restart them, or when you first log in. This applies to [ShipperXL for Windows](../instructions/install-desktop.md), [ShipperXL Mobile](../instructions/install-mobile.md), and [Scale Kiosk](../instructions/kiosk.md). The mobile apps will release on their own timelines according to the approval processes from Google and Apple.

**New Features**

- New Supplier Performance report shows inbound and outbound data by SKU, Shipment, and Customer for value, quantity, and weight. This is for Enterprise customers only and [admins will need to make this visible to non-admin users.](https://portal.hurkin.com/haal)
- QR Codes on Serial inventory tags, SKU inventory tags, Work Orders report, and Location Barcode reports. These can much more reliably read by scanners. Both QR and barcode styles are supported.
- Attachments show image previews instead of just listing filenames
- Cargo by Location report added to Shipment screen

**Bug Fixes**

- Mobile: fixed bug where ship and process serial barcodes could be added more than once
- Desktop: fixed bug where queue dates were off by a day for dates without time

## Version 2025.3

**Deployment:** May 15, 2025 17:30 PDT

This applies to the following:

- [ShipperXL for Windows](../instructions/install-desktop.md). No disruption of service. The app will prompt you to update once you restart it.
- [ShipperXL Mobile](../instructions/install-mobile.md) for Android and iPhone. Because the app needs to be approved by Google and Apple, the actual upgrade will happen anytime between May 13 and May 15. The older version of the mobile app will cease to work after May 15 at 5:30PDT. You may need to manually upgrade the newer version.
- [Scale Kiosk](../instructions/kiosk.md). No disruption of service. The app will prompt you to update once you restart it.

## Version 2025.2

**Deployment:** April 3, 2025 17:30 PDT

This applies only to [ShipperXL for Windows](../instructions/install-desktop.md) and the [Scale Kiosk](../instructions/kiosk.md). There will be no disruption of service as systems are upgraded. After the upgrade is completed and you restart your software, it will prompt you to upgrade your software. 

**New Features**

- Support for [Outlook for Windows](https://www.microsoft.com/en-us/microsoft-365/outlook/outlook-for-windows) instead of Outlook Classic
- [Mobile App](../instructions/install-mobile.md). Major improvements have been released as Beta. Join the Beta from the Play Store.
- Send Pictures allows up to 3 images at a time. No longer uses email to upload.
- Ability to Add and Edit SKUs
- Ability to Add and Edit Parties and Addresses
- SKU now shows Stats, Hay Analyses, and Images
- Improved Work Orders, including Completed Work Orders

**Bug Fixes**

- Data entry issues with Carrier Service Contract Rates
- Display a warning if selected Scale Id does not match the Kiosk's Scale Id
- Container Type issue when creating new Cargo under certain conditions
- Issue with grids on the Party screen
- Job Agent: Email failures not logged

## Version 2025.1

**Deployment:** December 31, 2024 18:00 PST

There will only be a brief disruption of service (a minute or less) as systems are upgraded. After the upgrade is completed, and you restart your software, it will prompt you to upgrade. This applies only to [ShipperXL for Windows](../instructions/install-desktop.md) and the [Scale Kiosk](../instructions/kiosk.md).

**New Features**

- Single-sign on supported for specific users and/or databases. This works with Google, Microsoft Accounts, and Microsoft Work or School accounts. Contact [support@shipperxl.com](mailto:support@shipperxl.com) to inquire or to configure.
- Cargo screen now has a warning message if a duplicate seal, copper plate, or cargo number was used. This appears only when you press Save or Save & Close.
- Exporting Word (.docx) files is now supported. The older .doc format is no longer supported.
- Scale Kiosk now supports more scale head serial scenarios (\r instead of \n)
- The [Readerboard](../instructions/hardware.md) is  now for sale! Contact [sales@hurkin.com](mailto:sales@hurkin.com) to inquire.

**Bug Fixes**

- Cargo screen had a bug making it cumbersome save Work Orders in some situations
- Carrier Service Contract was not able to set a master contract in some situations
- The Cargo inventory tab was unable to remove a location from a line

## Version 2024.4

**Deployment:** October 22, 2024 18:00 PDT

**New Features**

- [Inbound](../instructions/email-attachments.md) (IMAP) and [Outbound](../instructions/email-attachments.md?id=sending-email) (SMTP) email support for modern authentication (oAuth2).
- Adding commodity selector for dynamic query grid
- Groundwork ready for single-sign on, coming in 2025
- Groundwork started for modern API for the new ShipperXL App, coming in 2025

**Bug Fixes**

- Cargo screen errors and issues when saving work orders
- Desktop crashes after extended use of Cargo and Booking screens
- Main browser screen shows inflated logos
- Scale Ticket screen missing Reports menu after saving
- Inspection: now requires selection of an inspection type
- Item: movement type not saving
- Work Order: selecting a work center will update work zone on save
- Scale Ticket: round weights to nearest whole number
- Job Agent sets user on attachments to "from" address when adding inbound emails

## Version 2024.3

**Deployment:** September 17, 2024 18:00 PDT

- Cargo: Do not close the screen if there are validation errors
- Weight Ticket: showing only fulfilled and contents details and now excludes inventory
- Reporting: updated Semantic Model available for Power BI exclusively for Enterprise customers
- Sales Summary: exclude quotes from calculations
- Bug fix: change password does not show message from v2 HAAL
- Bug fix: SKU with leading or trailing spaces causes error when loading inventory ledger
- Bug fix: corrected issue calculation for items with "Each" unit type
- Bug fix: consistency issues with decimal places for assignments and fulfillments
- Bug fix: combo lookup boxes corrected performance and behavior issues

## Version 2024.2

**Deployment:** June 18, 2024 17:00 PDT

- Invoices: Pro Forma filter on search
- Bulk Edit Bookings: exclude canceled bookings
- Bulk Edit Bookings: add Booking Number search
- Bookings: Add seal number to the cargo list
- Bug fix: Sales Quote no longer carries contract connections when cloning from another object
- Scale Ticket: added Note/Comment field
- Stability and security updates to various internal components. See About screen on Desktop for details.
- Additional reports will be deployed in the week or two following June 18th.

**Deployment:** July 23, 2024, 08:00 PST

- Order Status: added "Commodity" filter and replaced "Days since Completed" with "Earliest Date"
- Agreement: created report header, including agreement number

## Version 2024.1

**Deployment:** January 1, 2024 07:00 PST

- Kiosk: support for Outbound load weights
- Kiosk: fixed bug with "Driver On" for Inbound loads
- Kiosk: real-time refresh of PIN and IP. Kiosk no longer requires restart if Readerboard is rebooted.
- Mobile: show all fields until an inventory barcode is scanned which may hide some fields
- Mobile: set cursor to the first data entry field upon screen load
- Mobile: improved error messages for Login and Scale; layout changes on SKU
- Invoices: when creating an invoice from Shipment screen, the currency of the Sales Order is used for the Invoice
- Cargo Bill of Lading: Show trucking company specified on scale ticket if not specified on cargo
- Work Order: show From and To ports if specified on the Work Order. Renamed Delivery Port to Final Destination Port
- Stability and security updates to various internal components. See About screen on Desktop for details.

## Version 2023.2

**Deployment:** July 3, 2023 17:00 PDT

- Fix for mobile hard crash on Scale screen
- Fix for missing SKU details on mobile SKU screen
- Showing read-only shipment number from Cargo on Work Order screen
- Fix for unexpected work order deletion when deselecting a planned work order
- Fix for some situations which were not recalculating SKU inventory if weights were added after units
- Fix for screen redraw of checkboxes on sales item contract item
- When creating a Cargo from the Work Order screen, set default movement type and shipment to match work order
- Traffic Audit Report will highlight when loaded, fumigated, open, and available dates are not sequential
- New: Assets have been added to the Pro edition. This allows for Vehicle selection on the Scale Ticket.
- New: Assets with Reference 1 = TARE will use the Reference 2 value as the tare weight in new scale tickets.
NOTE: This is the only documentation of this feature.

## Version 2023.1

**Deployment:** March 22, 2023 18:00 PDT

- Fix for "Out of Memory" error, after using many Cargo or Scale Ticket windows over time
- Updates to internal third-party components (like [Microsoft .NET](https://learn.microsoft.com/en-us/dotnet/framework/get-started/overview))
- Attachments report now includes related records for Shipments, Cargo, and Scale Tickets
- Inventory Transactions report now includes the Cargo of origin for non-inbound barcodes
- Fix for image rotation and sizing on images attached with a .jpeg or .png extension.
- On older machines, the Kiosk will be prompted to install upgrade components. A restart may be required. See [Kiosk Install](../instructions/install-kiosk.md).

## Version 2022.4

**Deployment:** October 31, 2022, 17:30 PDT

- Preview! Quick Sale screen for back-to-back single item trades, local sales, and other simple sales scenarios. Let us know what you think: [https://groups.google.com/g/shipperxl](https://groups.google.com/g/shipperxl)
- Processor Instruction: added Forwarder
- Incoterms: added code to description
- Cargo: fixed processor mismatches
- Search screens: fixed date searches to be more accurate.
- Addresses: now sorting by A/R, A/P, Delivery. Uncheck those boxes to move old addresses lower in the list.
- Cargo Bill of Lading: updated to short description
- Agreements: effective and expirations are now date-only
- Installer: fixed to allow upgrade/downgrade without reinstall
- Work Order: when unit type = None and Quantity = 0 then use Fulfilled Quantity.

**Deployment:** November 16, 2022, 17:30 PST

- Fixes to Work Order Scheduler dates and Quick Sales

**Deployment:** November 18, 2022, 06:30 PST

- Fixes to dates on Queues, Cargo search, and Bulk Edit Bookings

## Version 2022.3

**Deployment:** July 1, 2022, 17:30 PDT

- Kiosk: added Serial Mask -- a pattern for reading scale input
- Desktop: Adding Earliest Pickup, Earliest Receiving, and Rail due to Shipment screen. This also affects the Shipment Search, Queue, and Bulk Edit Bookings screens
- Desktop: slight rearrangement of dates on Work Order screen
- Desktop: bug fix for dates at UTC midnight were missing times
- Desktop: Is Taxable for items to allow for QuickBooks defaults
- Reports: updated dates and formats on Booking Status, Order Status, Processor Instruction, Shipment Advice, Shipment Status LTR.

## Version 2022.2

**Deployment:** March 1, 2022, 19:30 PST

- Desktop: Work Orders: add contact, currency
- Desktop: Fulfillment: add agreement search
- Desktop: Scale Ticket: add contact, driver on/off checkbox
- Desktop: Bulk Edit Bookings: allows adding to a queue too.
- Report: Agreement Summary: fixed fulfillment and as-of date logic
- Report: SKU Activity: add Avg Unit Weight to totals
- Report: Inventory Transactions by Cargo: add weight for work orders 
- Report: Cargo Bill of Lading: run from work order without attached cargo
- Scale Kiosk: improved reliability and logging
- Mobile App: SKU search
- Mobile App: SKU details, including Set Location 
- Mobile App: view work orders
- Mobile App:  remote scale control (Kiosk + Readerboard setup only)

**Patch 1:** March 25, 2022, 19:30 PDT

- Scale Kiosk Printing: reliability increased for [Acrobat Reader DC](https://get.adobe.com/reader/) or [FoxIT PDF](https://www.foxit.com/pdf-reader/)
- Scale Kiosk: preserve re-print across restarts of the program
- Desktop: bug fixed where overwriting saved reports corrupted files
- Desktop: bug fixed with Agreement Item variable costs data entry
- Desktop: bug fixed with Cargo Contents and incredibly high quantities
- Desktop: invoices now add all fulfillment records, even work orders

**Patch 2:** April 16, 2022, 13:30 PDT

- Scale Kiosk: support for RTSP camera streams. Fixes to label generation & printing.
- Desktop & Mobile App: compatibility updates to align with Kiosk

**Patch 3:** May 28, 2022 11:00 PDT

- Report: SKU Activity updated to match Estimated Shrink for partial load weight allocation
- Report: Estimated Shrink: normalized raw allocations for processed from inventory
- Desktop: bug fix for empty Scale Tickets being created with new Cargo records
- Desktop/Scheduler: Adding jpg attachments with [embedded EXIF GPS location information](https://en.wikipedia.org/wiki/Exif) to SKUs without location will update SKU location.
- Desktop: bug fix for various places where dates were showing in UTC instead of local time.

## Version 2022.1

**Deployment:** Dec 22, 2021 - 8:00pm PST

- The export button on reports is now the Save button. It will now properly set the filename to include detail like Cargo number, if available. Once the file is saved, you'll see a notification in Windows that you can click on to open the file immediately. That should save time!
- Adding search & add from SKU lookups
- Updating reports to respect scale unit type (LB, KG). 

**Patch 2.22.1.1:** Dec 31, 2021

- System Events are now Scheduled Jobs. Event Manager is now Job Agent.
- Scheduled Jobs can now send Text Messages (SMS)!
- Extended string size of Custom Fields from 200 to 1000.
- Switched to XLSX as Excel export format (instead of XLS)
- Added image processing to the Job Agent. The computer reads container numbers in images and compares them to cargo numbers associated with scale tickets. A report can be sent of potential mismatches and issues.
- Improved location dropdowns to pull list when list is small (less than 100).

**Patch 2.22.1.2:** Jan 15, 2022

- Updated [ShipperXL Kiosk](../instructions/install-kiosk.md) to a single installer.
- Updated [ShipperXL Desktop](../instructions/install-desktop.md)  installer to include barcode fonts.
- Added "Default weight unit" to Tools | Options menu. Pounds or Kilograms.
- Updated remaining reports to respect scale unit types, starting with the default type. Some reports will allow switching from LB to KB, and vice versa.

## Version 2021.4

**Deployment:** Oct 30, 2021 - 3:00pm PDT

- Fixed bug with Traffic Center that caused frequent silent crashes
- Fixed length issue on Asset screen for Vehicle Tracking Number
- Updated Cargo by Location report to include Vessel in order to compare and audit cut-off times
- Updated Estimated Shrink report bug causing "divide by zero" error in some cases
- Updated Physical Inventory Values report adding detail columns for variable and work order costs
- Updated Price List to allow Item to be different than the SKU's Item
- Updated auto upgrade technology from ClickOnce to passive MSI for faster launch time.
- Added API support for the next release of Scale Client, Readerboard, and RFID reader
- Added API endpoint for /reports/custom to enable pulling custom report data via API
- Added Tracking Number to Party to support RFID tags
- Added new info to Scale Ticket: Carrier, Vehicle, Environment, and Image Info

## Version 2021.2

**Deployment:** June 30, 2021 - 5:00pm PST

- All Screens with attachments: fixed issue where new attachments were not clickable until after saving, and where modifications were required to get attachments to really save. No further need to "over-save".
- Attachments: Added drag & drop, and also multiple-select when adding attachments.
- Work Order Statement: added manifest number, and split reference numbers, and associated bill (if any). Changed to landscape orientation.
- AES Data Entry Report: added Actual Value, and differentiated Estimated Value.
- Shipment Screen: corrected overflow for very long contract titles
- SKU Inventory / Cargo Screen: corrected scenario where unit weights are not updated if scale tickets are entered after barcodes are received.

## Version 2021.1

**Deployment:** Apr 10, 2021 - 11:00am PDT

- No functional updates, but a large number of compatibility updates to subcomponents.

## Version 2020.4

**Deployment:** Oct 31, 2020 - 11:00am PDT

- BUG FIX: sales order search does not honor reference search
- BUG FIX: bad screen redraw performance for grids
- BUG FIX: attachments not saving on agreements, bills, and shipments unless there is another change made to the record

## Version 2020.2

**Deployment:** May 22, 2020 - 6 to 7pm PST

- EXIF Orientation correction: pictures from DLSR cameras were being flipped during upload
- Search Results: the limit of results has been increased from 100 to 250
- Attachment Cleanup: every 11 hours invalid attachments are removed. This only applies to databases that have [System Events Manager](../context/G014.md).
- BUG FIX: sending attachments failed if the attachment wasn't saved properly
- BUG FIX: reports that were left open too long say "report execution has expired..."
- DID YOU KNOW that you can log in to Shipper on your Android or Apple phone? [See here](../instructions/install-mobile.md).

### Party Screen

related parties tab now includes phone, email, and sorting from any column

### Sales/Purchase Screens

shows a warning when a contract does not match the line items

### SKU Screen

inventory ledger now includes a Page feature. SKUs with 1000's of line items often took a long time to load or crashed

## Incoterms 2020

**Deployment:** March 5, 2020 - 18:30 PDT

- Several incoterms have been deactivated (DAF, DES, DEQ, DDU, DAT) and one has been added (DPU) 

## Version 2019.4

**Deployment:** October 19, 2019 - 7 to 8am PDT: Version 2.19.4.1

- Upgrading deployment certificate, which happens on a yearly basis. 
- Fix for multiplication of Bill descriptions

## Version 2019.2

**Deployment:** March 30, 2019 - 7 to 8pm PDT: Version 2.19.2.0

- The daylight savings time calculations table only included through 2018. The table is now extended through 2025. 
- The order of the columns for line items on the Purchase Order, Contract, Sales Order, Contract, and Quote were adjusted
- The Estimated Shrink report has been updated to include more accurate and consistent calculations based upon the inventory ledger

## Version 2019.1

**Deployment:** January 10, 2019 - 8 to 9pm PST: Version 2.19.1.5

- Patch: Jan 15 - 8am PST: Fixing regional display issue in Queues.

### Agreement Items

- Added Internal Memo 
- Renamed Reference 1 to Non-Inventory SKU, and Line Ref to Customer/Supplier Reference.
- Updated these reports for Non-Inventory SKU consistency: Agreement, Order Status, Processor Instruction, Shipment Advice, Shipment Schedule, Work Order Schedule, Work Order

### SKUs

- Changed Description to Location/Notes
- Added Year, Cutting

### Queues

- Date columns now sortable. Forwarder now filterable. Highlighted dates are overdue.
- Added Max Hours and Notify Email to configuration. When an item in a queue is older than the Max Hours, it is highlighted in the queue.
- Faster? They should be if you have less than 100 items in the Queue.

Custom Reports now have an indicator so you know they're custom. These reports are not upgraded unless specifically requested.

### Other miscellaneous changes:

- Work Order Template: now allows editing of memo and references
- Party Search: includes email, names, code, and keywords in search criteria
- Work Order Schedule: added links for Work Order, Shipment, Cargo
- Item: Added Barcode (for PLU/UPC codes)
- Party Address: Added memo to allow inclusion as location memo on reports (Shipment Schedule, Work Order)
- Increased speed of Search feature (likely to become a centerpiece of the a new homepage this year)

## Version 2018.4

**Deployment:** Oct 16, 2018 05:00 PM

- 1018  Item SKU Screen: InspectionId is showing on the Inspection detail tab
- 1028 Cargo: copying from order + inventory does not work without inventory
- 1019 Inspection: Add link to Google directions
- 1013 Queue: add column with latest notes to items
- 1016 Queue: Add buyer/seller contacts to grid, with filter
- 1015 SKU: Add notes for agreements; increase size of Memo field
- 1000 Traffic Audit Report: Add SKU
- 937 Add Average Moisture per SKU to Vendor Receipts Statement

## Version 2018.3

**Deployment:** Aug 30 2018 08:00 AM

This release includes a bunch of server-side changes to support the release of the [ShipperXL Mobile App](../instructions/install-mobile.md). 
The main changes to the Windows client are:

- removing unnecessary folders from the Custom and Actions folders on the menu. 
- Fixing inconsistencies with the "Copy from Inventory + Order" button on the Cargo screen.
- Reversing the default sort on the Inspections search screen
- Limiting SKU quantities to count units only (i.e. bales, each --- instead of tons, which are calculated elsewhere)

| ID | Work Item Type | Title | Area Path |
|---|---|---|---|
| 1014 | Product Backlog Item | Limit data entry quantity to 99999 | Hurkin\Shipper\Mobile Scanner |
| 1017 | Bug | SKUs Available to Sell not showing all Hay Analysis | Hurkin\Shipper\Reports |
| 995 | Product Backlog Item | Android Mobile Scanner | Hurkin\Shipper\Mobile Scanner |
| 1029 | Product Backlog Item | Inventory by Barcode should always return results, even if they are 0. | Hurkin\Shipper\Windows Client |

## Version 2018.2

**Deployment:** May 31, 2018 9:00 PM PDT

| ID | Work Item Type | Title | Area Path |
|---|---|---|---|
| 1011 | Product Backlog Item | Agreement Item: Rename Reference 1 & 2 to Item Reference 1 & 2 | Hurkin\Shipper\Windows Client |
| 1012 | Product Backlog Item | QBO: set CompanyName and DisplayName. Send email to all related parties. | Hurkin\Shipper\Event Manager Service |
| 1010 | Product Backlog Item | Agreement Item: Add Line Reference | Hurkin\Shipper\Windows Client |
| 1009 | Product Backlog Item | Tools \| Options: add configuration tab for admins to change email settings | Hurkin\Shipper\Windows Client |
| 1008 | Product Backlog Item | SCM update from VSTS to GIT | Hurkin\Shipper |

