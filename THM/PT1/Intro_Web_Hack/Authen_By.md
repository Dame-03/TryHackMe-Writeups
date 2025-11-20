# Authentication Bypass

**Date Completed:**  in progress

## Tools Used
- [x] ffuf
- [ ]  

## Method (What I Did)

**Username Enumeration - ffuf**
- Used ffuf to brute-force / enumerate valid usernames on a signup form by abusing the “username already exists” error message.
- Used `ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/signup -mr "username already exists"` to discover all valid usernames for the the URL `http://10.201.115.109/customers/signup` (VM Only)
- Placed results in txt file for later use which contained `admin, robert, simon, steve`

**something**


## Key Takeaway
- ...

