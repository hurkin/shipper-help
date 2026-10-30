# QuickBooks Service (QuickBooks Desktop)

The QuickBooks Service connects ShipperXL to QuickBooks Desktop. These instructions
are for IT staff.

**The QuickBooks Service is old and needs constant supervision by IT staff.** We
suggest [QuickBooks Online or Zoho Books](accounting-integration.md) instead.

## Before you start

You need [QODBC](http://qodbc.com/qodbc.htm) Server Edition ($499), installed and
set up on a dedicated, always-on machine (such as a server) that has QuickBooks
installed properly. Set QODBC up as shown: the **Advanced** tab, the **Optimizer**
tab (optimizer off), and **Server Edition** with **Use DCOM Servers** ticked.

![[qodbc-advanced.png|300]] ![[qodbc-optimizer.png|300]] ![[qodbc-server.png|300]]

Set up and test an ODBC data source named **QUICKBOOKS**.

## Install the service

1. On the server, download and run the
   [QuickBooks Service installer](https://hurkinapps.blob.core.windows.net/apps/prod/Hurkin.Shipper.QuickBooksService.msi).
2. Go to `C:\Program Files\Hurkin Software\ShipperToQuickBooks` and open
   `Hurkin.Shipper.QuickBooksService.exe.config` in Notepad.
3. Change `<value />` to `<value>the-value-you-set</value>` for:
   - **Instance:** your database code.
   - **License:** your license code.

   For example:

   ```xml
   <setting name="Instance" serializeAs="String">
     <value>DEV1</value>
   </setting>
   ```
4. Open `services.msc` and find **Hurkin Shipper to QuickBooks Service**.
5. Set the account it logs on as (strongly recommended).
6. Start the service and check that it stays running.
7. Watch the Windows Event Log for problems.

## Good to know

- Install the service on only one machine. One installation can connect up to 9
  databases, through HAAL. Each database it connects to needs its own license, set
  up in HAAL by support. You only need the database code and license for this one
  installation.
- See the
  [source to target mapping](https://docs.google.com/spreadsheets/d/112iGj_AAJtPMtBdEFnofBIzzEna7efsR8I1EjUWwm8c/edit?usp=sharing)
  for what is copied where.

## Related

[Accounting Integration](accounting-integration.md) · [Settings](../context/settings.md)
