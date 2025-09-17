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
- Viewable HTML human comments, asset files, and links gave me the ability to find multiple flags through non-customer authorized sections and find secret files.
- A comment was left for future developing content which contained a link. The link lead to a admin related service which gave direction to the admin login page path and credentials for it.
- Multiple sources were listed in a assets folder. Site didn't have proper protection for it so access was available through /assets path. Leading to readable flag.

**Inspector**
- Inspected page reserved for premium customers only. Page covered content with pop-up blocker
- The pop-up blocker was used the style "display:block", by replacing block with "none", this removed the blocker and allowed me to access the next flag. 

**Debugger**
- Page flashed a box with a message every time the page was loaded. Used the sources tab to find the JavaScript responsible for it.
- By reloading the page, the page used a js in the assets folder called flash.mini.js. Upon opening the script, a line contained the removale of the box after it was inserted. Setting a breakpoint allowed the message to be viewable and contained a flag.

**Network**
- In contact page, format is set up by name then message. This service uses a method called AJAX.
- Using the network tab while sending messages, creates a new entry "contact-msg". Reviewing this entry with network tab showed a response to the entry that contained a flag.

## Key Takeaway
- Hacking can simply be done by jsut viewing the content and connecting the dots after observation. Having a site be vulnerable to simple brower tools creates high risks due to the free cost of the tool, thus every user has access to the tool to hack your site. 


