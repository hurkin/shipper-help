# Enter a Purchase Contract

Use a **purchase contract** for product bought over time, usually from a grower or
supplier for a set of SKUs. Use a **purchase order** for a one-time purchase, such
as the buy side of a back-to-back trade.

1. Go to **Inbound > Purchase Contracts** (or **Purchase Orders**) and search first.
2. Click **New**, choose the seller, and click **Create**. Your company becomes the
   buyer and you become its purchase agent.
3. On **General**, add the seller's address and contact, ship-to, dates and
   references.
4. On **Line Items**, add one line per SKU you are buying:
   - Choose the **Item** and the **Inventory SKU**. If the SKU doesn't exist yet,
     create it first in **Lists > SKUs**, or with **Create SKU** on the item.
   - Enter the quantity, its unit (usually Each, for bales), and the purchase
     amount and what it is per (for example, per ton). The amount fills in from
     your cost list when one matches.
   - Once the line is saved, add costs you expect to pay later (trucking, tarping,
     insurance) under **Variable Costs** to get an all-in purchase cost. Shipper
     shows the cost per unit and the total estimated cost beneath them, and
     **Copy From Other Line Items** copies another line's costs. The **Auto Bill**
     box does nothing on its own. It is read by scheduled jobs that support sets up
     for you. See [Variable Costs](../context/A004.md?id=variable-costs).
5. Click **Save**, then use **Reports** to print the **Agreement** for the seller.

## Good to know

- Inbound loads fulfill the contract line through its SKU. See
  [Receive Inventory](receive-inventory.md).
- A purchase order can be drawn from a purchase contract. Its fulfillment then also
  counts on the contract.
- **Estimated** appears when the line is priced per a different unit than it is
  ordered in (for example, ordered in bales but paid per ton). It is the expected
  quantity in the pricing unit.

See also: [Purchase Contracts](../context/A003.md),
[Purchase Orders](../context/A002.md), [Cost Lists](../context/I005.md).
