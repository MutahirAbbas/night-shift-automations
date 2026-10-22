# Night Shift automations

The scheduler for [Night Shift](https://night-shift-f5ab0c86.base44.app), coworking for remote builders who work nights.
Built in Base44 for the Base44 Challenge.

Every 15 minutes this GitHub Action calls `nightTick`, a Base44 backend function, which:

1. **Closes shifts that ended** (even if the laptop was closed) and drafts the handoff note with Base44's AI.
2. **Emails handoff notes at 9:00 AM in the team's city**, not the builder's.
3. **Clocks out members who went quiet** for 2 hours, so the board only shows people who are really up.
4. **Sends the Friday recap** at 9:00 AM Dubai: nights, hours, rooms and notes sent that week.

The function checks a shared key (`NIGHT_TICK_KEY`, stored as a secret here and in Base44), and every step is safe to run twice.
The app also nudges the same function when a signed-in member opens it, as a backup.
