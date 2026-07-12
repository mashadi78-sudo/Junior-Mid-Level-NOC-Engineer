# 📖 SILABUS PELATIHAN NOC ENGINEER: DEEP-DIVE & MASTERY (EDISI 2026)

Selamat datang di repositori utama Pelatihan NOC Engineer. Kurikulum ini dirancang dengan prinsip **Kedalaman Materi di atas Keluasan Teori**. Setiap peserta wajib menguasai keterampilan secara tuntas sebelum diizinkan beralih ke materi berikutnya.

---

## 🏗️ FASE 0: FONDASI UTAMA & EKOSISTEM KERJA (Minggu 1)

### 📂 `00-ekosistem-dan-alat-kerja/`
#### 🛠️ SKILL-00: Pengenalan Alat Kerja Jaringan & Segitiga Komunikasi (NOC - CS - Teknisi)
*   **Alat Kerja (Tools):** 
    *   *Internal NOC:* Monitoring Dashboard, Ticketing Software, CLI Terminal.
    *   *Mitra Lapangan:* Fusion Splicer, OTDR (Optical Time Domain Reflectometer), Laser VFL, OPM.
    *   *Mitra Front-End:* CRM (Customer Relationship Management) Software, SLA Dashboard.
*   **Fokus Kedalaman Materi:**
    *   Memahami alur kerja Segitiga Emas: Keluhan CS ➔ Analisis & Isolasi NOC ➔ Eksekusi Teknisi.
    *   Mempelajari parameter fisik lapangan: Memahami toleransi loss sambungan Fusion Splicer (< 0.02 dB) dan cara membaca grafik kilometer putus kabel pada layar OTDR teknisi agar NOC tidak bisa dibohongi di ruang monitor.
    *   Mempelajari psikologi kerja CS Admin: Cara meredam kepanikan gardu depan dengan menyuplai informasi teknis instan yang siap disalin (*broadcast ready*).
*   **Uji Kelulusan (Gatekeeper):** Diberikan studi kasus krisis (misal: kabel utama putus tertabrak truk). Peserta wajib menyusun instruksi koordinasi logis: alat apa yang harus dibawa teknisi ke lapangan dan teks informasi apa yang harus dikirim ke CS dalam waktu < 5 menit.

