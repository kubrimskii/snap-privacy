---
title: Snap — Privacy Policy
---

# Snap — Privacy Policy

**Last updated:** 2026-05-10

Snap is a private Chrome extension built for use inside the Google Workspace organization that operates `nace.ai`. This document explains exactly what data Snap accesses, where it goes, and what we do *not* do with it.

## 1. Who we are

Snap is published and maintained by employees of nace.ai for internal bug-reporting use only. Contact: support@nace.ai.

## 2. Single purpose

Snap lets a user draw or type on any web page they are viewing, capture a screenshot of the visible viewport, and append the result as a bug report to a Google Doc inside the user's own Google Workspace account.

## 3. What data Snap accesses

When you click the Snap toolbar icon, the extension may access the following data **only on the active tab and only after that explicit click**:

- The **rendered visible content of the current tab** (via `chrome.tabs.captureVisibleTab`), so it can produce the PNG screenshot you choose to save.
- The current tab's **URL and page title**, so the saved draft can be labeled with where it came from.
- Anything you **draw or type** on the overlay.
- Any **comment** you choose to add to a draft.

When you sign in:

- Snap uses Chrome's `chrome.identity.launchWebAuthFlow` to perform a Google OAuth sign-in **restricted to the `nace.ai` hosted domain** (`hd=nace.ai`).
- Google returns an **access token** and the user's **email address** and (optionally) **profile picture**.
- These are used to call the Google Drive and Google Docs APIs on your behalf and to display your account in Settings.

## 4. What Snap does *not* collect

- Snap does **not** track your browsing.
- Snap does **not** read tab contents in the background — content access only happens on tabs where you explicitly clicked the Snap icon.
- Snap does **not** send data to any analytics or third-party server.
- Snap does **not** transmit data to any backend operated by the developer. The only outbound network calls are HTTPS requests to Google's own APIs (`googleapis.com`, `docs.googleapis.com`) using your own access token.

## 5. Where data is stored

- **Drafts** (screenshots, annotations, comments) are stored locally in the browser's IndexedDB inside the extension. They never leave the browser unless you click "Send".
- **Cached OAuth token** and **per-origin destination-doc preferences** are stored in `chrome.storage.local` / `chrome.storage.sync` so you don't have to re-sign-in or re-pick a doc each time.
- When you click "Send", the screenshot is uploaded to **your own Google Drive** and inserted into a **Google Doc you own** via the official Google APIs. From that moment on, the data is governed by your Google Workspace administrator and Google's privacy policy.

## 6. Data sharing

We do not sell, rent, or share user data with third parties. We do not use your data for advertising. The only entity that ever receives your data is Google itself, when you choose to send a draft to your own Google Doc.

## 7. Permissions used and why

- `activeTab` — limit page access to the tab on which you clicked the icon.
- `storage` — save your drafts and preferences locally.
- `identity` — perform Google sign-in via `launchWebAuthFlow`.
- `scripting` — inject the drawing overlay into the active tab on click.
- `tabs` — read the active tab's URL/title and capture its visible viewport.
- `<all_urls>` — required so the user can file a bug report from any page they visit. Content access is gated by the user's explicit click on the toolbar icon.
- `https://www.googleapis.com/*`, `https://docs.googleapis.com/*` — needed to call Google Drive and Google Docs APIs.

## 8. Remote code

Snap does **not** load remote code. All JavaScript and CSS is bundled at build time. No `eval()`, no remote `<script>` tags, no dynamically imported remote modules.

## 9. Account deletion / data removal

- To remove the cached OAuth token, click **Settings → Sign out** in the extension. This also revokes the token with Google.
- To remove all locally stored drafts and preferences, uninstall the extension from `chrome://extensions`. Chrome wipes its `storage` and IndexedDB on uninstall.
- To remove a bug-report Google Doc that was created by Snap, open it in Google Drive and delete it like any other doc you own.

## 10. Children

Snap is intended for use by employees of nace.ai and is not directed at children under 13.

## 11. Changes to this policy

If we make material changes, we will update the "Last updated" date above and, where appropriate, notify users in the extension UI.

## 12. Contact

For privacy questions, email support@nace.ai.
