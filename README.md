# status

Part of statuspage, an uptime monitor. This repo stores and shows check results:

- `status-api` registers monitors, serves the monitor list to check-scheduler, and serves current state and uptime history from Postgres.
- `result-ingester` reads the `results` stream from the checks team's Redis, writes results, and opens and closes incidents.
- `status-web` is the page at `status.localhost`.
- `rollup` is an hourly CronJob that writes aggregates. Raw results are kept 7 days.

The checks themselves run in [toil-lab/checks](https://github.com/toil-lab/checks).

The developer agent writes the code and each service's `service.yaml`. The
DevOps agent owns `.github/`, `CODEOWNERS`, and `toil.json`. A human approves
every merge. The services arrive in phase 4.
