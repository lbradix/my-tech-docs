# Troubleshooting Full Disk Issues on Linux Servers

> Audience: System Administrators, Home Lab Users, DevOps  
> Last Updated: July 2025  
> Author: LeValle Bradix

---

## Symptoms

You may encounter one or more of the following:

- `No space left on device` errors
- Failed systemd services or application crashes
- Inability to write files or restart processes
- Cron jobs or backup tasks failing
- System becomes unresponsive or fails to boot

---

## Immediate Checks

1. **Check overall disk usage:**
    ```bash
    df -h
    ```

2. **Find large directories:**
    ```bash
    sudo du -sh /* 2>/dev/null | sort -h
    ```

3. **Check inside `/var` (commonly problematic):**
    ```bash
    sudo du -sh /var/* | sort -h
    ```

4. **Look for large log files:**
    ```bash
    sudo find /var/log -type f -size +50M
    ```

---

## Safe Cleanup Actions

> Always verify before deleting. Use `ls -lh` to inspect.  

**Rotate or delete logs:**  
```bash
sudo journalctl --vacuum-size=100M
sudo rm -f /var/log/*.gz /var/log/*.[0-9]
```  

**Clean apt/yum cache:**  

- Debian/Ubuntu:  
```bash
sudo apt clean
```  
- RHEL/Fedora:
```bash
sudo dnf clean all
```  

**Clear thumbnail or temp files (desktop systems):**  
```bash
rm -rf ~/.cache/thumbnails/*
sudo rm -rf /tmp/*
```  

---
   
## Root Cause Analysis  

 - Did a service generate excessive logs? (`/var/log/syslog`, `journald`)  
 - Did backups or cron jobs write to the wrong location?  
 - Are containers, VMs, or snapshots eating space?  
 - Was logrotate or a cleanup script misconfigured?  

 ---

## Preventive Measures  

