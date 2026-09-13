# DSIB Timetable Explorer

A browser-based dashboard for exploring the school's weekly timetable.

The dashboard allows authorized users to browse lessons, search teacher schedules, view year-group totals, review timetable information, and identify possible timetable clashes.

## Features

- **Browse** — Filter and search lessons by:
  - Day
  - Session
  - Year group
  - Teacher
  - Teacher code
  - Room
  - Subject
- **Teacher Schedule** — View a teacher's weekly timetable in a Day × Session format.
- **Year Totals** — View registered student totals by year group, including gender breakdown where provided.
- **Analysis** — Explore timetable summaries such as:
  - Lessons by year
  - Students by year
  - Busiest teachers
  - Busiest rooms
  - Lessons by subject
  - Day × session workload
- **Clash Check** — Identify potential teacher or room clashes in the timetable.

## Data

The dashboard uses timetable and registration data stored in CSV files.


## Access

Access to dashboard features is controlled by the school's authorized administrator.

Users should only use the access details provided to them by the appropriate school administrator.

**Please do not share login credentials, administrator access, or other confidential information publicly.**

## Deployment

The dashboard is a static website and can be hosted using GitHub Pages or another static web-hosting service.

The required files are:

- `index.html`
- `data.csv`
- `reg-groups.csv`

The CSV files should remain in the same location as `index.html` unless the application configuration has been changed.

## Important

This repository may contain school timetable and student-related information. Treat all data as confidential and follow the school's data-protection and information-security policies.

Do not publish confidential student, staff, timetable, authentication, or administrator information in public documentation.

For technical or access-related issues, contact the designated system administrator.
