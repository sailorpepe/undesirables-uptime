# undesirables-uptime

Always-on uptime + freshness monitor for **oracle.the-undesirables.com**, run on
GitHub Actions (independent of the Mac Mini/Studio, so it still alerts if either
box is down).

Every 15 min it verifies:
1. `/health` returns 200 with `status: ok` (oracle live)
2. `latest_date` isn't >2 days stale (daily pipeline alive)
3. a paid endpoint returns `402` (x402 rail + gating alive)

On failure it pushes an alert to **ntfy topic `undsr-oracle-watch-4441`** and
fails the run (GitHub also emails the owner). Subscribe on the ntfy app to get
phone pushes. No secrets; public health checks only.
