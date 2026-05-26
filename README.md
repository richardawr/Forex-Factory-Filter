# FOREXFACTORY CREDIBILITY FILTER – README

A browser extension for Chromium‑based browsers (Chrome, Brave, Edge, Opera, etc.)
that cleans up Forex Factory forums by hiding posts from low‑credibility members.
You stay logged in; the extension works automatically on all forum threads.

Tested on Brave – should work on any Chromium browser.

## QUICK FEATURES

- Show only posts from members with:
  - More than X posts (configurable)
  - Joined more than Y months ago (configurable)
  - Low / Medium / High MIRS impact (selectable)
- Posts with many likes can override the rules (configurable threshold)
- **Crowd‑Sourced Ignore** – automatically blocks users who are frequently ignored by the most‑subscribed members
- Fully adjustable via an options page with sliders and checkboxes
- Block specific usernames manually
- Settings sync across your devices (using browser sync storage)

## DOWNLOAD FILES

- `credibility-filter.crx`  →  Ready‑to‑install packed extension
- `credibility-filter.zip`  →  Source code for manual installation or modification

## INSTALLATION

### Method 1 – Easy (using .crx file)
1. Open your Chromium browser (Chrome, Brave, Edge, etc.)
2. Go to the extensions page:
   - Chrome / Brave / Edge:  `chrome://extensions`
   - Opera:                  `opera://extensions`
3. Enable **Developer mode** (toggle in top‑right)
4. Drag the `.crx` file from your computer into the extensions page
5. Click **Add extension** when prompted

### Method 2 – Unpacked (from .zip archive)
1. Extract `credibility-filter.zip` into a folder
2. Go to your browser's extensions page (see above)
3. Enable **Developer mode**
4. Click **Load unpacked** and select the extracted folder
5. The extension appears in your toolbar

Both methods work identically. The unpacked version allows you to edit the code.

## HOW TO USE

1. Log into Forex Factory (the extension needs your session to see user data)
2. Open any forum thread
3. The extension automatically hides posts that don't meet your criteria
4. Adjust settings by right‑clicking the extension icon → **Options**

## CONFIGURATION (Options Page)

Open the options page to personalise the filter:

### Standard Filtering Rules
- **Minimum post count** – slider 0‑500 (0 = ignore this rule)
- **Minimum account age** – slider 0‑36 months (0 = ignore)
- **Likes threshold** – slider 0‑100 (0 = disable like override)
- **MIRS impact levels** – check Low / Medium / High
- **“Ignore MIRS entirely”** – when checked, the three checkboxes are disabled
- **Blocked usernames** – one username per line (manual blocklist)

### Crowd‑Sourced Ignore (new)
- **Enable crowd‑sourced auto‑ignore** – off by default, toggle on to activate
- **Number of top members to analyze** – default 15 (how many of the most‑subscribed members are examined)
- **Minimum number of top members who must ignore a user** – default 2 (e.g. if 2+ top members ignore a user, block them)
- **Refresh Candidate List Now** – manually rebuild the list of ignored users (may take a minute)
- **Current auto‑ignore candidates** – shows usernames that will be automatically blocked

> **How it works:** The extension periodically fetches the top 15 members (by subscriber count), reads their ignored lists from their profiles, and aggregates usernames that appear in multiple ignore lists. If a user reaches the threshold (e.g. ignored by 2+ top members), they are added to the crowd‑sourced block list.

> **Important:** The crowd‑sourced list is stored locally and updates every 24 hours (or manually). You must be logged in for the background worker to access ignored lists.

## NOTES

- The extension only works when you are **LOGGED IN** to Forex Factory.
- Data (post count, join date, MIRS, ignored lists) is read directly from the page’s HTML.
- If Forex Factory changes its layout, the selectors may need updating.
- Settings are saved using browser storage.
- The crowd‑sourced ignore feature is **off by default** – enable it in the options if you wish to use it.
- **Background service worker** runs silently to update the crowd‑sourced list; you can see its logs in the extension’s service worker console.

## TROUBLESHOOTING

- Nothing happens? Make sure you are logged in and on a thread URL.
- Posts still appear? Open Developer Tools (F12) → **Console** tab. Look for `[CredibilityFilter]` logs to see why posts are kept or hidden.
- Crowd‑sourced list not updating? Open the extension’s options and click **Refresh Candidate List Now**. Wait a minute – it fetches data from 15 profiles.
- Extension icon missing? Reload the extension on the extensions page.

## LICENSE

Free to use, modify, and share. Provided as‑is, without warranty.