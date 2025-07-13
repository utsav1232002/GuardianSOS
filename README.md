# GuardianSOS
Emergency SOS App
Overview
The Emergency SOS App is a safety-focused Android application designed to provide quick assistance in emergencies. It allows users to discreetly trigger an SOS mode that sends critical information (last 5 call logs and current GPS location) via SMS to a pre-set emergency contact. Additionally, it captures photos from all available device cameras and stores them securely in a password-protected folder. The app can be launched normally through the app icon or via a deliberate keypress sequence (4 successive power button presses within 2 seconds) to minimize accidental activations.

This app is built using Kotlin in Android Studio, targeting Android SDK 34 (Android 14) with a minimum SDK of 26. It emphasizes user privacy, requiring explicit permissions and biometric authentication for sensitive actions. Note: This is a prototype app developed through iterative AI-assisted coding (vibe coding). It is intended for personal use and testing; always verify functionality on your device and comply with local privacy laws.

Features
Dual Launch Modes:
Normal launch via app icon for setup and testing.
SOS launch via 4 quick power button presses (within 2 seconds) for discreet activation in emergencies.
SOS Actions:
Sends the user's last 5 call logs and current GPS location (latitude/longitude) via SMS to a user-defined emergency number.
Automatically captures photos from all available cameras (front and back) in a silent loop (e.g., every 5 seconds for 1 minute) and stores them in an encrypted, password-protected folder.
Provides a short, silent vibration feedback on SOS launch to confirm activation without alerting others.
Security and Control:
Requires biometric authentication (fingerprint/face) or device password/PIN to stop the app or cancel SOS actions, preventing unauthorized closure.
All permissions (e.g., location, camera, call logs) are requested and explained during setup.
Secure storage using encrypted files to protect captured photos.
User Customization:
Set emergency contact number and folder password via settings.
Guide to enable Accessibility Service for power button detection.
Error Handling:
Graceful handling of denied permissions, no GPS signal (uses last known location), or other issues with user notifications.
Requirements
Android device running version 8.0 (Oreo) or higher.
Google Play Services for location features.
Physical power button on the device.
User must grant permissions and enable Accessibility Service for full functionality.
Installation
From Source (Developer Setup):
Clone the repository: git clone https://github.com/your-repo/EmergencySOSApp.git (replace with actual repo if hosted).
Open the project in Android Studio.
Sync Gradle and build the project.
Run on an emulator or physical device.
From APK:
Download the signed APK from [releases] (or sideload via provided APK file).
Enable "Install from Unknown Sources" in device settings.
Install the APK and launch the app.
Note: For production use, consider publishing to Google Play Store after thorough testing and compliance checks (e.g., Google Play's permission policies).

Permissions Required
The app requests the following permissions at runtime (explained in-app):

READ_CALL_LOG: To access recent call history.
ACCESS_FINE_LOCATION: For precise GPS location.
CAMERA: To capture photos from device cameras.
READ_EXTERNAL_STORAGE / WRITE_EXTERNAL_STORAGE: For storing encrypted photos.
SEND_SMS: To send emergency messages.
VIBRATE: For silent haptic feedback.
Accessibility Service: For detecting power button presses (must be enabled manually in device settings).
If permissions are denied, the app will prompt explanations and allow re-requests. Denials may limit functionality (e.g., no location sending).

User Guide
This guide walks you through setting up and using the Emergency SOS App. The app is designed for simplicity and reliability in high-stress situations.

Step 1: Initial Setup
Launch the app normally via the app icon.
On first launch, you'll be directed to the Settings screen.
Set Emergency Contact:
Enter a phone number (e.g., a trusted friend, family, or emergency service).
Save it – this is stored securely on your device.
Set Secure Folder Password:
Choose a strong password for the photo storage folder (or use biometrics if preferred).
Grant Permissions:
Tap the "Request Permissions" button.
Allow each permission when prompted (e.g., location, camera). The app explains why each is needed.
If denied, you can retry or go to app settings.
Enable Accessibility Service:
Tap the "Enable Accessibility" button – this opens your device's Accessibility settings.
Find "Emergency SOS App" in the list and enable it.
This is required for power button SOS detection. The app will check if it's enabled and prompt if not.
Step 2: Testing the App (Normal Mode)
From the main screen, tap "Test SOS" (mock mode).
The app simulates sending data and capturing photos without actual SMS or storage.
View status indicators (e.g., "Location Fetched", "Photos Captured").
To stop the test, authenticate via biometrics or device password.
Step 3: Activating SOS in Emergency
Via Power Button:
Press the power button 4 times quickly (within 2 seconds).
Feel a short vibration to confirm launch (silent, no screen needed initially).
Actions Triggered:
App launches in background/foreground.
Fetches and sends last 5 call logs + GPS location via SMS to your emergency number.
Starts capturing photos from all cameras and saves them encrypted.
A notification or screen (if visible) shows "SOS Activated".
Cancel/Stop (If Accidental):
The app may delay full actions by 10 seconds with a cancel prompt.
To stop, use the close button or back press – authenticate with biometrics or password.
If authentication fails, the app continues for safety.
Step 4: Accessing Captured Photos
In normal mode, go to Settings > View Secure Folder.
Authenticate with password or biometrics.
View or decrypt photos (stored in app's private directory).
Step 5: Troubleshooting Common Issues
SOS Not Triggering: Ensure Accessibility Service is enabled. Test presses in a quiet environment. If issues persist, check device OEM restrictions (e.g., some phones remap power button).
No Vibration: Verify VIBRATE permission is granted. Test in settings.
Permissions Denied: Go to device Settings > Apps > Emergency SOS App > Permissions and enable manually.
No GPS: App uses last known location; ensure location services are on.
Battery Drain: SOS mode is short-lived; optimize by closing after use.
Multi-Camera Issues: On single-camera devices, it defaults to available one.
Accidental Launch Prevention: The 4-press sequence is deliberate; adjust timing if needed in code.
For advanced troubleshooting, check app logs via Android Studio or adb.

Privacy and Safety Notes
All data (logs, location, photos) is handled locally and only sent/shared with user consent.
Photos are encrypted and require authentication to access.
This app is not a substitute for official emergency services (e.g., 911). Use responsibly.
Comply with laws on data sharing and recording.
Contributing
Contributions welcome! Fork the repo, make changes, and submit a pull request. Focus on bug fixes, UI improvements, or additional features like cloud backup (with consent).
