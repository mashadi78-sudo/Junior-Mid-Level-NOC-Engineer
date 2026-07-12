# 📂 FASE 4: REALITAS & DINAMIKA GANGGUAN LAPANGAN

## 🛠️ SKILL-29: Tingkat Satu Pele (Masalah Sepele / Human Error End-User)
*   **Kategori:** Isolasi Masalah Ujung Jaringan & Edukasi Pelanggan
*   **Alat Kerja (Tools):** Script Pertanyaan CS, Remote Web GUI ONT/Modem, WinBox (IP ARP Table).

### 1. Dinamika Lapangan (Akar Masalah)
Masalah yang paling sering menghabiskan waktu tim NOC justru bukan server yang meledak, melainkan kecerobohan pengguna di rumah atau kantor (End-User). Contoh klasik:
*   Kabel LAN sengaja dicabut oleh petugas kebersihan saat menyapu.
*   Tombol WiFi di laptop pengguna tidak sengaja tertekan mati, tetapi pengguna melapor ke CS bahwa "WiFi ISP Anda mati total".
*   Adaptor listrik modem longgar atau dicolok ke sakelar yang arusnya sering dimatikan dari pusat sakelar lampu gedung.

### 2. Logika Kerja & Langkah Solusi NOC
1.  **Gunakan Aturan "Cek Lampu":** NOC menginstruksikan CS Admin untuk menuntun pelanggan melihat lampu fisik modem via telepon. Tanyakan: *"Lampu PON menyala hijau atau tidak? Lampu LAN menyala tidak?"*
2.  **Cek Tabel ARP di Router:** Masuk ke WinBox, buka `IP -> ARP`. Perhatikan apakah alamat MAC Address laptop pelanggan masih terbaca aktif di jaringan. Jika hilang, berarti perangkat pelanggan mati fisik atau kabel terlepas.

---

## 🛠️ SKILL-30: Tingkat Dua-Tiga Pele (Masalah Menengah Jaringan Lokal & Distribusi)
*   **Kategori:** Troubleshooting Segmen RT/RW Net & Kompatibilitas Kabel Distribusi
*   **Alat Kerja (Tools):** OPM (Optical Power Meter), CLI Switch (Loop Protect), Mikrotik IP Firewall Mangle.

### 1. Dinamika Lapangan (Akar Masalah)
Pada tingkat ini, masalah sudah melibatkan infrastruktur antar-tiang atau arsitektur lokal yang mulai kusut:
*   **Jebakan PoE Pasif Termakan Usia:** Teknisi RT/RW Net sering menyalurkan listrik switch lapangan menggunakan kabel LAN sisa (*PoE Extender*). Saat hujan atau cuaca panas, hambatan kabel naik, menyebabkan switch lapangan sering *restart* sendiri secara acak setiap jam 2 siang.
*   **Serangan IP Conflict Massal:** Ada pelanggan pintar yang membeli router tambahan di toko online, lalu memasang kabel dari port LAN router barunya langsung ke jaringan distribusi RT/RW Net tanpa mematikan fitur DHCP Server bawaan pabrik, mengakibatkan IP bocor (*IP Leaking*).

### 2. Logika Kerja & Langkah Solusi NOC
1.  **Isolasi Segmen Jaringan:** Matikan satu per satu interface rute ke arah wilayah RT/RW tertentu untuk melihat wilayah mana yang menjadi sumber kemacetan data.
2.  **Aktifkan Fitur Keamanan Switch:** Jalankan aturan `Bridge Filter` atau `IP DHCP Snooping` di switch/router utama agar port pelanggan dikunci dari luar dan tidak bisa menembakkan IP palsu ke tetangga sebelah.

---

## 🛠️ SKILL-31: Tingkat Berpele-Pele (Masalah Kompleks / Kerusakan Infrastruktur Pusat)
*   **Kategori:** Krisis Manajemen Data Center, Interferensi Frekuensi, & Redaman Drop Massal
*   **Alat Kerja (Tools):** OTDR Radar, DOM Telemetri via CLI OLT, WinBox Profile Tools, MXToolbox.

### 1. Dinamika Lapangan (Akar Masalah)
Ini adalah zona bahaya di mana ribuan pelanggan terancam mati internet secara bersamaan dan jam target kontrak SLA perusahaan berpacu mundur dengan cepat:
*   **Kabel Utama (Backbone) Putus Total:** Serat optik core utama di jalan raya putus akibat terkena galian proyek drainase, tertabrak truk kontainer, atau digigit tikus di dalam gorong-gorong bawah tanah.
*   **Ketimpangan Arsitektur Perangkat (x86 vs CCR Maut):** Ketika trafik RT/RW net melonjak di malam hari, driver kartu jaringan pada MikroTik berbasis PC (x86) mendadak tidak mampu menampung antrean paket data, memicu satu core prosesor melonjak 100% (*IRQ Sharing Overload*) sehingga internet melambat secara misterius ke seluruh kluster perumahan.
*   **Blacklist IP Publik Massal:** IP Publik utama ISP mendadak dicap kotor oleh sistem keamanan global, menyebabkan seluruh pelanggan di satu kota gagal total membuka aplikasi perbankan atau e-commerce aman (HTTPS Port 443).

### 2. Logika Kerja & Langkah Solusi NOC
1.  **Eksekusi Divide & Conquer Tercepat:** NOC menembakkan radar OTDR dari ruang server untuk mengukur di jarak kilometer ke berapa kabel optik tersebut terputus di jalan raya.
2.  **Manajemen Alur Kerja 3 Divisi:** NOC langsung menerbitkan *Broadcast Ticket* ke CS Admin untuk meredam komplain, sekaligus mengirimkan koordinasi GPS titik koordinat putus ke Tim Lapangan agar mereka bergerak membawa mesin **Fusion Splicer** ke lokasi yang tepat.
3.  **Buka Jalur Cadangan (Failover BGP/Static):** NOC mengalihkan rute lalu lintas internet utama ke arah link cadangan (*Backup ISP*) atau memindahkan segmen IP Publik yang kotor ke blok IP baru yang masih bersih via MXToolbox.

---

### 📊 LEMBAR CHECKLIST PROGRES GANGGUAN LAPANGAN
- [ ] Mampu memandu CS Admin menggunakan metode penuntunan cek lampu fisik modem pelanggan dari jarak jauh.
- [ ] Berhasil mendeteksi dan memblokir kebocoran server DHCP palsu (*Rogue DHCP*) pada topologi RT/RW Net.
- [ ] Sukses memimpin koordinasi krisis tingkat tinggi (menghitung kilometer kabel putus via OTDR dan menyuplai data broadcast ke CS) saat terjadi keadaan darurat massal.
