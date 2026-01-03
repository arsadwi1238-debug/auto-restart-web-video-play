```
📁 website-auto-restart-monitor/
│
├── 📄 README.md                    ← START HERE! Dokumentasi lengkap
├── 📄 BUILD_EXE.md                 ← Cara build jadi EXE
├── 📄 EXAMPLES.md                  ← Contoh config untuk berbagai kasus
├── 📄 ADVANCED.md                  ← Advanced features & customization
│
├── 📂 python-version/              ← Python Implementation
│   ├── app.py                      ← Main application
│   ├── build_exe.py                ← Automated EXE builder
│   ├── config.json                 ← Configuration file
│   ├── requirements.txt            ← Python dependencies
│   ├── setup.bat                   ← Quick setup (Windows)
│   ├── setup.sh                    ← Quick setup (Linux/Mac)
│   └── 📂 logs/                    ← Auto-created log files
│
├── 📂 nodejs-version/              ← Node.js Implementation
│   ├── app.js                      ← Main application
│   ├── config.json                 ← Configuration file
│   ├── package.json                ← Node.js dependencies
│   ├── setup.bat                   ← Quick setup (Windows)
│   ├── setup.sh                    ← Quick setup (Linux/Mac)
│   └── 📂 logs/                    ← Auto-created log files
│
└── 📂 dist/                        ← EXE files (after building)
    ├── WebsiteAutoRestart.exe      ← Python version EXE
    └── WebsiteAutoRestart.exe      ← Node.js version EXE
```

---

# 🚀 QUICK START GUIDE

## Pilih Versi Anda:

### ✅ PYTHON (Recommended - Lebih ringan & simple)

```powershell
# 1. Setup
cd python-version
.\setup.bat              # atau: python setup.py

# 2. Configure
# Edit config.json dengan URL website Anda

# 3. Run
python app.py           # Jalankan monitoring

# 4. Build EXE (optional)
python build_exe.py
```

### ✅ NODE.JS (Lebih powerful - built-in npm ecosystem)

```powershell
# 1. Setup
cd nodejs-version
.\setup.bat              # atau: npm install

# 2. Configure
# Edit config.json dengan URL website Anda

# 3. Run
npm start               # Jalankan monitoring

# 4. Build EXE (optional)
npm run build-exe
```

---

# 📋 WHAT DOES IT DO?

```
Website Monitor
    │
    ├─→ Load website di browser
    │
    ├─→ Check server health (ping)
    │
    └─→ Monitor video playback
         │
         ├─→ Video loading > 20 detik?
         │
         ├─→ YES → Reload page + Fullscreen video ✅
         │
         └─→ NO → Keep monitoring ✅
```

---

# 🎯 USE CASES

- ✅ Auto-restart video stream kalau stuck
- ✅ Monitor multiple websites simultaneously
- ✅ Public & Private URLs (localhost, IP internal, etc)
- ✅ Fullscreen video automatically
- ✅ Backend server crash detection & restart
- ✅ Automatic logging untuk troubleshooting
- ✅ Run as Windows service/startup app

---

# 📚 DOCUMENTATION

| File | Purpose |
|------|---------|
| **README.md** | Full documentation & features |
| **BUILD_EXE.md** | How to build standalone EXE |
| **EXAMPLES.md** | Config examples for different scenarios |
| **ADVANCED.md** | Custom features, auth, email, etc |

---

# 🎮 FEATURES

| Feature | Description |
|---------|-------------|
| 🎥 Video Monitoring | Detects stuck videos |
| 🔄 Auto Reload | Reloads page when video stuck |
| 📺 Fullscreen | Auto fullscreens video |
| 🌍 Multi-site | Monitor multiple URLs at once |
| 🔐 Public & Private | Support localhost & internal IPs |
| 📊 Logging | Detailed logs untuk debugging |
| 🖥️ EXE Build | Convert to standalone executable |
| ⚙️ Configurable | JSON config untuk easy setup |
| 🔧 Customizable | Support custom video selectors |
| 📱 Multi-monitor | Run multiple instances |

---

# 🛠️ TECH STACK

### Python Version
- **Language**: Python 3.8+
- **Browser Automation**: Selenium
- **HTTP Client**: Requests
- **Build Tool**: PyInstaller

### Node.js Version
- **Language**: JavaScript (Node.js)
- **Browser Automation**: Puppeteer
- **HTTP Client**: Axios
- **Build Tool**: pkg

Both versions bisa di-convert ke EXE standalone!

---

# 💾 FILE SIZES

| Build | Size | Includes |
|-------|------|----------|
| Python EXE | 50-100 MB | Python runtime + Selenium |
| Node.js EXE | 50-80 MB | Node.js runtime + Puppeteer |
| Config file | < 1 KB | JSON configuration |
| Logs | Varies | Daily log files |

---

# ⚙️ SYSTEM REQUIREMENTS

- **OS**: Windows 7+ (atau Linux/Mac untuk run, Windows untuk build)
- **Browser**: Google Chrome installed
- **RAM**: 512 MB minimum
- **Disk**: 200 MB free (untuk EXE + browser cache)
- **Internet**: Required (untuk akses website)

---

# 🎓 LEARNING PATH

1. **Beginner**: Read README.md, setup & run
2. **Intermediate**: Check EXAMPLES.md untuk kasus berbeda
3. **Advanced**: Study ADVANCED.md untuk customization
4. **Mastery**: Modify source code untuk kebutuhan spesifik

---

# 🆘 HELP & SUPPORT

1. **Check Logs**: `logs/monitor_YYYY-MM-DD.log`
2. **Read Docs**: EXAMPLES.md & ADVANCED.md
3. **Edit Config**: Update `config.json`
4. **Debug Mode**: Enable logging di source code
5. **Test**: Run dengan `headless: false` untuk lihat browser

---

# 📞 FREQUENTLY ASKED

**Q: Berapa lama untuk setup?**
A: 5 menit (setup) + 2 menit (config) = siap jalan!

**Q: Bisa monitor berapa website sekaligus?**
A: Unlimited, satu per browser instance

**Q: Gimana kalau video selector di situs berbeda?**
A: Lihat EXAMPLES.md untuk berbagai selector patterns

**Q: Bisa login otomatis?**
A: Ya, lihat ADVANCED.md untuk contoh code

**Q: Bisa send email notification?**
A: Ya, lihat ADVANCED.md untuk email integration

**Q: Bisa run as service?**
A: Ya, lihat BUILD_EXE.md untuk Windows Service setup

**Q: Bagaimana dengan update?**
A: Rebuild EXE dengan source code terbaru

**Q: Support macOS/Linux?**
A: Ya! Same code, bisa run di semua platform

---

# 🎉 READY TO GO?

1. **Baca**: README.md
2. **Setup**: Jalankan `setup.bat` atau `npm install`
3. **Config**: Edit `config.json`
4. **Run**: `python app.py` atau `npm start`
5. **Success**: Lihat logs & monitoring berjalan!

Happy monitoring! 🚀
