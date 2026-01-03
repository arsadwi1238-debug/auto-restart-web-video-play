# ⚡ MULAI 1-2-3 (SUPER CEPAT!)

**Waktu yang dibutuhkan: 5 menit total!**

---

## ✅ LANGKAH 1: PERSIAPAN (1 MENIT)

### Checklist:
```
☑ Google Chrome sudah installed?
  Jika belum: google.com/chrome → Download & Install

☑ Python atau Node.js sudah installed?        (disarankan pake nodejs agar optimal)

  - Python: python.org/downloads
  - Node.js: nodejs.org
  
```

---



## ✅ LANGKAH 2: SETUP (2 MENIT)

### Pilih Satu:

#### **OPSI A: Python (Recommended - Lebih Sederhana)**

```powershell
# 1. Buka PowerShell
# 2. Ketik & Enter:

cd "d:\downweb\website-auto-restart-monitor\python-version"
.\setup.bat
              atau kalo malas run software run.bat nya 

# 3. Tunggu sampai selesai (text akan muncul)
# 4. Klik tombol apapun untuk close window
```



#### **OPSI B: Node.js (Lebih Powerful)**

```powershell
# 1. Buka PowerShell
# 2. Ketik & Enter:

cd (partisi windows kalian) "\website-auto-restart-monitor\nodejs-version"
.\setup.bat
-             atau kalo malas run software run.bat nya 

# 3. Tunggu sampai selesai (lumayan lama - ada download)
# 4. Klik tombol apapun untuk close window
```

**Setup done!** ✅



---

## ✅ LANGKAH 3: KONFIGURASI (1 MENIT)

### Edit url website kalian (ini g otomatis detect):

```powershell
# 1. Buka Notepad
# 2. File → Open → Ketik path:

partisi windows kalian "website-auto-restart-monitor\python-version\config.json"

# Atau untuk Node.js:
partisi windows kalian  "website-auto-restart-monitor\nodejs-version\config.json"

# 3. Cari baris ini:
"url": "http://localhost:5173"

# 4. Ganti dengan URL website Anda:
"url": "http://localhost:3000"     # contoh localhost
"url": "http://192.168.1.100:8080" # contoh IP internal
"url": "https://example.com"       # contoh public

# 5. Save (Ctrl+S) & Close
```

**Config done!** ✅

---

## ✅ LANGKAH 4: JALANKAN (1 MENIT)

### Pilih Cara Tercepat:

#### **Cara A: Double-Click**

```
1. Buka folder: python-version (atau nodejs-version)
2. Lihat file: run.bat
3. Double-click run.bat
4. Browser Chrome buka otomatis!
5. Monitoring dimulai! 🎉
```

#### **Cara B: PowerShell**

```powershell
# Python:
cd "d:\downweb\website-auto-restart-monitor\python-version"
python app.py

# Node.js:
cd "d:\downweb\website-auto-restart-monitor\nodejs-version"
npm start

# Browser buka otomatis!
```

**Selesai!** ✅🎉

---

## 📊 TAMPILAN SAAT JALAN
    
### Yang Anda Lihat:
```
✅ Terminal window (hitam) → show monitoring status
✅ Browser Chrome → tampilkan website Anda
✅ Video player → bisa terlihat
✅ Log file di: logs/monitor_2026-01-02.log
```

### Monitoring Berjalan:
```
Terminal show status setiap 5 detik:
📊 Video OK
📊 Video OK
📊 Video OK

Kalau video stuck:
❌ VIDEO STUCK! → Reload + Fullscreen
```

---

## 🛑 ADA ERROR?

### Error: "Chrome not found"
```
Download: google.com/chrome
Install, restart PowerShell, jalankan lagi
```

### Error: "Python/Node not found"
```
Download: python.org atau nodejs.org
Install, restart PowerShell, jalankan lagi
```

### Error: "config.json not found"
```
Pastikan config.json ada di folder
Jangan rename atau pindahkan file
```

### Error: "Video element not found"
```
Buka website di browser
Inspect video element (F12)
Update videoSelector di config.json
```

**Baca file TROUBLESHOOTING_ID.md untuk semua solusi!**

---

## ⏹️ CARA STOP

```
Di terminal window: Tekan Ctrl+C

Atau: Tutup terminal window
```

---

## 📁 FILE PENTING

```
✅ config.json       → Edit dengan URL Anda
✅ run.bat           → Double-click untuk jalan
✅ app.py/app.js     → Main application
✅ logs/             → Tempat log file disimpan
```

---

## 🎯 CHECKLIST SUKSES

Setelah jalankan, pastikan:

```
☑ Terminal menunjukkan "✅ Config loaded"
☑ Browser terbuka dengan website Anda
☑ Terminal menunjukkan "✅ Page loaded"
☑ Terminal update setiap 5 detik: "📊 Video..."
☑ Log file dibuat di logs/
☑ Tidak ada error merah
```

Jika semua ☑ → **BERHASIL!** 🎊

---

## 📚 DOKUMENTASI LENGKAP

Baca jika ingin tahu lebih lanjut:

```
START_HERE.md          ← Intro 30 detik
CARA_MENJALANKAN.md    ← Panduan menjalankan (detail)
TROUBLESHOOTING_ID.md  ← Solusi error (lengkap)
README.md              ← Dokumentasi complete
```

---

## 🚀 SELESAI!

**Sekarang aplikasi Anda jalan dan monitor website!**

Jika video stuck > 20 detik → Auto reload + fullscreen ✅

Enjoy! 🎉

---

**Ada pertanyaan? Baca dokumentasi atau cek log file!**
