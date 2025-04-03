## ✅ 6. Scenario: Permission Denied When Running a Script

**Question:**  
A user runs a shell script but gets a "Permission denied" error. How would you resolve it?

**Answer:**
```bash
ls -l script.sh
chmod +x script.sh
```

**Explanation:**  
The issue is usually missing execute permission. I use `ls -l` to verify and `chmod +x` to fix. This shows basic but critical knowledge of Linux permissions and script execution.

---

## ✅ 7. Scenario: Port 80 is Already in Use

**Question:**  
You try to start Apache, but it fails because port 80 is already in use. How do you handle this?

**Answer:**
```bash
netstat -tuln | grep :80
lsof -i :80
kill -9 <PID>  # if safe to stop
```
netstat= it was used to see network connections,routing process,network interface issuses... simple shows all network releated issues
      -tuln  ==> t= tcp calls,u= udp calls,  l= listening ports , n= is it to knoe numerical ip address

**Explanation:**  
This shows the ability to identify conflicting services using `netstat` and `lsof`, and the judgment to safely terminate processes. It’s a real-world issue in multi-service environments.

---

## ✅ 8. Scenario: Root Password Forgotten

**Question:**  
You have physical access to a Linux machine but forgot the root password. How would you reset it?

**Answer:**
1. Reboot the machine.
2. In GRUB menu, edit the boot entry and add:
   ```
   init=/bin/bash ( int means it was the first process that will runs in linux system.... by using this init=/bin/bash we are skipping the normal intilizations and telling directly come to bash command line interface)
   ```
3. Once in shell:
   ```bash
   mount -o remount,rw / ( is used to mount that means changing the read only permission to read and write without doing from scratch)
   passwd root (giving password for root access)
   exec /sbin/init ( it will execites this sbin/init............ that means exec will replace completly the old with new aruguments in /sbin/init)
   ```

**Explanation:**  
This is a critical recovery scenario. Shows knowledge of boot process, GRUB, single-user mode, and password recovery—great for proving deep system understanding.

---

## ✅ 9. Scenario: Swap Memory is Full

**Question:**  
The system is using too much swap memory and becoming slow. What would you do?

**Answer:**
```bash
free -h
swapon --show
top  # check swap-using processes
swapoff -a ( it will clears all swap space on hard drive)
swapon -a ( it will again creates a swap space to store after tottally filled in ram)
```

**Explanation:**  
swap space means it was the space present in hard drive.. and it was filled after the ram is completely filled
Demonstrates understanding of virtual memory, how to monitor it, and how to clear swap. You might also investigate the need for more RAM or optimize heavy applications.

---

## ✅ 10. Scenario: File Deleted Accidentally – Need Recovery

**Question:**  
A critical file was deleted accidentally from the system. Can it be recovered?

**Answer:**  
- If it's still open by a process:
  ```bash
  lsof | grep deleted    (this was to see the process which are deleted)
  cp /proc/<pid>/fd/<fd> /recovered_file  (మీరు /proc/1234/fd/ డైరెక్టరీలోకి వెళ్ళి ఆ ప్రాసెస్ ఓపెన్ చేసిన ఫైళ్ళను చూడవచ్చు.)
  
  lsof= list of all files
  /proc = means shows the critical information of proccess
  pid = process id
  fd= file descriptions (that means to know what was in the file... same like cat)
  ```
- Otherwise, restore from backup or snapshots (if available).

**Explanation:**  
This scenario shows creative use of `/proc` and `lsof` for emergency recovery. It also highlights the importance of having backup policies in place.

---
```

