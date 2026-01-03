# 🚀 CARA MENJALANKAN SOFTWARE

## 🎯 PILIH SALAH SATU CARA (Paling Mudah):

---

## ✅ CARA 1: LANGSUNG DOUBLE-CLICK (TERCEPAT!)

### Untuk Python Version:

1. **Buka folder** `python-version`
2. **Double-click** file `run.bat`
3. **Selesai!** Browser otomatis buka ✅

**Apa yang terjadi:**
- Terminal window terbuka
- Python mulai load
- Browser Chrome buka otomatis
- Monitoring dimulai!
- Lihat video Anda playing... atau loading?

### Untuk Node.js Version:

1. **Buka folder** `nodejs-version`
2. **Double-click** file `run.bat`
3. **Selesai!** Browser otomatis buka ✅

---

## ✅ CARA 2: MENGGUNAKAN POWERSHELL/COMMAND PROMPT

### Setup Pertama Kali (Hanya 1x):

#### Untuk Python:
```powershell
# 1. Buka PowerShell
# 2. Ketik command ini:

cd "d:\downweb\website-auto-restart-monitor\python-version"
.\setup.bat

# Setup akan:
# ✅ Install Python packages (selenium, requests)
# ✅ Check Google Chrome
# ✅ Create logs folder
# ✅ Siap dijalankan!
```

#### Untuk Node.js:
```powershell
# 1. Buka PowerShell
# 2. Ketik command ini:

cd "d:\downweb\website-auto-restart-monitor\nodejs-version"
.\setup.bat

# Setup akan:
# ✅ Install npm packages (puppeteer, axios)
# ✅ Download Chromium
# ✅ Check Google Chrome
# ✅ Siap dijalankan!
```

### Jalankan Setelah Setup (Setiap Kali):

#### Python:
```powershell
cd "d:\downweb\website-auto-restart-monitor\python-version"
python app.py
```

#### Node.js:
```powershell
cd "d:\downweb\website-auto-restart-monitor\nodejs-version"
npm start
```

---

## 📝 SEBELUM MENJALANKAN - PENTING!

### 1. Edit config.json

**Buka file:** `config.json` dengan Notepad

**Lokasi file:**
```
python-version/config.json
atau
nodejs-version/config.json
```

**Apa yang perlu diganti:**

```json
{
  "websites": [
    {
      "name": "Public Website",
      "url": "http://localhost:5173",    // ← GANTI INI!
      //
      // Ganti dengan URL website Anda:
      // - http://localhost:3000
      // - http://192.168.1.100:8080
      // - https://example.com
      //
      "videoSelector": "video",
      "enabled": true,
      "timeout": 20
    }
  ],
  "headless": false,      // false = bisa lihat browser
  "windowWidth": 1920,
  "windowHeight": 1080
}
```

**CONTOH CONFIG YANG BENAR:**

```json
{
  "websites": [
    {
      "name": "My Video Site",
      "url": "http://localhost:3000",
      "videoSelector": "video",
      "enabled": true,
      "timeout": 20
    }
  ],
  "headless": false,
  "windowWidth": 1920,
  "windowHeight": 1080
}
```

### 2. Pastikan Requirements Terpenuhi

Sebelum run, check:

- ✅ **Google Chrome installed**
  - Download: https://www.google.com/chrome/
  - Sudah install? Cek di C:\Program Files\Google\Chrome\

- ✅ **Python 3.8+** (untuk Python version)
  - Cek dengan buka PowerShell: `python --version`
  - Output harus: `Python 3.8.0` atau lebih tinggi
  - Download: https://www.python.org/downloads/

- ✅ **Node.js 14+** (untuk Node.js version)
  - Cek dengan: `node --version`
  - Output harus: `v14.0.0` atau lebih tinggi
  - Download: https://nodejs.org/

---

## 🎬 LANGKAH-LANGKAH LENGKAP (PERTAMA KALI)

### Python Version - Step by Step:

#### Step 1: Install Dependencies
```powershell
cd "d:\downweb\website-auto-restart-monitor\python-version"
.\setup.bat

# Wait sampai selesai (2-3 menit)
# Anda akan lihat:
# [1/3] Installing Python dependencies...
# [2/3] Checking Google Chrome...
# [3/3] Build setup complete!
```

#### Step 2: Edit config.json
```powershell
# Buka dengan Notepad
notepad config.json

# Ganti "url": "http://localhost:5173" 
# Dengan URL website Anda
# Save (Ctrl+S) dan Close
```

