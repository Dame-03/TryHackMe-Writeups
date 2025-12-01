# IDOR

**Date Completed:** Dec 2025  

## Tools Used
- [x] Broswer Inspect Tool

## Method (What I Did)

**IDOR — IDOR Example**
- Used the example TryHackMe site to learn and identity the IDOR vulnerablity. The IDOR vulnerability was in the URL `https://onlinestore.thm/order/1234/invoice`. I changed the `1234` to `1000` to obtained a different users account that lead to the flag `THM{IDOR-VULN-FOUND}`

**IDOR — Finding IDORS**
- Learned how to find IDORs in encoded, hashed, and unpredicatble IDs. Decode IDs, use hash websites, or create different accounts to determine if login access is achievable from those accounts. Understood where to locate one as they're not always in the URL and can be seen through a different paremter like browser loads via AJAX requests.

**IDOR - practical example**
- Created an account and was given an ID=5. Inspecting the page on the network section, found `https://10-65-190-145.reverse-proxy.cell-prod-us-east-1b.vm.tryhackme.com/api/v1/customer?id=5`. I changed the id to = 1 and found the users username and email. `adam84` and `adam-84@fakemail.thm` Did the same for ID=3 and username= `john911` and email= `j@fakemail.thm`


## Key Takeaway
- Ensuring a protocol to detect privledges when requesting access is important. Skipping the login process by entering in different session values shouldn't allow users to bypass without entering correct credentials to gain access to privileges.
