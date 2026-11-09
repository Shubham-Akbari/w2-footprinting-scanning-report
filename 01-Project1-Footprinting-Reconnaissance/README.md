# Project 1 — Footprinting & Reconnaissance (W2-PM1)

**Target:** `shubham-tech.in`
**Tool environment:** Kali Linux
**Program:** Networkwalks Cybersecurity Internship — Week 2

## Objective

Perform passive and semi-active reconnaissance against the target domain using multiple Kali Linux tools to gather publicly available information about its registration, hosting, DNS and security posture — **without** exploiting or attacking the target.

## Disclaimer

This reconnaissance was performed only against a domain I own / had written permission to test, for educational purposes as part of an authorized internship module. No exploitation was attempted.

## Screenshots & Findings

| # | File | Tool / Command | What it shows |
|---|------|-----------------|----------------|
| 1 | `1_whois.png` | `whois shubham-tech.in` | Domain registration details — registrar **GoDaddy**, created **31 Aug 2026**, expires **31 Aug 2027**, registrant state **Gujarat, IN** (all other contact fields redacted for privacy). |
| 2 | `2_whatweb.png` | `whatweb shubham-tech.in` | Web technology fingerprint — site responds **200 OK** on both HTTP (`3.33.130.190`) and HTTPS (`15.197.148.33`), built with **HTML5**, hosted in the **United States**, with client-side **Script** detected. |
| 3 | `3_nslookup.png` | `nslookup shubham-tech.in` | DNS resolution — two IPv4 addresses (`3.33.130.190`, `15.197.148.33`) and two IPv6/NAT64 addresses (`64:ff9b::321:82be`, `64:ff9b::fc5:9421`). |
| 4 | `4_curl.png` | `nslookup` + `curl -I https://shubham-tech.in` | HTTP response headers — **HTTP/1.1 200 OK**, `Content-Type: text/html`, `Content-Length: 114`. |
| 5 | `5_wafw00f.png` | `wafw00f shubham-tech.in` | Web Application Firewall check — generic detection sent **7 requests** and found **no WAF** protecting the site. |
| 6 | `6_dnsrecon.png` | `dnsrecon -d shubham-tech.in` | Full DNS enumeration — SOA/NS records (`ns39`/`ns40.domaincontrol.com`), A/AAAA records (matching Nslookup), a DMARC TXT record (`p=quarantine`), and no SRV records found. |

## Summary

The reconnaissance confirmed the domain is hosted behind GoDaddy-managed DNS, resolves to two public IPv4 and two NAT64 IPv6 addresses, runs a basic HTML5 web front end, has a DMARC policy configured, and currently shows **no WAF** protection by generic detection. These findings feed into the Risk Analysis section of the full penetration testing report.
