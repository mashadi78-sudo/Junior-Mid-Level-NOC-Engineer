# 📂 FASE 1: FONDASI JARINGAN FISIK & LOGIK

## 🛠️ SKILL-03: Standarisasi Model OSI & Arsitektur TCP/IP
*   **Kategori:** Teori Analitis & Pemetaan Isolasi Gangguan Sistem
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Aplikasi Diagram (Draw.io), Mode Simulasi Cisco Packet Tracer.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Staf NOC profesional tidak memanfaatkan Model OSI hanya untuk dihafalkan urutannya, melainkan sebagai **peta navigasi pelacakan masalah**. Setiap lapisan (*layer*) memiliki indikasi kerusakan dan pesan error yang spesifik. NOC harus bisa mendeteksi lokasi kerusakan berdasarkan jenis errornya:

*   **Layer 1 - Physical Layer (Fisik):** Tempat mengalir bit data berupa sinyal listrik atau cahaya.
    *   *Gejala Gangguan:* Lampu port mati, kabel UTP terkelupas, redaman SFP drop, kabel FO patah.
    *   *Status Sistem:* `Link Down`, `Hardware Radio Off`.
*   **Layer 2 - Data Link Layer (Alamat Fisik Perangkat / MAC):** Tempat pembungkusan data menjadi *Frame* dan pengaturan lalu lintas lokal switch.
    *   *Gejala Gangguan:* Terjadi tumpukan data tanpa henti akibat kabel melingkar (*Looping / Broadcast Storm*) yang membuat seluruh lampu switch berkedip sangat cepat secara bersamaan dan alat menjadi hang, atau kesalahan tag ID jalur VLAN.
    *   *Status Sistem:* `Interface flaps (up/down berulang)`, `MAC Address Table Full`.
*   **Layer 3 - Network Layer (Alamat Logik / IP & Routing):** Tempat penentuan rute jalan data (*Routing*) melalui nomor IP Address.
    *   *Gejala Gangguan:* Salah mengetik subnet mask, lupa mengisi konfigurasi *Default Gateway*, atau tabel rute router terputus.
    *   *Status Sistem:* `Request Timed Out (RTO)`, `Destination Host Unreachable`.
*   **Layer 4 - Transport Layer (Aturan Pengiriman / Port & Protokol):** Tempat jabat tangan (*handshake*) pengiriman paket menggunakan nomor pintu layanan (Port).
    *   *Gejala Gangguan:* Pengguna bisa melakukan *ping* ke IP Google, tetapi tidak bisa membuka situs web HTTPS perbankan (Port 443) atau remote server (SSH Port 22) karena pintu port ditutup oleh aturan dinding keamanan (*Firewall Rules*).
    *   *Status Sistem:* `Connection Refused`, `Connection Timed Out`.

---

### 2. TAHAP DEMI TAHAP PRAKTIK (Langkah Mandiri Siswa)
1.  **Langkah Awal:** Siswa membuka aplikasi **Cisco Packet Tracer**, lalu membangun topologi sederhana: menghubungkan 1 Laptop menuju 1 Server menggunakan kabel jenis *Straight*. Isi nomor IP Address segmen yang sama pada kedua alat tersebut (misal: `192.168.1.1` dan `192.168.1.2`).
2.  **Langkah Inti:** Klik tombol menu **Simulation** di pojok kanan bawah layar untuk mengaktifkan pelacakan visual paket data. Lakukan uji perintah `ping` dari Laptop menuju ke Server via terminal.
3.  **Langkah Verifikasi:** Klik pada gambar kotak surat berwarna yang muncul berjalan di kabel. Buka tab **OSI Model**. Siswa wajib mengamati bagaimana sebuah paket data dibungkus dari Layer atas (Layer 4: protokol ICMP), turun ke Layer 3 (disuntik IP asal-tujuan), turun ke Layer 2 (disuntik nomor MAC), hingga berubah menjadi bit sinyal kabel di Layer 1.

---

### 3. SKENARIO UJI KEMAMPUAN (Ujian Kelulusan Gerbang)
*   **Kondisi Ujian:** Instruktur memberikan 3 jenis pesan keluhan acak dari tim CS Admin atau sistem alarm dasbor monitoring:
    *   *Laporan A:* "Aplikasi absensi kantor lancar bisa diakses, tetapi teknisi gagal total melakukan remote manajemen OLT via SSH Port 22."
    *   *Laporan B:* "Seluruh jaringan satu ruangan mendadak putus bersamaan, dan semua lampu indikator pada Switch berkedip menyala serentak tanpa jeda."
    *   *Laporan C:* "Saat menguji koneksi ke server pusat, layar monitor menampilkan status tulisan Request Timed Out (RTO)."
*   **Target Kelulusan:** Siswa wajib menuliskan jawaban analisis secara cepat dan tepat pada file Markdown mereka dalam waktu < 5 menit: Laporan A dikategorikan gangguan pada OSI Layer berapa, Laporan B di Layer berapa, dan Laporan C di Layer berapa, disertai dengan alasan logisnya.

---

