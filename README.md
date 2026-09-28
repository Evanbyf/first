# first

Small, dependency-free browser projects.

## focus-timer/

A Pomodoro timer with a task list. Open `focus-timer/index.html` in any browser — no build step.

- **Focus → break cycle:** 25 min focus, 5 min short break, and a 15 min long break after every 4 focus sessions (all adjustable under Settings).
- **Tasks:** add tasks, click one to make it active, and each finished focus session adds a 🍅 to it. Tick a task off when it's done.
- **Stays accurate in background tabs:** the timer counts toward a fixed end time instead of counting ticks, and the tab title shows the countdown.
- **Chime + desktop notification** when a session ends (you'll be asked for notification permission on first Start).
- **Saved in your browser** via `localStorage`: tasks, counts and settings survive a reload.
- **Keys:** `Space` start/pause · `R` reset · `N` jump to new-task box.
