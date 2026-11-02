# Clearaer

A small Mac app that scans cache folders, shows their sizes, and lets you choose what to move to Trash.

It lives on its own. It is not part of MealLensAI.

## Open the app

Double-click `Clearaer.app`.

The first time on another Mac, Apple may say **Clearaer Not Opened**.
That is Gatekeeper. It happens because this build is not yet Apple-notarized.
Do not click **Move to Trash**.

1. Right-click `Clearaer.app`
2. Choose **Open**
3. Click **Open** again

Or click **Done**, then System Settings → Privacy & Security → **Open Anyway**.

Install from Terminal (this also clears the warning):

```bash
hdiutil attach ~/Downloads/Clearaer.dmg -nobrowse
rm -rf /Applications/Clearaer.app
cp -R "/Volumes/Install Clearaer/Clearaer.app" /Applications/
xattr -dr com.apple.quarantine /Applications/Clearaer.app
hdiutil detach "/Volumes/Install Clearaer"
open /Applications/Clearaer.app
```

If the app is already in Applications:

```bash
xattr -dr com.apple.quarantine /Applications/Clearaer.app && open /Applications/Clearaer.app
```

Or one line from the website:

```bash
curl -fsSL https://healthassistant.meallensai.com/downloads/install-clearaer.sh | bash
```

To make double-click work for everyone with no warning, join the
[Apple Developer Program](https://developer.apple.com/programs/) ($99/year)
and run `./scripts/notarize.sh`.

## How to use it

1. The app scans automatically when it opens.
2. Safe caches are selected. Items marked **Ask first** (Docker, Ollama, macOS temp) stay unchecked.
3. Tick or untick folders.
4. Watch **You'll free** update as you tick folders, then click **Clean Up**.
5. Empty Trash later if you want the space back immediately.

Login files, Keychain, and Cursor/VS Code user data are blocked and cannot be deleted from this app.

## Build it again

```bash
cd ~/clearaer
./build.sh
open Clearaer.app
```

Needs macOS 13+ on Intel or Apple Silicon, and Xcode Command Line Tools (`xcode-select --install`). The DMG is a universal binary.

## Share with friends

Send `Clearaer.dmg`. Friends open it and drag **Clearaer** into **Applications**.

The first time they should right-click the app and choose **Open**, or
double-click **Open Clearaer.command** in the disk image.
