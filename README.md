# cc-edge-macos-diagnostic-reports-io

Cribl Edge pack for macOS diagnostic reports (`.ips`, `.crash`, `.panic`, `.diag`, `.hang`, `.spin`, `.shutdownStall`).

## Contents

| Path | What it does |
| --- | --- |
| `default/pipelines/macos_crash_reports/conf.yml` | Sets `index` `os` and `sourcetype` `macos:crashreport`; adds `crash_time_in_band` for in-band timestamps. |
| `default/breakers.yml` | `MacOS Crash Reports` breaker: one event per report. |
| `default/pipelines/route.yml` | Routes events with `sourcetype` `macos:crashreport` to the `macos_crash_reports` pipeline. |
| `tests/fixtures/macos_crash_reports/` | Fixtures for the `.ips` JSON-header and `Date/Time:` report forms. |

## Installation

Install the pack on a Cribl Edge worker. The pack declares no Sources. Connect a file Source to the `macos_crash_reports` pipeline by its id.

## Usage

Point a file Source at the macOS DiagnosticReports directories with the `MacOS Crash Reports` breaker ruleset.
Connect that Source to the `macos_crash_reports` pipeline.

To run the pipeline tests, start a Cribl container and run the test suite from `tests/`:

```sh
cd tests
pnpm install --frozen-lockfile
pnpm run test
```
