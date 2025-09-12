# Walking an Application

**Date Completed:** Sept 2025  

![Method: Browser-only](https://img.shields.io/badge/Method-Browser--only-informational)
![Evidence: Screenshots](https://img.shields.io/badge/Evidence-Screenshots-green)
![Flags: Redacted](https://img.shields.io/badge/Flags-REDACTED-blue)

## Tools Used
- [x] View Source
- [x] Inspector (Elements/CSS)
- [x] Debugger (JS breakpoints/step-through)
- [x] Network (request/response review)

## Evidence (Screenshots Only)
| Tool      | Screenshot(s) to include                                 | Notes |
|-----------|-----------------------------------------------------------|-------|
| View Source | `evidence/screenshots/view-source_highlight.png`        | Highlighted relevant HTML/comment (flags redacted) |
| Inspector  | `evidence/screenshots/inspector_before.png`, `inspector_after.png` | Before/after toggling `hidden` / `disabled` / CSS |
| Debugger   | `evidence/screenshots/debugger_paused.png`               | Paused at a breakpoint showing key variable/state |
| Network    | `evidence/screenshots/network_request.png`               | Specific request/response panel with interesting param/header (redacted) |

## Method (What I Did)
**View Source**
- Opened page source and reviewed human-readable HTML.
- Noted informative comments/strings relevant to progression. *(redacted in screenshots)*

**Inspector**
- Located DOM elements hidden via attributes/classes and toggled them to verify what appears.
- Edited text/attributes **temporarily** to confirm client-side gating. *(no permanent changes)*

**Debugger**
- Set a breakpoint at a relevant JS line/function and stepped execution to observe state changes.
- Verified which variable/branch controlled visibility or flow. *(screenshot shows paused state, redacted)*

**Network**
- Observed requests as actions occurred; inspected one response/param that influenced page behavior.
- Confirmed what data the client relied on vs. what the server returned.

## Key Takeaway (Redacted)
- Client-side controls (DOM/CSS/JS) influenced what was shown. After safe, temporary inspection steps, additional content became visible.
- **Mitigation:** Do not rely on client-side checks for authorization; enforce on the server and avoid leaking sensitive hints in source/comments.


