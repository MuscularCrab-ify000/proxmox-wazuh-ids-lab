# SOC Home Lab - Proxmox + Wazuh

Security Operations Center home lab built on Proxmox VE to practice threat detection, log analysis, and incident response.

## Objective

Build a realistic SOC Analyst environment with:
- Endpoint monitoring (Windows + Sysmon)
- Open-source SIEM (Wazuh)
- Attack simulation
- Alert investigation and documentation

## Architecture

| VM              | OS                  | Role                      | Resources    |
|-----------------|---------------------|---------------------------|--------------|
| wazuh-siem      | Ubuntu Server 24.04 | SIEM / XDR                | 4 vCPU / 8GB |
| win-endpoint    | Windows 11          | Monitored endpoint        | 2 vCPU / 4GB |
| kali            | Kali Linux          | Attack machine            | 2 vCPU / 4GB |

## Stack

- **Hypervisor**: Proxmox VE
- **SIEM**: Wazuh
- **Endpoint Telemetry**: Sysmon (SwiftOnSecurity config)
- **Attack Simulation**: Kali Linux + Atomic Red Team

## Status

- [ ] Proxmox configured
- [ ] Isolated network created (vmbr1)
- [ ] Wazuh installed
- [ ] Wazuh agent on Windows
- [ ] Sysmon installed
- [ ] First attack simulated (brute force)
- [ ] Incident write-up

## Repository Structure
