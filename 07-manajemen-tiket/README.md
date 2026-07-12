# 📂 FASE 3: TATA KELOLA INSIDEN & LOGIKA TROUBLESHOOTING

## 🛠️ SKILL-19: Anatomi Pembuatan Tiket Gangguan yang Baku
*   **Kategori:** Dokumentasi Administrasi Insiden & Manajemen Aplikasi Tiket
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Platform Aplikasi Manajemen Tiket (Jira Service Desk / ServiceNow / GLPI Open Source).

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
NOC tidak boleh menyelesaikan masalah hanya lewat obrolan lisan. Setiap ada indikasi gangguan atau alarm yang berbunyi merah, NOC wajib menerbitkan berkas laporan digital resmi yang disebut **Tiket Gangguan (*Incident Ticket*)**. Penulisan tiket ini memiliki aturan internasional yang baku dan ketat. Isi deskripsi tiket tidak boleh ditulis asal-asalan atau ambigu karena akan dibaca oleh tim Senior Engineer, Vendor ISP, dan pihak manajemen perusahaan sebagai bukti rekam jejak performa kerja. Tiket yang profesional wajib memuat: Judul Padat, Waktu Kejadian, Dampak Kerusakan (*Severity Level*), Detail Perangkat Terinfeksi, Grafik Bukti Monitoring, dan Langkah Awal Pengujian yang Sudah Dilakukan.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka aplikasi Jira Service Desk atau ServiceNow kelas. Klik tombol *Create Ticket / New Incident*.
2.  **Langkah Inti:** Isi komponen formulir tiket dengan bahasa teknis yang baku:
    *   *Summary (Judul):* `[CRITICAL] [LINK DOWN] Jalur Utama Backbone ISP Biznet Gedung Pusat Cirebon`
    *   *Description:* Tuliskan urutan kronologi kejadian secara terperinci (Jam berapa alarm menyala, hasil pengujian ping RTO total, dan nomor ID sirkuit vendor kabel yang terdampak).
    *   *Attachment:* Lampirkan gambar tangkapan layar grafik pemantauan Zabbix yang turun drastis ke angka nol sebagai bukti penguat autentik.
3.  **Langkah Verifikasi:** Jalankan proses perpindahan status tiket mulai dari status `Open/New` -> `In Progress` (Saat sedang diperbaiki) -> `Resolved` (Saat koneksi sudah pulih kembali).

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Muncul alarm gawat darurat: *Link koneksi internet utama antar-kantor pusat dan cabang putus total akibat tiang roboh di jalan*. Suasana ruang kerja panik.
*   **Target Kelulusan:** Siswa wajib membuat satu berkas tiket insiden resmi pada platform Jira/ServiceNow dengan struktur format yang 100% rapi, padat, bebas dari salah ketik atau kalimat ambigu, serta melampirkan bukti foto sensor yang rusak dalam waktu < 5 menit sejak gangguan terdeteksi.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami anatomi struktur komponen wajib dalam penyusunan berkas tiket gangguan standar industri internasional.
- [ ] Mahir mengoperasikan platform manajemen tiket (Jira / ServiceNow / GLPI) untuk mengelola siklus hidup insiden (*Incident Lifecycle*).
- [ ] Mampu menuliskan deskripsi kronologi masalah menggunakan bahasa teknis yang baku, rapi, informatif, dan mudah dipahami lintas divisi.

---
---

