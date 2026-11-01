# Sysmon Configuration – SwiftOnSecurity

## Overview
The Windows endpoint is monitored using Microsoft Sysmon with the community-maintained configuration from SwiftOnSecurity.

This configuration provides high-quality telemetry focused on process creation, network connections, file modifications, registry changes, and other events useful for threat detection and hunting.

## Why this configuration?
- Widely adopted in the security community
- Well-commented and balanced (good coverage with reduced noise)
- Excellent starting point for SOC labs and production environments
- Focuses on events relevant for incident investigation

## Installation
1. Downloaded Sysmon from Microsoft Sysinternals
2. Downloaded `sysmonconfig-export.xml` from the SwiftOnSecurity repository
3. Applied the configuration:

```powershell
C:\Windows\Sysmon64.exe -c "C:\path\to\sysmonconfig-export.xml"