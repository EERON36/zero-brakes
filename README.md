# Zero Brakes

A one-thumb arcade game for iPhone and iPad. A WCMX daredevil in a sports wheelchair with side-mounted rockets jumps oncoming traffic, pulls stunts and chases a high score.

**Status:** M1 (playable prototype) in progress. The game runs on placeholder shapes until the real art lands.

## Docs
- [Game plan](docs/PLAN.md): design, tech stack, roadmap, monetization, risks
- [Art style guide](docs/art-style.md): the rules every asset follows
- [Asset manifest](docs/asset-manifest.md): every sprite and sound, with sizes and status
- [Tuning guide](docs/tuning.md): what every gameplay number does
- [Playtest template](docs/playtests/TEMPLATE.md)

---

## Mac setup (one time, about 1 hour)

You need a Mac with recent macOS and plenty of free disk space (Xcode is large, around 40 GB with simulators).

### 1. Install Xcode
1. Open the **App Store** on the Mac, search for **Xcode**, and install it. It's free, and it's big, so it takes a while.
2. Open Xcode once. Let it install its extra components. When it asks which platforms to download, tick **iOS**.
3. In the Terminal (Applications → Utilities → Terminal), run this once so the command-line tools use the full Xcode:
   ```bash
   sudo xcode-select -s /Applications/Xcode.app
   ```

### 2. Sign in with your Apple ID in Xcode
1. Xcode → **Settings…** → **Accounts** → **+** → **Apple ID**, and sign in.
2. This creates a free **Personal Team**. That's enough to run the game on your own iPhone. The paid Apple Developer account ($99/year) is only needed later for TestFlight and the App Store.

### 3. Install Homebrew and the tools
[Homebrew](https://brew.sh) is a free installer for developer tools.
1. Paste the install command from https://brew.sh into the Terminal and follow its instructions. At the end it tells you to run two extra lines to add Homebrew to your PATH. Run them.
2. Install the project's tools:
   ```bash
   brew install git gh xcodegen
   ```
   - `git`: version control
   - `gh`: GitHub from the Terminal (for issues)
   - `xcodegen`: builds the Xcode project file from `project.yml`
3. Log in to GitHub:
   ```bash
   gh auth login
   ```
   Choose **GitHub.com**, then **HTTPS**, then **Login with a web browser**.

### 4. Get the code
```bash
mkdir -p ~/Projects && cd ~/Projects
gh repo clone EERON36/zero-brakes
cd zero-brakes
```

### 5. Install Claude Code
Install the Claude desktop app (or the `claude` command-line tool) from https://claude.com/claude-code, and open it in the `~/Projects/zero-brakes` folder. It reads `CLAUDE.md` automatically and knows the project rules.

### 6. Build the project (once M1 code exists)
```bash
xcodegen generate
open ZeroBrakes.xcodeproj
```
- Run `xcodegen generate` again whenever files are added or removed. Claude Code does this for you.
- In Xcode, click the **ZeroBrakes** target → **Signing & Capabilities** → **Team**, and pick your Personal Team. If Xcode complains the bundle ID is taken, change it to something unique like `com.yourname.zerobrakes`.
- To test without a phone, pick an **iPhone simulator** at the top of the Xcode window and press **▶ Run** (⌘R).

---

## iPhone setup (one time)

### 1. Connect the iPhone to the Mac
1. Plug the iPhone into the Mac with a USB cable.
2. Unlock it and tap **Trust** when it asks "Trust This Computer?", then enter your passcode.
3. In Xcode, go to **Window → Devices and Simulators**. The iPhone should appear. The first time, Xcode spends a few minutes "preparing" it. Wait until that finishes.

### 2. Turn on Developer Mode
The option only appears after the iPhone has been connected to Xcode once.
1. On the iPhone: **Settings → Privacy & Security → Developer Mode** (near the bottom) → turn it on.
2. The iPhone restarts. After restarting, tap **Turn On** and enter your passcode.

### 3. Run the game on the iPhone
1. In Xcode, pick your **iPhone** in the device menu at the top of the window (instead of a simulator).
2. Press **▶ Run** (⌘R).
3. **First time only:** iOS blocks apps from a new developer. On the iPhone, go to **Settings → General → VPN & Device Management**, tap your Apple ID under "Developer App", and tap **Trust**. Then press Run again.
4. The game launches. Turn the phone sideways, since the game is landscape.

### Good to know
- **Free Personal Team installs expire after 7 days.** The icon stays, but the app won't open. Plug in and press Run again to refresh it.
- **Wireless running:** after the first cable run, in **Window → Devices and Simulators**, tick **Connect via network**. As long as the phone and Mac are on the same Wi-Fi, you can run without the cable.
- **Tuning panel:** during a run, triple-tap the **top-left corner** to open the tuning sliders (see [docs/tuning.md](docs/tuning.md)).
- **iPad:** exactly the same steps as the iPhone.

---

## Sharing a test version (after the paid Apple Developer account is active)

The first almost-finished version goes to friends through **TestFlight**, Apple's free beta-testing app.
1. In [App Store Connect](https://appstoreconnect.apple.com), create the app (this also reserves the name).
2. In Xcode: **Product → Archive**, then **Distribute App → App Store Connect → Upload**.
3. In App Store Connect → **TestFlight**, create an **external testing** group and add the build. The first build gets a short Apple review, usually about a day.
4. Invite testers by email or share the **public link**. On their iPhone they install the **TestFlight** app from the App Store and tap the link. No cable or Mac needed on their side.

---

## License
Copyright © 2026. **All rights reserved.** The source code and art are public to view but not licensed for reuse or redistribution.
