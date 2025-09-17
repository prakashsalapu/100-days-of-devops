# 📅 Day 3 – Linux Folder Structure & Root Access  

## 🔑 What I Learned
Today, I explored **Linux Folder Structure** in depth.  

### 🧑‍💻 `sudo su`
- `sudo` → Run commands with superuser (root) privileges.
- `sudo su` → Switch user to root account **with root shell**.
- `sudo su -` → Switch to root **login shell** (loads root’s environment variables).



### 🗂️ **Root Directory `/`**
The root directory `/` is the **top-most folder** in Linux.  
Everything starts here – all files, folders, devices are connected under `/`.



### 📂 **Important Folders in Linux**

| Folder       | Purpose |
|-------------|---------|
| `/bin`      | Essential user binaries (commands like `ls`, `cp`, `mv`) |
| `/sbin`     | System binaries (for admin tasks like `shutdown`, `mount`) |
| `/etc`      | Configuration files (system-wide settings, network config) |
| `/home`     | Home directories for users |
| `/root`     | Root user's home directory |
| `/usr`      | User applications, libraries, documentation |
| `/var`      | Variable files (logs, mail, spool) |
| `/tmp`      | Temporary files (cleared after reboot) |
| `/opt`      | Optional software (third-party applications) |
| `/dev`      | Device files (hard drives, USB, etc.) |
| `/proc`     | Virtual filesystem for processes |
| `/lib`      | Shared libraries required for programs in `/bin` and `/sbin` |



### 🧠 **Key Takeaways**
- The root `/` is like **C:\ in Windows** - everything lives here.
- System commands are stored in `/bin` and `/sbin`.
- `/etc` is the heart of configuration (be careful when editing files here).
- `/home` is where user files & configs live (like your Desktop/Documents).



### 🛠️ **Practical Task**
- Run `ls /` to explore folders under root.
- Open `/etc/passwd` using `cat /etc/passwd` to see user accounts.
- Try `sudo su -` and check `whoami` (should say `root`).



## ✅ Day 3 Completed!
Learning the folder structure makes navigating Linux much easier – it’s like knowing the map before exploring a city.  

---

## 📌 Connect With Me
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/prakashsalapu/)  
You're already here on **GitHub** 😉

