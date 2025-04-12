# 📱 Android Lifecycle Breakdown — Transparent Popup Over WhatsApp (Truecaller-style)

## 🧪 Scenario

- WhatsApp is open and running.
- A phone call ends.
- Your app (e.g., Truecaller-style) receives a `BroadcastReceiver`.
- You launch a popup-style Activity with:

```kotlin
intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
startActivity(intent)

	•	The launched Activity has a transparent theme:

<style name="PopupTheme" parent="Theme.AppCompat.NoActionBar">
    <item name="android:background">@android:color/transparent</item>
    <item name="android:windowIsTranslucent">true</item>
    <item name="android:windowNoTitle">true</item>
    <item name="android:windowIsFloating">true</item>
</style>



⸻

❓ Observation
	•	The popup appears on top.
	•	WhatsApp is still visible in the background.
	•	WhatsApp’s lifecycle only shows:

onPause()

— not onStop().

⸻

🧠 Why?

✅ Android Lifecycle Rule:

Screen Coverage	Lifecycle Triggered on Underlying Activity
Fully visible	onResume()
Partially covered	onPause()
Fully hidden (no pixels visible)	onStop()

Your transparent activity is only partially obscuring WhatsApp (due to translucency), so:

WhatsApp → onPause()

It’s not fully hidden, so:

WhatsApp → NOT onStop()



⸻

🔍 Full Lifecycle Timeline

WhatsApp → onPause()
Popup Activity → onCreate() → onStart() → onResume()

No call to onStop() for WhatsApp because it’s still visually present behind the translucent activity.

⸻

✅ Key Takeaways
	•	FLAG_ACTIVITY_NEW_TASK alone does not kill or cover previous apps.
	•	Visual coverage is what triggers onStop(), not just the Activity being in background.
	•	If your popup was opaque, WhatsApp would go:

onPause() → onStop()



⸻

🔄 Comparison Table

Popup Type	WhatsApp Lifecycle	WhatsApp Visible?
Transparent Activity	onPause()	✅ Yes
Opaque Activity	onPause() → onStop()	❌ No



⸻

🧠 Optional Enhancement

If you want WhatsApp to auto-return after popup closes, you’ll need to:

override fun onBackPressed() {
    val pm = packageManager
    val launchIntent = pm.getLaunchIntentForPackage("com.whatsapp")
    launchIntent?.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
    startActivity(launchIntent)
    finish()
}



⸻



