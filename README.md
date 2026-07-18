# Cybersecurity-Labs

A structured, hands-on cybersecurity lab portfolio built while 
self-studying offensive and defensive security concepts. Each lab 
is an original investigation of one specific topic — not a tutorial 
walkthrough — with real captured evidence, documented findings, and 
written analysis.

Built on: Kali Linux + Metasploitable2 in VirtualBox  
Focus areas: Networking, Packet Analysis, Reconnaissance, 
Exploitation, Detection

---

## Repository Structure

cybersecurity-labs/
├── lab-00-virtualbox-network-modes/
│   ├── screenshots/
│   │   ├── nat/
│   │   ├── natnetwork/
│   │   ├── bridged/
│   │   ├── hostonly/
│   │   └── internal/
│   ├── diagrams/
│   ├── report/
│   └── README.md
│
├── lab-01-packet-capture-fundamentals/
│   ├── screenshots/
│   │   ├── task1-baseline/
│   │   ├── task2-promiscuous/
│   │   ├── task3-filters/
│   │   ├── task4-tcpdump/
│   │   └── task5-layers/
│   ├── pcap/
│   ├── report/
│   └── README.md
│
├── lab-02-arp-fundamentals/
│   ├── screenshots/
│   │   ├── task1-arp-capture/
│   │   ├── task2-arp-cache/
│   │   ├── task3-packet-structure/
│   │   ├── task4-broadcast/
│   │   └── task5-arp-before-tcp/
│   ├── pcap/
│   ├── report/
│   └── README.md
│
├── lab-03-icmp-ping-traceroute/     [coming soon]
├── lab-04-tcp-three-way-handshake/  [coming soon]
├── lab-05-udp-vs-tcp/               [coming soon]
├── lab-06-dns-resolution/           [coming soon]
└── lab-07-nmap-scanning/            [coming soon]

---

## Labs Index

| Lab | Topic | Status |
|-----|-------|--------|
| lab-00 | VirtualBox Network Mode Comparison | ✅ Complete |
| lab-01 | Packet Capture Fundamentals | ✅ Complete |
| lab-02 | ARP Fundamentals | ✅ Complete |
| lab-03 | ICMP / Ping / Traceroute | 🔄 In Progress |
| lab-04 | TCP Three-Way Handshake | 🔜 Upcoming |
| lab-05 | UDP vs TCP Comparison | 🔜 Upcoming |
| lab-06 | DNS Resolution | 🔜 Upcoming |
| lab-07 | Nmap Scanning Against Metasploitable2 | 🔜 Upcoming |

---

## Lab Environment

- Host: Windows 11, Intel Core i7-1355U, 8GB RAM
- Hypervisor: Oracle VirtualBox 7.2.12
- Attacker Machine: Kali Linux 2026.2 (2GB RAM, 2 CPUs)
- Target Machine: Metasploitable2 — Ubuntu 8.04-based, 
  intentionally vulnerable (512MB RAM, 1 CPU)
- Primary Network Mode: Internal Network (isolated, 
  no internet, no host access — clean lab traffic only)
- Tools: Wireshark, tcpdump, nmap, netcat, hydra, john


