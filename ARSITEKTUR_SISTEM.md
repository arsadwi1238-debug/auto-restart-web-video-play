# 🎬 BAGAIMANA SISTEM BEKERJA (ARSITEKTUR)

## 🎯 PENJELASAN SINGKAT

Anda menginginkan:
```
Aplikasi saya HANYA mengontrol browser untuk monitor video
Video streaming tetap dari server asli indihometv.com
Tidak ada proxy, tidak ada redirect, pure monitoring saja
```

**TEPAT SEKALI!** Itulah yang aplikasi saya lakukan!

---

## 📊 DIAGRAM ALUR KERJA

```
┌─────────────────────────────────────────────────────────────┐
│                    KOMPUTER ANDA                            │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  APLIKASI AUTO-RESTART (Node.js)                    │  │
│  │  ┌─────────────────────────────────────────────────┐│  │
│  │  │ 1. Buka Browser Chrome dengan Puppeteer       ││  │
│  │  │    └─ Browser ini pakai Chrome ASLI komputer  ││  │
│  │  │       (tidak virtualnya, bukan fake!)          ││  │
│  │  │                                                 ││  │
│  │  │ 2. Navigate ke website indihometv.com          ││  │
│  │  │    └─ Website load NORMAL (tidak diproxy)      ││  │
│  │  │       └─ Video fetch dari server ASLI          ││  │
│  │  │          indihometv.com                        ││  │
│  │  │                                                 ││  │
│  │  │ 3. MONITOR video setiap 5 detik                ││  │
│  │  │    └─ Check: video playing atau stuck?         ││  │
│  │  │    └─ Log status: ✅ OK atau ❌ STUCK          ││  │
│  │  │                                                 ││  │
│  │  │ 4. Jika VIDEO STUCK (>20 detik)               ││  │
│  │  │    ├─ Reload page (F5)                         ││  │
│  │  │    ├─ Fullscreen video                         ││  │
│  │  │    └─ Mulai monitor ulang                      ││  │
│  │  │                                                 ││  │
│  │  │ 5. LOG SEMUA ke file                           ││  │
│  │  │    └─ logs/monitor_2026-01-02.log              ││  │
│  │  └─────────────────────────────────────────────────┘│  │
│  │                                                      │  │
│  └──────────────────────────────────────────────────────┘  │
│                          │                                  │
│                          │ Control                          │
│                          ↓                                  │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  BROWSER CHROME (Pakai yang dari komputer Anda)      │  │
│  │  ┌─────────────────────────────────────────────────┐│  │
│  │  │ - Window normal Chrome (1920x1080)             ││  │
│  │  │ - Bisa lihat video playing                     ││  │
│  │  │ - Bisa fullscreen                             ││  │
│  │  │ - Bisa reload                                  ││  │
│  │  │ - Fetch video dari server asli                ││  │
│  │  │ - Internet connection normal                   ││  │
│  │  └─────────────────────────────────────────────────┘│  │
│  │                                                      │  │
│  └──────────────────────────────────────────────────────┘  │
│                          │                                  │
│                          │ FETCH (Stream)                  │
│                          ↓                                  │
└─────────────────────────────────────────────────────────────┘
                          │
                          │ Internet (Normal)
                          ↓
        ┌──────────────────────────────────┐
        │  SERVER INDIHOMETV.COM           │
        │  ┌──────────────────────────────┐│
        │  │ Video Stream                 ││
        │  │ - Video file                 ││
        │  │ - Live stream                ││
        │  │ - HLS/DASH stream            ││
        │  │ - Transcode                  ││
        │  └──────────────────────────────┘│
        │                                  │
        └──────────────────────────────────┘
```

---

## 🔄 URUTAN KERJA DETAIL

### Awal (Startup):

```
1. Anda run: npm start
   ↓
2. Aplikasi start
   ├─ Buka config.json
   ├─ Check requirements
   └─ Ready to monitor
   ↓
3. Aplikasi buka Browser Chrome
   ├─ Puppeteer control Chrome dari code
   ├─ Chrome adalah browser real dari komputer Anda
   └─ Window terbuka, visible, normal
   ↓
4. Browser navigate ke: https://www.indihometv.com/livetv/trans7
   ├─ Fetch HTML dari server
   ├─ Load CSS, JS, resources
   ├─ Execute JavaScript (player script)
   ├─ Load video player
   └─ Video mulai loading...
```

