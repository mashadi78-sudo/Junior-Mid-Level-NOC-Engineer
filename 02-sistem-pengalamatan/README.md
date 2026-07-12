# 📂 FASE 1: FONDASI JARINGAN FISIK & LOGIK

## 🛠️ SKILL-06: Skema IPv4 & Perhitungan Subnetting Mendalam (VLSM)
*   **Kategori:** Sistem Pengalamatan Jaringan & Optimasi Alokasi Host
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** CIDR Calculator Online, Google Sheets/Spreadsheet, Whiteboard.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
NOC profesional wajib menguasai perhitungan pembagian alokasi IP (*Subnetting*) menggunakan metode VLSM (*Variable Length Subnet Mask*) secara manual dan cepat. Pemahaman ini krusial agar tidak ada pemborosan kuota IP publik/privat dan mencegah terjadinya tabrakan alamat (*IP Conflict*) antar-ruangan atau divisi. Peserta harus mampu memetakan secara presisi: Network Address, Broadcast Address, Subnet Mask desimal, dan range IP valid yang bisa dipakai (*Usable IP*).

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Ambil satu blok IP besar (misal: `192.168.10.0/24`). Urutkan kebutuhan divisi mulai dari yang membutuhkan jumlah komputer terbanyak hingga yang paling sedikit (Divisi A: 50 host, Divisi B: 20 host, Divisi C: 2 host untuk interkoneksi router).
2.  **Langkah Inti:** Hitung manual kebutuhan CIDR untuk tiap segmen (A: `/26`, B: `/27`, C: `/30`). Petakan blok range IP untuk Divisi A terlebih dahulu, disusul Divisi B, lalu Divisi C tanpa ada nomor yang tumpang tindih (*overlapping*).
3.  **Langkah Verifikasi:** Catat hasil pembagian IP ke dalam tabel dokumentasi jaringan dan pastikan tidak ada nomor IP gerbang utama (*Gateway*) yang terbalik antara divisi satu dengan lainnya.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Instruktur memberikan blok IP `172.16.0.0/22`. Siswa diminta membaginya secara manual untuk 4 ruangan kantor dengan kebutuhan: Ruang CS (100 PC), Ruang Teknisi (50 PC), Ruang Server Internal (10 PC), dan Jalur Koneksi OLT ke Router Utama (2 IP).
*   **Target Kelulusan:** Siswa wajib menuliskan hasil perhitungan manual dengan 100% akurat dalam waktu < 15 menit. Salah menghitung atau terjadi tumpang tindih 1 digit IP saja dinyatakan GAGAL.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Mampu menghitung konversi nilai CIDR (seperti `/26`, `/29`) menjadi nilai Subnet Mask desimal secara manual.
- [ ] Berhasil menentukan Network Address dan Broadcast Address dari sebuah segmen IP acak tanpa bantuan kalkulator online.
- [ ] Sukses membagi blok IP besar menggunakan metode VLSM secara urut dari host terbesar ke terkecil tanpa *overlapping*.

---
---

