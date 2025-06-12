# 📱 Convert Python App to APK with Buildozer (Full Setup Guide)

This repository contains a Kivy/KivyMD-based Python app and complete steps to convert it into an Android APK using Buildozer.

---

## 🧰 Prerequisites

Make sure you have the following installed:

- Python 3.10+ (avoid 3.12+ for Kivy compatibility)
- pip
- git
- Virtualenv
- Ubuntu/Linux system or WSL2 (Windows Subsystem for Linux) **(Recommended)**

---

## 🐍 Step 1: Set Up Virtual Environment

```bash
sudo apt update
sudo apt install python3-venv python3-pip git unzip zip openjdk-17-jdk -y

# Create project folder
mkdir MyApp && cd MyApp

# Create virtual environment
python3 -m venv .venv

# Activate the environment
source .venv/bin/activate
```
##📦 Step 2: Install Required Python Modules
```bash

pip install --upgrade pip setuptools wheel Cython virtualenv

# Install buildozer
pip install buildozer

# Install Kivy (choose one)
pip install kivy           # For basic Kivy apps
pip install kivymd         # If using KivyMD
```
🏗️ Step 3: Initialize Buildozer
bash
Copy
Edit
buildozer init
This creates a buildozer.spec file.

✏️ Step 4: Configure buildozer.spec
Open buildozer.spec and configure these settings:

ini
Copy
Edit
[app]
title = MyApp
package.name = myapp
package.domain = org.myname
source.include_exts = py,png,jpg,kv,json,ttf,txt,md
requirements = python3,kivy,kivymd,requests
android.permissions = INTERNET, CAMERA
fullscreen = 1
orientation = portrait
✅ Add any other required permissions like READ_EXTERNAL_STORAGE, WRITE_EXTERNAL_STORAGE, etc.

📁 Recommended Project Structure
graphql
Copy
Edit
MyApp/
├── main.py
├── main.kv                  # If using Kivy language
├── buildozer.spec
├── assets/                  # Custom fonts, sounds, etc.
├── images/
├── data/
└── README.md
🚧 Step 5: Build the APK
⚠️ Make sure you are still inside the virtual environment and in Linux/WSL2.

```bash

# To build the debug APK
buildozer -v android debug

# To automatically install on connected device
buildozer android deploy run
```
The APK will be created in the bin/ folder:

```bash

bin/myapp-debug.apk
```
🔄 Step 6: Update or Rebuild

If you make changes to main.py or any other file, simply rebuild with:

```bash

buildozer android debug
```