#### Step 3: Jalankan Aplikasi
```powershell
python app.py

# Tunggu sampai terbuka... (10-15 detik)
# Browser Chrome akan buka otomatis
# Terminal akan show:
# ✅ Config loaded
# ✅ Browser initialized
# ✅ Page loaded
# 🚀 Memulai monitoring...
```

#### Step 4: Lihat Hasil
- ✅ Browser shows website Anda
- ✅ Video player visible
- ✅ Terminal show monitoring status
- ✅ Log file created di `logs/monitor_2026-01-02.log`

#### Step 5: Stop Monitoring
```
Press Ctrl+C di terminal
# Atau close terminal window
```

---

### Node.js Version - Step by Step:

#### Step 1: Install Dependencies
```powershell
cd "d:\downweb\website-auto-restart-monitor\nodejs-version"
.\setup.bat

# Wait sampai selesai (3-5 menit)
# Chromium akan di-download (large file!)
```

#### Step 2: Edit config.json
```powershell
notepad config.json
# Ganti URL website Anda
# Save (Ctrl+S)
```

#### Step 3: Jalankan Aplikasi
```powershell
npm start

# Atau:
node app.js
```

#### Step 4-5: Sama seperti Python version

---

## 🖥️ TAMPILAN SAAT RUNNING

### Terminal Output (Expected):

```
============================================================
🎬 WEBSITE AUTO RESTART MONITOR v1.0
============================================================
✅ Config loaded dari config.json
✅ WebDriver initialized untuk Public Website
✅ Page loaded: Public Website
🚀 Memulai monitoring Public Website...
📊 Public Website - Ready: 4, Network: 1, Paused: False
📊 Public Website - Ready: 4, Network: 1, Paused: False
📊 Public Website - Ready: 4, Network: 1, Paused: False

[Terus monitor setiap 5 detik...]
```

### Browser Window (Expected):

- ✅ Chrome window terbuka
- ✅ Website Anda loaded
- ✅ Video player visible
- ✅ Bisa lihat video playing atau loading

### Log File:

Otomatis dibuat di: `logs/monitor_2026-01-02.log`

---

## ✅ CHECKLIST SEBELUM JALANKAN

- [ ] Google Chrome sudah install (buka chrome.exe test)
- [ ] Python/Node.js sudah install (buka PowerShell, cek versi)
- [ ] config.json sudah di-edit dengan URL yang benar
- [ ] Folder `logs/` akan auto-create (tidak perlu buat manual)
- [ ] Internet connection aktif (untuk akses website)

---

## 🎯 TESTING: APAKAH BERJALAN DENGAN BENAR?

### Test 1: Setup Berhasil?

Lihat output setup:
```
✅ Installing Python dependencies...
✅ Checking Google Chrome...
✅ Build setup complete!
```

### Test 2: Config Benar?

Lihat output run:
```
✅ Config loaded dari config.json
✅ Page loaded: [Your Website Name]
```

### Test 3: Video Ditemukan?

Lihat output monitoring:
```
📊 Ready: 4, Network: 1, Paused: False
```

Artinya: Video ready, network idle, video paused/playing ✅

### Test 4: Monitoring Berjalan?

Log file dibuat:
```
logs/monitor_2026-01-02.log
```

Dengan content:
```
[10:30:45] ✅ Page loaded
[10:30:50] 📊 Video OK
[10:31:00] 📊 Video OK
```

---

## 🛑 ADA ERROR? BACA INI:

### ❌ "Chrome not found"
**Solusi:**
```
1. Download Google Chrome: https://www.google.com/chrome/
2. Install dengan default settings
3. Restart PowerShell
4. Run lagi
```

### ❌ "Python not found"
**Solusi:**
```
1. Download Python: https://www.python.org/downloads/
2. Install dengan CENTANG "Add Python to PATH"
3. Restart PowerShell
4. Cek: python --version
5. Run lagi
```

### ❌ "config.json not found"
**Solusi:**
```
1. Pastikan file config.json ada di folder
2. Jangan pindah/rename file
3. Edit dengan Notepad (jangan Word!)
```

### ❌ "Video element not found"
**Solusi:**
```
1. Buka website di browser manual
2. Tekan F12 (Developer Tools)
3. Cari <video> tag di HTML
4. Update "videoSelector" di config.json
```

### ❌ "Port already in use" atau Error lain
**Solusi:**
```
1. Baca file: logs/monitor_2026-01-02.log
2. Lihat error message di log
3. Baca ADVANCED.md untuk solusi
```

