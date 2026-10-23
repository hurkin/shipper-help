# Install the ShipperXL Kiosk

These instructions are for IT staff. See [Hardware and Supplies](hardware.md) for
what to buy.

## Hardware

1. If you use cameras, set them up first so they are available on your network.
2. Assemble the stand and the barcode reader.
3. Plug in the scale's serial cable (it may need an adapter), the barcode reader, and
   the power.
4. Power up the tablet and connect it to your network.
5. Connect the _label_ printer and name it **labels**.
6. Connect the _standard_ printer and
   [make it the default](https://support.microsoft.com/en-us/windows/set-a-default-printer-in-windows-e10cf8b8-e596-b102-bf84-c41022b5036f).
7. Configure the barcode reader with its configuration sheet (see
   [Hardware and Supplies](hardware.md?id=desktop-barcode-scanner)).

## Set up the scale in Shipper

1. Add the scale in **Admin > Scales**. You need the COM port the serial cable is
   connected to.
2. Note the scale's id. The kiosk software asks for it.

Each scale supports one kiosk.

## Install the kiosk software

1. Download the
   [kiosk installer](https://hurkinapps.blob.core.windows.net/apps/downloads/Hurkin.Scale.Client.Setup.msi).
2. If [.NET 10](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) isn't
   installed, you are asked to install it. Install both the **ASP.NET Core Runtime
   10.0** and the **.NET Desktop Runtime 10.0** (Windows x64).
3. Enter your database code, license key and scale id.
4. Restart the computer if asked.

When the kiosk connects, it fills in the scale's service URL in Shipper.

See also: [Using the Kiosk](kiosk.md), [Scales](../context/B007.md),
[Label Printer Setup](label-printer.md).
