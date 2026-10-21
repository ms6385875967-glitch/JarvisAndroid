# Vaani: voice phone assistant (Android)

Speak a command, Vaani does it on your phone. Replies in Tanglish or Tamil, aloud.

## Build the APK (Android Studio)

1. Install Android Studio (free): https://developer.android.com/studio
2. File > Open > choose this `VaaniApp` folder. Wait for Gradle sync (first time downloads ~1 GB, needs internet).
3. Build > Build Bundle(s) / APK(s) > Build APK(s). Studio shows a "locate" link to `app/build/outputs/apk/debug/app-debug.apk`.
4. Copy the APK to your phone and install it (allow "install unknown apps" when asked).
   Or plug the phone in with USB debugging on and press the green Run button.
5. On first launch, allow Microphone, Contacts and Phone.

Needs Android 8.0 or newer and the Google app (speech recognition uses Google's service; it needs internet).

## Commands

| Say | What happens |
|---|---|
| open youtube / whatsapp / any app name | opens that app |
| amma kku call pannu / call 98765 43210 | calls a contact or number |
| send message to amma saying vandhuten | opens SMS with the text ready |
| send whatsapp message to anna saying hi | opens WhatsApp chat with text ready |
| 6:30 am alarm | sets the alarm directly |
| timer 5 min | starts a timer directly |
| torch on / torch off | flashlight |
| volume up / down / mute | volume |
| play <song name> | YouTube search |
| navigate Marina Beach / pizza near me | Google Maps |
| search <anything> | web search |
| wifi / bluetooth / brightness / settings | opens that settings screen |
| camera | opens camera |
| battery, time, date | spoken answer |
| nillu / stop listening | turns off hands-free |

Hands-free: the button keeps listening again after each reply while the app is open.

## Limits (Android rules, not bugs)

- Wi-Fi, Bluetooth and brightness cannot be switched silently by a normal app. Vaani opens the right screen and you tap once.
- Messages and WhatsApp open with the text filled in. You press Send. This is deliberate so nothing is sent by mistake.
- The app must be open (screen on) to listen. Always-on "Hey Vaani" needs a background service and extra permissions; it is the next step if you want it.
- Contact names are matched by text, so say the name as it is saved.

## Build the APK using only your phone (cloud build)

This ZIP includes a GitHub Actions workflow so you can build the APK without installing Android Studio on your phone.

1. Extract this ZIP on your phone.
2. Create a repository on GitHub and upload the **contents of the `VaaniApp` folder** (including the hidden `.github` folder). In GitHub's mobile website, use the repository's **Add file** option; uploading a ZIP alone does not run the build.
3. Open the repository's **Actions** tab and select **Build Vaani APK**. Tap **Run workflow** if it has not started automatically.
4. When the workflow finishes successfully, open that run and download the **Vaani-debug-apk** artifact.
5. Extract the downloaded artifact ZIP and tap `app-debug.apk` to install it. If Android asks, allow your browser or file manager to install unknown apps.

The build needs internet access in GitHub Actions. Vaani's speech recognition also relies on Google's speech service and may need internet; this project is not fully offline as currently written.
