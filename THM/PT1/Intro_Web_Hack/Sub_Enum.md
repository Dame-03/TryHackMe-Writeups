# Subdomain Enumeration

**Date Completed:** <Sept. 2025>  

## Tools Used
- [ ] OSINT – SSL/TLS certificate transparency logs (e.g., crt.sh)
- [ ] OSINT – Search engines (dorking)
- [ ] DNS brute force (tool: <…>, wordlist: <…>)
- [ ] OSINT – Sublist3r
- [ ] Virtual host enumeration (Host header / wordlist)

## Method (What I Did)

**OSINT — SSL/TLS Certificates**
- Where I looked: <site / CT log URL or platform>
- Evidence that helped (sanitized): <domain(s) or patterns>
- Result (redacted): <…>

**OSINT — Search Engines**
- Dorks used (sanitized): <…>
- Useful hits/leads: <…>
- Result (redacted): <…>

**DNS Bruteforce**
- Command(s) run: `<tool> -d <target> -w <wordlist> <flags>`
- Notable findings (sanitized): <…>
- Validation step (how I confirmed): <…>

**OSINT — Sublist3r**
- Command(s): `sublist3r -d <target> -o results.txt`
- Cross-check/validation: <…>
- Result (redacted): <…>

**Virtual Hosts**
- Approach: Host header fuzzing against a target IP / wildcard vhosts
- Command(s): `<tool> -u http://<ip> -H "Host: FUZZ.<domain>" -w <wordlist>`
- Positive indicators (responses/codes/lengths): <…>

## Key Takeaway
- Mapping subdomains via OSINT, brute force, and vhost probing expands attack surface quickly; cross-validating results avoids chasing noise. (No spoilers.)
