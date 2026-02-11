# CHX
CHX Repository and Things of Chimo Cinder and Chimo Versions above

---

# 📦 CHX Apps – Developer Guide

## 🚀 What is CHX?
CHX is a packaging format for **Chimo Linux** that makes distributing applications simple, portable, and user-friendly.  
Each app installs into the user’s HOME directory (`~/.chimo-apps/`) with its own Python virtual environment and a desktop shortcut in the system menu.

---

## 📂 App Structure

A CHX app should follow this layout:

```
my-app/
├── src/
│   └── main.py
├── assets/
│   └── icon.png
├── requirements.txt
```

- **src/main.py** → main application code.  
- **assets/icon.png** → application icon for the menu.  
- **requirements.txt** → Python dependencies (e.g., `PyQt6`, `PyQt6-WebEngine`).  

---

## 📝 Example `main.py`

```python
import sys
from PyQt6.QtWidgets import QApplication, QLabel

app = QApplication(sys.argv)
window = QLabel("Hello from CHX!")
window.resize(400, 200)
window.show()
sys.exit(app.exec())
```

---

## 📦 Packaging

From the app’s root directory:

```bash
chx pack my-app -o my-app.chx
```

This generates `my-app.chx`, ready for installation.

---

## 📥 Installation

```bash
chx install my-app.chx
```

The CHX Manager will:
- Extract the package into `~/.chimo-apps/my-app/`.  
- Automatically fix duplicate folder structures if present.  
- Create a Python virtual environment.  
- Install dependencies from `requirements.txt`.  
- Generate a `.desktop` shortcut in the system menu.  

---

## 🗑️ Removal

```bash
chx remove my-app
```

This deletes the app folder and its desktop shortcut.

---

## 🌍 Global Registration (Optional)

To allow any user on the system to open `.chx` files with a double click:

```bash
sudo chx register-global
```

This will:
- Register the MIME type `application/x-chimo`.  
- Install a global `.desktop` entry for the CHX Installer.  

---

## ✅ Best Practices

- Use simple, unique names for the root folder (`my-app`).  
- Always include an icon in `assets/icon.png`.  
- Keep `requirements.txt` updated.  
- Test your app before packaging:  
  ```bash
  python3 src/main.py
  ```

---

## 📖 Example Workflow

1. Create your app folder with `src/`, `assets/`, and `requirements.txt`.  
2. Write your app code in `src/main.py`.  
3. Package it:  
   ```bash
   chx pack my-app -o my-app.chx
   ```  
4. Install it locally:  
   ```bash
   chx install my-app.chx
   ```  
5. Launch it from the KDE/GNOME menu.  

---

This README gives developers a clear path to build and distribute CHX apps.  
