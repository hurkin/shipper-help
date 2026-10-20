# Internal (developers and operations)

Moved from support.hurkin.com/shipper/dev. This folder isn't published on the help
site (only `docs/` is), but **this repo is public**, so anything here can be read on
GitHub.

- [Team process](process.md): work items, releases, time sheets, dev machine setup
- [Architecture](architecture.md)
- [Custom plug-ins](custom-plug-ins.md) for ShipperXL Desktop
- [VM configuration](vm-configuration.md)
- [Deployment checklist](deployment-checklist.md)

Customer-facing developer pages are on the help site:
[ShipperXL APIs](../docs/instructions/api.md) and
[QuickBooks Service](../docs/instructions/quickbooks-service.md). Release notes from
before 2026 are in [the archive](../docs/release-notes/archive.md).

## Links

- **Development:** [Postman](https://interstellar-water-13009.postman.co/workspace/HURKIN-APIs~bd5803c1-6572-48da-8265-2f6066aa04ec) ·
  [Cloudflare DNS](https://dash.cloudflare.com/2c887dfc12d224f55896468610eab1cb/hurkin.com/dns/records) ·
  [Backlog](https://github.com/orgs/hurkin/projects/1)
- **Operations:** [K8s metrics](https://hurkin.grafana.net/a/grafana-metricsdrilldown-app/drilldown?from=now-12h&to=now&timezone=browser&var-metrics_filters=cluster%7C%3D%7Caks-prod-wus2&var-filters=cluster%7C%3D%7Caks-prod-wus2&var-labelsWingman=namespace&layout=grid&filters-rule=&filters-prefix=container:cpu,container:memory&filters-suffix=&search_txt=&filter-firing-alerts=&var-metrics-reducer-sort-by=default&filters-recent=&var-ds=grafanacloud-prom&var-other_metric_filters=filters-prefix,prefix%7C%3D%7Ccontainer%20%3E%20cpu__gfc__%20container%20%3E%20memory&refresh=auto&var-wingmanLabelValues=$__all&actionView=breakdown) ·
  [K8s logs](https://hurkin.grafana.net/a/grafana-lokiexplore-app/explore?patterns=%5B%5D&var-primary_label=service_name%7C%3D~%7C.%2B&from=now-12h&to=now&timezone=browser&var-ds=grafanacloud-logs&var-filters=cluster%7C%3D%7Caks-prod-wus2&var-filters=job%7C%21%3D%7Cvarlogs&var-fields=&var-levels=&var-metadata=&var-all-fields=&var-patterns=&var-lineFilterV2=&var-lineFilters=&var-filters_replica=cluster%7C%3D%7Caks-prod-wus2&var-filters_replica=job%7C%21%3D%7Cvarlogs&refresh=auto) ·
  [Dashboard](https://app.powerbi.com/groups/52700061-9b11-4e8d-b7bd-9266b9ec5929/reports/1169497b-7b02-4435-8749-8f50497e77fd/1c767a80b540d6befd2d?experience=power-bi) ·
  [Azure](https://portal.azure.com/#home) ·
  [ShipsGo](https://shipsgo.com/dashboard)
- **Accounting:** [Zoho Books](https://books.zoho.com/) · [Ting](https://ting.com/account) ·
  [Stripe](https://dashboard.stripe.com/) · [Wise](https://wise.com/home)
