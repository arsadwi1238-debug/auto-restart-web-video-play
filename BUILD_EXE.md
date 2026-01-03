# Build EXE Instructions

## 🐍 Python Version → EXE

### Prerequisites
- Python 3.8 atau lebih tinggi
- Google Chrome installed

### Step 1: Install PyInstaller

```powershell
cd python-version
pip install pyinstaller
```

### Step 2: Update config.json

Pastikan `config.json` sudah sesuai dengan website yang mau di-monitor.

### Step 3: Build

**Opsi A - Automatic (Recommended)**

```powershell
python build_exe.py
```

**Opsi B - Manual**

```powershell
pyinstaller --name=WebsiteAutoRestart ^
  --onefile ^
  --windowed ^
  --add-data "config.json:." ^
  --hidden-import=selenium ^
  --hidden-import=requests ^
  app.py
```

### Step 4: Output

- **File**: `dist/WebsiteAutoRestart.exe`
- **Size**: ~50-100 MB (includes Python + dependencies)
- **Copy**: `config.json` ke folder yang sama dengan EXE

### Step 5: Run

```powershell
# Double-click EXE
# atau
.\WebsiteAutoRestart.exe

# Logs akan tersimpan di: logs/monitor_YYYY-MM-DD.log
```

---

## 🟢 Node.js Version → EXE

### Prerequisites
- Node.js 14+ dan npm
- Google Chrome installed

### Step 1: Install Dependencies

```powershell
cd nodejs-version
npm install
```

### Step 2: Install pkg

```powershell
npm install -g pkg
```

### Step 3: Update config.json

Pastikan `config.json` sudah sesuai.

### Step 4: Build

```powershell
npm run build-exe
```

**atau manual:**

```powershell
pkg . --targets win-x64 --output WebsiteAutoRestart.exe
```

### Step 5: Output

- **File**: `WebsiteAutoRestart.exe`
- **Size**: ~50-80 MB (includes Node.js + Puppeteer)
- **Copy**: `config.json` ke folder yang sama dengan EXE

### Step 6: Run

```powershell
.\WebsiteAutoRestart.exe
```

---

## 📦 Advanced Build Options

### Python - Custom Icon

1. Siapkan file `app.ico` (recommended size: 256x256)
2. Copy ke `python-version/` folder
3. Build dengan icon:

```powershell
pyinstaller --name=WebsiteAutoRestart ^
  --onefile ^
  --icon=app.ico ^
  --add-data "config.json:." ^
  --hidden-import=selenium ^
  --hidden-import=requests ^
  app.py
```

### Node.js - With Resource Files

```powershell
pkg . --targets win-x64 ^
  --output WebsiteAutoRestart.exe ^
  --compress "GZip"
```

---

## 🚨 Troubleshooting Build

### Python: "ModuleNotFoundError"

```powershell
# Add missing modules with --hidden-import
pyinstaller --hidden-import=module_name ...
```

### Node.js: EXE not detecting config.json

```powershell
# Ensure config.json in same directory as EXE
copy config.json dist/
```

### Build Too Large

Python - Use UPX compression:
```powershell
pip install pyinstaller-hooks-contrib
pyinstaller --upx-dir="C:\upx" ...
```

---

## 🔐 Distributing EXE

### What to Include

```
WebsiteAutoRestart/
├── WebsiteAutoRestart.exe    (Main executable)
├── config.json               (Configuration file)
├── README.txt                (Quick instructions)
└── logs/                     (Auto-created for logs)
```

### Create Distribution Package

**Python:**
```powershell
cd dist
copy ..\config.json .
copy ..\README.md README.txt
# Zip it: WebsiteAutoRestart_v1.0.zip
```

**Node.js:**
```powershell
copy config.json .
copy README.md README.txt
# Zip it: WebsiteAutoRestart_v1.0.zip
```

---

## 🎯 Running as Windows Startup

### Method 1: Startup Folder

1. Create shortcut dari EXE
2. Copy ke: `C:\Users\[YourUsername]\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
3. App akan auto-run saat login

### Method 2: Task Scheduler

1. Open **Task Scheduler**
2. Create Basic Task
3. Set trigger: "At log on" atau "At startup"
4. Set action: Start program → Path ke EXE
5. Check "Run with highest privileges"

### Method 3: Windows Service (NSSM)

```powershell
# Install NSSM
choco install nssm

# Create service
nssm install WebsiteAutoRestart "C:\path\to\WebsiteAutoRestart.exe"

# Start service
nssm start WebsiteAutoRestart

# Check status
nssm status WebsiteAutoRestart
```

---

## 📝 Version Update

Untuk update ke versi baru:
1. Update `app.py` atau `app.js`
2. Rebuild EXE dengan langkah yang sama
3. Replace old EXE dengan yang baru
4. Keep `config.json` tetap sama (jika format tidak berubah)

---

## ✅ Verification Checklist

- [ ] EXE file exists di `dist/` atau root folder
- [ ] Config.json file ada di same directory as EXE
- [ ] Chrome/Chromium installed pada system
- [ ] EXE bisa di-run double-click tanpa error
- [ ] Logs folder auto-created
- [ ] Monitor logs menunjukkan activity yang benar

---

Siap! EXE Anda sudah bisa didistribusi! 🎉
