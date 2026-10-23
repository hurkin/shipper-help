# Deployment Checklist

When deploying a release of Shipper and/or Console:

1. Pick a date and time for the deployment, and work out the impact on users of every
   kind and device.
2. Send a MailChimp campaign about the release: the date and time, and what users
   need to do.

## Release timeline

**-08:00** (8 to 24 hours before the stated release)

- Update the ShipperXL system message in Console.

**-01:00 or -00:30** prior to release, depending upon release size

- Create PRs to merge to _main_ on each repo, in order, as follows:
   - `haal-api`
   - `haal-ui`
   - `shipper-db`
   - `shipper-api`
   - `shipper-svc`
   - `shipper-kiosk`
   - `shipper-windows`


**+00:00** stated release completion time

- Update the ShipperXL home page and help urls in [Console](https://secure.hurkin.com).
- Remove the alert message.
- Update the ShipperXL version numbers in Console.
- Check every interface: ShipperXL, Kiosk, Mobile App, Job Agent.
