# 🧾 Linux Mint + GTX 970 + Steam (AoE II DE Setup Guide)

This guide restores your working setup if you reinstall Linux Mint from scratch.  
It ensures Age of Empires II DE runs smoothly via Proton using DXVK 1.x.

---

## 🧩 1. Install NVIDIA driver and Vulkan stack

```bash
sudo apt update
sudo apt install -y nvidia-driver-535 nvidia-dkms-535
sudo apt install -y vulkan-tools libvulkan1 libvulkan1:i386

Enable 32-bit architecture (needed for Proton/Wine):

sudo dpkg --add-architecture i386
sudo apt update
```

🎮 2. Install Steam (Debian package)

Use Software Manager → search Steam → install the regular .deb version.
(Avoid the Flatpak version to prevent Proton library isolation issues.)

Run Steam once and log in.
⚙️ 3. Enable Steam Play for all titles

In Steam:

    Steam → Settings → Compatibility

    ✅ Check “Enable Steam Play for all other titles”

    Choose Proton Experimental (temporarily — you’ll install GE Proton next).

🧰 4. Install GE-Proton (community build with DXVK 1.x)

Install ProtonUp-Qt:

```
flatpak install flathub net.davidotek.pupgui2
```

Run it → click Add version → install GE-Proton7-55 (or newer GE 8.x).

In Steam → Age of Empires II DE → Properties → Compatibility →
✅ Force the use of a specific Proton version → choose GE-Proton7-55.
🧹 5. Clean start (if needed)

To reset the game’s Wine/Proton environment:

```bash
rm -rf ~/.steam/steam/steamapps/compatdata/813780
```

🚀 6. Launch options (optional)

For smoother shader compilation:

```bash
DXVK_ASYNC=1 %command%
```

To skip the launcher:

```
%command% ./AoE2DE_s.exe
```

🧩 7. Verify Vulkan setup

```
vulkaninfo | grep -E "apiVersion|deviceName"
```

Expected output (example):

```
Vulkan Instance Version: 1.3.275
deviceName: NVIDIA GeForce GTX 970
```