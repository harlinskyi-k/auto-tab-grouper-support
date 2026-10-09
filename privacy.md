---
title: Privacy Policy — Auto Tab Grouper
permalink: /privacy/
---

# Privacy Policy — Auto Tab Grouper

_Last updated: 2026-10-09_

Auto Tab Grouper is a browser extension that puts your open tabs into Chrome tab groups according to rules you write. This policy explains what the extension does with your data.

## Summary

**Auto Tab Grouper does not collect, transmit, sell or share any personal data.** Everything happens locally in your browser. The extension makes no network requests, has no analytics or tracking, and loads no remote code.

## Limited Use

The use of information that Auto Tab Grouper receives through Chrome's extension APIs (such as the addresses and titles of your tabs) adheres to the [Chrome Web Store User Data Policy](https://developer.chrome.com/docs/webstore/program-policies/user-data-faq), including the [Limited Use](https://developer.chrome.com/docs/webstore/program-policies/limited-use) requirements. This data is used only to provide the extension's single purpose — organizing your tabs into groups — is never sold, never used for advertising or credit decisions, and is not read by people.

## What the extension accesses and why

| Data | Why it is needed | Where it stays |
|---|---|---|
| Addresses (URLs) and titles of your open tabs | To check each tab against your rules (including rules on the page title) and move it into the matching tab group | Read in memory only, never sent anywhere; stored only if you save a group (see below) |
| Your tab groups (title, color, collapsed state) | To create, reuse, reorder, collapse or ungroup the groups made by your rules | In memory only |
| Your rules and settings | So the extension remembers what you configured | `chrome.storage.sync` — Chrome's own storage. If you have Chrome Sync turned on, Chrome syncs it between your browsers through your Google account, the same as other extension settings |
| A temporary list of tabs you moved by hand, and when each rule group was last used | So the extension doesn't move them back, and can put unused groups to sleep if you enable it | `chrome.storage.session` — in memory, deleted when the browser closes |
| The address, title and place of the last duplicate tab the extension closed (only if you chose to close duplicates) | So the popup can offer to reopen it | `chrome.storage.session` — in memory, deleted when you reopen it or the browser closes |
| Sites you dismissed from “Suggested groups” | So the same suggestion isn't shown again | `chrome.storage.local` — on this computer only |
| Groups you save with **Save** (group name, color, and the addresses and titles of its tabs) | So you can reopen the group later | `chrome.storage.local` — on this computer only, until you delete the saved group. Groups of incognito windows can't be saved |
| Names of groups created for sites without a rule, with the site they belong to | So these groups are recognized after a browser restart | `chrome.storage.local` — on this computer only. For incognito windows: `chrome.storage.session` only — in memory, deleted when the browser closes, never written to disk |
| Only when you click one of the AI buttons: **Group by topic** — titles and site names of the tabs no rule matches; **Fit into rules** — titles and addresses (without the part after “?”) of those tabs, and the names and patterns of your rules; **Suggest patterns** — titles and addresses (without the part after “?”) of the tabs in the group you picked; **Suggest a name** — the patterns in the rule form, the titles of open tabs they match and the names of your rules | To let Chrome's built-in AI model (Gemini Nano) suggest topic groups, the rule a tab belongs to, patterns or a group name. Nothing changes until you accept a suggestion | Passed to the model that Chrome runs on your device; nothing is sent over the network and nothing is stored. Chrome itself downloads the model from Google the first time it is used, as for any Chrome feature that uses it |
| Install date and the number of tabs the extension has grouped, plus whether you answered the rating prompt | To show the “Rate this extension” card only after the extension has been useful, and never again once you answer it | `chrome.storage.local` — on this computer only, never sent anywhere |

The extension does **not** read page content, form data, passwords, cookies, browsing history or any other information.

## Incognito windows

The extension works in incognito windows only if you allow it on Chrome's extension page. Even then, nothing from an incognito window is written to disk: its groups can't be saved, and the names of site groups made there are kept in memory only until the browser closes.

## Permissions

- **tabs** — read tab addresses to match them against your rules; move, close (only duplicate tabs, if you enable that option), activate or put to sleep (unload from memory) tabs; list open tabs for the search in the popup.
- **tabGroups** — create and manage tab groups.
- **storage** — save your rules and settings.
- **contextMenus** — add “Add this site to group” and “Group tabs from this site” to the page menu and quick actions to the toolbar-icon menu.
- **alarms** — timers for the optional “Sleep inactive groups” and delayed “Collapse inactive groups” settings.
- **sidePanel** — open the extension in Chrome's side panel, if you choose to.

## Reporting a problem

**Report a problem** in the extension opens the support page in a new tab. The extension adds its version, the Chrome version, the operating system, the interface language and where you opened it from (popup, side panel or page) to that page's address, so you don't have to look them up. Nothing is sent until you choose to write: the short form is run by [Tally](https://tally.so/help/privacy-policy), an issue by GitHub, an email by your mail provider. What you write there, and your email address if you leave it, is used only to answer you.

## Export files

If you use **Export**, the extension creates a JSON file with your rules and settings and saves it where you choose. That file is only on your computer; the extension never uploads it.

## Children

The extension does not collect data from anyone, including children.

## Changes

If this policy changes, the new version will be published at the same address with a new date.

## Contact

Questions about this policy: [k.harlinskyi@gmail.com](mailto:k.harlinskyi@gmail.com) or [the support page](https://github.com/harlinskyi-k/auto-tab-grouper-support/issues/new/choose).
