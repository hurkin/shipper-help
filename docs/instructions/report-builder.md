# Using Report Builder

Report Builder makes real-time operational reports that run inside Shipper, like
the standard ones. It needs report server credentials from support@shipperxl.com,
which cost extra. See [Create Custom Reports](custom-reports.md).

## Learn the tools

1. Download [Report Builder](https://www.microsoft.com/en-us/download/details.aspx?id=42301).
2. Learn it with Microsoft's
   [Reporting Services tutorials](https://learn.microsoft.com/en-us/sql/reporting-services/reporting-services-tutorials-ssrs).
3. Learn to [write T-SQL](https://learn.microsoft.com/en-us/sql/t-sql/tutorial-writing-transact-sql-statements).
4. Follow the patterns in the standard reports. To get a standard report's
   definition, contact support.

## Report properties

- **Language:** set to `=User!Language`.
- **Description:** set to the report's feature code (such as `R163`). It ties the
  report to the feature permissions that decide who sees it. **If the code isn't a
  known feature, the report isn't shown.** In the web app, a custom report with no
  description is shown to everyone.

## Parameters Shipper fills in

These parameters are replaced with values from the user's session when the report
runs. Use only the ones you need.

| Parameter | Value |
|---|---|
| `CNN` | Connection string |
| `TIMEOFFSET` | The current offset from UTC, in minutes (Pacific Standard Time is -480) |
| `IMG` | Your company logo's URL |
| `ALIAS` | The user's alias |
| `USERID` | The user's account id |
| `USERPARTY` | The id of the user's contact record |
| `Locale` | The 5-character locale, such as `en-US` |
| `IsGlobal` | If present, the report shows on the main menu even if other rules would hide it |
| `REPORT` | The name of the report as it was run |
| `WEBURL` | The web app's address, such as `https://example.com/shipper`. Web app only |

If a parameter has the same name as a screen's key, such as `BookingId` on a
booking, the report is offered on that screen automatically.

## Links in reports

To open a Shipper screen from a report, give a text box a hyperlink action with
this URL:

```
http://autourl.aspx?[FEATURE]=[ID]
```

`[FEATURE]` is the screen's feature code and `[ID]` (optional) is the record's
database id. For example, `http://autourl.aspx?B008=12345` opens booking 12345.

To open an attachment:

```
="javascript:void(window.open('autourl.aspx?ATT=30717&FN=2011-08-17-020933.jpg','_new'))"
```

where `30717` is the attachment id and `2011-08-17-020933.jpg` its file name.

In the web app, a report can link to a record's page with `WEBURL`, for example
`=Parameters!WEBURL.Value & "/workorders/" & Fields!WorkOrderId.Value`.

## Where to save

- Save custom reports in `/Custom/[your folder]`.
- **A custom report with the same feature code as a standard report replaces it**
  everywhere, and takes its permissions. In the web app it also takes the standard
  report's name, marked **Custom**.
- Otherwise custom reports show only under [Custom Reports](../context/CUSTREPS.md).

## Related

[Create Custom Reports](custom-reports.md) · [Using Power BI](power-bi.md) ·
[Custom Fields](../context/G009.md)
