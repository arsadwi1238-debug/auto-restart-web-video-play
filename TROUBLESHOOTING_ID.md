# 🔧 TROUBLESHOOTING - SOLUTION UNTUK MASALAH

## 🎯 PANDUAN INI UNTUK:
- ❌ Ketika ada error
- ❌ Aplikasi tidak jalan
- ❌ Browser tidak buka
- ❌ Video tidak terdeteksi

---

## 🔴 ERROR: "Chrome not found" atau "Chrome not installed"

### Penyebab:
Google Chrome tidak terinstall atau tidak ada di PATH

### Solusi (3 langkah):

#### Langkah 1: Download Chrome
```
1. Buka browser apa saja
2. Ketik: google.com/chrome
3. Klik Download
4. Install seperti biasa
5. Tunggu selesai
```

#### Langkah 2: Verify Chrome Installed
```powershell
# Buka PowerShell
# Ketik:

where chrome

# Jika output:
# C:\Program Files\Google\Chrome\Application\chrome.exe
# → Berarti Chrome sudah terinstall! ✅

# Jika "tidak ditemukan" → Install manual
```

#### Langkah 3: Jalankan Lagi
```powershell
# Restart PowerShell
# Run lagi:

python app.py
# atau
npm start
```

**Selesai!** ✅

---

## 🔴 ERROR: "Python not found" atau "python: command not found"

### Penyebab:
Python tidak terinstall atau tidak ada di PATH

### Solusi (4 langkah):

#### Langkah 1: Check Python Version
```powershell
# Buka PowerShell baru
# Ketik:

python --version

# Jika output: Python 3.8.0+ → Python OK ✅
# Jika "command not found" → Install
```

#### Langkah 2: Download Python
```
1. Buka: python.org/downloads
2. Download latest (3.11+)
3. Run installer
```

#### Langkah 3: PENTING! Check 2 Box Ini:
```
☑ Install Python 3.11.0 for all users
☑ Add Python 3.11.0 to PATH  ← JANGAN LUPA!
```

#### Langkah 4: Verify & Jalankan Lagi
```powershell
# Tutup PowerShell lama, buka yang baru
# Ketik:

python --version

# Output harus: Python 3.8.0 atau lebih tinggi ✅

# Sekarang jalankan:
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "Node not found" atau "npm not found"

### Penyebab:
Node.js tidak terinstall atau tidak ada di PATH

### Solusi (3 langkah):

#### Langkah 1: Download Node.js
```
1. Buka: nodejs.org
2. Download LTS version (recommended)
3. Run installer
4. Next, Next, Install
5. Selesai
```

#### Langkah 2: Verify Node Installed
```powershell
# Tutup PowerShell lama, buka yang baru
# Ketik:

node --version
npm --version

# Output:
# v18.0.0+ (untuk node)
# 9.0.0+ (untuk npm)
```

#### Langkah 3: Jalankan Lagi
```powershell
npm start
```

**Selesai!** ✅

---

## 🔴 ERROR: "ModuleNotFoundError: No module named 'selenium'"

### Penyebab:
Python packages belum di-install

### Solusi (2 langkah):

#### Langkah 1: Install Dependencies
```powershell
cd python-version

# Run setup:
.\setup.bat

# Atau manual install:
pip install -r requirements.txt
```

#### Langkah 2: Jalankan Lagi
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "config.json not found"

### Penyebab:
File config.json hilang atau typo nama file

### Solusi (3 langkah):

#### Langkah 1: Check File Ada
```powershell
# Di folder python-version atau nodejs-version
# Harus ada file: config.json

# Cek:
ls *.json

# Lihat apakah ada "config.json"
```

#### Langkah 2: File Hilang? Download Ulang
Dari file yang sudah saya buat, ada template `config.json`

#### Langkah 3: Jalankan Lagi
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "JSON Decode Error" atau "config.json format invalid"

### Penyebab:
config.json punya syntax error

### Solusi (2 langkah):

#### Langkah 1: Check Format JSON
```json
// HARUS VALID:
{
  "websites": [
    {
      "name": "My Site",
      "url": "http://localhost:3000",
      "videoSelector": "video",
      "enabled": true,
      "timeout": 20
    }
  ],
  "headless": false
}
```

**Common Mistakes:**
```javascript
// ❌ SALAH: Comma di akhir
"timeout": 20,    // ← Jangan ada koma kalau elemen terakhir!

// ❌ SALAH: Single quote
'url': 'http://...'   // Harus double quote

// ❌ SALAH: Trailing comma
{
  "name": "Site",
  "url": "...",     // ← Ada koma tapi tidak ada elemen setelah
}
```

#### Langkah 2: Perbaiki & Jalankan
```powershell
# Buka config.json dengan Notepad
notepad config.json

