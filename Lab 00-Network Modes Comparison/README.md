# Lab 00 — VirtualBox Network Mode Comparison

## Objective
Investigate how all five VirtualBox network adapter modes affect 
connectivity between Kali Linux and Metasploitable2, and establish 
which mode to use for which type of future lab.

---

## Environment
- Kali Linux 2026.2 + Metasploitable2 in VirtualBox 7.2.12
- Host: Windows 11
- Both VMs tested across all five modes identically

---

## What Was Tested
- IP address assignment behavior per mode (automatic vs manual)
- VM-to-VM connectivity in both directions via ping
- Internet access from each VM
- Host-to-VM reachability from Windows PowerShell
- Exact error messages on failure (timeout vs unreachable — 
  these mean different things)

---

## Key Findings
- NAT gives each VM its own isolated bubble — both VMs got 
  identical IPs (10.0.2.15) with no conflict, but cannot 
  reach each other at all
- NAT Network places VMs on a shared network — VM-to-VM 
  communication works, internet works, host access does not
- Host-Only provides VM-to-VM + host access but no internet; 
  the Windows host has a dedicated virtual interface into 
  this network
- Internal Network is the strictest mode — VM-to-VM only, 
  no host access, no internet, no DHCP (manual IP required); 
  chosen as the default for all offensive labs in this repo
- Bridged makes VMs full peers on the real physical LAN — 
  full access everywhere but exposes Metasploitable2 to the 
  real network, which is a security risk
- "Network is unreachable" and a ping timeout are completely 
  different failures — one means no route exists, the other 
  means a route exists but nobody answered

---

## Files in This Lab
- `screenshots/` — adapter config + ip a output + all ping 
  tests per mode, organized by mode subfolder
- `diagrams/` — architecture diagram per mode showing traffic 
  flow and isolation boundaries
- `report/` — full PDF report (objective → config → diagrams 
  → screenshots → result tables → analysis → conclusion)

---

## Skills Demonstrated
- VirtualBox network adapter configuration
- Reading `ip a` output and interpreting addressing
- Understanding subnet boundaries and routing decisions
- Distinguishing network isolation levels and their 
  security implications
- Selecting appropriate lab network topology for a 
  given objective
