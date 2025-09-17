# Content Discovery

**Date Completed:** <Month YYYY>  

## Tools Used
- [x] robots.txt review
- [x] Favicon analysis (/favicon.ico)
- [x] sitemap.xml review
- [x] HTTP header inspection
- [x] Framework stack fingerprinting
- [ ] Google dorking
- [ ] Wappalyzer
- [ ] Wayback Machine
- [ ] GitHub code/search
- [ ] S3 bucket checks
- [x] Automated discovery (tool used: <…>)

## Method (What I Did)

**Manual Discovery — robots.txt**
- URL checked: `<http://10.201.7.34>/robots.txt` (only avaible on created VM)
- Content Displayed:
    - `User-agent: *`
    - `Allow: /`
    - `Disallow: /staff-portal`
- /staff-portal directory isn't availbe for web crawlings to view
- Did the same process for other sites to see different results

**Manual Discovery — favicon**
- Path checked: `view-source:https://static-labs.tryhackme.cloud/sites/favicon/` (only avaible on created VM)
- Viewing the page source lead to me finding left over installiation of a favicon link. This allowed me to use the following command to get the md5 hash value for later research: `curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum`
- Using the OWASP favicon database, I search up the hash value `f276b19aabcb4ae8cda4d22625c6735f` and found that its framework is `cgiirc (0.5.9)`

**Manual Discovery — sitemap.xml**
- URL checked: `http://10.201.7.34/sitemap.xml` (only avaible on created VM)
- Interesting path discovered: `<loc>http://10.201.7.34/s3cr3t-area</loc>`
- The other paths were normal intentional working client paths but there was no way of accessing this path on the main site. Secret path lead to a flag. 

**Manual Discovery — HTTP Headers**
- URL Curled: `curl http://10.201.7.34 -v`
- Produced useful headers such as server and version to use later for related vulnerabilities for that type. One of the headers was a flag.

**Manual Discovery — Framework Stack**
- Using the content given from the previous task, there is a comment at the bottom describing the framework that was used: `https://static-labs.tryhackme.cloud/sites/thm-web-framework` (only avaible on created VM)
- The link lead to the framework documentaition of the site which gave intel of login credentials of a directory not for client use. Adding `/thm-framework-login` to `http://10.201.7.34` lead to the login page. After entering credentials, a flag awaits. I already did this task in a different room because of my curiosity.

**OSINT — Google Dorking**
- Learned about the Dorks available and what they do. Example as `inurl:admin` which returns results that have admin in the url

**OSINT — Wappalyzer**
- Learned about the concept of Wappalyzer and purpose but didn't use it.

**OSINT — Wayback Machine**
- Same with Wayback Machine. Learned about concept but nver used it.

**OSINT — GitHub**
- Talked about Github, but never used.

**OSINT — S3 Buckets**
- Same with this task.

**Automated Discovery**
- fluff:
    - Used fluff `ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt -u http://10.201.77.31/FUZZ` on `http://10.201.77.31` to discover any hidden paths. Two hidden paths being private and development.log.
- dirb:
    - Used dirb `dirb http://10.201.77.31/ /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt` to an additional hidden path: /monthly which contained a flag.
- gobuster:
    - Used gobuster `gobuster dir --url http://10.201.77.31/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt` which discovered path already know or already discovered but just for practice.

## Key Takeaway
- Research is key to pent testing. Understanding who/what you're dealing with matters therefore you can find vulnerabilities. Many tools, browser or not, allow you to collect info to break/exploit systems.

