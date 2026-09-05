# DSIB Timetable Explorer

A browser-based dashboard for exploring the school's weekly timetable — browse lessons, look up a teacher's full week, check total students per year group, spot double-booked teachers/rooms, and view workload/utilisation charts.

No server, no database, no build step. It's a static site — open it in a browser and it just works.

**Live site:** `https://<your-username>.github.io/<your-repo>/`

---

## Files in this repo

| File | What it is | Do you edit it? |
|---|---|---|
| `index.html` | The whole app — login, layout, filters, charts, logic | No — leave this alone |
| `data.csv` | Every lesson in the week (day, session, time, year, teacher, subject, room, students) | **Yes — this is your weekly update** |
| `reg-groups.csv` | Total registered students per year group (Year 07–13), with gender split | **Yes — update when rolls change** |

`index.html` reads the two CSV files automatically when the page loads. You never need to touch the HTML/JS to update the data — just replace the CSV content.

---

## Logging in

- **Username:** `Admin`
- **Password:** `Admin123@`

Once signed in, the browser remembers you until you click **Log out**.

> **Please read — this is not real security.** This is a static page with no backend, so the login is a front-end gate only. The username and password are stored in plain text inside `index.html` — anyone who opens the browser's "View Page Source" can read them. This is enough to stop casual visitors from wandering in, but **not** enough to stop someone who deliberately wants access. Don't put anything genuinely confidential behind this login. If you need real security, that requires an actual backend (login server + database), which is a different kind of project.

---

## Updating the timetable

1. Export your latest data (from the `Da` sheet in the Excel workbook) as a CSV with these exact columns:

   ```
   day,session,time,year,teacher,subject,room,students
   Mon,S1,14:00,Year 07,Naumana Malik,Registration,B105,20
   Mon,S2,07:25,Year 07,Zara Hamid,English,B002,22
   ...
   ```

   - `session` uses `S1`–`S8` (Session 1 = Registration/Tut, Session 2 = first teaching period, ... Session 8 = last).
   - `day` uses `Mon`, `Tue`, `Wed`, `Thu`, `Fri`.

2. In GitHub, open `data.csv` → pencil icon (Edit) → select all, paste the new content → **Commit changes**.
3. GitHub Pages redeploys automatically within about a minute. Refresh the site to see the update.

### Updating year group totals

Same idea, but for `reg-groups.csv`:

```
year,reg_groups,males,females,total_students
Year 07,15,165,149,314
...
```

Edit this whenever roll numbers change (start of term, new admissions, etc.) — it doesn't need to change as often as the lesson data.

### Uploading without touching GitHub

The page also has an **Upload CSV** option (top of the dashboard) for testing a new file before committing it, or for a quick local look. Anything uploaded this way is saved in *your browser only* — it won't update the site for other people, and it stays until you upload again or click "Reset to default."

---

## Deploying / redeploying

1. Push all three files (`index.html`, `data.csv`, `reg-groups.csv`) to the repo root.
2. Repo → **Settings → Pages**.
3. Source: **Deploy from a branch** → Branch: `main`, folder: `/ (root)` → Save.
4. Wait ~30–60 seconds, refresh the Pages settings screen for your live URL.

No other setup, no dependencies to install — it's plain HTML/CSS/JS plus two small JS libraries loaded from a CDN (PapaParse for CSV parsing, Chart.js for the graphs).

---

## What's in the dashboard

- **Browse** — filter every lesson by day, session, year, teacher, room, or subject; sort by clicking column headers.
- **Teacher schedule** — pick a teacher, see their whole week as a Day × Session grid.
- **Year totals** — total registered students per year group, with gender split.
- **Analysis** — lessons per year, students per year, busiest teachers, busiest rooms, lessons by subject, and a day × session load heatmap.
- **Clash check** — automatically flags any teacher or room booked into two places at once.

---

## Troubleshooting

- **Page loads but shows "0 lessons"** — check that `data.csv` is in the same folder as `index.html` and has the exact column headers shown above.
- **Opening `index.html` directly from your computer doesn't load the data** — browsers block local file access for security. Either use the "Upload a CSV instead" button, or view it through the live GitHub Pages link (or any local web server).
- **Login not working** — username and password are case-sensitive: `Admin` / `Admin123@`.
