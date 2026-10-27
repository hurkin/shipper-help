# Auto Work Orders on Purchases and Sales

Auto Work Orders put the work an agreement always needs, such as loading a
flatbed or delivering a container to port, on each cargo for you. Set them up
once on the purchase or sales order. Shipper then creates the work orders when a
line is assigned to a cargo.

Each Auto Work Order has a movement type, and it goes only on cargo with the same
movement:

| Auto Work Order | Created on |
| --- | --- |
| Inbound | inbound cargo |
| Outbound | outbound cargo |
| Outbound from Supplier | direct-ship cargo |
| Process | process-only cargo |

A cargo gets one work order per work item. If the cargo already has a work order
for that item, Shipper doesn't add another, so you can create the important work
orders early and let Shipper fill in the rest.

Purchases and sales differ in one step. On a purchase, the cargo usually doesn't
exist until the load arrives, so you create it from the work order. On a sale,
the booking and container are usually set up already, so you put the work order
on that cargo.

## Purchases

1. **Set up the Auto Work Orders.** On the purchase order (or contract), go to
   **Auto Work Orders** and click **Add Auto Work Order** for each job. Here,
   every load needs Load Flatbed and Commission, both Inbound. A line can turn
   one off or add its own on the line's **Auto Work Orders** tab.

   ![[awo-purchase-tab.png]]

   At this point you can stop. Assigning a line to a cargo creates both work
   orders on that cargo.

2. **Optional: plan the key work ahead.** Auto Work Orders appear only once
   there is a cargo. To see work in the
   [Work Order Scheduler](work-orders.md?id=plan-the-week-with-the-scheduler)
   before then, open the line and click **Create Work Orders**:
   - **Movement Type** starts at Inbound on a purchase. Only the line's Auto Work
     Orders of that movement type are offered.
   - Choose the **Auto Work Order**, such as Load Flatbed. Its worker, zone,
     center and cost fill each work order.
   - Enter the **Planned Start** (or leave it empty), the **Number of Work
     Orders** (one per expected load) and the **Quantity Each**.

   ![[awo-purchase-create.png|500]]

3. **Create the cargo when the load arrives** (or is on its way). Go to
   **Inbound > Work Orders**, find the work order and click **Create Cargo**. The
   cargo takes the work order's movement, and the work order's line moves onto
   it.

   ![[awo-inbound-create-cargo.png]]

4. **Shipper adds what's missing.** The cargo already has the flatbed work order
   from step 2, so only Commission is created.

   ![[awo-inbound-cargo.png]]

## Sales

1. **Set up the Auto Work Orders.** On the sales order (or contract), go to
   **Auto Work Orders**. Here, the order needs Hay Press, which is Process work
   done before the container is loaded, and Deliver Container to Port, which is
   Outbound.

   ![[awo-sales-tab.png]]

   Assigning a line to an outbound cargo creates Deliver Container to Port on it.
   Hay Press is Process, so it isn't created on an outbound cargo. Create it as in
   the next step.

2. **Create the press work order.** Open the line and click **Create Work
   Orders**. Choose **Process** as the **Movement Type**, then choose Hay Press,
   the planned start, the number of work orders and the quantity of each.

   ![[awo-sales-create.png|500]]

3. **Put the work order on the container.** Open the work order and choose the
   container in **Cargo**. The **Shipment** is the cargo's booking. Saving moves
   the work order's line onto the cargo.

   ![[awo-sales-work-order-cargo.png]]

4. **Shipper adds what's missing.** The cargo is outbound, so Deliver Container
   to Port is created beside the press work order.

   ![[awo-outbound-cargo.png]]

## Good to know

- Removing a line, or turning an Auto Work Order off, doesn't delete work orders
  that were already created.
- A completed cargo gets no new work orders.
- Until a created work order starts, its quantity follows later changes to the
  line's quantity on the cargo.
- A cost entered on the Auto Work Order is locked onto every work order made from
  it. Leave it blank to use the cost list.

See also: [Work Orders and the Scheduler](work-orders.md),
[Work Orders](../context/W001.md?id=auto-work-orders).
