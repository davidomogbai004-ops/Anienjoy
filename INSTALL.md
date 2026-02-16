# AniEnjoy Installation Guide

Welcome to AniEnjoy! This guide will help you install and set up the application on your Android device.

## System Requirements

- **Android Version**: Android 6.0 (API 23) or higher
- **RAM**: Minimum 2GB, Recommended 4GB+
- **Storage**: 200MB free space
- **Internet**: Required for streaming and downloading content

## Installation Methods

### Method 1: Download Website (Recommended)

1. Visit the AniEnjoy download page
2. Click the **"Download APK"** button
3. Wait for the download to complete
4. Proceed to **Installation Steps** below

### Method 2: GitHub Releases

1. Go to [GitHub Releases](https://github.com/davidomogbai004-ops/Anienjoy/releases/latest)
2. Download the latest `app-release.apk` file
3. Proceed to **Installation Steps** below

### Method 3: Terminal/Command Line

For users comfortable with terminal:

```bash
curl -sSL https://raw.githubusercontent.com/davidomogbai004-ops/Anienjoy/main/download.sh | bash
```

This script will:
- Fetch the latest APK automatically
- Download to your current directory
- Optionally install via ADB if device is connected

## Installation Steps

### Step 1: Enable Unknown Sources

Before installing, you need to allow installation from unknown sources:

1. Open **Settings** on your Android device
2. Navigate to **Security** or **Privacy** (varies by device)
3. Find **Unknown Sources** or **Install unknown apps**
4. Enable the permission
   - Some devices may ask you to enable this for specific apps (like your file manager or browser)

### Step 2: Install the APK

1. Locate the downloaded `app-release.apk` file
   - Usually in your **Downloads** folder
2. Tap the APK file to open it
3. Review the permissions (this is normal)
4. Tap **Install**
5. Wait for installation to complete
6. Tap **Done** or **Open**

### Step 3: Grant Permissions

When you first launch AniEnjoy, it may request permissions for:
- **Storage**: To cache downloaded content
- **Internet**: To stream and access content
- **Camera** (if applicable): For certain features

Grant the necessary permissions to use all features.

## First Launch

1. The app will initialize on first launch (may take a few moments)
2. You may see a loading screen - this is normal
3. Once loaded, you can start browsing manga, anime, and novels

## Troubleshooting

### "App not installed" Error

**Solution 1**: Check Storage Space
- Ensure you have at least 200MB free space
- Clear some cache if needed

**Solution 2**: Clear Google Play Services Cache
```
Settings → Apps → Google Play Services → Storage → Clear Cache
```

**Solution 3**: Update Google Play Services
- Open Google Play Store
- Search for "Google Play Services"
- Tap "Update"

### "Unknown Error" During Installation

**Solution**: Restart and Retry
1. Restart your device
2. Delete the APK file
3. Download the APK again
4. Try installing again

### App Crashes on Launch

**Solution 1**: Clear App Cache
```
Settings → Apps → AniEnjoy → Storage → Clear Cache
```

**Solution 2**: Uninstall and Reinstall
1. Uninstall the app
2. Restart your device
3. Download and install the latest APK

**Solution 3**: Update Device
- Go to **Settings → System → System Update**
- Install any available updates

### Cannot Download Content

**Check**: Internet Connection
- Ensure you have stable Wi-Fi or mobile data
- Try disabling VPN if you're using one

**Check**: Storage Space
- You need enough free space for downloads
- Clear cache: **Settings → Apps → AniEnjoy → Storage → Clear Cache**

### App Runs Slowly

**Solution 1**: Clear Cache
```
Settings → Apps → AniEnjoy → Storage → Clear Cache
```

**Solution 2**: Close Background Apps
- Close unnecessary apps to free up RAM
- Restart your device

**Solution 3**: Check Available Storage
- Ensure you have at least 500MB free space
- Delete old downloads to free up space

## ADB Installation (Advanced)

If you're familiar with Android Debug Bridge (ADB), you can install directly from your computer:

```bash
adb devices
adb install app-release.apk
```

## Updating AniEnjoy

The app will notify you when updates are available. To update:

1. Visit the download page or GitHub Releases
2. Download the latest APK
3. Install it (it will overwrite the old version)
4. Your data and settings will be preserved

## Uninstalling

To uninstall AniEnjoy:

1. Go to **Settings → Apps → AniEnjoy**
2. Tap **Uninstall**
3. Confirm the uninstallation

Your cached files will be deleted, but you can always reinstall later.

## Advanced: Building from Source

If you want to build the app yourself:

1. Clone the repository:
```bash
git clone https://github.com/davidomogbai004-ops/Anienjoy.git
cd Anienjoy
```

2. Build the APK:
```bash
# For Gradle-based projects
./gradlew assembleRelease

# For Flutter projects
flutter build apk --release
```

3. The built APK will be in the `build/` directory

## Getting Help

- **Report Issues**: [GitHub Issues](https://github.com/davidomogbai004-ops/Anienjoy/issues)
- **Discussions**: [GitHub Discussions](https://github.com/davidomogbai004-ops/Anienjoy/discussions)

## Security & Privacy

- AniEnjoy requires storage and internet permissions to function
- No personal data is collected
- All your data is stored locally on your device
- Review our privacy policy for more information

---

Enjoy AniEnjoy! If you have any questions or issues, please don't hesitate to reach out. Happy streaming! 📚🎬📖