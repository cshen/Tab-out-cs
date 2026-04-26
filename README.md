# Tab Out

**Keep tabs on your tabs.**

Tab Out is a Chrome extension that replaces your new tab page with a dashboard of everything you have open.

---

## Added features

The following features were added to this fork by **C Shen** using **Deepseek V4**:

- **Dark / light theme toggle** — a button in the header that switches between a warm light theme and a dark theme. Preference is persisted in `chrome.storage.local` so it survives browser restarts. The entire dashboard, panels, and calendar adapt automatically via CSS custom properties.

- **iCal calendar panel** — a floating slide-out panel on the right edge of the page that displays upcoming events from any iCal feed (ICS format). Events are shown as a chronological to-do list using FullCalendar. The calendar auto-refreshes every 5 minutes.

  - **Resizable panel** — drag the left edge of the panel to make it wider or narrower (280–600 px). Width is persisted across sessions.
  - **Inbox toggle** — a button in the panel header that switches to showing *all* upcoming events (not limited to the current month) and hides the month navigation. Toggle off to return to the standard month view.
  - The ICS feed URL is configured in `extension/config.local.js` (gitignored), so each user can point it to their own calendar without modifying application code.
  - ICS fetching goes through the background service worker to avoid CORS issues with third-party calendar providers.

    <details>
    <summary><b>How to configure your own calendar</b></summary>

    Create or edit `extension/config.local.js` with your iCal feed URL:

    ```js
    // Personal config — gitignored so you can keep your own ICS feed URL here.
    var LOCAL_ICS_FEED_URL = 'https://your-provider.com/your-calendar.ics';
    ```

    **Where to find your iCal URL:**
    - **Dida365 / TickTick** — Calendar → Settings → Subscribe Calendar → copy the ICS link
    - **Google Calendar** — Settings → [your calendar] → Integrate calendar → Secret address in iCal format
    - **Apple Calendar** — Calendar → [your calendar] → Public Calendar → Share Link → copy the `.ics` URL
    - **Outlook** — Settings → Calendar → Shared calendars → Publish → copy the ICS link

    The file is gitignored, so your personal URL won't be committed. Reload the extension at `chrome://extensions` after editing.
    </details>


- Tabs are grouped by domain, with homepages (Gmail, X, LinkedIn, etc.) pulled into their own group. Close tabs with a satisfying swoosh + confetti.

No server. No account. No external API calls. Just a Chrome extension.



## Install with a coding agent

Send your coding agent (Claude Code, Codex, etc.) this repo and say **"install this"**:

```
https://github.com/zarazhangrui/tab-out
```

The agent will walk you through it. Takes about 1 minute.

---

## Features

- **See all your tabs at a glance** on a clean grid, grouped by domain
- **Homepages group** pulls Gmail inbox, X home, YouTube, LinkedIn, GitHub homepages into one card
- **Close tabs with style** with swoosh sound + confetti burst
- **Duplicate detection** flags when you have the same page open twice, with one-click cleanup
- **Click any tab to jump to it** across windows, no new tab opened
- **Save for later** bookmark tabs to a checklist before closing them
- **Localhost grouping** shows port numbers next to each tab so you can tell your vibe coding projects apart
- **Expandable groups** show the first 8 tabs with a clickable "+N more"
- **100% local** your data never leaves your machine
- **Pure Chrome extension** no server, no Node.js, no npm, no setup beyond loading the extension

---

## Manual Setup

**1. Clone the repo**

```bash
git clone https://github.com/zarazhangrui/tab-out.git
```

**2. Load the Chrome extension**

1. Open Chrome and go to `chrome://extensions`
2. Enable **Developer mode** (top-right toggle)
3. Click **Load unpacked**
4. Navigate to the `extension/` folder inside the cloned repo and select it

**3. Open a new tab**

You'll see Tab Out.

---

## How it works

```
You open a new tab
  -> Tab Out shows your open tabs grouped by domain
  -> Homepages (Gmail, X, etc.) get their own group at the top
  -> Click any tab title to jump to it
  -> Close groups you're done with (swoosh + confetti)
  -> Save tabs for later before closing them
```

Everything runs inside the Chrome extension. No external server, no API calls, no data sent anywhere. Saved tabs are stored in `chrome.storage.local`.

---

## Tech stack

| What | How |
|------|-----|
| Extension | Chrome Manifest V3 |
| Storage | chrome.storage.local |
| Sound | Web Audio API (synthesized, no files) |
| Animations | CSS transitions + JS confetti particles |

---

## License

MIT

---

Built by [Zara](https://x.com/zarazhangrui)
