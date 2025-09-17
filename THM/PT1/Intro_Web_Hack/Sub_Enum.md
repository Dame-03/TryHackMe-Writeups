# Subdomain Enumeration

**Date Completed:** Sept. 2025  

## Tools Used
- [x] OSINT – SSL/TLS certificate transparency logs crt.sh
- [x] OSINT – Search engines (dorking)
- [x] DNS brute force: Dnsrecon
- [x] OSINT – Sublist3r
- [x] Virtual host enumeration fluff

## Method (What I Did)

**OSINT — SSL/TLS Certificates**
- Using `https://crt.sh/` to search tryhackme.com to find a list of certificates. Specifically looking for the entry for 2020-12-26. 
- That entry was `store.tryhackme.com` which allowed me to progress to the next task. 

**OSINT — Search Engines**
- Dork used:  `site:*.tryhackme.com -site:www.tryhackme.com`
- practicing using dorks to find specific content. This dork searches for subdomains for tryhackme.com
- Using this Dork, I got `store.tryhackme.com` which allowed me to progress further.

**DNS Bruteforce**
- Command ran: `dnsrecon -t brt -d acmeitsupport.thm'
- Gave me twi results but was only looking for `api.acmeitsupport.thm`
- dnsrecon allowed me to use a list of common subdomain names to request for each name.

**OSINT — Sublist3r**
- Command ran: `./sublist3r.py -d acmeitsupport.thm`
- Used sublist3r to speed the process of the above OSINT methods. 
- Gained 2 subdomain results but the important one was `web55.acmeitsupport.thm`

**Virtual Hosts**
- Using `ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.17.130` we can discover a new subdomain name. However, the result needs to be filtered. So after running the command, I identify the most reoccuring size, which is 2395, plug it into `ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.17.130 -fs 2395`
- This gave me two subdomain results. delta and yellow acting as flags for completing the room.

## Key Takeaway
- There are many ways for searching for subdomains from searching for a certificate, using a list of common subdomain names, to using a virtual version of DNS bruteforcing. This lets me know that subdomains need to be on the look out as they can be the reason for additional info to the attacker.
