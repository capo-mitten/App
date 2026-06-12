# Reset (v2)

A quiet personal check-in app. Installable PWA for iPhone. All data stays on your device.

## What's new in v2

- Detailed emotion wheel: 7 core emotions → ~75 specific feelings → optional body sensations
- Check-ins no longer assume anything: "Just checking in" logs mood + what you're doing; "Feeling the pull" handles urge moments
- Custom coping: type anything (TV, scrolling, a walk) — it's remembered as one of "your usuals"
- Log earlier: backfill entries with a date/time picker
- Daily nudge times (Settings) with an honest fallback banner
- Weekly summary: a shareable .txt report for your therapist — counts, amounts, the feelings that preceded urges, and what you did instead. Legend on/off toggle.

## Deploy (~3 minutes, pick one)

Must be served over **https**.

- **Netlify:** drag this folder onto https://app.netlify.com/drop
- **GitHub Pages:** upload to a repo → Settings → Pages → deploy from main
- **Vercel:** `npx vercel` in this folder

If you deployed v1 to the same URL, just re-upload — the service worker version is bumped, so the installed app updates itself on next open.

## Install on iPhone

Open the URL in **Safari** → Share → **Add to Home Screen** → open from the icon.

## Notifications — the honest version

- **Check-backs and daily nudges fire as real notifications only while the app is open** (allow them in Settings).
- **When the app is closed, iOS will not run timers for a web app.** Anything missed becomes a banner on Home the next time you open it. Nothing is lost.
- **For reliable daily buzzes when the app is closed**, set up a 2-minute iPhone automation:
  1. Shortcuts app → Automation tab → + → **Time of Day** → pick a time → Run Immediately
  2. Add action → **Open URL** → paste your Reset URL (or Open App → Reset if it appears)
  3. Repeat for each daily time you want.
  This opens Reset at those times — and the in-app nudge banner takes it from there. Alternatively, plain iOS Reminders/Alarms labeled "Take a moment" work fine.
- **The real fix** is server-driven Web Push (VAPID + a tiny scheduled job). The app is structured so this can be added without changing the UI — ask Claude when ready.

## Privacy

- Data lives only in the installed app's storage. No server, no account, no analytics.
- **Back up via Settings → Export** now and then; deleting the app or clearing Safari data deletes the data.
- The weekly summary's plain-language legend is **on by default** (it's meant for your therapist). Toggle it off to keep exports fully coded.
- The passcode is a shoulder-surfing deterrent, not encryption.

## Code legend (yours — shown in-app only as codes)

| Prefix | Unit  |
|--------|-------|
| e      | mg    |
| vp     | hits  |
| pf     | dabs  |
| j      | grams |
