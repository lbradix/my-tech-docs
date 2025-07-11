# Installing Linux Mint

Linux Mint is a beginner-friendly, full-featured Linux distribution that's perfect for new and experienced users alike. This guide walks you through installing Linux Mint on your machine—whether you’re replacing an existing OS or setting up dual-boot.

---

## 📝 Prerequisites

- A USB flash drive (8GB or larger)
- Access to a working computer with internet
- Basic familiarity with boot menus and BIOS/UEFI settings
- Optional: Backup your existing data

---

## 1. Download Linux Mint

1. Visit the official [Linux Mint website](https://linuxmint.com/download.php).
2. Choose a desktop environment (Cinnamon is the default).
3. Download the latest ISO file.

> 💡 *Choose the closest mirror to your location for faster download speeds.*

---

## 2. Create a Bootable USB

Use a tool like:

- **Windows:** [Rufus](https://rufus.ie)
- **macOS:** [BalenaEtcher](https://www.balena.io/etcher/)
- **Linux:** Use the `dd` command or USB Creator tool

Steps (example using Rufus):
1. Insert USB drive.
2. Open Rufus and select your downloaded ISO.
3. Click **Start** and wait for the process to complete.

---

## 3. Boot from the USB Drive

1. Restart your computer and enter the boot menu:
   - Common keys: `F12`, `ESC`, `DEL`, or `F2`
2. Select the USB device from the list.
3. Choose **"Start Linux Mint"** from the boot menu.

---

## 4. Install Linux Mint

Once the live environment loads:

1. Click the **"Install Linux Mint"** icon on the desktop.
2. Choose your language and keyboard layout.
3. **Installation type:**
   - Replace existing OS
   - Install alongside Windows (dual-boot)
   - Manual partitioning (advanced users)

4. Follow the prompts to:
   - Set time zone
   - Create a username and password
   - Begin installation

> ⚠️ *Double-check your partitioning choices—this step can delete data.*

---

## 5. First Boot & Updates

After installation:

1. Remove your USB when prompted.
2. Restart your computer.
3. Log in with your new user account.
4. Run:  
   ```bash  
   sudo apt update && sudo apt upgrade
   ```
   
