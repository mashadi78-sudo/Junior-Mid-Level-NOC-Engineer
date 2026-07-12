# 📂 FASE 2: TELEMETRI & PERANGKAT MONITORING

## 🛠️ SKILL-14: Pengenalan Protokol SNMP (MIB, OID, Get, dan Walk)
*   **Kategori:** Protokol Telemetri Pemantauan & Penarikan Data Kesehatan Aset
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Perintah Linux CLI (`snmpwalk`, `snmpget`), Aplikasi MIB Browser, Router/Switch aktif yang menyalakan fitur SNMP Service.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Aplikasi monitoring tidak menebak-nebak isi kesehatan router. Mereka menarik data menggunakan protokol **SNMP (*Simple Network Management Protocol*)**. Router menyediakan lemari data rahasia bernama **MIB (*Management Information Base*)**, dan setiap parameter data (seperti data suhu, data memori, data trafik port) memiliki kode angka koordinat penunjuk khusus bernama **OID (*Object Identifier*)**. NOC harus tahu cara menarik data mentah OID ini menggunakan perintah CLI untuk memastikan router merespons sebelum mendaftarkannya ke dasbor visual.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Aktifkan fitur SNMP Service pada Router (masukkan nama kunci kecocokan/*Community String*, misal: `noc-monitoring-2026`).
2.  **Langkah Inti:** Dari server monitoring Linux, jalankan perintah pengujian untuk menarik seluruh isi data lemari router: `snmpwalk -v 2c -c noc-monitoring-2026 [IP_Router]`.
3.  **Langkah Verifikasi:** Gunakan perintah spesifik `snmpget` diikuti kode nomor koordinat OID tertentu (misal OID untuk utilitas CPU) untuk memverifikasi apakah router sukses mengirimkan angka parameter kesehatan internalnya secara akurat.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Sebuah router merek baru dipasang di lapangan, tetapi datanya tidak mau muncul di layar dasbor aplikasi monitoring utama kantor. Diduga ada ketidakcocokan kunci string atau penolakan port SNMP.
*   **Target Kelulusan:** Siswa wajib melakukan uji tembak data manual menggunakan perintah `snmpwalk/snmpget` via CLI server untuk menganalisis letak kesalahannya (apakah salah string atau port terblokir firewall) dan memperbaikinya hingga data merespons dalam waktu < 10 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami konsep fungsi arsitektur protokol SNMP, fungsi buku petunjuk MIB, dan kode koordinat data OID.
- [ ] Berhasil melakukan penarikan data mentah dari router menggunakan utilitas perintah CLI `snmpwalk` secara mandiri.
- [ ] Mampu memecahkan masalah kegagalan komunikasi sensor SNMP antara server pemantau dengan aset perangkat jaringan.

---
---

## 🛠️ SKILL-15: Analisis Aliran Lalu Lintas Data Menggunakan Flow Data (NetFlow/sFlow)
*   **Kategori:** Analisis Kapasitas Bandwidth & Identifikasi Konsumsi Trafik Pengguna
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Perangkat Lunak Penganalisis Flow (NfSen / SolarWinds NetFlow / ElastiFlow), Core Router/Firewall utama yang mendukung fitur ekspor NetFlow.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Jika sensor SNMP bertugas memantau *kesehatan mesin* (CPU/Memori), maka **Flow Data (NetFlow/sFlow/IPFIX)** bertugas membongkar *isi pipa lalu lintas data* yang lewat di dalamnya. Core Router akan menangkap cuplikan informasi paket data lalu mengirimkannya ke server kolektor NOC. Data ini sangat vital bagi NOC untuk memecahkan misteri kasus **"Bandwidth internet kantor mendadak penuh sesak 100% sampai macet, padahal tidak ada gangguan fisik kabel."** Dengan Flow Data, NOC bisa melihat secara transparan alamat IP mana yang sedang menyedot kuota paling besar dan jenis protokol aplikasinya (YouTube, Torrent, Zoom, dll).

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Aktifkan fitur NetFlow Export pada Core Router utama, arahkan tujuannya ke IP Server NetFlow Collector NOC (Port default biasanya: 9996).
2.  **Langkah Inti:** Buka dasbor aplikasi web kolektor NetFlow (seperti ElastiFlow/NfSen). Buka menu grafik *Top Talkers* atau *Top Conversations*.
3.  **Langkah Verifikasi:** Analisis grafik pie chart atau baris tabel untuk membaca alamat IP internal mana saja yang menduduki peringkat penggunaan kuota *bandwidth* (Mbps) tertinggi dan periksa jenis pintu port aplikasinya.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Terjadi lonjakan trafik internet misterius di kantor cabang yang mengakibatkan koneksi meeting direksi terputus-nyambung. Sensor monitoring SNMP hanya menunjukkan grafik penggunaan bandwidth menyentuh batas maksimal merah.
*   **Target Kelulusan:** Siswa wajib membuka dasbor NetFlow, mengidentifikasi nomor IP komputer karyawan mana yang sedang melakukan aktivitas unduhan ilegal skala besar (misal: download file film/torrent) berdasarkan analisis data percakapan trafik tertinggi, dan melaporkan nomor IP tersebut dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami perbedaan fungsi analisis antara parameter data SNMP (kesehatan mesin) dengan parameter NetFlow (isi lalu lintas).
- [ ] Berhasil mengonfigurasi aturan ekspor data lalu lintas (*NetFlow Export*) dari sisi perangkat Core Router menuju server pusat.
- [ ] Mampu membaca dan menganalisis grafik dasbor Flow Data untuk mendeteksi anomali penggunaan bandwidth (*Top Talkers Identification*).
