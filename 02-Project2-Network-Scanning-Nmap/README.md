# Project 2 — Network Scanning with Nmap/Zenmap (W2-PM5)

**Target:** Local LAN subnet — `192.168.56.0/24`
**Tool environment:** Nmap (Zenmap GUI)
**Program:** Networkwalks Cybersecurity Internship — Week 2

## Objective

Perform host discovery on my own local network to identify live hosts, their IP addresses and MAC addresses, and generate a network topology diagram.

## Disclaimer

This scan was performed only against my own local LAN network, which I own, for educational purposes as part of an authorized internship module. No exploitation was attempted.

## Screenshots & Findings

| # | File | Tool / Command | What it shows |
|---|------|-----------------|----------------|
| 1 | `1_nmap_ping_scan.png` | `nmap -sn 192.168.56.0/24` | Ping scan of the local subnet — scanned **256 IP addresses** in **5.58 seconds** and found **2 live hosts**: `192.168.56.1` and `192.168.56.100`. The host `192.168.56.100` returned MAC address **08:00:27:6D:BD:BE**, identified as an **Oracle VirtualBox virtual NIC**. |
| 2 | `2_network_topology.jpg` | Zenmap → **Topology** tab (saved as PDF/image) | Visual network topology showing `localhost` connected to the two discovered hosts, `192.168.56.1` and `192.168.56.100`, both marked as live (green). |

## Summary

The ping scan confirmed only 2 active hosts on the `192.168.56.0/24` subnet at scan time — the gateway/host machine (`192.168.56.1`) and a VirtualBox virtual machine (`192.168.56.100`, identified by its Oracle NIC MAC prefix). No unexpected or unknown devices were found. These findings feed into the Risk Analysis section of the full penetration testing report.
