# Data note

## Source

Seattle Real Time Fire 911 Calls, City of Seattle Open Data portal (data.seattle.gov), dataset maintained by the Seattle Fire Department.

- Portal: https://data.seattle.gov/Public-Safety/Seattle-Real-Time-Fire-911-Calls/kzjm-xkqj
- Access: public, no key required (Socrata API / CSV export)
- License: City of Seattle open data terms (public domain dedication for city data; see the portal page)

## Coverage used here

- Window: 2024-01-01 to 2026-11-24 (1,059 days)
- Records after cleaning: 351,099 incidents
- Fields used: incident datetime, incident type, address-derived location

## Preparation

1. Exported the full CSV from the Socrata endpoint (~47 MB uncompressed).
2. Parsed timestamps to local time (America/Los_Angeles); dropped rows with missing or unparseable datetimes or types.
3. Grouped the raw incident types into four analysis categories: Medical / aid (75%), Fire & alarms, Vehicle incidents, Other.
4. Aggregated to hourly counts by day, weekday, month, type and map cell; all published figures come from these aggregates.

## Honest limits

- "Calls" here are fire/EMS dispatches, not police calls and not call-center phone calls; the staffing model is a worked example on real demand, not Seattle's actual roster.
- Agent-hour conversion uses an assumed average service time and a P90 buffer; both are stated on the Fix tab and easy to change.
- Location is as reported at dispatch time; a small share of records lacks usable coordinates and is excluded from the map analysis only.
