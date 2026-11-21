# RepRise — Fitness for 13 Year Old Boys

RepRise is a native **iPhone app** (SwiftUI, iOS 17+) built for fitness fun for
13-year-old boys. It is designed from day one to be **expanded later** (new
workout programs, coaching, wearables, family plans, etc.) while starting with a
small, safe, bodyweight-only fitness core.

## Current features (starting point)

- **Safety onboarding** — required consent toggles (parental/doctor OK, listen to
  your coach / body, stop if pain) before anything else.
- **Today tab** — today's workout generated from a rotating library, quick start.
- **Library tab** — browse workouts (Daily Basics, Push Power, Pull Power, Play
  Cardio, Recovery & Stretch), all bodyweight only, age-gated.
- **Workout player** — countdown timer per exercise (via `TimelineView`), rest
  timer with skip, progress bar, "I Did It!" / auto-complete.
- **Progress tab** — workouts completed, day streak, best streak, recent history.

## Project layout

```
RepRise.xcodeproj/          Xcode project (uses synchronized folders)
RepRise/
    Info.plist
    RepRiseApp.swift        App entry (@main App)
    RootView.swift          Tabs + safety onboarding + tab bar
    Theme.swift             Colors, cards, buttons
    Models.swift             Exercise / Workout models
    WorkoutLibrary.swift    Built-in workout catalog
    AppState.swift           App state, stats, persistence
    TodayView.swift         Today tab
    LibraryView.swift       Library tab + row
    WorkoutDetailView.swift Workout detail + start
    WorkoutPlayerView.swift Fullscreen player (idle / running / finished)
    WorkoutSession.swift    Session phase machine (idle / running / resting / finished)
    ProgressView.swift      Progress tab
```

## Expanding the app

- **Add a workout**: append a `Workout` to `WorkoutLibrary.workouts` in
  `RepRise/WorkoutLibrary.swift`. It is picked up automatically by the Xcode
  synchronized folder (no project file edits needed).
- **Add a feature module**: create a new folder inside `RepRise/` (e.g. `Social/`,
  `Wearables/`, `Coach/`) — Xcode 16 synchronized groups will include it
  automatically in the app target.
- **Add platform capability**: add new Swift files / folders and extend the
  relevant view models, or plug in a service behind the existing protocols-style
  structure as the app grows.

## Building

1. Open `RepRise.xcodeproj` in Xcode (requires Xcode 16+).
2. Select an iPhone simulator (e.g. "iPhone 15 Pro").
3. Press Cmd+R to run.

## Safety notes

- All starter workouts are bodyweight-only and short.
- Kids should get medical clearance from a parent/guardian or physical therapist.
- Stop immediately if there is sharp pain; follow coach cues.
