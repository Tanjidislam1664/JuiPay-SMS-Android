# JuiPay SMS (Android)

Reads incoming payment SMS (bKash / Nagad / Rocket / Upay …) on the phone that receives your money and sends them to your
JuiPay gateway, which matches the **sender number + amount** with the customer's payment and confirms it instantly.
Only SMS from the allowed sender list (set in Admin → Devices) are uploaded; all other messages are ignored on the phone.

## Build the APK
1. Install Android Studio (Koala or newer) and open this folder.
2. Let Gradle sync (it downloads Gradle 8.7 / Android Gradle Plugin 8.5.2 / SDK 34 automatically).
3. Build → Build Bundle(s) / APK(s) → Build APK(s). Result: `app/build/outputs/apk/debug/app-debug.apk`.
4. Copy the APK to the phone and install it (allow “install unknown apps”).
Command line: `gradle wrapper --gradle-version 8.7` once, then `./gradlew assembleDebug`.

## Pair
1. Admin → **Devices** → Create device. A server address and 8-character code appear.
2. Open the app, enter both, tap **Connect**.
3. Allow SMS + notifications, then **Allow background running** (unrestricted battery).
4. The app now runs as a foreground service, restarts after reboot, and retries offline SMS automatically.

## Notes
* The phone must use a SIM that receives the money notifications and have internet.
* Keep the phone's date & time on automatic (requests are signed and time-checked).
* Android lets the user force-stop an app; if that happens, open the app once to restart it.
* The Play Store restricts SMS-permission apps — install the APK directly (sideload).
