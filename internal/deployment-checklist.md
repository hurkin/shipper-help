# Deployment Checklist

When deploying a release of Shipper and/or Console:

1. Pick a date and time for the deployment, and work out the impact on users of every
   kind and device.
2. Send a MailChimp campaign about the release: the date and time, and what users
   need to do.

## Release timeline

**-08:00** (8 to 24 hours before the stated release)

- Update the ShipperXL system message in Console.

**-01:00**

- Pause the Database, Webservice and Reports pipelines in DevOps.
- Create a PR to merge to main.
- Monitor the pipelines. All client and web installers should run.
- Digitally sign the client executables.

**+00:00**

- Update the ShipperXL home page image in Console.
- Unpause the SXL Database, Webservice and Reports pipelines in DevOps.
- Delete all user sessions from the HAALService database.
- Remove the alert message.
- Update the ShipperXL version numbers in Console.
- Check every interface: ShipperXL, Kiosk, Mobile App, Job Agent.
