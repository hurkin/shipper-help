# How Shipper Works

Shipper follows product from the moment you agree to buy it until it is invoiced
and posted to accounting. Most screens are one step in that chain. Once you know
the chain, you can tell what each screen expects and what it changes.

![[information-flow.png]]

## The building blocks

Set these up before anything else. Every other record points at them.

| Record | What it is |
|---|---|
| **Item** | Something you buy, sell or do. A *product* (raw or processed) or a *service* (trucking, pressing, commission). |
| **SKU** | One identifiable lot of a product item, such as one grower's stack. Inventory is always counted by SKU. |
| **Location** | A place inventory sits: a barn, a bay, a yard. Each belongs to a work zone. |
| **Work Zone / Work Center** | A work zone is an area, such as a valley. A work center is a place inside a zone where work is done, such as one press. |
| **Company / Contact** | Anyone you deal with: customers, suppliers, carriers, workers. |
| **Price List / Cost List** | What you charge (price) and what you pay (cost) per unit of an item. Shipper fills amounts from these. |

## The key events

### 1. Agreements say what you will buy and sell

- **Purchase contracts and orders** record what you buy. **Sales contracts, orders
  and quotes** record what you sell.
- Each line has an item, often a SKU, a quantity and a price.
- An order can be *drawn from* a contract. Anything fulfilled on the order also
  counts towards the contract.
- A quote becomes an order or contract with **Copy To**.

### 2. Bookings reserve the transport

- A booking (also called a shipment) is a reservation with a carrier: vessel, ports
  and dates.
- Agreement lines are **assigned** to a booking to say what will travel on it.

### 3. Cargo is each physical load

- A cargo is one truck, container or railcar, inbound or outbound.
- It carries a scale ticket (weights), work orders, inventory rows and, when
  outbound, a contents list.
- Cargo on a booking is offered the booking's line items. Entering a fulfilled
  quantity on the cargo **fulfills** that line.

### 4. Work orders record the work

- A work order is one job: haul, press, load, inspect.
- It sits on a cargo, or on a booking when there is no cargo yet.
- Its cost comes from the cost list. Finished work orders can be billed with
  **Create Bills**.

### 5. Inventory is a ledger

- Every receipt, move, process and deduction is a row with a **date, location and
  SKU**. Balances are the sum of the rows.
- A row with no date or no location doesn't count yet. This is how printed tags
  wait to be received.
- Weights are worked out from the inbound scale ticket: net weight divided by the
  units received.

### 6. Invoices and bills settle up

- **Invoices** are created from a sales order or from a booking.
- **Bills** (what you owe suppliers and workers) are created one at a time or in
  bulk from finished work orders or from fulfillment.
- **Credit memos** reduce what a customer owes.

### 7. Completed, then Posted

- Setting a record's **Completed** date says your part is done.
- If accounting integration is set up, completed agreements, bookings and bills are
  sent to accounting. Each one is then given a **Posted** date.
- A posted record is read-only. Only an owner can change the Posted date.

## Ordered, assigned and fulfilled

Agreement lines track three quantities:

- **Ordered:** what the line is for.
- **Assigned:** how much is planned onto a booking (or a cargo or work order).
- **Fulfilled:** how much actually moved, recorded by a cargo, work order or scale
  ticket.

A sale is usually fulfilled in containers (1 per container). A purchase is usually
fulfilled in units, such as bales.

## Rules that apply everywhere

- **Every minute matters.** Inventory is ordered by date and time. If you record a
  shipment at 10:00 and its receipt at 11:00, the balance goes negative in between.
- **Dates are shown in your time zone.** Booking vessel dates (sail and arrive) are
  calendar days at the port and are never converted.
- **Saving keeps what you have.** Most records save even when they are incomplete,
  so you can come back later.
- **Numbers are issued when you save.** Blank numbers are filled from the number
  scheme, and an issued number is never reused.
- **Queues route the work.** New agreements, bills and bookings can start in a
  queue, and each team moves them along. See [Queues](queues.md).
- **Scheduled jobs react to events.** Completing or posting a record, posting a
  payment, or adding a record to a queue can send an email, run a report or update
  another system.
- **What you see depends on your role and your subscription.** A missing menu entry
  means your role doesn't include it, or your edition doesn't. Owners have every
  right, but only to what the edition includes. Read lets you look, Write lets you
  edit, and Delete lets you delete and do a few heavier actions.

## Barcodes

Shipper prints its own barcodes. The first two digits say what a barcode is, and
the last digit is a check digit.

| Starts with | Means |
|---|---|
| 10 | An inventory tag (followed by the tag number, then the cargo) |
| 11 | A cargo |
| 12 | A work order |
| 15 | A SKU |
| 22 | A location |

A scanner field accepts any of these. Shipper works out what was scanned.
