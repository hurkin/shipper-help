# ShipperXL APIs

ShipperXL has REST APIs for building your own apps and integrations.

- [HAAL API](https://documenter.getpostman.com/view/262290/2sAYdcrXZh): sign-in,
  users and databases.
- [Shipper API](https://documenter.getpostman.com/view/262290/2sAYdcrXZf): your
  ShipperXL data.

## Authentication

All authentication goes through HAAL, with either an API key or a user name and
password. For server apps, API keys are preferred.

## A typical user flow

1. The user gives their email address to your app.
2. Your app gets the list of ShipperXL databases they can use:
   `https://secure.hurkin.com/api/shp/user/instances?user=user@example.com`
3. The user gives their password.
4. Your app gets an authenticated session, with Basic authentication. The database
   code chosen is part of the URL for authentication, for example
   `https://secure.hurkin.com/api/shp/{database}/session`. The session returns a
   session id, user details, roles, feature access and settings.
5. To look up inventory for a SKU, your app calls the specific Shipper service for your database:
   - The base URL comes from the **SVCURL** setting in the session.
   - The ItemSKUId is part of the URL.
   - Use a Bearer authentication header with the base64-encoded session id

   For example, `https://api.shipperxl.com/api/sku/1764` returns the inventory for
   that SKU.

## A typical api-key flow

1. Your app gets an authenticated session using an api-key header. The database
   code chosen is part of the URL for authentication, for example
   `https://secure.hurkin.com/api/shp/{database}/session`. The session returns a
   session id, roles, feature access and settings.
2. To look up inventory for a SKU, your app calls the specific Shipper service for your database:
   - The base URL comes from the **SVCURL** setting in the session.
   - The ItemSKUId is part of the URL.
   - Use a Bearer authentication header with the base64-encoded session id, or use an api-key header with the API key (not encoded)

   For example, `https://api.shipperxl.com/api/sku/1764` returns the inventory for
   that SKU.

## Notes
   - Some endpoints include paging. The default paging is 250 items. If the rows received is 250, then call the next page for additional rows until the rows received is less than 250.

## Related

[Using Power BI](power-bi.md) · [Using Report Builder](report-builder.md) ·
[Create Custom Reports](custom-reports.md)
