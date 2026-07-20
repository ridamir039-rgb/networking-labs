# Lab 01 — Packet Capture Fundamentals

## Objective
Investigate how packet capture works at the interface level — 
what Wireshark and tcpdump are actually doing, why promiscuous 
mode matters, and the practical difference between capture 
filters and display filters.

---

## Environment
- Kali Linux (analysis machine) running Wireshark + tcpdump
- Metasploitable2 (traffic generator)
- Network: Internal Network (lab-0) — 192.168.56.0/24
- Kali: 192.168.56.10 | Metasploitable2: 192.168.56.20

---

## What Was Tested
- Baseline bidirectional capture — ICMP request and reply 
  visibility on a single interface
- Promiscuous mode ON vs OFF — what traffic is visible 
  in each state and why
- Capture filter (`icmp`) vs display filter (`icmp`) — 
  data retention difference between the two approaches
- tcpdump command-line capture saved to `.pcap` and opened 
  in Wireshark — confirming both tools share the same 
  underlying library
- Layer-by-layer packet inspection: Frame → Ethernet II 
  → IPv4 → ICMP with every field expanded and explained

---

## Key Findings
- A capture on eth0 is bidirectional — both inbound and 
  outbound frames are captured at the same interface
- Promiscuous mode allows the NIC to accept frames not 
  addressed to its own MAC; without it, unicast traffic 
  to other hosts is dropped at hardware level before the 
  OS ever sees it
- Broadcast frames (like ARP) are always visible regardless 
  of promiscuous mode — the NIC always accepts broadcasts
- Capture filter discards non-matching packets permanently 
  at capture time — they cannot be recovered later
- Display filter hides non-matching packets from view but 
  retains them in the capture — fully reversible
- tcpdump and Wireshark both sit on top of libpcap; a 
  .pcap file saved by either tool is readable by both

---

## Files in This Lab
- `screenshots/` — one subfolder per task with annotated 
  Wireshark and terminal screenshots
- `pcap/capture.pcap` — raw packet capture from Task 4 
  (tcpdump output)
- `report/` — full PDF report

---

## Skills Demonstrated
- Wireshark interface configuration and capture setup
- Understanding NIC promiscuous mode at hardware level
- Applying and distinguishing capture vs display filters
- Command-line packet capture with tcpdump
- Reading and interpreting packet layers in Wireshark 
  (encapsulation, protocol fields, TTL, checksums)
