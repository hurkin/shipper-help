# VM Configuration

For knowledgeable IT staff only.

1. Provision an Azure VM: SQL Server Web Edition, at least 2 cores and 8 GB memory.
2. Open HTTPS (443), FTP (21, 50000-50100) and RDP (3389) in a network security
   group. Copy or reuse the network security groups for DB01 or DB04.
3. Add disks for `F:\data` and `G:\logs`.
4. Copy [vmsetup.ps1](https://github.com/hurkin/shipper-windows/blob/main/Documents/Config/vmsetup.ps1),
   [renew.ps1](https://github.com/hurkin/shipper-windows/blob/main/Documents/Config/renew.ps1) and
   [Offsite_To_B.cmd](https://github.com/hurkin/shipper-windows/blob/main/Documents/Config/Offsite_To_B.cmd)
   to `F:\config`.
5. In `Offsite_To_B.cmd`, fill in the `{key}`.
6. In `renew.ps1`, set `$dns` (for example `db01.shipperxl.com`).
7. Run `vmsetup.ps1` with its parameters. Along the way you do these by hand:
   - Install [SQL Server Reporting Services 2022](https://www.microsoft.com/en-us/download/details.aspx?id=104502).
   - Report user ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/CreateReportUser.sql)).
   - Archive ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/_Archive.sql)):
     yearly, the first Saturday of every January.
   - Backups ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/_Backups.sql)):
     every hour.
   - Maintenance ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/_Maintenance.sql)):
     every Saturday at 12:00 PM UTC.
   - CreationQueue ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/_db03_CreationQueue.sql)):
     on DB04 only, every 15 minutes.
   - Linked server ([script](https://github.com/hurkin/shipper-db/blob/main/SpecialScripts/_db03_haaldb_linked_server.sql)):
     only for the sxl_hurkin server.
8. Run the GitHub Actions deployments for
   [reports](https://github.com/hurkin/shipper-reports/actions/workflows/shipper-reports.yml)
   and the
   [web service](https://github.com/hurkin/shipper-windows/actions/workflows/shipper-windows-webservices.yml).
9. Install [ShipperXL Desktop](../docs/instructions/install-desktop.md) on the VM.

## Troubleshooting

- [PowerShell 5.1 not accepting keyboard input](https://learn.microsoft.com/en-us/answers/questions/1192910/powershell-5-1-not-accepting-keyboard-input-when-u)
