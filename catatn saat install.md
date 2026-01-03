# 📥 INSTALLATION GUIDE

## 🎯 Prerequisites

Required:

1. **Google Chrome** (Required)
   - Download: https://www.google.com/chrome/
   - Install dengan default settings

2. **Python 3.8+** (Untuk Python version)
   - Download: https://www.python.org/downloads/
   - ✅ Check "Add Python to PATH"
   - ✅ Check "Install pip"

   **Verify installation:**
   ```powershell
   python --version
   pip --version
   ```

3. **Node.js 14+** (Untuk Node.js version)
   - Download: https://nodejs.org/
   - Install LTS version (recommended)

   **Verify installation:**
   ```powershell
   node --version
   npm --version
   ```

---

## 🐍 Python Version - Step by Step

### 1️⃣ Navigate to Python Folder

```powershell
# Open PowerShell/Command Prompt
cd d:\downweb\video-downloader\website-auto-restart-monitor\python-version
```

### 2️⃣ Run Setup

```powershell
# Windows
.\setup.bat

# Linux/Mac
bash setup.sh
```

**What it does:**
- ✅ Install Python dependencies (selenium, requests)
- ✅ Check Google Chrome
- ✅ Create logs folder

### 3️⃣ Configure Website

Edit `config.json`:

```json
{
  "websites": [
    {
      "name": "Public Website",
      "url": "http://YOUR-WEBSITE:PORT",      // Change this!
      "videoSelector": "video",
      "enabled": true,
      "timeout": 20
    }
  ],
  "browserType": "chrome", (kalo ada selain chrome ganti)
  "headless": false,
  "windowWidth": 1920,      (kalo kebesaran ganti reso sesuai resolusi komputer kalian)
  "windowHeight": 1080
}
```

**Example:**
```json
"url": "http://localhost:5173"
// atau
"url": "http://192.168.1.100:3000"
// atau
"url": "https://streaming.example.com"
```

### 4️⃣ Test Run    (python)

```powershell
python app.py
```

**Expected output:**
```
============================================================
🎬 WEBSITE AUTO RESTART MONITOR v1.0
============================================================
✅ Config loaded dari config.json
✅ WebDriver initialized untuk Public Website
✅ Page loaded: Public Website
🚀 Memulai monitoring Public Website...
📊 Public Website - Ready: 4, Network: 1, Paused: False
```

**Press Ctrl+C to stop**

### 5️⃣ Build EXE (Optional)

```powershell
python build_exe.py
```

**Output:**
```
📦 Installing PyInstaller...
🔨 Building EXE dengan PyInstaller...
✅ Build sukses!
📁 EXE file: D:\...\python-version\dist\WebsiteAutoRestart.exe
```

---

## 🟢 Node.js Version - Step by Step

### 1️⃣ Navigate to Node.js Folder

```powershell
partisi windows kalianvideo-downloader\website-auto-restart-monitor\nodejs-version
```

### 2️⃣ Run Setup

```powershell
# Windows
.\setup.bat

# Linux/Mac
bash setup.sh
```

**What it does:**
- ✅ Install npm dependencies (puppeteer, axios)
- ✅ Download Chromium
- ✅ Check Google Chrome
- ✅ Create logs folder

### 3️⃣ Configure Website

Edit `config.json`:

```json
{
  "websites": [
    {
      "name": "Public Website",
      "url": "http://YOUR-WEBSITE:PORT",      // Change this!
      "videoSelector": "video",
      "enabled": true,
      "timeout": 20
    }
  ],
  "headless": false,
  "windowWidth": 1920,
  "windowHeight": 1080,
  "checkInterval": 5
}
```

### 4️⃣ Test Run

```powershell
npm start
```

**atau**

```powershell
node app.js
```

**Expected output:**
```
============================================================
🎬 WEBSITE AUTO RESTART MONITOR v1.0 (Node.js)
============================================================
✅ Config loaded dari config.json
✅ Browser initialized untuk Public Website
✅ Page loaded: Public Website
🚀 Memulai monitoring Public Website...
📊 Public Website - Ready: 4, Network: 1, Paused: False
```

**Press Ctrl+C to stop**

### 5️⃣ Build EXE (Optional)

```powershell
npm install -g pkg
npm run build-exe
```

**Output:**
```
✅ Build sukses!
📁 EXE file: D:\...\nodejs-version\WebsiteAutoRestart.exe
```

---

## 🔧 Common Setup Issues & Solutions

### ❌ "Python not found" atau "python: command not found"

**Solution:**
1. Uninstall Python
2. Re-download from https://www.python.org/downloads/
3. ✅ **CHECK BOTH:**
   - "Install Python 3.x.x for all users"
   - "Add Python 3.x.x to PATH"
4. Restart PowerShell
5. Verify: `python --version`

### ❌ "Chrome not found"

**Solution:**
1. Download Google Chrome: https://www.google.com/chrome/
2. Install dengan default settings
3. Verify installed: Check "C:\Program Files\Google\Chrome\Application\chrome.exe"

### ❌ "ModuleNotFoundError: No module named 'selenium'"