### 📂 `00a-dokumentasi-dan-kontrol-versi/`
#### 🛠️ SKILL-01: Penguasaan Standar Dokumentasi dengan Markdown (`.md`)
*   **Alat Kerja (Tools):** VS Code (Markdown Preview), HackMD.io.
*   **Fokus Kedalaman Materi:** Sintaksis judul (`#`), penekanan (`**`), tabel parameter, blok kode (` ``` `), dan kotak centang progress (`- [ ]`). Markdown digunakan sebagai bahasa resmi pelaporan tim.
*   **Uji Kelulusan (Gatekeeper):** Mengubah coretan nota laporan gangguan yang berantakan dari grup WhatsApp lapangan menjadi dokumen Markdown resmi yang rapi, bebas salah ketik, dan siap dibaca manajemen dalam waktu < 10 menit.

#### 🛠️ SKILL-02: Manajemen Kode dan Kontrol Versi dengan Git & GitHub
*   **Alat Kerja (Tools):** Git CLI (Terminal), GitHub Web.
*   **Fokus Kedalaman Materi:** Memahami siklus hidup berkas (*File Lifecycle*). Menguasai secara mendalam perintah `git clone`, `git status`, `git add`, `git commit -m`, dan `git push origin main`.
*   **Uji Kelulusan (Gatekeeper):** Berhasil membuat file progress mandiri di dalam folder `peserta/` dan mengunggahnya ke repositori instruktur tanpa memicu *merge conflict* atau error perizinan (*permission denied*).

---

## 🌐 FASE 1: FONDASI JARINGAN FISIK & LOGIK (Minggu 2 - 4)

### 📂 `01-jaringan-fisik-kabel/`
#### 🛠️ SKILL-03: Standarisasi Model OSI & Arsitektur TCP/IP
*   **Alat Kerja (Tools):** Draw.io, Cisco Packet Tracer.
*   **Fokus Kedalaman Materi:** Analisis enkapsulasi data. Bukan sekadar menghafal 7 layer, tetapi tahu jenis gangguan spesifik per layer (Layer 1: Kabel putus, Layer 2: Loop/Mac-Address penuh, Layer 3: Salah IP/RTO, Layer 4: Port terblokir).
*   **Uji Kelulusan (Gatekeeper):** Diberikan 5 jenis pesan error acak dari sistem. Peserta harus mampu memetakan error tersebut berada di layer berapa dan bagian perangkat mana yang harus diperiksa pertama kali.

#### 🛠️ SKILL-04: Pembuatan dan Troubleshooting Kabel UTP (Crimping & Testing)
*   **Alat Kerja (Tools):** Tang Crimping, Konektor RJ45, Kabel UTP Cat6, LAN Cable Analyzer / Fluke Tester.
*   **Fokus Kedalaman Materi:** Konstruksi fisik pin T568B. **Fokus pada investigasi kegagalan pin parsial (jalur TX kuat, RX lemah)** akibat pin 3 atau 6 longgar/kotor yang sering mengakibatkan kecepatan internet timpang sebelah (download hancur, upload normal, atau sebaliknya).
*   **Uji Kelulusan (Gatekeeper):** Mendeteksi kerusakan fisik kabel LAN tiruan yang sengaja dibuat cacat oleh instruktur menggunakan tester dalam waktu < 2 menit, lalu melakukan crimping ulang hingga status redaman/hambatan listrik 100% lulus uji.

#### 🛠️ SKILL-05: Karakteristik Serat Optik, Teknologi SFP, & Redaman
*   **Alat Kerja (Tools):** Modul SFP (Single Mode & Multi Mode), Optical Power Meter (OPM), Built-in DOM (Digital Optical Monitoring) via CLI WinBox/Cisco.
*   **Fokus Kedalaman Materi:** Persyaratan teknis kecocokan SFP (panjang gelombang nm, tipe kabel SM/MM, kecepatan 1G/10G). **Mengecek data DOM langsung dari sistem (melihat Tx Power dan Rx Power dalam satuan dBm)** untuk mendeteksi gejala penurunan kualitas laser sebelum link mati total.
*   **Uji Kelulusan (Gatekeeper):** Membaca parameter DOM SFP pada router/switch produksi. Menentukan apakah nilai dBm yang tertera masuk kategori aman, kritis (*attenuation*), atau berbahaya (terlalu kuat/lemah) bagi sensor perangkat.

### 📂 `02-sistem-pengalamatan/`
#### 🛠️ SKILL-06: Skema IPv4 & Perhitungan Subnetting Mendalam (VLSM)
*   **Alat Kerja (Tools):** CIDR Calculator Online, Google Sheets, Whiteboard.
*   **Fokus Kedalaman Materi:** Perhitungan alokasi IP manual tanpa kalkulator. Menentukan Network Address, Broadcast Address, Subnet Mask desimal, dan range IP valid untuk topologi multi-ruangan secara presisi agar tidak terjadi bentrok IP (*IP conflict*).
*   **Uji Kelulusan (Gatekeeper):** Diberikan satu blok IP besar (misal `/22`) dan diminta membaginya secara VLSM ke 5 segmen dengan kebutuhan jumlah host yang berbeda-beda. Salah menghitung 1 digit IP dianggap gagal.

#### 🛠️ SKILL-07: Konsep IP Publik vs IP Privat dan Mekanisme NAT
*   **Alat Kerja (Tools):** MXToolbox (IP Blacklist Check), IPVoid, Cisco Talos Intelligence, WinBox (IP Cloud).
*   **Fokus Kedalaman Materi:** Arsitektur translasi IP. **Investigasi reputasi IP Publik kantor saat terjadi krisis "tidak bisa membuka situs perbankan/HTTPS" akibat IP terblokir firewall luar (Spamhaus/Cloudflare)**. Mengonfigurasi jalur kontrol jarak jauh aman (**Secure Remote Access via VPN / Port Forwarding NAT**) untuk infrastruktur vital seperti OLT dan Server internal.
*   **Uji Kelulusan (Gatekeeper):** Mengisolasi masalah web perbankan yang macet: membuktikan apakah IP publik kantor sedang masuk daftar hitam global menggunakan MXToolbox, lalu mensimulasikan pemindahan rute ke IP publik cadangan.

#### 🛠️ SKILL-08: Dasar Protokol Layanan Aplikasi (DNS, DHCP, HTTP/HTTPS)
*   **Alat Kerja (Tools):** Perintah CLI `nslookup`, `dig`, `curl`, Browser Developer Tools (Network Tab).
*   **Fokus Kedalaman Materi:** Menganalisis alur paket jabat tangan (*handshake*) protokol. Melacak kegagalan internet akibat DNS mati atau korup menggunakan investigasi `dig`, serta mendeteksi pemblokiran port spesifik (Port 53, 80, 443).
*   **Uji Kelulusan (Gatekeeper):** Menyelesaikan masalah komputer yang mendapat IP salah (*rogue DHCP*) dan melacak keberadaan server DHCP palsu tersebut di jaringan lokal dalam waktu < 10 menit.

### 📂 `03-perangkat-keras-jaringan/`
#### 🛠️ SKILL-09: Manajemen Dasar Switch & Prinsip "Uji Perangkat Lokal Pertama"
*   **Alat Kerja (Tools):** Cisco Packet Tracer / GNS3, Terminal CLI (Putty / SecureCRT).
*   **Fokus Kedalaman Materi:** Konfigurasi VLAN, Access Port, dan Trunking. **Menguasai teknik investigasi kesehatan port lokal: membaca statistik `CRC Error`, `FCS Error`, dan `Rx/Tx Drop` pada port Switch via CLI** untuk mendeteksi kabel RJ45 kotor/longgar sebelum berasumsi ada gangguan massal di sisi ISP eksternal.
*   **Uji Kelulusan (Gatekeeper):** Melacak port switch mana yang mengalami bad-cable (mengalami lonjakan CRC Error akibat RJ45 cacat) hanya dengan membaca statistik counter CLI dalam waktu < 5 menit.

#### 🛠️ SKILL-10: Manajemen Dasar Router & Perbedaan Arsitektur Hardware (CCR vs x86)
*   **Alat Kerja (Tools):** MikroTik WinBox, VMware/VirtualBox (simulasi x86/CHR), CLI `/system resources cpu print`.
*   **Fokus Kedalaman Materi:** Konfigurasi Static Route dan manipulasi ukuran **MTU/MSS** untuk kelancaran jalur data HTTPS perbankan. **Menganalisis perbedaan performa MikroTik CCR (multi-core ARM/Tile) vs MikroTik x86/CHR (Arsitektur PC)** terkait penanganan driver kartu jaringan (NIC), IRQ Sharing, dan CPU balancing agar port tidak mendadak loncat 100% pada satu core (*CPU core starvation*). Mengonfigurasi **Default Gateway** balik pada perangkat akhir (seperti OLT) untuk mencegah masalah *asymmetric routing*.
*   **Uji Kelulusan (Gatekeeper - Uji Gerbang Fase 1):** Membangun topologi utuh di simulator dari nol: menghubungkan OLT tiruan, mengonfigurasi IP, menyetel MTU, membagi core CPU x86 agar seimbang, dan memastikan seluruh jaringan internal bisa melakukan ping tembus ke internet luar dengan status zero-packet-loss.

---

## 📊 FASE 2: TELEMETRI & PERANGKAT MONITORING (Minggu 5 - 7)
*(Rincian instrumen tools dan kedalaman materi pada Zabbix, PRTG, Linux CLI, Syslog Severity, SNMP Walk, dan Wireshark Packet Sniffing).*

## 🎫 FASE 3: TATA KELOLA INSIDEN & LOGIKA TROUBLESHOOTING (Minggu 8 - 10)
*(Rincian instrumen tools dan kedalaman materi pada Jira/ServiceNow ticketing, SLA Timer, Shift Handover Logbook, Metode Divide & Conquer, serta Incident Response Playbook).*

---

### 📝 CARA PENGGUNAAN REPOSITORI INI UNTUK PESERTA
1. Lakukan `git clone` repositori ini ke laptop Anda.
2. Buat file baru di folder `peserta/nama-lengkap-anda.md`.
3. Salin lembar checklist kemampuan di bawah ini ke dalam file Anda.
4. Mintalah tanda tangan digital (Centang `[x]`) kepada instruktur setiap kali Anda menyelesaikan ujian praktik langsung di lab.
