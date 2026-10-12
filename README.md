# TIQ World – Freelancer UX redesign (design mock)

Static HTML/CSS/JS prototype. Dummy data only, no backend, no credentials.

Entry point: `index.html` (Home feed). Design docs: `compare.html`, `ia.html`, `rationale.html`, `mobile.html`.

## Publish to GitHub Pages
1. Create a separate repo (e.g. `tiq-freelancer-ux-mock`), not the consumer-app repo.
2. Copy these files to the repo root and push to `main`.
3. Repo Settings > Pages > Source: Deploy from a branch > `main` / root.
4. Post the URL `https://<org>.github.io/tiq-freelancer-ux-mock/` on the task.

## Insights page (added 12 Oct)
`insights.html` is a clickable analytics page: five tabs, about 20 charts, slicers that cross-filter every chart, drill-down modals, a table view per chart and a Sample / My-current-data switch.
Files: `assets/insights.js`, `assets/insights-data.js` (dummy data, global `INSDATA`), `assets/insights.css`, `assets/vendor/chart.umd.js` (Chart.js 4.4.1, bundled so it works offline).
Note: `assets/data.js` (global `TIQDATA`) feeds the Home, Jobs and Job-detail pages and was rebuilt on 12 Oct after an accidental overwrite, so its dummy jobs may differ from the earlier version.

## v3 (12 Oct 2026): LinkedIn-inspired Home + light/dark theme
- **Run locally:** `cd tiq-mock && python3 -m http.server 8000`, then open http://localhost:8000/ (opening index.html directly also works).
- **Theme:** sun/moon button in the top bar (mobile: top-right). Saved in `localStorage` key `tiq-theme`; first visit follows the system setting. Tokens live in `assets/style.css` (`:root` dark, `:root[data-theme="light"]`). `assets/theme.js` is loaded in every page `<head>`.
- **Home (`index.html`, `assets/home.css`):** welcome banner, 7 clickable summary cards, activity overview, schedule, continue learning, recommended jobs (filters), recent activity, quick actions. Removed invented KPIs (15 applications this month, profile views).
- **New:** `certificates.html`. **Dummy data added** to `assets/data.js` (contracts, interviews, training, assessments, certificates, profile); `work.html`, `learn.html`, `profile.html` read it.
- Charts (`charts.js`, Insights) read theme colours and redraw on theme change.
- All data is dummy. Publishing to GitHub Pages is still a manual step (see above).

## v3.1: Work analytics band on Home
`assets/home-charts.js` + `assets/insights-data.js`: KPI tiles with deltas and sparklines, applications-over-time line with a 7D/30D/6M/1Y date range, work-mode donut, skills bars and employment-type columns. Click any slice/bar/column (or press Enter) to filter every chart; chips show active filters. Data is invented sample data and labelled as such.