## 🛠️ SKILL-07: Konsep IP Publik vs IP Privat, Mekanisme NAT, & Investigasi Reputasi IP
*   **Kategori:** Translasi Alamat Jaringan & Analisis Keamanan Eksternal
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** MXToolbox (IP Blacklist Check), IPVoid, Cisco Talos Intelligence, WhatsMyIP, Router MikroTik/Cisco via CLI.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Komputer internal menggunakan IP Privat dan ditranslasikan menjadi satu IP Publik oleh Router melalui mekanisme NAT (*Network Address Translation*) agar bisa mengakses internet luar. 
*   **Masalah IP Kotor / Blacklist:** Jika ada satu komputer internal terinfeksi *malware* atau melakukan aktivitas ilegal, maka IP Publik kantor akan dicap "kotor" dan masuk daftar hitam global (Spamhaus, Barracuda, dll). Dampak nyatanya: **pengguna tidak bisa membuka situs HTTPS perbankan atau Cloudflare karena diblokir otomatis dari sisi server luar**.
*   **Remote Akses Infrastruktur Pusat:** NOC wajib tahu cara membuat jalur kontrol jarak jauh yang aman (**Secure Remote Access via VPN atau Port Forwarding NAT**) agar perangkat vital di lapangan seperti **OLT** atau Server internal bisa di-remote dari pusat operasional NOC secara aman melalui internet publik.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Cek IP Publik yang sedang digunakan kantor melalui situs WhatsMyIP atau via CLI Router. 
2.  **Langkah Inti:** Masukkan nomor IP Publik tersebut ke kolom pencarian **MXToolbox Blacklist Check** dan **Cisco Talos Intelligence**. Analisis apakah reputasi IP berstatus *Good*, *Neutral*, atau *Poor/Listed*.
3.  **Langkah Verifikasi:** Praktikkan konfigurasi aturan NAT *Port Forwarding* di Router utama menuju ke IP Management OLT lokal (Port 22/SSH atau Port 80/HTTPS) agar OLT tersebut bisa ditembus dan di-remote secara publik secara aman melalui VPN khusus NOC.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Muncul komplain massal: *"Internet lancar bisa buka YouTube, tapi seluruh komputer direksi tidak bisa login ke internet banking."* Hasil pengujian teknis dasar (ping) ke IP bank berjalan normal.
*   **Target Kelulusan:** Siswa harus membuktikan secara digital menggunakan MXToolbox bahwa IP Publik kantor sedang masuk daftar blokir server bank akibat "IP Kotor". Siswa wajib menyusun laporan isolasi masalah dan mendemonstrasikan tindakan eskalasi/solusi (memindahkan jalur rute ke IP Publik cadangan yang bersih atau meminta *release lease* ke ISP) dalam waktu < 10 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami perbedaan fungsi teknis IP Publik dan IP Privat serta mekanisme kerja aturan NAT.
- [ ] Mahir menggunakan tools eksternal (MXToolbox & IPVoid) untuk melakukan investigasi reputasi kebersihan IP Publik.
- [ ] Mampu mengonfigurasi Port Forwarding NAT dan VPN secara aman untuk kebutuhan akses remote perangkat OLT/Server dari jaringan publik.

---
---

## 🛠️ SKILL-08: Dasar Protokol Layanan Aplikasi (DNS, DHCP, HTTP/HTTPS)
*   **Kategori:** Analisis Protokol Lapangan Aplikasi & Troubleshooting Layanan
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Perintah CLI `nslookup`, `dig`, `curl`, Browser Developer Tools (Network Tab).

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
NOC wajib memahami jabat tangan (*handshake*) protokol aplikasi yang sering memicu komplain internet mati:
*   **DNS (Port 53):** Penerjemah nama domain (seperti `google.com`) menjadi nomor IP Address. Jika DNS server internal mati atau korup, komputer user tidak akan bisa membuka web apa pun meskipun jalur kabel fisik normal.
*   **DHCP (Port 67/68):** Pembagi IP otomatis ke pengguna. Gangguan terbesar di area ini adalah adanya **Rogue DHCP (DHCP Palsu)**, yaitu perangkat WiFi router liar milik karyawan yang dicolok sembarangan sehingga menyebarkan IP salah ke komputer lain, mengakibatkan tabrakan jaringan lokal secara acak.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka terminal komputer, jalankan perintah `nslookup klikbca.com` atau `dig klikbca.com` untuk memverifikasi apakah server DNS merespons dengan memberikan IP tujuan yang benar.
2.  **Langkah Inti:** Gunakan perintah `curl -I https://google.com` untuk memeriksa apakah pintu gerbang web aman (Port 443/HTTPS) merespons dengan status `200 OK`.
3.  **Langkah Verifikasi:** Analisis Network Tab pada Browser Developer Tools (Klik kanan -> Inspect Element -> Network) untuk melihat waktu muat (*load time*) komponen web dan mendeteksi jika ada port aplikasi tertentu yang terhambat.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Di jaringan lokal kantor, mendadak puluhan komputer salah mendapatkan IP Address (mendapat segmen IP aneh dan tidak bisa internetan) akibat adanya serangan atau tidak sengaja terpasang perangkat *Rogue DHCP Server*.
*   **Target Kelulusan:** Siswa wajib melacak alamat MAC (*MAC Address*) dari server DHCP palsu tersebut menggunakan perintah investigasi CLI dan mengisolasi jalurnya di switch lokal dalam waktu < 10 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Mampu menganalisis kegagalan internet akibat kerusakan DNS menggunakan utilitas perintah `nslookup` atau `dig`.
- [ ] Memahami nomor port esensial (DNS: 53, HTTP: 80, HTTPS: 443) beserta status respon kodenya.
- [ ] Berhasil mengidentifikasi dan melacak keberadaan server DHCP liar (*Rogue DHCP*) yang mengacaukan pembagian IP lokal.
