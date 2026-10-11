# Lab Architecture

## Overview

This lab is built on Proxmox VE and simulates a small Security Operations Center environment. The goal is to generate realistic telemetry, detect attacks, and document investigations.

## Network Design

Two Linux bridges are used on the Proxmox host:

- **vmbr0** — Connected to the home network (management + internet access)
- **vmbr1** — Isolated lab network (no gateway)

Attack traffic stays inside `vmbr1` and never touches the real network.

## Virtual Machines

| VM Name         | OS                  | Network | Purpose                          | Resources     |
|-----------------|---------------------|---------|----------------------------------|---------------|
| wazuh-siem      | Ubuntu Server 24.04 | vmbr0   | Wazuh Manager + Indexer + Dashboard | 4 vCPU / 8 GB |
| win-endpoint    | Windows 11          | vmbr1   | Monitored endpoint with Sysmon   | 2 vCPU / 4 GB |
| kali            | Kali Linux          | vmbr1   | Attack simulation machine        | 2 vCPU / 4 GB |

## Data Flow

1. Sysmon runs on the Windows endpoint and generates detailed process, network, and registry events.
2. The Wazuh agent on Windows collects these events and forwards them to the Wazuh Manager.
3. Wazuh applies its ruleset and generates alerts.
4. Alerts are visible in the Wazuh Dashboard.

## Isolation Notes

- The Windows and Kali VMs only have a network interface on `vmbr1`.
- The Wazuh server has an interface on `vmbr0` so it can be accessed from the host and can download updates.
- Optional: a second NIC can be added to Windows/Kali on `vmbr0` solely for agent communication if needed.

## Future Improvements

- [ ] Add a Domain Controller (Windows Server)
- [ ] Deploy Suricata for network detection
- [ ] Integrate Atomic Red Team for automated attack simulation
- [ ] Create custom Wazuh rules for specific techniques