# Walking an Application

**Date Completed:** Sept 2025  

## Tools Used
- [x] View Source
- [x] Inspector (Elements/CSS)
- [x] Debugger (JS breakpoints/step-through)
- [x] Network (request/response review)

## Method (What I Did)

**View Source**
- Opened page source and reviewed human-readable HTML.
- Comments, asset links, and internal paths revealed multiple flags in non-customer pages and exposed “secret” files.
- A developer comment contained a link to an admin-related service, which disclosed the admin login path and credentials.
- The `/assets` directory listed multiple resources; with no protection, direct access to that path exposed a readable flag.

**Inspector**
- Inspected a page reserved for premium customers that was covered by an overlay “pop-up blocker.”
- The overlay used `display: block`; switching it to `display: none` removed the blocker and exposed the next flag.

**Debugger**
- A message box flashed briefly on load. In **Sources**, found the JavaScript responsible (e.g., `assets/flash.mini.js`).
- Reloaded and set a breakpoint on the line that removed the box. Pausing execution kept the message visible and it contained a flag.

**Network**
- On the contact page, submissions were sent via AJAX.
- Watching **Network** while sending a message showed a `contact-msg` request; inspecting its response revealed a flag.

## Key Takeaway
- You can uncover real issues with **just the browser** by reading source, editing the DOM, pausing JS, and inspecting requests/responses. Relying on client-side controls (overlays, comments, exposed assets, or verbose AJAX responses) creates risk because every user has these tools for free.



