# Complete a Booking

Before you mark a booking complete, check that what it recorded is right.

1. Run **Booking Cargo** to check that every container is there, with proper
   weights and inventory.
2. Run **Estimated Shrink** to check that the product used on the booking looks
   right against what was received and processed.
3. Run **Shipment Inventory Cost** to give accounting the value of inventory used.
4. [Audit and reconcile](audit-inventory.md) the SKUs the booking used.
5. Run **Work Order Summary** to review the work orders on each container.
6. Invoice and prepare documents. See [Create Invoices](create-invoices.md) and
   [Prepare Documentation](documentation.md).
7. On the booking's **Freight** tab, enter the **Completed** date and save. You can
   also complete bookings in bulk from a queue with **Set Completed**.

Reports that run for one booking are on its **Reports** button. The rest are under
**Reports** in the menu.

## Good to know

- **Completing a booking needs delete rights** on bookings (or an owner).
- If accounting integration is set up, a completed booking is posted. A posted
  booking and its cargo are read-only, and only an owner can change the Posted date.
- Completing fires the *Booking Completed* and *Shipment Completed* scheduled jobs,
  if you have any.

See also: [Bookings](../context/B008.md).
