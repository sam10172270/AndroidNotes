## 📱 Android Activity Lifecycle Summary

### ▶️ Launch Activity A
- `onCreate()`
- `onStart()`
- `onResume()`

---

### 🔁 Transition: A → B
- `A.onPause()`
- `B.onCreate()`
- `B.onStart()`
- `B.onResume()`
- `A.onStop()`

---

### ⬅️ Back from B to A
- `B.onPause()`
- `A.onRestart()`
- `A.onStart()`
- `A.onResume()`
- `B.onStop()`
- `B.onDestroy()`

---

### 🔄 Device Rotation (Recreation)
- `onPause()`
- `onStop()`
- `onDestroy()`
- `onCreate()`
- `onStart()`
- `onResume()`

---

### 🧠 Key Notes
- `onPause()` always before `onStop()`
- `onRestart()` is only called when returning from background
- Pressing **Back** → `onDestroy()`
- Pressing **Home** → stays in memory (no `onDestroy()`)