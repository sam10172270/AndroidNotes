
# Android ForegroundService + Popup Summary

## 1. ForegroundService (24Ã—7 Safe Service)

- Extend `Service` (not a special class)
- Call `startForeground(NOTIF_ID, notification)` inside `onStartCommand()`
- Return `START_STICKY` to auto-restart on system kill
- Example use: continuous location tracking, ride polling

## 2. Popup Over Any App (System Overlay)

- Use `WindowManager` to inject a custom view
- Requires `SYSTEM_ALERT_WINDOW` permission
- Window type: `TYPE_APPLICATION_OVERLAY` (Android 8+)
- Shown from a running service, not an Activity

## 3. Show Popup on Lock Screen

- Add flags to `WindowManager.LayoutParams`:
  - `FLAG_SHOW_WHEN_LOCKED`
  - `FLAG_TURN_SCREEN_ON`
  - `FLAG_KEEP_SCREEN_ON`
- Optional: Use `WakeLock` to wake the screen

## 4. Survive App Swipe or Kill

- Use `START_STICKY` to let Android auto-restart service
- Handle `intent == null` in `onStartCommand()`
- (Optional) Use `AlarmManager` in `onTaskRemoved()` for extra safety
- Ask user to disable battery optimizations for reliability

## 5. UI Binding (Optional)

- Use a `Binder` class inside the service
- Activity binds via `bindService()` and communicates directly
- Useful for updating UI from a long-running service

## Permissions Needed

- `FOREGROUND_SERVICE`
- `SYSTEM_ALERT_WINDOW`
- `WAKE_LOCK` (optional)
- Battery Optimization exemption prompt

---

> This setup is how apps like Uber/Ola/Swiggy ensure uninterrupted driver logic, ride alerts, and location tracking â€” even when the phone is locked or the app is closed.
