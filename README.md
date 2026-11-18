# GTA VI Clip Engine

A one-file web app that runs the GTA VI clipping operation from the operator prompt: campaigns, clips, posts, payouts and the weekly review in one place.

## Run it

Open `index.html` in any browser. There is nothing to install or build. On a phone, host it with GitHub Pages (Settings → Pages → deploy from this branch) and add it to your home screen.

Data is saved in that browser only. Use **Setup → Download backup** regularly, and **Restore** to move it to another device.

## What's in it

| Tab | Covers (prompt section) |
| --- | --- |
| Today | Countdown to launch, money vs target, alerts, daily schedule checklist, launch week playbook, 7 day kickoff (12, 13, 22) |
| Campaigns | `campaigns.csv` fields, expected value per clip ranked, budget, deadline and daily-recheck flags (6) |
| Clips | `clips.csv` log, transformation checklist that blocks approval until complete, `[date]_[pillar]_[streamer]_[n].mp4` names, ready-to-paste yt-dlp / Whisper / ffmpeg commands, caption builder (4, 9, 10, 11) |
| Scoreboard | `scoreboard.csv` with 24h / 72h / 7d views, min-views check, cap, estimated payout, "submit now" flags (15) |
| Submissions | `submissions.csv` with pending / approved / rejected and late-payout flags (15) |
| Accounts | Handles, device, warmup status, median views. No password fields by design (21) |
| Watchlist | Streamers, schedules, whether a campaign allows the source (8) |
| Hooks | Hook bank by pillar with per-account reuse tracking, caption template (11) |
| Insights | Medians by pillar / account / hook / campaign, top and bottom 5, kill flags, payout per hour, payout math calculator (16, 17) |
| Notes | `learnings.md`, `playbook.md`, `ideas.md` |
| Setup | Targets, kill thresholds, timezone, launch and kickoff dates, safety rules, backup and restore |

Every table can be copied or downloaded as CSV with the same file names the prompt uses.

## Money logic

- **Estimated payout** = views ÷ 1,000 × CPM, capped per clip, and $0 if min views aren't met. Latest of 7d → 72h → 24h views is used; blanks stay blank.
- **Campaign EV per clip** = likely views ÷ 1,000 × CPM, limited by the cap and budget left. Likely views = your median for that campaign, then your overall median, then the default in Setup.
