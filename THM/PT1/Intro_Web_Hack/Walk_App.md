# Walking an Application

**Date Completed:** Sept 2025  
**Tools Used:** Browser Developer Tools (Elements, Console, Network, Sources, Application)

## Summary
Manually reviewed a web application using only the browser’s developer tools. Practiced revealing hidden/disabled DOM, inspecting client-side code, analyzing HTTP requests/responses, and enumerating client storage (cookies, localStorage, sessionStorage). Demonstrated how to validate hypotheses with Local Overrides and breakpoints, and captured reproducible, redacted evidence without external tools or scripts.

## Skills Learned / Improved
- Revealing hidden/disabled/ARIA-hidden content via Elements panel
- Inspecting and modifying `localStorage`, `sessionStorage`, and cookies
- Exporting and reviewing HAR files (requests, responses, headers)
- Using Local Overrides to test/bypass client-side checks safely
- Setting XHR/Fetch, DOM, and Event Listener breakpoints
- Console scripting for quick probing and state changes
- Redacting sensitive data and structuring evidence for reproducibility

---

![Method: Browser-only](https://img.shields.io/badge/Method-Browser--only-informational)
![Evidence: HAR attached](https://img.shields.io/badge/Evidence-HAR-green)
![Flags: Redacted](https://img.shields.io/badge/Flags-REDACTED-blue)
![Reproducible](https://img.shields.io/badge/Reproducible-Yes-success)

## Artifacts (Reproducibility)
| Artifact | Path | Notes |
|---|---|---|
| HAR export | `evidence/HAR/full.har` | “Preserve log”, “Disable cache” enabled |
| localStorage dump | `evidence/storage/localStorage.json` | Captured via `copy(JSON.stringify(localStorage))` |
| sessionStorage dump | `evidence/storage/sessionStorage.json` | Same method as above |
| Cookies | `evidence/storage/cookies.txt` | `document.cookie` (sanitized) |
| Screenshots | `evidence/screenshots/` | Before/after revealing hidden DOM, Overrides effect |
| Console log | `evidence/notes/console.log.txt` | Key commands & outputs (redacted) |

## Environment & Versions
- OS: <Windows 10 / Linux / macOS>
- Browser: <Chrome/Edge/Firefox> `<version>`
- VPN: <THM VPN / N/A>
- Time Spent: <hh:mm>

## Method Details (Expandable)
<details><summary>DevTools Actions (click to expand)</summary>

- **Elements:** Removed `hidden` / `disabled` / `aria-hidden` to reveal DOM.
- **Sources → Search:** `flag`, `token`, `.map`, `TODO`, `base64`.
- **Network:** Exported HAR; noted endpoints/params; replayed requests.
- **Application:** Enumerated and modified `localStorage` / `sessionStorage` / cookies.
- **Breakpoints:** XHR/Fetch, DOM subtree modified, Event Listener (click/submit).
- **Local Overrides:** Toggled client-side checks to validate hypotheses.
</details>

<details><summary>Console Snippets Used</summary>

```js
// Snapshot storage (pasted to .json files)
copy(JSON.stringify(localStorage, null, 2));
copy(JSON.stringify(sessionStorage, null, 2));
document.cookie;

// Example hypothesis test
localStorage.setItem('featureFlag', 'true'); location.reload();
