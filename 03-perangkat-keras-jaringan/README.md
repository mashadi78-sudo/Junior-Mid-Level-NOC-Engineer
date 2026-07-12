# 📂 FASE 1: FONDASI JARINGAN FISIK & LOGIK

## 🛠️ SKILL-09: Manajemen Dasar Switch & Prinsip "Uji Perangkat Lokal Pertama"
*   **Kategori:** Konfigurasi Perangkat Switch & Deteksi Dini Kerusakan Lokal
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Cisco Packet Tracer / GNS3, Terminal CLI (Putty / SecureCRT), Switch Manageable.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Switch berfungsi membagi jaringan lokal (*LAN*) menjadi kelompok-kelompok kecil melalui sistem **VLAN (Virtual LAN)** agar keamanan data antar-divisi terjaga. NOC wajib menguasai konfigurasi *Access Port* (ke komputer user) dan *Trunk Port* (jalur pipa antar-switch/router).
*   **Prinsip Uji Perangkat Lokal Pertama (*Local First Testing*):** Saat menerima komplain internet lambat atau timpang (*upload/download unbalance*), seorang NOC tidak boleh langsung menyalahkan ISP luar. NOC wajib masuk ke CLI Switch lokal terdekat dan membaca data statistik error pada port tersebut. Jika parameter **`CRC Errors`**, **`FCS Errors`**, atau **`Rx Drop/Error`** melonjak tinggi, maka dipastikan masalahnya ada di konektor RJ45 lokal yang longgar/kotor.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka CLI Switch via Putty. Buat database VLAN baru, contoh: `vlan 10` nama "CS", dan `vlan 20` nama "Teknisi".
2.  **Langkah Inti:** Masuk ke spesifik interface port, set port user menjadi `switchport mode access` + `switchport access vlan 10`. Set port uplink menuju router menjadi `switchport mode trunk`.
3.  **Langkah Verifikasi:** Jalankan perintah `show interfaces counter error` atau `print stats` pada port switch aktif. Amati pergerakan angka pada kolom CRC Error untuk memastikan kualitas fisik kabel dan konektor RJ45 lokal bersih tanpa cacat sinyal elektrik.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Instruktur sengaja memasang kabel LAN yang konektor RJ45-nya cacat (pin RX longgar) sehingga komputer user mengalami trafik unduh hancur di bawah 1 Mbps. Siswa dilarang mencabut kabel fisik secara langsung di awal.
*   **Target Kelulusan:** Siswa wajib masuk ke CLI Switch, menemukan port mana yang mengalami masalah fisik kabel dengan membuktikan lonjakan statistik *CRC Error* yang terus bertambah, lalu memerintahkan tindakan perbaikan fisik (*crimping* ulang) hingga parameter *error* kembali menjadi `0` dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Berhasil mengonfigurasi VLAN, Access Port, dan Trunk Port pada Switch melalui perintah CLI secara mandiri.
- [ ] Menguasai prinsip "Uji Perangkat Lokal Pertama" sebelum melakukan penelusuran skala luas ke arah ISP luar.
- [ ] Mahir membaca statistik counter port Switch (`CRC Error`, `FCS Error`, `Rx/Tx Drop`) untuk mendeteksi RJ45 kotor secara digital.

---
---

## 🛠️ SKILL-10: Manajemen Router & Analisis Perbedaan Arsitektur Hardware (CCR vs x86)
*   **Kategori:** Konfigurasi Router, Manipulasi MTU/MSS, & Analisis Kinerja Hardware
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** MikroTik WinBox, VMware/VirtualBox (Simulasi MikroTik x86/CHR), Perintah CLI `/system resources cpu print`, `/ip route print`.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Router bertugas menghubungkan jaringan internal ke internet global menggunakan rute statis (*Static Route*) atau dinamis. NOC wajib memahami dua parameter krusial lapangan:
*   **Manipulasi MTU/MSS:** Situs perbankan yang super aman menolak paket data HTTPS (Port 443) yang pecah (*fragmented*). Jika nilai **MTU (Maximum Transmission Unit)** atau **MSS (Maximum Segment Size)** pada Router salah dikonfigurasi, situs perbankan tidak akan bisa terbuka sama sekali. NOC harus bisa menyetel MTU/MSS secara presisi di Router.
*   **Jebakan Perbedaan Arsitektur Hardware (CCR vs x86):** MikroTik tipe **CCR (Cloud Core Router)** menggunakan arsitektur prosesor multi-core pabrikan (ARM/Tile) yang memiliki puluhan core kecil untuk membagi beban lalu lintas (*interrupt handling*). Sebaliknya, MikroTik versi **x86 / CHR** diinstal di atas arsitektur PC biasa. Jika fitur akselerasi perangkat keras (*FastPath/Hardware Offloading*) mati atau driver kartu jaringan (NIC) tidak kompatibel di x86, **satu core CPU x86 bisa mendadak loncat 100% (*CPU core starvation*) menyebabkan jaringan macet total**, sementara core lainnya menganggur.
*   **Default Gateway Perangkat Akhir (OLT):** Saat mengonfigurasi jalur kontrol jarak jauh untuk **OLT**, OLT tersebut wajib disuntik aturan *Default Gateway* yang mengarah tepat ke IP Router Utama agar paket data balasan dari OLT tahu jalan pulang ke laptop NOC dan tidak terjadi masalah *asymmetric routing* (gagal remote dari publik).

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buat rute keluar internet menggunakan perintah `/ip route add gateway=[IP_ISP]`. Sediakan jalur IP Publik/VPN menuju ke IP Management perangkat OLT lapangan.
2.  **Langkah Inti:** Konfigurasikan aturan perubahan ukuran paket data HTTPS pada menu IP Firewall Mangle: `change MSS` menjadi `1300` pada interface internet (*change-mss=yes new-mss=1300*).
3.  **Langkah Verifikasi:** Pantau pembagian beban prosesor komputer melalui WinBox (Menu *Tools -> Profile* atau perintah `/system resources cpu print`). Pastikan seluruh core CPU pada arsitektur x86/CCR terbagi rata beban kerjanya saat dilewati trafik data besar tanpa ada satu core pun yang menyentuh angka 100%.

### 3. SKENARIO UJI KEMAMPUAN (UJIAN GERBANG FASE 1)
*   **Kondisi Ujian:** Siswa diberikan simulator jaringan lab berisi Router x86 dan perangkat OLT. Jaringan bisa terhubung (ping aman), tetapi OLT tidak bisa di-remote dari luar kantor (publik), dan komputer internal gagal total membuka website aman HTTPS perbankan akibat satu core CPU Router mendadak melonjak 100%.
*   **Target Kelulusan:** Siswa wajib menyeimbangkan beban *interrupt* CPU core pada x86, menyetel Default Gateway yang benar pada sistem internal OLT agar rute balik aman, serta menyetel aturan MTU/MSS pada firewall Router hingga akses remote OLT publik aktif dan situs perbankan terbuka lancar dalam waktu maksimal 20 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Berhasil mengonfigurasi rute statis (*Static Route*) dan jalur Default Gateway pada Router dan OLT dengan benar.
- [ ] Menguasai konfigurasi perubahan nilai MTU/MSS pada firewall Router untuk mengatasi masalah web perbankan macet.
- [ ] Mampu menganalisis dan mengatasi masalah ketimpangan beban prosesor (*CPU core starvation*) akibat perbedaan arsitektur hardware CCR vs x86.
