# IDOR

**Date Completed:** <Dec 2025>  

## Tools Used
- [x] 

## Method (What I Did)

**Manual Discovery — robots.txt**

**Manual Discovery — favicon**
- Path checked: `view-source:https://static-labs.tryhackme.cloud/sites/favicon/` (only avaible on created VM)
- Viewing the page source lead to me finding left over installiation of a favicon link. This allowed me to use the following command to get the md5 hash value for later research: `curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum`
- Using the OWASP favicon database, I search up the hash value `f276b19aabcb4ae8cda4d22625c6735f` and found that its framework is `cgiirc (0.5.9)`

**Manual Discovery — sitemap.xml**

## Key Takeaway
- Research is key to pent testing. Understanding who/what you're dealing with matters therefore you can find vulnerabilities. Many tools, browser or not, allow you to collect info to break/exploit systems.
