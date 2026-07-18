# TaskFlow — Simple Task Dashboard

A responsive frontend web application built with plain **HTML, CSS, and JavaScript** — no frameworks or build tools. TaskFlow lets a user manage a daily task checklist through a clean, dashboard-style UI, with live stats and a completion chart.

## Project Info

**Project:** Frontend Interface Development
**Goal:** Create a responsive frontend interface for a simple web application.

### Key Requirements
- Use HTML, CSS, and basic JavaScript
- Responsive layout for different screen sizes
- Clean and user-friendly UI

### Key Skills
Frontend development, responsive design, UI basics

## Features

- **Task checklist** — add, complete, and delete tasks
- **Live search** — filter the task list as you type
- **Progress bar** — updates automatically based on completed vs. total tasks
- **Quick stats panel** — shows total, completed, and pending task counts
- **Completion chart** — bar chart showing today's completed tasks against the days of the week
- **Responsive layout** — adapts from a multi-column desktop dashboard down to a single-column mobile view

## Project Structure

```
├── index.html      # Markup, styles, and JavaScript (single-file app)
└── README.md
```

All CSS is defined using custom properties (`:root` variables) for easy theming, and all layout is done with CSS Grid and Flexbox — no external CSS/JS libraries required (only Google Fonts is loaded via CDN).

## How It Works

### HTML
The page is structured into a sidebar, a topbar (title, search box, avatar), and a main content grid containing three cards:
1. **Today's Checklist** — the task list, progress bar, and add-task form
2. **Quick Stats** — total / completed / pending counters
3. **Tasks Completed This Week** — bar chart

### CSS
- Design tokens (colors, radii, fonts) are defined once as CSS variables in `:root` for consistency
- CSS Grid (`.app`, `.content`) handles the overall page layout
- Media queries at `900px` and `600px` breakpoints reflow the grid from two columns to one column, and collapse the sidebar into a horizontal top strip on mobile

### JavaScript
- `tasks` is an array of `{ text, done }` objects held in memory (no backend/storage — resets on page reload)
- `renderTasks()` renders the current (and search-filtered) task list into the DOM, and wires up the checkbox toggle and delete button for each task
- `updateStats()` recalculates and displays total/completed/pending counts and updates the progress bar
- `renderChart()` draws a simple bar chart showing today's completed task count against the current weekday
- `addTask()` reads the input field, validates it isn't empty, and pushes a new task
- Event listeners handle: adding a task (button click or Enter key), live search filtering, checkbox toggling, and task deletion

## Getting Started

No installation or build step needed.

1. Download/clone the project
2. Open `index.html` directly in any modern browser

## Notes / Possible Improvements

- Tasks are stored only in memory; refreshing the page resets the list. Adding `localStorage` persistence would be a natural next step.
- The chart currently reflects only today's completed count (mapped to the matching weekday); it could be extended to track real daily history over time.
- Task IDs aren't tracked — toggling/deleting relies on array index, which works for this simple use case but would need real IDs for a more complex app.
