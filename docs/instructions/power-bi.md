# Using Power BI

Power BI is for analysis: trends over time, not real-time numbers. See
[Create Custom Reports](custom-reports.md) for the other options.

## You need

- [Power BI Desktop](https://powerbi.microsoft.com/desktop/). You can also publish
  to the [Power BI service](https://app.powerbi.com), which needs a Microsoft 365
  subscription and lets you share reports, build dashboards and mobile views, and
  refresh data on a schedule.
- Your database code.
- An API-KEY which you can obtain by contacting [support@shipperxl.com](mailto:support@shipperxl.com)
- This [sample file](https://hurkinapps.blob.core.windows.net/apps/downloads/SemanticModel.pbix).

## Connect

1. Save the sample file with your database's name, such as `ACME.pbix`.
2. Open it in Power BI Desktop.
3. Choose **Transform data > Edit parameters**.

   ![[power-bi-edit-parameters.png|300]]
4. Enter your database as the **Instance** and enter your API-KEY, and click **OK**.

   ![[power-bi-instance.png|500]]
5. Click **Apply changes**.

   ![[power-bi-apply-changes.png|500]]
6. When connecting, choose Anonymous.

## Good to know

This is powerful and somewhat complicated:

- Double-check your numbers before you trust them.
- Focus on why you want the data. What decision are you trying to make?
- Data is refreshed as often as you like, but isn't real-time.
- It is meant for watching trends over time.
- It can forecast the future, but only as well as the data you have given it.

## Related

[Create Custom Reports](custom-reports.md) ·
[Using Report Builder](report-builder.md)
