# The Workroom
Mobile-first, offline-capable task and calendar planner. Preloaded with Christmas 2026 tasks. No build step.

## Publish for Android
1. Create a GitHub repository, upload all files in this folder to the repository root.
2. In GitHub Settings → Pages, select Deploy from a branch, main, / (root). Wait for the HTTPS Pages URL.
3. On Android, open the URL in Chrome → ⋮ → Add to Home screen / Install app.
4. Task data is stored per-browser in localStorage. Export a JSON backup in Settings. It does NOT automatically sync across devices.

## Google Calendar (read-only)
1. In Google Cloud Console, create/select a project and enable **Google Calendar API**.
2. Configure OAuth consent screen and add your Google account as a test user if the app is in Testing mode.
3. Create an OAuth Client ID of type **Web application**. Under **Authorized JavaScript origins**, add your GitHub Pages origin (e.g. https://username.github.io), **without the repository path**.
4. Paste the public OAuth Client ID into Workroom Settings, save, then Connect Google. Approve calendar read-only access.
5. Refresh imports events for ~7 days past and 90 days future. Tokens are held only in memory; calendar events are cached in localStorage. Reconnect to refresh after closing the app.

The OAuth client ID is public, not a secret. Never paste a client secret or Google password into the app. Calendar events remain read-only and are not written back. Google access needs internet. Google OAuth cannot work from file:// URLs.

## Limitations
- No automatic cross-device sync: browser-local tasks only, manual JSON export/import.
- Calendar file import supports simple VEVENT records; recurrence expansion and timezone rules are not fully supported. Prefer live Google Calendar connection for recurring work shifts.
- Work shifts Tue–Sat 2:30–11 pm are displayed as a reference, not generated calendar events. Import your actual work calendar for exceptions.
- No push notifications or background Google Calendar sync yet.


## Version 3: wellbeing and cycle planning
- On Today, choose one of five faces. This suggests a capacity level; manual capacity selection overrides it.
- The Review flexible tasks button asks before moving unfinished project tasks to the unscheduled inbox. It does not alter calendar events or household essentials.
- In Settings, optionally enable menstrual-cycle tracking and log period start dates. Estimates are approximate and should not be used for contraception or medical diagnosis.
- Wellbeing and cycle entries are stored in the current browser only, included in JSON exports, and are **not encrypted**. Do not share backups publicly. The public GitHub repository holds app code, not your browser entries.
- This version does not automatically reschedule calendar events.
