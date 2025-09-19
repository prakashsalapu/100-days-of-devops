# Day 5 – Linux File Permissions

## 📖 Introduction to File Permissions
File permissions control **who can read, write, or execute** files and directories in Linux. There are three types of users:
- **Owner (User)** – The file creator.
- **Group** – Users belonging to the file's group.
- **Others** – Everyone else on the system.

Permissions are:
- **Read (`r` / `4`)** – View file contents or list directory.
- **Write (`w` / `2`)** – Modify file contents or create/delete files in a directory.
- **Execute (`x` / `1`)** – Run the file (if script/program) or access directory.

Check permissions:
```bash
ls -l filename
```
Example:
```bash
-rwxr--r-- 1 prakash devops 1234 Sep 19 10:00 script.sh
```
Here:
- `rwx` → Owner permissions
- `r--` → Group permissions
- `r--` → Others permissions



## 🔑 Viewing Permissions
```bash
ls -l                # Long listing format
ls -lha              # Long + hidden files + human-readable
stat filename        # Detailed permission info
```



## ✏️ Changing Permissions with `chmod`

### **Symbolic Mode**
Use symbols `u` (user), `g` (group), `o` (others), `a` (all):
```bash
chmod u+x file       # Add execute for user
chmod g-w file       # Remove write for group
chmod o=r file       # Read-only for others
chmod u=rwx,g=rx,o= file   # Full for user, read+execute for group, none for others
```

### **Numeric (Octal) Mode**
Permissions are numbers: `r=4, w=2, x=1`.
```bash
chmod 755 file       # u=rwx, g=rx, o=rx
chmod 644 file       # u=rw, g=r, o=r
chmod 700 file       # Only owner has full access
chmod 750 file       # u=rwx, g=rx, o=---
```



## 👑 Changing Ownership

### **Change Owner & Group**
```bash
sudo chown prakash file.txt           # Change owner only
sudo chown prakash:devops file.txt    # Change owner & group
sudo chown :devops file.txt           # Change group only
```
Recursively change for folders:
```bash
sudo chown -R prakash:devops folder/
```

### **Change Group Only**
```bash
sudo chgrp devops file.txt
sudo chgrp -R devops folder/
```



## 📂 Parent-Child Permissions
- **Directories** must have `x` permission to access files inside.
- **Child files** can have different permissions from parent directory.
- **SGID** can enforce all new files inherit the group of parent folder.


## ⭐ Special Permissions

### **SetUID (s on user execute bit)**
Runs file as file **owner** instead of executor.
```bash
chmod u+s filename
```
Example: `/usr/bin/passwd` lets normal users change password.

### **SetGID (s on group execute bit)**
- **On files**: Run file as file's group.
- **On directories**: New files inherit parent directory group.
```bash
chmod g+s directory/
```

### **Sticky Bit (t on others execute bit)**
Restricts delete permission to file owner/root only.
```bash
chmod +t /shared
```
Example: `/tmp` directory uses sticky bit.



## 🧮 Default Permissions with `umask`
`umask` sets **default permissions** for new files & directories.
```bash
umask            # View current mask
umask 027        # Set new umask (Files: 640, Dirs: 750)
```
Formula:
```
Default File Permission = 666 - umask
Default Dir Permission  = 777 - umask
```



## 🏢 Real-World: Shared Folder Setup

### **Goal:** Team collaboration directory where all files share same group.
```bash
sudo mkdir /shared
sudo groupadd devops
sudo chgrp devops /shared
sudo chmod 2775 /shared     # 2=SGID
sudo chmod +t /shared       # Sticky bit (optional)
```
Now:
- Any file inside `/shared` will have group `devops`.
- Users cannot delete each other’s files (because of sticky bit).

---

## 📝 Summary Table (Quick Reference)
| Numeric | Symbolic | Meaning                 |
|--------|----------|----------------------|
| 7      | rwx      | Full access          |
| 6      | rw-      | Read + Write        |
| 5      | r-x      | Read + Execute      |
| 4      | r--      | Read only           |
| 3      | -wx      | Write + Execute     |
| 2      | -w-      | Write only          |
| 1      | --x      | Execute only        |
| 0      | ---      | No access           |



Mastering file permissions is crucial for **security & collaboration**. Practice with `chmod`, `chown`, `chgrp`, `umask`, and special permissions to become confident.