### 📊 LEMBAR CHECKLIST PROGRES (Kriteria Centang Kelulusan)
- [ ] Mampu menganalisis dan memetakan letak lapisan gangguan (*Layer Isolation*) secara instan ketika melihat pesan error sistem.
- [ ] Memahami perbedaan karakteristik error jaringan lokal (Layer 2) dengan error jalur rute luar (Layer 3).
- [ ] Sukses mempraktikkan pengamatan proses pembungkusan data (*Data Encapsulation*) lapis demi lapis menggunakan alat Simulation Mode pada Cisco Packet Tracer.

---
---

## 🛠️ SKILL-04: Pembuatan dan Troubleshooting Kabel UTP (Crimping & Testing)
*   **Kategori:** Jaringan Fisik & Isolasi Kerusakan Perangkat Lokal
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Tang Crimping, Konektor RJ45, Kabel UTP Cat6, LAN Cable Analyzer / Fluke Tester (atau LAN Tester dengan mode *Slow Test*), Switch Manageable (Cisco/MikroTik) via CLI.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Di dalam kabel UTP, pin **TX (Transmit/Mengirim)** dan pin **RX (Receive/Menerima)** menggunakan jalur tembaga yang terpisah secara fisik. Pada standar T568B, pin 1 & 2 berfungsi sebagai TX, sedangkan pin 3 & 6 berfungsi sebagai RX.

Banyak teknisi mengira jika internet tersambung, berarti kabel LAN 100% normal. Ini adalah kesalahan fatal. Jika proses *crimping* tidak sempurna (misalnya pin 3 atau 6 longgar, kotor, atau tembaganya kurang tergigit oleh pisau RJ45), hambatan listrik pada jalur RX akan melonjak. 

**Akibat Nyata di Lapangan:**
*   Sinyal TX (keluar) kuat, tetapi sinyal RX (masuk) penuh dengan gangguan (*noise/error*).
*   Hal ini memicu masalah **ketidakseimbangan (*unbalanced*) trafik internet yang ekstrem**, contohnya: kecepatan *download* hancur total (di bawah 1 Mbps), tetapi kecepatan *upload* berjalan normal 100 Mbps (atau sebaliknya).
*   **Tindakan NOC:** Sebelum mencurigai gangguan massal di sisi ISP, NOC wajib melakukan uji perangkat lokal pertama dengan memeriksa statistik *error* pada port Switch yang terhubung ke kabel tersebut. Jika nilai **`CRC Errors`**, **`FCS Errors`**, atau **`Rx Drop`** bertambah setiap detik, maka masalahnya **100% ada pada fisik konektor RJ45/Kabel LAN lokal**, bukan di pihak ISP.

---

### 2. TAHAP DEMI TAHAP PRAKTIK (Langkah Mandiri Siswa)
1.  **Langkah Awal:** Siswa memotong kabel UTP Cat6, mengupas kulit pelindung luar sepanjang 2 cm, lalu menyusun urutan pin standar internasional **T568B**: *Putih Oranye (1), Oranye (2), Putih Hijau (3), Biru (4), Putih Biru (5), Hijau (6), Putih Cokelat (7), Cokelat (8)*.
2.  **Langkah Inti:** Masukkan kabel ke konektor RJ45 dengan memastikan setiap ujung tembaga sudah mentok di ujung konektor, lalu jepit menggunakan tang *crimping* hingga berbunyi "klik" dan pin besi mengunci sempurna. Hubungkan kabel tersebut ke port Switch *Manageable*.
3.  **Langkah Verifikasi (Uji Sistem):** Buka terminal CLI Switch (Cisco/MikroTik) yang terhubung. Ketik perintah `/interface ethernet monitor-traffic` atau `show interface counter error`. Lakukan transfer file besar atau *speedtest*. Amati apakah angka pada baris `CRC Error` atau `FCS Error` tetap bernilai `0`. Jika angkanya melonjak naik, kabel wajib dipotong dan di-*crimping* ulang.

---

### 3. SKENARIO UJI KEMAMPUAN (Ujian Kelulusan Gerbang)
*   **Kondisi Ujian:** Instruktur akan memberikan sebuah komputer yang mengalami masalah aneh: *"Komputer ini bisa internetan, tetapi saat dipakai streaming video patah-patah parah. Hasil speedtest menunjukkan Download: 0.5 Mbps, sedangkan Upload: 90 Mbps."* Siswa dilarang mencabut kabel atau mengubah konfigurasi IP.
*   **Target Kelulusan:** Siswa harus memeriksa statistik port internal Switch melalui CLI. Siswa dinyatakan **LULUS** jika berhasil membuktikan adanya lonjakan *CRC/FCS Error* pada port lokal tersebut, mendiagnosis bahwa pin RX (pin 3/6) pada RJ45 bermasalah, lalu melakukan *crimping* ulang kabel hingga hasil *speedtest* seimbang kembali dalam waktu < 15 menit.

---

### 📊 LEMBAR CHECKLIST PROGRES (Kriteria Centang Kelulusan)
- [ ] Menghafal dan mampu menyusun urutan kabel standar T568B dengan rapi tanpa melihat catatan.
- [ ] Memahami korelasi antara pin fisik TX/RX (pin 1,2,3,6) dengan gejala ketidakseimbangan kecepatan *download/upload* (*unbalanced traffic*).
- [ ] Mampu mendeteksi kerusakan kabel LAN lokal secara digital dengan membaca data statistik `CRC Error` dan `Rx Drop` pada CLI Switch.