### Monitoring (Setiap 5 detik):

```
5. Aplikasi cek: "Apakah video ada?"
   ├─ Query HTML dengan selector: "video, iframe, canvas, ..."
   ├─ Ketemu? → Continue (GOOD!)
   └─ Tidak? → Log warning, skip this round
   ↓
6. Aplikasi cek: "Apakah video playing?"
   ├─ Check video properties:
   │  ├─ readyState (buffering status)
   │  ├─ networkState (download status)
   │  └─ currentTime (position)
   ├─ Status:
   │  ├─ OK (4, 1, time incrementing) → Log ✅
   │  ├─ LOADING (2, 2) → Start timer
   │  └─ STUCK (>20 detik) → ACTION!
   └─ Log result
   ↓
7. Jika STUCK:
   ├─ Browser reload page (F5)
   ├─ Website load ulang
   ├─ Video player reinit
   ├─ Video fetch ulang dari server
   └─ Reset stuck timer
   ↓
8. Log result
   ├─ 📊 Status updates
   ├─ 🔄 Reload actions
   ├─ ❌ Errors
   └─ File: logs/monitor_2026-01-02.log
```

---

## 🎯 APA YANG KAMI LAKUKAN vs TIDAK LAKUKAN

### ✅ YANG KAMI LAKUKAN:

```
✅ Control browser (open, navigate, reload, fullscreen)
✅ Monitor video status (playing, stuck, error)
✅ Detect timeout (>20 detik loading)
✅ Auto-reload page
✅ Auto-fullscreen video
✅ Log semua action
✅ Repeat monitoring every 5 seconds
```

### ❌ YANG TIDAK KAMI LAKUKAN:

```
❌ Serve video file
❌ Create/host server
❌ Proxy/redirect video
❌ Encrypt/encode video
❌ Change video source
❌ Intercept stream
❌ Cache video locally
❌ Modify website code
```

### 🎬 VIDEO TETAP DARI:

```
→ Server indihometv.com (original server)
→ Browser fetch normal HTTP/HTTPS request
→ No man-in-the-middle
→ No proxy
→ Pure streaming sama seperti user biasa buka website
```

---

## 🔌 DATA FLOW

```
APPLICATION (Monitor)
   ↓
   ├─ Read config.json
   │  └─ URL, selector, timeout, check interval
   │
   ├─ Open browser via Puppeteer
   │  └─ Control Chrome dengan JavaScript
   │
   ├─ Browser navigates to URL
   │  ├─ HTTP request ke indihometv.com
   │  ├─ Server respond dengan HTML
   │  ├─ Browser render page
   │  ├─ Execute website JavaScript
   │  └─ Video player load & start streaming
   │
   ├─ Monitor loop (every 5 seconds)
   │  ├─ Query video element (DOM)
   │  ├─ Get video status properties
   │  ├─ Evaluate readyState & networkState
   │  ├─ Check currentTime (moving or stuck?)
   │  ├─ Log status
   │  └─ If stuck → Reload
   │
   └─ Write logs
      └─ File: logs/monitor_YYYY-MM-DD.log


SERVER (Origin)
   ↓
   ├─ Serve HTML (website code)
   ├─ Serve JS (player script)
   ├─ Serve video stream
   │  ├─ HLS (.m3u8)
   │  ├─ DASH (.mpd)
   │  └─ MP4 direct
   └─ Handle requests normal

NO PROXY, NO MODIFICATION!
```

---

## 🌐 NETWORK PERSPECTIVE

```
SCENARIO: Video streaming indihometv

Timeline:
1. [0s] User/App buka browser
2. [1s] Browser request HTML ke indihometv.com
3. [2s] Server reply HTML
4. [3s] Browser load CSS/JS
5. [5s] Player script execute
6. [6s] Player request video manifest (HLS/DASH)
7. [7s] Server reply manifest
8. [8s] Player request first chunk
9. [10s] Video start playing ▶️
10. [Every 5s] App monitor: "Is video playing? YES ✅"
...
15. [Video stuck] [60s] No buffering → STUCK!
16. Browser reload (app command)
17. [65s] [Back to step 1]
18. [75s] Video play again ▶️
```

