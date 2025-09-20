# Day 6 - Process Management in Linux

## 📖 Introduction to Process Management
A **process** is simply a running program. Linux gives us powerful tools to monitor, manage, and control processes. Every process has a unique **PID (Process ID)** and a **PPID (Parent Process ID)**.

Understanding process management is critical to ensure system stability, manage resources, and troubleshoot performance issues.

## 🧠 What I Learned Today

### 🔍 Viewing Processes
```bash
ps aux              # View all running processes with CPU, memory usage
ps -ef              # View process tree with UID, PID, PPID, CMD
ps -u prakash       # Show processes of a specific user
ps -C sleep         # Show process by name
pgrep sleep         # Get PID by process name
pidof sleep         # Get PID(s) of a running program
```

### 🌳 Process Tree View
```bash
ps -e --forest      # View process hierarchy in tree format
```
Helps visualize parent-child relationships of processes.

### 🎭 Background & Foreground Processes
```bash
sleep 200 &         # Run process in background
jobs                # List all background jobs
fg %1               # Bring job 1 to foreground
Ctrl + Z            # Suspend a process
bg %1               # Resume process in background
```

### 🛑 Stopping & Resuming Processes
```bash
kill -STOP 930      # Stop process with PID 930
kill -CONT 930      # Resume process with PID 930
```

### 💀 Killing Processes
```bash
kill 930            # Terminate process by PID
kill -9 930         # Force kill (SIGKILL) – dangerous in production!
pkill sleep         # Kill process by name
pkill -9 sleep      # Force kill all processes with name sleep
```

### 🎚️ Process Priorities (Nice & Renice)
```bash
nice -n 10 sleep 200      # Start process with lower priority (10)
renice -n 10 -p 930       # Change priority of a running process
```
- **Lower nice value (-5, 0)** = higher priority
- **Higher nice value (10, 19)** = lower priority

### 📊 Monitoring System Processes
```bash
top                 # Real-time process monitoring
htop                # Interactive process viewer (needs installation)
```
- Press `k` in top → enter PID → kill process
- Press `r` in top → enter PID → change priority (renice)

### ⚙️ Daemon Process Management
Daemon processes are background services that run without user interaction.
```bash
systemctl list-units --type=service   # List services
systemctl start ssh                   # Start SSH service
systemctl stop ssh                    # Stop SSH service
systemctl enable ssh                  # Enable service on boot
```
Example daemons: `cron`, `ssh`, `rsyslog`, `systemd`

## 🧪 Practical Example
```bash
sleep 200 &             # Start a background process
ps aux | grep sleep     # Get PID of sleep process
kill -STOP <PID>        # Stop the process
kill -CONT <PID>        # Resume process
sudo renice -n 10 -p <PID>  # Lower priority
kill -9 <PID>           # Force kill process
```

## 💡 Key Takeaways
✅ `ps aux` gives detailed process info including CPU/memory.
✅ `ps -ef` is more about UID, PID, PPID in tree view.
✅ `kill -9` is last resort – use it carefully.
✅ Daemon processes keep services running in the background.
✅ Nice values control process scheduling priority.


