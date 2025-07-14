# Joining a Linux Device to Windows Server 2025 Active Directory (Winbind Method)

Use this guide to join a Debian/Ubuntu-based Linux system (like KDE Neon, Mint or Zorin) to a Windows Server 2025 AD domain using `winbind`, `samba`, and Kerberos.

---

## 📝 Prerequisites

- Windows Server 2025 configured as Domain Controller
- Domain name: `bradix.org`
- AD server IP: `192.168.10.31`
- Domain join account (e.g., `lbradix`)
- Linux client with sudo access

---

## 1. Set hostname
- Run:
  ```bash  
  sudo hostnamectl set-hostname <your-hostname>
  ```
- Update any old occurrences of the hostname located at `/etc/hosts`
- Run:
  ```bash
  sudo nano /etc/hosts
  ```
- Reboot
  ```bash
  sudo reboot
  ```

---

## 2. Set DNS to the AD server
- Point `/etc/resolv.conf` to your Windows Server:  
  ```bash  
  sudo nano /etc/resolv.conf
  ```
- Edit `/etc/resolv.conf` to show the follow output:
  ```bash
  nameserver <server-IP>
  search <server-domain>
  ```

---

## 3. Install required packages
- Run:
```bash
sudo apt update
sudo apt install samba krb5-user winbind libpam-winbind libnss-winbind -y
```
- When prompted during `krb5-user` install, enter:  
```rust
Default realm: <server-domain>
```
- Press enter on any other prompts, leaving them blank

---

## 4. Configure Kerberos
- Edit `/etc/krb5.conf`:
```ini
[libdefaults]
    default_realm = <server-domain>
    dns_lookup_realm = false
    dns_lookup_kdc = true
```

---

## 5. Configure Samba
- Backup and replace `/etc/samba/smb.conf`:
```bash  
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo nano /etc/samba/smb.conf
```
- Paste in:
```ini
[global]
  workgroup = <server-workgroup>
  realm = <server-domain>
  security = ads
  client signing = yes
  client use spnego = yes
  kerberos method = secrets and keytab
  log file = /var/log/samba/%m/log
  log level = 1
  winbind refresh tickets = yes
  winbind use default domain = yes
  winbind offline logon = yes
  idmap config * : backend = tdb
  idmap config * : range = 10000-20000
  template shell = /bin/bash
  template homedir = /home/%U
```
??? tip "How to Select all in Nano Text Editor"
    
    1. Press "Alt + Backslash" keys together. This moves the cursor to the start of the file.  
    2. Press "Ctrl + 6" keys together. This sets a mark at the current cursor position.  
    3. Press "Alt + Forward Slash" keys together. This moves the cursor to the end of the file.
    4. Press "Ctrl Shift K keys together. This will clear all selected text.

---

## 6. Configure nss
- Edit `/etc/nsswitch.conf`, update these lines:  
```ini
passwd:         compat winbind
group:          compat winbind
shadow:         compat
```

---

## 7. Restart services
```bash  
sudo systemctl restart smbd nmbd winbind
```
- Enable on boot:
```bash  
sudo systemctl enable winbind
```

---

## 8. Test kerberos and join domain
- Test authentication: 
```bash  
kinit <server-domian-user>
```
!!! note "You'll most likely see a password expiration message, that's fine."

- Then join:  
```bash  
sudo net ads join -U <server-domian-user>
```
!!! note "Seeing DNS update failed is normal."

---

## 9. Test identity resolution
```bash
wbinfo -u     # List domain users
wbinfo -g     # List domain groups
getent passwd <server-domian-user>
```

---

## 10. Enable domain login and home creation
- Edit PAM and enable home dir creation:  
```bash
sudo pam-auth-update
```
> Below is what your pam settings should look like:

![GitHub Pages settings screenshot](assets/pam.png)

<br>

---

## 11. Reboot and log in
- Now reboot and log in with domain user:
!!! note "Password will be pulled from the domain."

---

!!! success "Success! Your Linux device is now joined to the Windows Server 2025 Active Directory domain using the Winbind method"







