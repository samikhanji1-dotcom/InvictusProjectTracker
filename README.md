# Invictus Project Tracker

A mobile-first deal and project tracker for Invictus, styled to the Invictus brand guidelines. It runs entirely in your browser: one `index.html` file with no frameworks, no build step and no external requests. The Poppins font, the logo and the Africa map are all embedded in the file.

## Features

### Dashboard
- **Urgency summary:** counts of open items by tier (Critical, High, Medium, Low) and the number of at-risk projects. Tap a tier to filter the deadline list; tap "At-risk projects" to open those projects.
- **Africa project map:** every project with a location is pinned on the map.
  - Each pin is labelled with target equity and deal type, e.g. "51% JV".
  - **Red** means blocked or has a critical item, **amber** means at risk or has a high-urgency item, and **blue** means on track. Red pins pulse.
  - Pins that are close together are grouped into a numbered circle. Tap a pin or group to see the projects and why they're flagged.
  - Pinch, double-tap or use the + / − buttons to zoom, and drag to pan when zoomed in. Chips above the map filter by deal type.
  - **Countries are interactive.** With a mouse, hovering shows the country's name and project count. Tapping or clicking a country opens its **country page**. Small countries can also be opened from the "Country details…" dropdown under the map.
- **Upcoming deadlines:** project due dates, tasks and milestones in one list, grouped by urgency tier.
- **Deal mix:** number of projects and average target equity for each deal type, plus total enterprise value (per currency).
- **Scope and owner:** switch between All, Pipeline (deals) and Portfolio (acquired), and filter by owner.

### Projects
- Fields: name, stage, risk status and risks/blockers, deal type (Full Buyout, Joint Venture, Minority, Associate), target equity %, sector, country, city/site, map pin, owner, priority, start and due dates, next action and notes.
- **Stages** cover the whole lifecycle:
  - Pipeline: Origination → Screening → Due diligence → Negotiation / Term sheet → Signing → Closing.
  - Portfolio: Integration planning → Day 1–100 → Integration ongoing → Integrated.
  - Also: On hold and Dropped.
  - A deal at Closing shows a **Move to portfolio** button.
- **Region** (North, West, Central, East or Southern Africa) is set automatically from the country.
- **Map pins:** choosing a country places the pin at that country's capital. Use **Set pin on map** to tap the exact location. Nothing is looked up online.
- The form warns when equity doesn't fit the deal type, for example a Full Buyout below 100%.
- **Valuation & financing** (in millions, with a currency per project): enterprise value, equity value, net debt (negative for net cash), debt financing and equity financing.
  - Enter any two of EV, equity value and net debt and the form offers the third, using EV = equity value + net debt. It warns if all three don't add up.
  - The project page shows Invictus's share of equity (target equity % × equity value), total financing and the debt/equity split.
- The list is sorted by due date, with search and filters for stage, deal type, alert level, region, sector and owner.

### Country pages
Each African country has a page showing:
- active projects, how many need attention, and total EV;
- a map of the country with its projects;
- country details you can edit: country risk rating (Low, Medium or High), local currency, key contacts, regulatory/legal notes, market notes and other notes.

Use **+ Project here** to start a project already set to that country. A project's page links to its country page.

### Tasks
- Create tasks, assign an owner, set a due date, status (To do, In progress, Blocked, Done) and priority, mark milestones, and link each task to a project.
- Tasks are grouped by urgency tier. Change status from the list, or tick the box to mark a task done.
- Filter by owner, project, status or tier. Completed tasks are hidden unless you turn on "Show completed".

### Urgency tiers
| Tier | Rule |
|---|---|
| **Critical** | Overdue, due within 2 days, blocked, or an open milestone due within 7 days |
| **High** | Due within 7 days, or High priority and due within 14 days |
| **Medium** | Due within 30 days |
| **Low** | Due later, or no due date |

Finished tasks, and projects that are Integrated or Dropped, have no tier.

### People and sectors
Open **Settings** (the icon at the top right) to manage the People list and the Sectors list. Everyone in the People list can be tagged as an owner. You can also add a person straight from any Owner dropdown with "+ Add person…".

People are tags, not user accounts. Nobody logs in or gets notifications.

### Other
- Automatic dark mode that follows your device setting.
- Works offline once the page has loaded.

## Where your data is stored

All data is saved in your browser's **localStorage** under the key `invictusTracker.v2`. This means:

- Nothing is sent to any server, and no project data is ever committed to this repository. The host only serves the app's code.
- Data belongs to **one browser on one device**. Your phone and laptop each keep their own copy.
- Clearing your browser's site data **deletes your projects**. Private/incognito windows lose their data when closed.
- Safari may clear storage for sites you haven't visited for a while. Adding the site to your Home Screen avoids this.

**Upgrading from the first version:** existing data (key `projectTracker.v1`) is upgraded automatically the first time you open this version. Checklist items become linked tasks, statuses map to the nearest stage, owners become People, and categories become Sectors. The old copy is left untouched as a safety net.

## Backing up and moving data

Open **Settings → Backup & restore**:

- **Export JSON (full backup):** everything, including people, sectors, tasks and country details. Save it somewhere private, such as iCloud Drive, Google Drive or a password manager.
- **Projects CSV / Tasks CSV:** spreadsheet reports. These can't be imported back.
- **Import JSON…:** load a backup. Choose **Merge** to add or update by ID (people with the same name are matched) or **Replace** to swap out everything (asks for confirmation). Backups from the first version of the tracker can also be imported.

To move to another device, export JSON on the old one, get the file onto the new one, then import it.

**Never put backup files in this GitHub repository**, especially if it's public. Anyone who can see the repo could read them, and Git keeps old versions even after you delete a file.

## Hosting

The app is a single static file, so any static host works.

**GitHub Pages:** go to **Settings → Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save. On the free GitHub plan this needs a public repository.

**Cloudflare Pages or Netlify (free, repository can stay private):** connect your GitHub account, pick this repository, leave the build command empty, and set the output directory to `/`.

In every case, the site itself is reachable by anyone with the link, but each visitor sees only the data in their own browser.

## Running locally

Open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit http://localhost:8000.

## Credits

- Font: [Poppins](https://github.com/itfoundry/Poppins), SIL Open Font License 1.1 (see `LICENSE-Poppins-OFL.txt`).
- Map outlines: simplified from [Natural Earth](https://www.naturalearthdata.com/) (public domain) via the `world-atlas` package.