**Solution:**
```powershell
# Reinstall dependencies
pip install --upgrade pip
pip install -r requirements.txt
```

### ❌ "npm: command not found"

**Solution:**
1. Download Node.js: https://nodejs.org/
2. Install LTS version
3. Restart PowerShell
4. Verify: `npm --version`

### ❌ Folder permission denied

**Solution:**
```powershell
# Run PowerShell as Administrator
# Right-click PowerShell → "Run as administrator"
# Then run setup again
```

### ❌ EXE file won't start

**Solution:**
1. Check Windows Defender / Antivirus (mungkin quarantine)
2. Check `logs/monitor_YYYY-MM-DD.log` for error details
3. Verify config.json is in same directory as EXE
4. Check file permissions (need read access)

---

## ✅ Verification Checklist

After installation, verify:

- [ ] `config.json` exists dan valid JSON
- [ ] Website URL bisa di-akses manual
- [ ] Google Chrome installed
- [ ] app.py atau app.js bisa di-run without errors
- [ ] Browser window opens (jika headless: false)
- [ ] `logs/` folder auto-created
- [ ] Log file shows "Video monitoring started"

---

## 📍 Finding Your Website URL & Port

### Localhost (Local Development)

If running locally:
```
http://localhost:3000       // Common ports
http://localhost:5173       // Vite default
http://localhost:8000       // Django default
http://localhost:8080       // General purpose
```

### Private Network (Internal IP)

If on same network:
```
http://192.168.1.100:3000   // Replace with your IP
http://192.168.0.50:8080
```

**Find your IP:**
```powershell
ipconfig
# Look for "IPv4 Address" like 192.168.x.x
```

### Public Website

```
https://example.com
https://streaming.service.com/player
```

---

## 🎨 Finding Video CSS Selector

### Step 1: Open Browser DevTools

Press **F12** atau Right-click → **Inspect Element**

### Step 2: Find Video Element

Look for `<video>` tag in HTML:

```html
<!-- Simple -->
<video src="video.mp4" controls></video>

<!-- With class -->
<div class="player">
  <video class="video-player"></video>
</div>

<!-- Custom player -->
<div id="my-player">
  <div class="player-wrapper">
    <video data-player="main"></video>
  </div>
</div>
```

### Step 3: Get CSS Selector

Use these patterns:
- `video` - Tag selector
- `.player video` - Class selector (nested)
- `#main-video` - ID selector
- `video.video-player` - Tag + class
- `[data-player='main']` - Attribute selector

### Step 4: Update config.json

```json
{
  "videoSelector": "video"  // Change this
}
```

---

## 🚀 Running at Startup

### Option 1: Startup Folder (Easiest)

1. Create shortcut dari EXE
2. Copy to startup folder:
   ```
   C:\Users\[YourUsername]\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
   ```
3. App runs automatically saat login

### Option 2: Task Scheduler

1. Press Windows + R
2. Type: `taskschd.msc`
3. **Create Basic Task:**
   - Name: "Website Auto Restart"
   - Trigger: "At log on" atau "At startup"
   - Action: Start program → path/to/EXE
   - ✅ Check "Run with highest privileges"

### Option 3: Windows Service (Advanced)

```powershell
# Install NSSM (Windows service manager)
choco install nssm

# Create service
nssm install WebsiteAutoRestart "C:\path\to\WebsiteAutoRestart.exe"

# Start service
nssm start WebsiteAutoRestart

# Check status
nssm status WebsiteAutoRestart
```

---

## 📊 Monitoring the Application

### Check Logs

```powershell
# Python version
type python-version\logs\monitor_2026-01-02.log

# Node.js version
type nodejs-version\logs\monitor_2026-01-02.log
```

### What to Look For

```
✅ ✅ Page loaded: OK
📊 Video tracking: OK
⚠️ Video loading > 20s: Stuck detected
🔄 Reload page: Action taken
🔴 Server unreachable: Critical error
```

### Monitor Running Process

**Python:**
```powershell
# Check if python process running
Get-Process python

# Kill if needed
Stop-Process -Name python
```

**Node.js:**
```powershell
# Check if node process running
Get-Process node

# Kill if needed
Stop-Process -Name node
```

---

## 🎓 Next Steps

1. ✅ **Installation Complete** - Aplikasi sudah ready
2. 📝 **Configure** - Update config.json dengan website Anda
3. 🧪 **Test** - Run dan monitor logs
4. 📦 **Build EXE** - Create standalone executable
5. 🚀 **Deploy** - Set to run at startup

---

## 📞 Troubleshooting Support

**Check these files for help:**
- `README.md` - Full documentation
- `EXAMPLES.md` - Config examples
- `ADVANCED.md` - Custom features
- `logs/monitor_YYYY-MM-DD.log` - Error details

**General debugging:**
1. Check Windows Defender/Antivirus (blocks?)
2. Try running as Administrator
3. Verify Chrome is installed correctly
4. Check config.json JSON format
5. Check website URL is accessible
6. Look at log files for detailed errors

---

Ready to run! Start with step 1 above. 🎉
