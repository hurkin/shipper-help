# Work Orders and the Scheduler

A work order is one job, such as hauling a load, pressing a stack or loading a
container. It ties the work to a cargo or a booking, and its cost becomes a bill.

## Create a work order

1. Open the cargo the work is for and click **Add work order** on its **Work
   Orders** tab. Or use **Processing > Work Orders > New Work Order**, and put the
   work order on a cargo or a booking there.
2. Choose the **Work Item Type** (a service item). The unit and cost fill in from
   the item and your cost list.
3. Choose the **Worker** (the company doing the work), the **Work Zone** and
   **Work Center**, and the planned start.
4. Save. The work order number comes from the number scheme if you leave it blank.

Work that every load of an agreement needs, such as hauling or pressing, can be
created for you instead. See **Have work orders created for you**, below.

As the work happens, record **Actual Start** and **Actual Finish**. Finishing a
work order makes it billable in [Create Bills](../context/W005.md).

## Have work orders created for you

1. Open the purchase or sales agreement and go to its **Auto Work Orders** tab.
2. Click **Add Auto Work Order**. Choose the work item, and the worker, zone,
   center and anything else that is always the same. Enter a cost only to lock it.
   Leave it blank to use the cost list. Its movement type decides which cargo it
   is created on: Inbound on inbound cargo, Outbound on outbound, Process on
   process-only cargo.
3. Tick **Include on bills and invoices** if the work is billed to the customer.
4. Save. Every line of the agreement now takes it. To leave it off one line, open
   the line, go to its **Auto Work Orders** tab and clear its box. A line can also
   have its own under **This line only**.

When a line is assigned to a cargo, or fulfilled on one, the work order appears on
the cargo's **Work Orders** tab. See [Work Orders](../context/W001.md).

## Plan the week with the scheduler

1. Go to **Processing > Work Order Scheduler**.
2. Set the days, then narrow it to a work zone, work center or movement type.
3. Drag work orders into the right day and order. You can also use the buttons:
   up and down, top or bottom of the day, previous or next day, or **Move to
   date**. **Unschedule** clears a work order's plan.
4. To make identical work orders, such as one per container, select one and use
   **Clone**. Then use **Spread** to put the copies a few per day.
5. Click **Save**. Nothing changes until you save.
6. To change the worker, work center, cost or other details on several work
   orders at once, select them and click **Edit N Selected**. See
   [Bulk Edit](../context/W004.md?id=bulk-edit).
7. Share the plan with the **Work Order Schedule** report.

## Good to know

- Started work orders show on the schedule but are locked.
- Within a day, times never run backwards. A moved work order keeps its time if it
  still fits between its neighbours. Otherwise it takes the time of the one above
  it.
- Reports group the schedule by the day in UTC. A work order planned late in the
  evening can show under the next day. The scheduler marks these.
- A clone copies the plan (item, worker, zone, center, ports, booking, quantities,
  references, memo and order lines). It doesn't copy the cargo, actual dates,
  fulfillment or inventory.

See also: [Work Orders](../context/W001.md),
[Work Order Scheduler](../context/W004.md).
