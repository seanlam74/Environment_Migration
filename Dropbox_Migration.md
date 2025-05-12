# 📁 Linking a Folder from D: Drive to Dropbox without Moving It

If your Dropbox folder is located on `C:` (e.g., `C:\Users\rog\NUS Dropbox`) and your large folder is on another drive (e.g., `D:\1_Teaching_Work_Folder`), you can link the D: folder to Dropbox using a **symbolic link (symlink)** without duplicating or moving the data.

---

## ✅ Goal

Sync contents of:

```
D:\1_Teaching_Work_Folder
```

into:

```
C:\Users\rog\NUS Dropbox\Teaching_Work
```

without copying the data to the C: drive.

---

## 🛠️ Step-by-Step Instructions

### 1. Open Command Prompt as Administrator

- Press `Start`
- Search for **cmd**
- Right-click and choose **Run as administrator**

---

### 2. Create the Symbolic Link

Run this command:

```cmd
mklink /D "C:\Users\rog\NUS Dropbox\Teaching_Work" "D:\1_Teaching_Work_Folder"
```

- `/D` indicates it is a directory symlink
- Replace folder names if needed

---

### ✅ What Happens

- A new folder called `Teaching_Work` will appear inside your Dropbox folder
- Dropbox will **sync the files as if they were local to Dropbox**
- Actual files remain on `D:` — saving space on `C:`

---

## ⚠️ Notes

- Changes in the original `D:` folder will reflect in Dropbox automatically
- Avoid modifying files while Dropbox is syncing them
- Works on **Windows 10/11**

---

## 🧪 To Check if the Link Worked

You can verify it in Command Prompt:

```cmd
dir "C:\Users\rog\NUS Dropbox"
```

It should show:
```
<SYMLINKD>     Teaching_Work [D:\1_Teaching_Work_Folder]
```

---

## ✅ Summary

| Action | Benefit |
|--------|---------|
| Use symlink | Avoids file duplication |
| Dropbox syncs as normal | Saves space on `C:` |
| Easy to reverse | Just delete the link in Dropbox folder |

---
