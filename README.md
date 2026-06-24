Markdown

# 📦 CHX: The Chimo Linux Package Manager

**CHX** is a robust, portable packaging format for **Chimo Linux**. Each app installs into `~/.chimo-apps/`, creating an isolated environment with its own **Python virtual environment** (`venv`) and system-level dependencies.

---

## 📂 Project Structure

A professional CHX-compatible application must follow this structure:

```text
my-app/
├── src/
│   └── main.py            # Entry point
├── assets/                # Icons, sounds, images
├── manifest.json          # Metadata and dependency specs
└── requirements.txt       # Python PIP dependencies

🛠️ The manifest.json Standard

This file is mandatory for chx to manage your app's environment automatically.
JSON

{
  "name": "AppName",
  "version": "0.1.0",
  "entry_point": "src/main.py",
  "sys_dependencies": ["espeak-ng", "clamav"],
  "pip_dependencies": ["PyQt6", "pyclamd"]
}

🚀 Creating Your Own CHX App

    Setup your project:
    Organize your files following the structure above.

    Define dependencies:
    List your Python libraries in requirements.txt and system tools in manifest.json.

    Package it:

Bash

   chx pack my-app -o my-app.chx

    Install it:

Bash

   chx install my-app.chx

The manager will automatically create a venv, install PIP packages, and set up your system launcher.
📖 Usage Reference
Command	Description
chx install <pkg.chx>	Installs app, setups venv, and resolves dependencies.
chx remove <appname>	Removes the app and purges its isolated environment.
chx pack <folder>	Compresses your project into a .chx file.
chx register-global	Registers MIME types for double-click installations.
⚙️ Installing CHX Manager
Bash

git clone [https://github.com/chimoinc/chx.git](https://github.com/chimoinc/chx.git)
cd chx/manager
sudo cp chx /usr/local/bin/chx
sudo chmod +x /usr/local/bin/chx

Required System Dependencies:

    python3, python3-venv, python3-pip

    kdialog

    tar

✅ Best Practices

    Isolation: Always rely on requirements.txt and manifest.json so your app remains portable.

    Assets: Include an assets/icon.png so the manager can generate a desktop shortcut.

    Testing: Always test your app locally with: python3 src/main.py before packaging.

📖 Documentation

See the docs/ folder for:

    packaging.md → Advanced manifest configurations.

    usage.md → Detailed installation and troubleshooting guide.
