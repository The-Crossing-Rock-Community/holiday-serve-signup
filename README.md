# Holiday Serve Signup

A custom volunteer campaign management app for [Rock RMS](https://www.rockrms.com), built with Helix (Lava Applications), Groups, and Group Scheduling.

Built by Stan Yoder & Karen Rossi at [The Crossing](https://thecrossing.church) – St. Louis, MO. Presented at RX2026.

---

## What It Does

Holiday Serve Signup replaces the need for a third-party plugin when running short-term volunteer campaigns (Christmas, Easter, etc.). It has three parts:

- **Public signup** — volunteers choose their role, campus location, and service time(s) via a clean, branded page
- **Staff admin** — ministry teams manage their groups and volunteers without needing Rock admin access
- **Status board** — a real-time, printable view of volunteer coverage across all roles and service times

Everything is driven by standard Rock features: Group Scheduling for slot capacity, Attendance Occurrences for tracking signups, and Group Member attributes for a few extra fields.

---

## What's in This Repo

```
/endpoints/                          — 12 Helix endpoint files
/lava-application-blocks/            — 3 Lava Application Content block files
/shortcodes/                         — Custom shortcodes used by the app
application-rigging.lava             — Configuration Rigging JSON template
holidayserve-styles.lava             — CSS block for the public signup page
holidayserveadmin-styles.lava        — CSS block for the admin page
holidayserveadmin-scripts.lava       — JS block for the admin page
holidayservestatusboard-styles.lava  — CSS block for the status board page
holidayservestatusboard-scripts.lava — JS block for the status board page
holidayservewf-styles.lava           — CSS + page title block for the workflow entry page
holidayserve-introparagraph.lava     — Example intro/login block for the public page (customize before use)
holiday-serve-signup-workflow.json   — Rock workflow export (import via Admin Tools > Power Tools)
HolidayServeStatusBoardPrint.css     — Print stylesheet (deploy to your Rock theme folder)
```

---

## Prerequisites

- **Rock RMS** with Helix (Lava Applications) available
- **Group Scheduling** enabled on your Group Type
- The custom shortcodes in `/shortcodes/` installed in your Rock environment:
  - `dropdownxing`, `radiobuttonlistxing`, `checkboxlistxing` — form controls with `name` attributes wired for HTMX (these are The Crossing's customized versions of Rock's built-in shortcodes)
  - `handlehelixresponseerror` — HTMX error handler, place at the end of each page block
  - `bkgdcheckstatus` — background check status shortcode (**example/reference only** — Crossing-specific, replace with your own implementation)

---

## Setup

Full setup instructions, data model explanation, configuration guide, and technical walkthrough are in the community post:

**[Rock Community Post — link coming soon]**

The short version:
1. Create your Ministry Team Defined Type and Group Type
2. Create your serving groups with locations and schedules
3. Set up the signup workflow (import from `holiday-serve-signup-workflow.json`)
4. Create the Helix application and add endpoints
5. Configure the Configuration Rigging JSON
6. Set up three Rock pages with the Lava Application Content blocks and HTML Content blocks for styles/scripts

---

## Customization

- **Brand color** — change `--secondary-color-lifeblood: #a1302b` in all four style files to match your brand
- **Holiday campaigns** — rename URL paths and update the holiday switch logic in `lava-application-blocks/HolidaySignup.lava` to support your campaigns
- **Ministry teams** — add or remove Defined Values in your Ministry Team Defined Type; the app pulls from this list dynamically
- **Background check column** — remove or replace the `bkgdcheckstatus` shortcode references if your ministry doesn't need this

---

## License

MIT — use, adapt, and share freely. If you build something from this, we'd love to hear about it in the [Rock Community](https://community.rockrms.com).
