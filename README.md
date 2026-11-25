# Workout Lab

An iPhone-friendly workout tracker for a five-day, 12-week hybrid physique program. Built as a self-contained HTML app, with a web manifest and service worker for Home Screen installation and offline use.

## Use on iPhone

Open the GitHub Pages website in Safari, tap Share, then Add to Home Screen. Enable Open as Web App if shown. Open the installed app once online to cache its assets.

- **Train:** choose a date and workout; log load, reps, both sides where applicable, and RIR. Mark each set complete. Rest timers respect superset transitions and unequal set counts.
- **Plan:** see the five-day blueprint and 12-week phases. The first two weeks cap most accessories at two sets; week six reduces sets by roughly half.
- **Progress:** weekly primary-muscle set counts, load trends, body weight and circumference records.
- **History:** resume or edit sessions and review cardio records.
- **Settings:** change cycle start and default units, export JSON backups or CSV, and restore backups.

Workout history is stored locally on the current device/browser, not in this repository. There is no account or cross-device sync. Export backups regularly, especially before clearing website data, changing browsers or devices. Import merges records by ID after confirmation; settings stay unchanged.

## Training model

The exercise prescriptions come from the supplied training program. Phase adjustments are conservative: regular assigned RIR targets remain during intensification. Progression suggestions require every planned set at the upper rep target, the same load, target RIR and a technique confirmation. They are prompts for judgment, not an automatic load prescription.

Cable plates, kg, lb and bodyweight-added kg are kept distinct. Previous-session matching requires the same exercise name, equipment/setup and unit. Muscle coverage assigns one primary group per exercise and does not double-count compound secondary stimulation. Both sides count as one working set.

## Files

- `index.html`: complete standalone tracker (inline CSS, program and JavaScript).
- `sw.js`: network-first app-shell cache, with offline fallback.
- `manifest.webmanifest`, icons: installation metadata.
- `qa/core.test.cjs`: core behavior checks; run with `node qa/core.test.cjs`.

No build step or external runtime dependencies. Serve the root directory over HTTPS. GitHub Pages is configured to publish `main` / root.

## Validation and limits

Core checks cover program extraction, phase targets, date handling, persistence, progression, timed/unilateral sets, superset rest and backup merging. Browser checks cover a 390 px layout, set logging, reload/resume, partial finish, measurements and offline service-worker registration. Native iOS Safari and airplane-mode behavior require device testing. Timers use wall-clock timestamps; there are no background sound alerts.
