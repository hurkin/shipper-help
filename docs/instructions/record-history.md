# See Who Changed a Record

Every record shows when it was last modified, but that date covers only the record
itself, not its lines or details. **History** shows every saved change to the
record and its parts: who made it, when, and each field's old and new value.

## Opening it

- On a record page, **History** is at the far right of the row with **Save**.
- In an admin list's edit window, **History** is beside **Delete**.
- You see **History** only with the highest rights the screen offers: Delete, or
  Write (or Read) where the screen stops there.

## What it shows

- **Created** says who created the record and when. **Last changed** is the newest
  change to the record *or any of its parts*, such as a booking's sea details or an
  order's lines.
- Changes are listed newest first. Changes one person saved a few seconds apart,
  such as an order and its lines, show together as one save.
- Each change lists the fields that changed, from the old value to the new one.
  Fields that point to another record show that record's name as it is now.
- The buttons at the top narrow the list to the record or one of its parts, with
  how many changes each has.
- Dates and times are shown exactly as stored.

## What's included

| Record | Its parts |
|---|---|
| Bookings | Ocean, land and rail details; documents and documentation tasks |
| Orders, contracts and quotes | Lines and their SKUs; documents |
| Invoices, bills, credit memos and letters of credit | Lines, letter of credit details, payments; documents |
| Cargo | Containers, railcars, contents, scale tickets |
| Work orders | Scale tickets |
| Companies and contacts | Company, person and address details |
| Items, SKUs, assets, cost lists and price lists | Their details and lines |
| Admin lists (countries, ports, terminals, units of measure, custom fields, documentation tasks, terms, terms templates, categories, commodities, container types) | Countries' regions, ports' terminals, units' conversions, custom fields' choices, documentation tasks' defaults |

Documents and documentation tasks are included only if you have the documents
permission.

History covers what a record owns, not the records that use it. A port's history
is changes to the port and its terminals, not every booking that sails from it.

## Limits

- **A removed line shows who and when only approximately.** Shipper records a
  line's last version but not who removed it or when, so it shows as removed
  *after* its last change.
- **Some older records start partway.** When the first change wasn't kept, the
  first entry reads *earliest version kept* instead of *Created*.
- Very busy records show the latest 500 changes for each part, and say so.

## Related

[Getting Started](getting-started.md) · [How Shipper Works](how-shipper-works.md)
