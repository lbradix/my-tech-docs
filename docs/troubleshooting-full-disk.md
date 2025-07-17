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

- Enable log rotation:  
```bash  
sudo nano /etc/logrotate.conf  
``` 

- Schedule a monthly disk usage audit via cron:  
```bash  
crontab -e
# Add:
0 7 1 * * df -h | mail -s "Monthly Disk Report" your@email.com
```  

- Monitor disk usage with tools like:  

    - `ncdu`  
    - `glances`  
    - `netdata` or `grafana`  

---

## When to Escalate or Reboot  

- Root (`/`) partition is full and blocking critical services  
- You can't delete anything safely  
- Disk hardware is failing (use `smartctl`, `dmesg`)  

---

## Quick Fix Checklist  

+ [ ] `df -h` run, issue confirmed  
+ [ ] Large folders identified via `du -sh`  
+ [ ] Logs or cache cleaned  
+ [ ] Root cause documented  
+ [ ] Prevention in place  

---

!!! tip "**Pro Tip**: Keep `/var/log`, `/tmp`, and `/home` on separate partitions when possible to isolate failures."


 