# Perbaiki syntax
# Save (Ctrl+S)

# Jalankan:
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "Website unreachable" atau "Connection timeout"

### Penyebab:
URL tidak benar atau website tidak bisa diakses

### Solusi (4 langkah):

#### Langkah 1: Test Manual
```powershell
# Buka website manual di browser
# Ketik di address bar: http://localhost:3000

# Bisa diakses? → URL benar ✅
# Tidak bisa? → Masalah website/server
```

#### Langkah 2: Check URL di config.json
```json
{
  "url": "http://localhost:3000"  // Cek format ini
}
```

**Format harus:**
- `http://localhost:3000` (dengan http://)
- `http://192.168.1.100:8080` (dengan port)
- Tidak boleh typo!

#### Langkah 3: Check Website Running
```powershell
# Jika website local (localhost):
# Pastikan server sudah running

# Misalnya pakai Node.js:
npm start     # Di folder project Anda yang lain
```

#### Langkah 4: Jalankan Lagi
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "Video element not found"

### Penyebab:
CSS selector di config.json tidak sesuai

### Solusi (4 langkah):

#### Langkah 1: Buka Website Manual
```
1. Buka website di Chrome (bukan aplikasi auto-restart)
2. Lihat video playing atau ada video player?
3. Video element ada? → lanjut
```

#### Langkah 2: Inspect Video Element
```
1. Klik kanan pada video
2. Pilih "Inspect" atau "Inspect Element"
3. Developer Tools akan membuka di bawah
4. Cari tag <video> di HTML
```

#### Langkah 3: Find CSS Selector
```html
<!-- Cek struktur HTML -->

<!-- Contoh 1: Simple -->
<video src="video.mp4"></video>
Selector: "video"

<!-- Contoh 2: Dengan class -->
<div class="player">
  <video></video>
</div>
Selector: ".player video"

<!-- Contoh 3: Dengan ID -->
<video id="main-video"></video>
Selector: "#main-video"
```

#### Langkah 4: Update config.json
```json
{
  "videoSelector": "video"     // Atau selector Anda
}
```

Contoh lain:
```json
"videoSelector": ".player video"
"videoSelector": "#main-video"
"videoSelector": "div.player-wrapper > video"
```

Save dan jalankan:
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "Permission denied" atau "Access denied"

### Penyebab:
Folder/file tidak punya permission untuk baca/tulis

### Solusi (2 langkah):

#### Langkah 1: Run as Administrator
```powershell
# Buka PowerShell sebagai Administrator
# Right-click PowerShell → "Run as Administrator"

cd python-version
python app.py
```

#### Langkah 2: Check Folder Permission
```powershell
# Check apakah bisa tulis ke folder:
# Folder harus bisa create/write logs/

# Jika masih error:
# Pindah ke folder user (C:\Users\[YourName]\)
# Bukan C:\ langsung
```

**Selesai!** ✅

---

## 🔴 ERROR: "Browser crashed" atau "WebDriver exception"

### Penyebab:
Browser Chrome crash atau selenium error

### Solusi (3 langkah):

#### Langkah 1: Check Chrome Version
```powershell
# Buka Chrome
# Click 3 dots → Settings → About Chrome
# Check versi Chrome Anda

# Harus versi: 90+ (modern Chrome)
```

#### Langkah 2: Kill Chrome Process
```powershell
# Tutup semua Chrome window
# Buka PowerShell:

taskkill /IM chrome.exe /F

# Tunggu 5 detik
# Jalankan ulang:
python app.py
```

#### Langkah 3: Clear Cache
```powershell
# Delete Chrome cache folder:
# C:\Users\[YourName]\AppData\Local\Google\Chrome\User Data\Default\Cache

# Atau jalankan Chrome dengan fresh profile:
# Aplikasi akan otomatis create fresh profile
```

**Selesai!** ✅

---

## 🔴 ERROR: "Port already in use" atau "Address already in use"

### Penyebab:
Aplikasi lain sudah pakai port yang sama

### Solusi (2 langkah):

#### Langkah 1: Kill Process yang Pakai Port
```powershell
# Cari process yang pakai port (contoh: 3000)
netstat -ano | findstr :3000

# Output contoh:
# TCP  0.0.0.0:3000  LISTENING  12345

# Kill process tersebut (PID 12345):
taskkill /PID 12345 /F
```

#### Langkah 2: Jalankan Lagi
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "EXE tidak buka" atau "EXE langsung close"

### Penyebab:
Ketika build EXE, ada error di config atau dependencies

### Solusi (4 langkah):

#### Langkah 1: Check config.json
```
1. Pastikan config.json ada di folder yang sama dengan EXE
2. Format JSON harus valid
3. URL harus benar
```

#### Langkah 2: Check Chrome Installed
```
EXE memerlukan Chrome terinstall di system
Pastikan Chrome ada!
```

#### Langkah 3: Jalankan dari Command Prompt
```powershell
# Jangan double-click EXE
# Buka PowerShell, navigate ke folder EXE:

cd path/to/exe/folder
.\WebsiteAutoRestart.exe

# Lihat error message di terminal
# Copy error message ke file: error.txt
```

#### Langkah 4: Check Log File
```
Lihat: logs/monitor_YYYY-MM-DD.log
Error message ada di sini
```

**Selesai!** ✅

---

## 🔴 ERROR: "Video stuck tidak terdeteksi" (Selalu reload)

### Penyebab:
Timeout terlalu pendek atau video selector salah

### Solusi (2 langkah):

#### Langkah 1: Increase Timeout
```json
{
  "timeout": 20    // Coba naikkan jadi:
}

// Coba value lain:
"timeout": 15    // Lebih pendek (aggressive)
"timeout": 25    // Lebih lama (relaxed)
"timeout": 30    // Sangat lama (untuk slow network)
```

#### Langkah 2: Check Video Selector
```
Pastikan videoSelector benar!
Buka browser, inspect video element
Cek apakah selector match dengan <video> tag
```

Save dan test lagi:
```powershell
python app.py
```

**Selesai!** ✅

---

## 🔴 ERROR: "Multiple websites running, tapi salah satu crash"

### Penyebab:
Ada masalah dengan salah satu website

### Solusi (2 langkah):

#### Langkah 1: Disable Website yang Error
```json
{
  "websites": [
    {
      "name": "Working Site",
      "url": "http://localhost:3000",
      "enabled": true    // Ini OK
    },
    {
      "name": "Broken Site",
      "url": "http://localhost:5000",
      "enabled": false   // Disable ini sementara
    }
  ]
}
```

#### Langkah 2: Debug Website yang Error
```powershell
# Test website yang error:
# Buka manual di browser
# Check config.json URL
# Check video selector
# Perbaiki
# Enable kembali
```

**Selesai!** ✅

---

## 📊 CARA CHECK ERROR MESSAGE

### Check 1: Terminal Output
```
Lihat apa yang ditampilkan di PowerShell window
Ada error merah? → Tulis di sini
```

### Check 2: Log File
```
Lokasi: logs/monitor_2026-01-02.log
Buka dengan Notepad
Cari kata "ERROR" atau "❌"
```

### Check 3: Browser DevTools
```
F12 di browser (saat website terbuka)
Check Console tab
Ada error JavaScript? → Lihat di sini
```

---

## 📞 TIPS DEBUGGING

### Cara 1: Verbose Logging
Edit `app.py` atau `app.js`:
```python
# Change log level:
logging.basicConfig(level=logging.DEBUG)  # Lebih detail
```

### Cara 2: Headless False
```json
{
  "headless": false  // Lihat apa yang terjadi di browser
}
```

### Cara 3: Longer Timeout
```json
{
  "timeout": 30  // Beri lebih lama untuk debug
}
```

### Cara 4: Single Website
```json
{
  "websites": [
    {
      "name": "Test Site",
      "url": "http://localhost:3000"
    }
  ]
}
// Disable website lainnya
```

---

## ✅ SUDAH DICOBA?

Jika semua langkah di atas sudah dicoba tapi masih error:

1. **Baca file log** → `logs/monitor_YYYY-MM-DD.log`
2. **Copy error message** lengkap
3. **Baca file** → `ADVANCED.md` (untuk custom solution)
4. **Check online** → Google error message Anda

---

## 🎓 CONTOH DEBUGGING

### Problem: Video tidak terdeteksi
```
Terminal show: ⚠️ Video element not found

Solusi:
1. Buka website manual di browser
2. F12 → Inspect video
3. Check HTML struktur
4. Update videoSelector
5. Test lagi
```

### Problem: Browser tidak mau fullscreen
```
Terminal show: ⚠️ Gagal fullscreen video

Solusi:
1. Video selector mungkin salah
2. Atau browser security prevent fullscreen
3. Test di mode headless: false
4. Update selector
```

### Problem: Reload terlalu sering
```
Terminal show: 🔄 Reload page 3x dalam 1 menit

Solusi:
1. Timeout terlalu pendek
2. Naikkan timeout: 20 → 30
3. Atau video player memang lambat
4. Test dengan timeout 40-60
```

---

**Good luck debugging!** 🚀

Jika masih ada masalah, baca:
- INSTALLATION.md (instalasi lengkap)
- ADVANCED.md (fitur advanced)
- EXAMPLES.md (config examples)

Happy monitoring! 🎉
