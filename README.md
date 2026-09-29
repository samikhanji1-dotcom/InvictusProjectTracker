# Project Tracker

A small, mobile-first project tracker that runs entirely in your browser. It is one `index.html` file with no frameworks, no build step and no external dependencies.

## Features

- **Dashboard strip:** counts by status, plus how many projects are overdue and how many are due in the next 7 days. Tap a tile to filter by it.
- **Project list:** sorted by due date (projects with no due date come last and Done projects sit at the bottom). You can search and filter by status, category, priority and due date.
- **Highlighting:** projects and tasks that are overdue are marked red, and those due within 7 days are marked amber.
- **Projects:** name, category (Work/Personal), status, priority, owner, start and due dates, next action, notes, and a checklist of tasks. Progress is the percentage of tasks done.
- **Detail view:** tap a project to see its details and tick off tasks. Add, edit and delete projects and tasks through forms. Every delete asks for confirmation first.
- **Backup:** export to JSON (full backup) or CSV (for spreadsheets), and import from JSON.
- **Dark mode:** follows your phone's or computer's system setting automatically.

## Enabling GitHub Pages

1. Push this repository to GitHub, with `index.html` at the root of the `main` branch.
2. On GitHub, open the repository and go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Set **Branch** to `main` and the folder to `/ (root)`, then click **Save**.
5. After a minute or two the site is live at `https://<your-username>.github.io/<repository-name>/`. The Pages settings screen shows the exact link.

Tip: on your phone, open the link and use **Add to Home Screen** (Safari share menu, or the Chrome ⋮ menu) so it opens like an app.

The empty `.nojekyll` file tells GitHub Pages to serve the files as they are, without running Jekyll.

## Where your data is stored

All project data is saved in your browser's **localStorage**, under the key `projectTracker.v1`. This means:

- Nothing is sent to any server, and no project data is ever committed to this repository. GitHub Pages only serves the app itself.
- Data belongs to **one browser on one device**. Your phone and your laptop each keep their own separate copy, and so do different browsers on the same device.
- Clearing your browser's site data or history for the site, or uninstalling the browser, **deletes your projects**. Private/incognito windows throw their data away when closed.
- Safari may clear storage for sites you haven't visited in a while. A site added to the Home Screen is exempt from this, which is another reason to add it.

## Backing up and moving data

Tap **Backup** in the top-right corner:

- **Export JSON (full backup):** downloads `projects-YYYY-MM-DD.json` with everything, including tasks. Keep this file somewhere safe, such as iCloud Drive, Google Drive or email to yourself. Export regularly.
- **Export CSV (spreadsheet):** downloads one row per project, with its tasks listed in the last column. Use it for viewing in Excel or Google Sheets. This is a report, so it can't be imported back.
- **Import JSON…:** choose a JSON file you exported earlier. You then get two choices:
  - **Merge with existing:** adds the imported projects. A project with the same ID as one you already have is overwritten by the imported copy.
  - **Replace all existing data:** deletes what is currently in this browser and loads the file instead. It asks you to confirm first.

**To move to a new device:** export JSON on the old device, get the file onto the new device (AirDrop, cloud drive, email), open the tracker there, and import it.

## Running locally

Open `index.html` directly in a browser, or serve the folder with any static server, for example `python3 -m http.server`, then visit http://localhost:8000.
