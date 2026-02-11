---

# 📦 CHX Repo

## 🚀 What is CHX?
CHX is a packaging format for **Chimo Linux** that makes distributing applications simple, portable, and user-friendly.  
Each app installs into the user’s HOME directory (`~/.chimo-apps/`) with its own Python virtual environment and a desktop shortcut in the system menu.

---

## 📂 Repository Structure

```
chx/
├── README.md              # Documentation for developers and users
├── manager/               # The CHX Manager script
│   └── chx
├── apps/                  # Example CHX apps
│   ├── hello-world.chx
│   └── browser.chx
├── docs/                  # Guides and tutorials
│   ├── packaging.md
│   └── usage.md
└── LICENSE
```

---

## 🛠️ Installing CHX Manager

Clone the repository and copy the manager script:

```bash
git clone https://github.com/chimoinc/chx.git
cd chx/manager
sudo cp chx /usr/local/bin/chx
sudo chmod +x /usr/local/bin/chx
```

Dependencies required:
- `python3`
- `python3-venv`
- `python3-pip`
- `kdialog`
- `tar`

---

## 📖 Usage

```
chx install <package.chx>      # Install an app
chx remove <appname>           # Remove an app
chx register-global            # Register MIME and global installer
chx pack <app-folder> -o file  # Package a folder into .chx
```

---

## 📥 Example Apps

### Hello World
```bash
chx install apps/hello-world.chx
```

### Browser
```bash
chx install apps/browser.chx
```

Both apps will appear in your system menu after installation.

---

## 📦 Creating Your Own CHX App

1. Create a folder with this structure:
   ```
   my-app/
   ├── src/main.py
   ├── assets/icon.png
   └── requirements.txt
   ```
2. Package it:
   ```bash
   chx pack my-app -o my-app.chx
   ```
3. Install it:
   ```bash
   chx install my-app.chx
   ```

---

## 🌍 Global Registration

To enable double-click installation of `.chx` files:

```bash
sudo chx register-global
```

This registers the MIME type and adds a global installer entry.

---

## ✅ Best Practices

- Use unique names for your app folder.  
- Always include an icon in `assets/icon.png`.  
- Keep `requirements.txt` updated.  
- Test your app before packaging:  
  ```bash
  python3 src/main.py
  ```

---

## 📖 Documentation

See the `docs/` folder for:
- `packaging.md` → How to package apps.  
- `usage.md` → Detailed usage guide.  

---
