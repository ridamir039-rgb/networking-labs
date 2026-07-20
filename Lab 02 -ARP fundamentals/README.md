# Lab 02 — ARP Fundamentals

## Objective
Investigate how ARP (Address Resolution Protocol) works in 
practice — the full request/reply exchange, ARP cache behavior, 
packet field structure, broadcast vs unicast delivery, and how 
ARP fires automatically before every Layer 3+ communication 
on a local network.

---

## Environment
- Kali Linux (observer + initiator)
- Metasploitable2 (responder)
- Network: Internal Network (lab-0) — 192.168.56.0/24
- Kali: 192.168.56.10 | Metasploitable2: 192.168.56.20

---

## What Was Tested
- ARP request/reply exchange captured fresh after flushing 
  the ARP cache
- ARP cache state before and after resolution (`ip neigh`)
- Full ARP packet structure — every field in both request 
  and reply
- Broadcast vs unicast delivery: ARP Request goes to 
  ff:ff:ff:ff:ff:ff, ARP Reply goes unicast back to requester
- ARP triggering automatically before TCP/SSH — confirming 
  ARP fires before any Layer 3+ communication, not just ping

---

## Key Findings
- ARP exists because Ethernet needs MAC addresses to deliver 
  frames locally, but applications only know IP addresses — 
  ARP is the translation layer between them
- ARP Request is always broadcast (ff:ff:ff:ff:ff:ff) — 
  the sender doesn't know which device holds the target IP
- Target MAC in an ARP Request is always 00:00:00:00:00:00 
  — that's the unknown value being asked for
- ARP Reply is always unicast — Metasploitable2 replies 
  directly to Kali's MAC since it learned it from the request
- ARP cache entries have states: REACHABLE → STALE → FAILED; 
  caching avoids an ARP exchange before every single packet
- ARP fires automatically before SSH/TCP SYN — kernel 
  handles resolution transparently before any app-level 
  traffic hits the wire
- ARP has no authentication — any device can claim any IP, 
  which is the basis of ARP Spoofing attacks (covered in 
  a later lab)

---

## Files in This Lab
- `screenshots/` — one subfolder per task showing Wireshark 
  captures, cache state, and full packet field expansion
- `pcap/` — ARP capture files from Tasks 1 and 5
- `report/` — full PDF report

---

## Skills Demonstrated
- ARP cache management (`ip neigh flush`, `ip neigh`)
- Wireshark capture and filtering at Layer 2
- Reading ARP packet fields (opcode, hardware/protocol 
  type, sender/target MAC and IP)
- Understanding broadcast vs unicast at the Ethernet frame level
- Observing kernel-level ARP resolution triggered by 
  application traffic
