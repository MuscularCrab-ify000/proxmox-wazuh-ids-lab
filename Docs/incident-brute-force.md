# Incident Write-up: Brute Force Attempt

## Summary
Multiple failed authentication attempts were detected against the Windows endpoint (`windows-agent`).

## Timeline
- **Date**: 2026-10-11
- **Detection**: Wazuh alerted on authentication failures (Event ID 4625)
- **Source**: Local simulation / failed logon attempts

## Evidence
- 27 authentication failure alerts
- MITRE ATT&CK: Brute Force
- Agent: windows-agent

## Investigation
1. Reviewed Security Events in Wazuh
2. Confirmed multiple Event ID 4625 (failed logons)
3. Identified the target account (`cat`)

## Response
- Alerts reviewed and documented
- No further malicious activity observed (lab simulation)

## Screenshots
- `Screenshots/brute force dashboard`
- `screenshots/events brute force`
- `Screenshots/event details`

## Lessons Learned
- Sysmon + Wazuh successfully detected authentication failures
- Importance of correlating Windows Event Logs with SIEM alerts