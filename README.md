# Optimise: iPhone app (free build)

This project wraps your Daily Optimisation web app in a real iPhone app (using Capacitor).
GitHub's free Mac computers build it for you, and you install it on your iPhone from a Windows PC.
You do not need a Mac and you do not need to pay Apple.

IMPORTANT: I could not run a build from where I wrote this, so the first build may fail with an
error. That is normal. Copy the end of the error log and send it to me, and I will fix it.

## What is in this folder
- `www/index.html`      your app (the same one you tested in Safari)
- `package.json`        the list of building blocks the app uses
- `capacitor.config.json`  the app's name and settings
- `resources/icon-1024.png`  the app icon
- `.github/workflows/build-ios.yml`  the instructions GitHub follows to build the app

## Part A. Put the project on GitHub and build it (one time, about 30 minutes)
1. Make a free account at github.com (Sign up). Verify your email.
2. Click the + at the top right, then **New repository**. Name it `optimise-ios`.
   - **Public**: free and unlimited building. Anyone could see the code. It contains no personal data
     (your food, workouts and weight stay on your phone), and no passwords or keys.
   - **Private**: only you see it, but GitHub's free plan gives about 200 Mac-build minutes a month
     (Mac minutes count 10 times). A build takes roughly 10 to 25 minutes, so that is a handful of builds.
   Click **Create repository**.
3. Unzip this project on your PC. On the new repository page click **uploading an existing file**.
   Drag in everything from inside the unzipped folder (the `www`, `resources` and `.github` folders and the
   other files). Wait for the uploads to finish, then click **Commit changes**.
   - If the `.github` folder did not upload (folders starting with a dot can be skipped), do this instead:
     click **Add file, Create new file**, type `.github/workflows/build-ios.yml` as the name, paste in the
     contents of that file, and commit.
4. Click the **Actions** tab. If GitHub asks, click the green button to enable workflows.
5. Click **Build iOS app (unsigned IPA)** on the left, then **Run workflow**, then the green **Run workflow**.
6. Wait. A yellow dot means it is running. A green tick means it worked. A red cross means it failed.
7. Green tick: click the run, scroll to **Artifacts**, and download **Optimise-ipa**. Unzip it and you get
   `Optimise-unsigned.ipa`. Keep this file.
8. Red cross: click the run, click the failed step (it has a red cross), and copy the last 40 or so lines of
   the log. Send them to me.

## Part B. Get your Windows PC ready (one time)
1. If you have iTunes or iCloud from the Microsoft Store, uninstall them. Sideloadly needs the versions from Apple's website.
2. Download iTunes for Windows (64-bit) from apple.com/itunes and install it.
3. Download and install iCloud for Windows from Apple's website (not the Microsoft Store).
4. Download and install **Sideloadly** from sideloadly.io.
5. Plug your iPhone into the PC with a USB cable. Tap **Trust** on the phone and enter your passcode.
   Open iTunes once and check it can see your iPhone.

## Part C. Install the app on your iPhone
1. Open Sideloadly. Your iPhone should appear at the top.
2. Drag `Optimise-unsigned.ipa` onto Sideloadly.
3. Type your Apple ID email. A free Apple ID is enough. Some people prefer a separate free Apple ID just for
   this. Click **Start** and enter the password (and the two-factor code if asked).
4. Wait for "Done".
5. On the iPhone: **Settings > General > VPN & Device Management**, tap your Apple ID under "Developer App",
   then **Trust**.
6. On iOS 16 and later: **Settings > Privacy & Security > Developer Mode**, switch it on and restart when asked.
   (This switch can appear only after the first install attempt.)
7. Open **Optimise** from your home screen.

## Part D. Move your data from the Safari version
1. In the web version: **Goals > Backup > Export backup**. Copy the text (it is also shown in a box) and
   send it to yourself, for example in Notes or a message.
2. In the new app: **Goals > Backup**. Paste the text in the box, tap **Check pasted backup**, then
   **Replace my data with this backup**.
The web version and the iPhone app keep separate data, so do this once and use only one from then on.

## The 7-day rule (free Apple ID)
- The app stops opening after 7 days. Repeat Part C with the same file to renew it.
- Before renewing, use **Goals > Backup > Export backup** in case something goes wrong.
- Sideloadly has an option to refresh automatically. It only works while Sideloadly is running on your PC,
  and the PC and phone are connected.
- A free Apple ID can only have 3 apps like this at once, and Apple limits how many it will sign per week.
- If the app ever gets deleted and reinstalled, its data is lost, so keep backups.

## What works in this first iPhone build
- Everything in the web version, with your data stored in the app.
- **Reminders**: habit reminders (every day at the time you set) and tasks that have a time. They arrive as
  real notifications. The app asks for permission the first time you set one.
- **Barcode scanner and food lookups**: the camera asks for permission the first time you scan.
- **Golf course search**: works once you enter your GolfCourseAPI key.
- **Backup**: Goals > Backup uses the iPhone Share sheet (Save to Files, AirDrop, email).

## What does not work yet
- **Apple Health** (needs a paid Apple Developer account). The paste-in workout import still works.
- **Outlook calendar section**: it needs the Claude connection, which only exists in the web version.
  Reading the iPhone Calendar app instead (which can include your Outlook calendar) is a later step.
- Notifications use Apple's local notification system. Apple limits an app to 64 waiting at once, so the app
  schedules the next two weeks and refreshes them whenever you open it.

## Updating the app later
Whenever I give you a new `index.html`: on GitHub open `www/index.html`, click the pencil, replace the
contents, commit, then run the workflow again (Part A, steps 5 to 7) and reinstall (Part C).
