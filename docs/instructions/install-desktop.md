# Install ShipperXL Desktop

ShipperXL Desktop is the full-featured Windows app for day-to-day work.

- Requires Windows 10 or 11.
- You must be signed in to Windows as an administrator to install it.

[Download ShipperXL Desktop](https://hurkinapps.blob.core.windows.net/apps/prod/Hurkin.Shipper.Client.Setup.msi)

The app updates itself: after a release it asks to update the next time you start
it or sign in.

## The web application

The web app works on the same database as the desktop app, so you can work in
either. Sign in at [https://app.shipperxl.com](https://app.shipperxl.com).

## Troubleshooting

- **Nothing happens when you open the app.** Your profile files may be damaged.
  Open `%appdata%\..\Local\HURKIN_Software`, delete the folders and files there,
  and try again.
- **"The system cannot find the file specified. (Exception from HRESULT:
  0x80070002)" on the home page.** Install the
  [Microsoft Edge WebView2 runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section).

See also: [Test Versions](test-versions.md).