---

## 📂 FILE PENTING YANG PERLU ANDA KETAHUI

```
python-version/
├── run.bat           ← DOUBLE-CLICK INI (tercepat!)
├── setup.bat         ← Run ini pertama kali
├── app.py            ← Main application
├── config.json       ← EDIT INI DENGAN URL ANDA
├── requirements.txt  ← Dependencies list
└── logs/
    └── monitor_YYYY-MM-DD.log ← Check ini kalau error
```

---

## 🔄 SETELAH SETUP, SETIAP KALI INGIN JALANKAN:

### Cara Tercepat: Double-click
```
python-version/run.bat
atau
nodejs-version/run.bat
```

### Cara Manual: PowerShell
```powershell
# Python
cd python-version
python app.py

# Node.js
cd nodejs-version
npm start
```

### Cara Service: Startup Otomatis
1. Buat shortcut dari `run.bat`
2. Copy ke: `C:\Users\[YourName]\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
3. Setiap Windows start → App otomatis jalan

---

## ⏹️ CARA BERHENTI

### Cara 1: Tekan Ctrl+C
```
Di terminal window, tekan Ctrl+C
```

### Cara 2: Close Terminal
```
Klik X untuk close terminal window
```

### Cara 3: Task Manager
```
Ctrl+Shift+Esc → Find python.exe atau node.exe → End Task
```

---

## 📊 MONITORING BERJALAN - LIHAT APA?

### Browser Window:
- Menunjukkan website Anda
- Video player terlihat
- Bisa lihat status loading

### Terminal Window:
- Setiap 5 detik: `📊 Video status`
- Kalau video stuck: `❌ Video stuck selama XX seconds`
- Reload page: `🔄 Reload page...`

### Log File:
```
logs/monitor_2026-01-02.log

Isi:
[timestamp] ✅ Success
[timestamp] ⚠️ Warning
[timestamp] ❌ Error
[timestamp] 📊 Status update
```

---

## 🎓 CONTOH SEBENARNYA

### Skenario 1: Video Playing dengan Baik
```
[10:30:45] ✅ Page loaded: My Site
[10:30:50] 📊 Ready: 4, Network: 1, Video OK ✅
[10:31:00] 📊 Ready: 4, Network: 1, Video OK ✅
[10:31:10] 📊 Ready: 4, Network: 1, Video OK ✅
[Terus monitoring... semua OK]
```

### Skenario 2: Video Stuck (20+ detik loading)
```
[10:31:00] ⚠️ Video mulai loading...
[10:31:10] ⚠️ Video masih loading...
[10:31:20] ⚠️ Video masih loading...
[10:31:30] ❌ VIDEO STUCK DETECTED! (20.5s)
[10:31:31] 🔄 Reload page My Site...
[10:31:32] ✅ Page reloaded
[10:31:33] 📺 Fullscreen video
[10:31:40] 📊 Video OK ✅
[Monitoring resume...]
```

---

## 🎯 CHECKLIST SUKSES

Setelah menjalankan, pastikan:

- ✅ Terminal show: `✅ Config loaded`
- ✅ Browser terbuka dengan website Anda
- ✅ Terminal show: `✅ Page loaded`
- ✅ Terminal show: `📊 Video status` setiap 5 detik
- ✅ Log file dibuat di `logs/`
- ✅ Tidak ada error merah di terminal

Jika semua ✅ → **BERHASIL!** 🎉

---

## 📞 MASIH BINGUNG?

Baca file ini dalam urutan:

1. **START_HERE.md** ← Mulai dari sini
2. **INSTALLATION.md** ← Detail setup
3. **EXAMPLES.md** ← Config examples
4. **logs/monitor_*.log** ← Lihat error message

---

## 🚀 NEXT: BUILD EXE (Optional)

Setelah berhasil jalankan, bisa build jadi EXE:

### Python:
```powershell
cd python-version
python build_exe.py
# Output: dist/WebsiteAutoRestart.exe
```

### Node.js:
```powershell
cd nodejs-version
npm run build-exe
# Output: WebsiteAutoRestart.exe
```

EXE bisa di-share ke orang lain tanpa install Python/Node.js!

---

**Sekarang sudah paham cara menjalankannya!** 🎉

Mulai sekarang:
1. Edit `config.json`
2. Double-click `run.bat`
3. Lihat browser terbuka
4. Monitoring mulai! 🎬

Good luck! 🚀