## 🛠️ SKILL-20: Pemahaman SLA (Service Level Agreement) & Penentuan Prioritas Gangguan
*   **Kategori:** Tata Kelola Aturan Hukum Kontrak Kerja & Manajemen Skala Prioritas Urgensi
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Lembar Matriks Prioritas Insiden (Matriks Dampak vs Urgensi P1 s.d P4), Aplikasi Jam Hitung Mundur Target (*SLA Timer Dashboard*).

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Perusahaan penyedia internet terikat kontrak hukum dengan klien bisnis yang disebut **SLA (*Service Level Agreement*)**. Kontrak ini menetapkan batas waktu maksimal bagi tim NOC untuk merespons dan menyelesaikan sebuah gangguan jaringan hingga pulih kembali (*MTTR - Mean Time to Resolution*). Jika NOC melanggar batas waktu ini (*SLA Breach*), perusahaan wajib membayar denda ganti rugi yang sangat mahal kepada klien. Oleh karena itu, NOC harus cerdas menentukan **Skala Prioritas Tiket** menggunakan matriks dampak agar tahu masalah mana yang harus diselamatkan paling pertama:
*   **Priority 1 (P1 - Critical):** Gangguan berdampak massal ke seluruh perusahaan atau melumpuhkan bisnis utama (Contoh: Server core pusat mati total). Target penyelesaian wajib < 1 Jam.
*   **Priority 2 (P2 - High):** Gangguan berdampak luas tetapi sistem cadangan masih berjalan, atau melumpuhkan satu kantor cabang penuh. Target penyelesaian < 2 Jam.
*   **Priority 4 (P4 - Low):** Gangguan ringan berbau kosmetik atau hanya berdampak pada 1 orang user saja (Contoh: Printer meja si Budi tidak bisa terkoneksi). Target perbaikan bisa 24 jam.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Pelajari matriks persilangan antara kolom *Impact* (Berapa banyak jumlah korban user yang terdampak) dengan kolom *Urgency* (Seberapa kritis fungsi sistem tersebut terhadap kelangsungan bisnis).
2.  **Langkah Inti:** Saat sebuah tiket baru masuk, lakukan analisis klasifikasi. Jika ada dua tiket masuk bersamaan (Tiket A: Server transaksi utama lambat vs Tiket B: WiFi kantin mati), ubah status Tiket A menjadi Prioritas P1, dan Tiket B menjadi Prioritas P4.
3.  **Langkah Verifikasi:** Pantau pergerakan jam hitung mundur (*SLA Timer*) pada aplikasi dasbor tiket. Pastikan status penanganan tiket P1/P2 bergerak maju cepat sebelum batas waktu toleransi habis dilanggar.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Siswa diberikan 5 buah berkas laporan komplain jaringan yang masuk secara serentak di layar monitor. Siswa diminta mengurutkan penanganannya berdasarkan urutan kasta prioritas hukum kontrak SLA.
*   **Target Kelulusan:** Siswa harus mampu menyortir dan mengurutkan kelima tiket tersebut dengan 100% tepat (Mana yang masuk label P1, P2, P3, hingga P4) disertai argumentasi landasan hukum bisnis yang logis dalam waktu maksimal 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami konsep hukum bisnis di balik kontrak *Service Level Agreement (SLA)* dan parameter waktu maksimal pemulihan (*MTTR*).
- [ ] Mahir menentukan skala prioritas tingkat urgensi gangguan (P1-Critical s.d P4-Low) menggunakan papan matriks dampak secara objektif.
- [ ] Mampu mengelola manajemen waktu kerja penanganan masalah di bawah tekanan jam hitung mundur target SLA agar tidak memicu denda klaim.

---
---

## 🛠️ SKILL-21: Prosedur Serah Terima Tugas Jaga (Shift Handover Logbook)
*   **Kategori:** Komunikasi Estafet Divisi & Administrasi Pencatatan Buku Kerja Harian
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Google Docs Shared Logbook / Confluence Wiki Platform, Template Catatan Serah Terima Jabatan (*Handover Template*).

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Ruang monitor NOC beroperasi tanpa henti 24 jam sehari selama 7 hari seminggu menggunakan sistem pembagian kerja bergilir (*Shift Work*). Titik paling rawan terjadinya kegagalan perbaikan masalah adalah saat momen **Pergantian Shift (Shift Handover)**. Jika staf *shift* pagi pulang begitu saja tanpa memberikan catatan koordinasi yang jelas kepada staf *shift* malam, maka penanganan masalah gangguan besar yang sedang berjalan akan terputus di tengah jalan (*lost information*). NOC profesional wajib menulis buku laporan harian (**Logbook Handover**) yang rapi, berisi daftar tiket apa saja yang sudah berhasil diselesaikan (*Resolved*), dan tiket menggantung apa saja yang statusnya masih berjalan (*Pending*) dan wajib dikawal ketat oleh tim *shift* berikutnya.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** 30 Menit sebelum jam kerja *shift* Anda berakhir, buka dokumen platform bersama *Logbook Handover*.
2.  **Langkah Inti:** Tuliskan ringkasan dengan struktur format baku:
    *   *Tiket Selesai:* Sebutkan nomor tiket yang sudah sukses diperbaiki beserta solusi akhirnya.
    *   *Tiket Pending (Utang Tugas):* Sebutkan nomor tiket yang masih rusak, siapa nama teknisi lapangan yang sedang berjaga di lokasi, dan apa langkah eskalasi terakhir yang sedang ditunggu.
3.  **Langkah Verifikasi:** Lakukan *Briefing* lisan tatap muka langsung selama 5 menit dengan tim *shift* pengganti yang baru datang. Lakukan serah terima dokumen secara estafet dan pastikan tim yang baru datang memahami seluruh utang tugas penanganan masalah yang diwariskan.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Siswa berada di akhir jam kerja *shift* pagi. Masih ada satu kasus besar jaringan terputus yang belum selesai diperbaiki karena teknisi di lapangan masih terjebak macet di jalan menuju lokasi kabel putus. Tim *shift* malam baru saja melangkah masuk ruangan.
*   **Target Kelulusan:** Siswa wajib menyusun naskah dokumen laporan serah terima kerja harian (*Handover Logbook*) secara instan, padat data, dan melakukan simulasi *briefing* estafet tugas secara lisan di depan instruktur dengan sangat komunikatif dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami pentingnya prosedur administrasi dan etika profesionalisme dalam proses pergantian jam kerja *shift (Handover)*.
- [ ] Berhasil membuat dokumen pencatatan buku kerja harian (*Logbook Handover*) dengan pemisahan status tugas yang rapi (*Resolved vs Pending*).
- [ ] Mampu melakukan komunikasi penyampaian estafet masalah (*Briefing Operational*) secara jelas, singkat, dan terarah kepada rekan tim pengganti.