---

## 💾 FILES & STORAGE

```
Aplikasi folder:
d:\downweb\website-auto-restart-monitor\
├── nodejs-version\
│   ├── app.js                      (aplikasi logic)
│   ├── config.json                 (konfigurasi)
│   ├── node_modules\               (dependencies)
│   └── logs\
│       └── monitor_2026-01-02.log  (hasil monitoring)
│
└── (file lain)

Chromium/Chrome:
C:\Users\[YourName]\AppData\Local\Chromium\  (downloaded)
or
C:\Program Files\Google\Chrome\               (if using system Chrome)
```

---

## 🔧 REQUIREMENTS

```
✅ NODE.JS (application runtime)
   └─ Puppeteer (browser automation)

✅ CHROME BROWSER (system Chrome atau auto-download Chromium)
   └─ Real browser, real rendering
   └─ Fetch video normal
   └─ No special setup needed

✅ INTERNET CONNECTION
   └─ Browser need to access indihometv.com
   └─ Need bandwidth for video streaming

✅ CONFIG.JSON
   └─ URL, selector, timeout settings

❌ SERVER software needed?
   NO! Server is indihometv.com (external)

❌ Proxy needed?
   NO! Direct connection to indihometv.com

❌ Special video library?
   NO! Browser handle video natively
```

---

## 🎬 VIDEO DETECTION MECHANISM

Aplikasi find video ini cara:

```
JavaScript yang dijalankan di browser:

// 1. Find video element
const video = document.querySelector("video, iframe, canvas, ...");

// 2. Get properties
const readyState = video.readyState;      // 0-4
const networkState = video.networkState;  // 0-3
const currentTime = video.currentTime;    // seconds
const paused = video.paused;              // true/false

// 3. Evaluate
if (readyState < 2 && networkState === 2) {
  // Video is LOADING but no data yet
  // Start stuck timer...
}

if (stuckDuration > timeout) {
  // VIDEO STUCK! Do something!
  // Reload, fullscreen, etc
}

// 4. Log
log.info("Video status: Ready=" + readyState + ", Network=" + networkState);
```

**Ini JavaScript standard untuk monitoring HTML5 video!**

---

## 🛡️ SECURITY & SAFETY

```
✅ AMAN?
   - Tidak ada malware
   - Tidak ada data harvesting
   - Tidak modify indihometv code
   - Browser pakai Chrome standard
   - Just monitor & control

✅ LEGAL?
   - Automation untuk monitoring adalah legal
   - Tidak hack/bypass security
   - Tidak download video
   - Hanya reload page kalau stuck

❌ BISA DI-DETECT INDIHOMETV?
   - Theoretically: Yes (bisa detect automation)
   - Practically: Puppeteer anti-detection enabled
   - Website tidak block normal reloading
```

---

## ✅ KESIMPULAN

**Sistem kami adalah:**

```
MONITORING BROWSER AUTOMATION

→ Pure monitoring (tidak modify website)
→ Pure control (reload, fullscreen)
→ Pure logging (track status)
→ 100% dari server asli indihometv.com
→ No proxy, no modification, no fancy stuff
→ Just watch video & reload kalau stuck
```

**Bukan:**
- Server hijacking
- Stream proxy
- Content modification
- Illegal streaming
- Video download

**Sederhananya:**
```
Seperti Anda buka indihometv.com manually
Tapi dibuat otomatis sama aplikasi
Dan auto-reload kalau video stuck
```

---

## 🚀 SEKARANG JALANKAN

```
1. cd nodejs-version
2. Update config.json (selector)
3. npm start
4. Lihat browser terbuka, video play
5. Terminal show monitoring status
6. Jika stuck → Auto reload!
7. Logs di: logs/monitor_2026-01-02.log
```

**All from your laptop, all from your browser!** ✅

---

**Paham sekarang bagaimana sistemnya?** 

Jika ada pertanyaan, tanya saja! 🚀
