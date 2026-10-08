---
title: Security Policy — Auto Tab Grouper
permalink: /security/
---

# Security Policy

## Supported versions

Only the latest version published in the Chrome Web Store receives security fixes. Chrome updates extensions automatically, so a fix reaches users with the next release.

| Version | Supported |
|---|---|
| Latest Chrome Web Store release | ✅ |
| Older versions | ❌ |

## Reporting a vulnerability

**Please do not report security issues in public GitHub issues.**

Report privately through one of these channels:

1. **GitHub private vulnerability reporting** — open the [Security tab of the support repository](https://github.com/harlinskyi-k/auto-tab-grouper-support/security) → **Report a vulnerability**. Only the maintainer sees the report.
2. **Email** — [k.harlinskyi@gmail.com](mailto:k.harlinskyi@gmail.com) with the subject `Auto Tab Grouper security`.

Please include:

- the extension version (`chrome://extensions` → Auto Tab Grouper → Details);
- your Chrome version and operating system;
- steps to reproduce, and a proof of concept if you have one (for example, a rules JSON file used with **Import**);
- the impact you expect (what an attacker could read, change or run).

### What to expect

- An acknowledgement within **7 days**.
- An assessment and, if the issue is confirmed, a plan for a fix. The time to release depends on severity and on Chrome Web Store review, which usually takes a few days.
- Credit in the release notes if you would like it.

Please give a reasonable amount of time to release a fix before disclosing the issue publicly.

## Scope

In scope — anything that ships in the extension:

- the service worker (`background.js`, `background/`), popup / options page (`popup.*`, `popup/`), welcome page (`welcome.*`) and shared modules (`rules.js`, `i18n.js`, `locales/`);
- for example: script injection through rule titles, patterns, translations or an imported JSON file; the extension acting on tabs or groups it should not touch; data leaving the browser.

Out of scope:

- vulnerabilities in Chrome itself — report them to the [Chromium security team](https://www.chromium.org/Home/chromium-security/reporting-security-bugs/);
- issues that require a compromised browser profile or physical access to an unlocked device;
- the extension's development tools (build scripts and tests), which are not part of the published extension.

## Security design

For context when assessing a report:

- **No network access.** The extension makes no network requests, has no analytics and requests no host permissions.
- **No remote code.** All JavaScript is in the package; translations are loaded only from the extension's own files. The default Manifest V3 content security policy applies.
- **Minimal permissions:** `tabs`, `tabGroups`, `storage`, `contextMenus`, `alarms`, `sidePanel` — see the [privacy policy](https://harlinskyi-k.github.io/auto-tab-grouper-support/privacy/#permissions) for what each is used for.
- **On-device AI only.** "Group by topic" uses the language model Chrome runs on the device (Prompt API); tab titles are passed to it and nowhere else.
- **Untrusted input is escaped.** Rule titles, patterns and imported data are HTML-escaped before rendering; imported files are size-limited (1 MB), parsed as JSON only and normalized before use.
- **Data stays local.** Rules and settings live in `chrome.storage` (synced by Chrome itself when Chrome Sync is on); nothing is sent anywhere by the extension.
