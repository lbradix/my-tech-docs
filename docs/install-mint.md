# Installing Linux Mint (Step-by-Step Guide for Beginners)

> Linux Mint is a beginner-friendly, full-featured Linux distribution that's perfect for new and experienced users alike. Providing an easy transition from the Windows environment, this is an excellent first choice within the Linux realm. This guide  walks you through installing Linux Mint on your machine, whether you’re replacing an existing OS or setting up dual-boot.

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

    !!! tip "Choose the closest mirror to your location for faster download speeds."

---

## 2. Create a Bootable USB

Use a tool like:

- **Windows:** [Rufus](https://rufus.ie), [balenaEtcher](https://www.balena.io/etcher/)
- **macOS:** [balenaEtcher](https://www.balena.io/etcher/)
- **Linux:** Use the `dd` command or USB Creator tool

??? note "Steps using Rufus"

    1. Insert USB drive.
    2. Open Rufus and select your downloaded ISO.
    3. Click **Start** and wait for the process to complete.

??? note "Steps using balenaEtcher"

    1. Insert USB drive.
    2. Open balenaEtcher and select flash from file.
    3. Open your downloaded ISO.
    4. Click select target and select USB.
    5. **Flash!**

??? note "Steps using Linux"

    **Option 1**: USB Creator Tool  
    1. Insert USB drive.  
    2. Open "USB Image Writer"  
    3. Select ISO and choose the USB.  
    4. Click **Write**, enter password when prompted.   
    5. Done! 

    **Option 2**: `dd` command  
    1. Insert your USB and find its device name.  
    Run:  
    `lsblk`  
    2. Navigate to the directory with the ISO  
    `cd ~/Downloads`  
    3. **Write** the ISO to USB  
    Replace `/dev/sdX` with the correct device (e.g., `/dev/sdb`):  
    `sudo dd if=kdeneon-useredition-current.iso of=/dev/sdX bs=4M status=progress oflag=sync`  
    4. Wait for the process to finish.  
    It can take several minutes. Once you see a prompt again, it's done.  
    5. Eject the USB safely.  
    `sudo eject /dev/sdX`


---

## 3. Boot from the USB Drive

1. Restart your computer and enter the boot menu:  
   - Common keys: `F12`, `ESC`, `DEL`, or `F2` 
   
    !!! warning "Confirm BIOS SATA operation is set to AHCI, not RAID." 

2. Select the USB device from the list.
3. Choose **"Start Linux Mint"** from the boot menu.

---

## 4. Install Linux Mint

Once the live environment loads:

1. Click the **"Install Linux Mint"** icon on the desktop.
2. Choose your language and keyboard layout.
3. Connect to internet (optional)
4. **Installation type:**  
    - Replace existing OS
    - Install alongside Windows (dual-boot)
    - Manual partitioning (advanced users)

5. Follow the prompts to:
    - Set time zone
    - Create a computer name, username, and password
    - Begin installation

    !!! warning "Double-check your partitioning choices, this step can delete data."

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
   to install latest updates.

    !!! note "Passwords typed in the terminal are invisible."

---

## Final Thoughts

🎉 Congrats! You have now successfully installed Linux Mint. From here focus on setting up different apps, customizing the desktop or moving over data. Make it feel like home.

---

## Additional Resources  
- [10 Things to Do First in Linux Mint](https://easylinuxtipsproject.blogspot.com/p/first-mint-cinnamon.html)  
- [The Linux Mint User Guide](https://community.linuxmint.com/tutorial/view/20)

<br>

[&uarr; Back to top](#installing-linux-mint-step-by-step-guide-for-beginners)



   
