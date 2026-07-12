# 📂 FASE 2: TELEMETRI & PERANGKAT MONITORING

## 🛠️ SKILL-16: Implementasi Dasbor Pemantauan (Zabbix/PRTG) & Strategi Sensor OLT
*   **Kategori:** Integrasi Aset Monitoring & Pemisahan Logika Sensor Kerusakan
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Zabbix Web UI, PRTG Network Monitor, Perangkat Infrastruktur Pusat (**OLT**), Sensor ICMP & SNMP.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
NOC tidak boleh mengecek router satu per satu. Seluruh aset komputer, switch, router, hingga **OLT (Optical Line Terminal)** wajib didaftarkan ke dalam satu aplikasi dasbor terpusat (**Zabbix** atau **PRTG**). 
*   **Taktik Membedah Kasus Remote OLT via Sensor:** Kasus misterius yang sering terjadi di industri ISP adalah perangkat OLT lapangan tiba-tiba tidak bisa di-remote secara publik dari kantor NOC. NOC harus cerdas menggabungkan dua logika sensor monitoring: **Sensor ICMP (Ping)** dan **Sensor SNMP**.
    *   Jika status sensor PING = **UP (Hijau)**, tetapi sensor SNMP = **DOWN (Merah)**: Kesimpulannya, mesin fisik OLT masih hidup normal di lapangan dan ribuan layanan internet pelanggan di bawahnya aman. Yang rusak hanyalah aplikasi remote manajemennya (*service crash* atau terblokir firewall internal OLT). NOC tidak perlu panik mengirim teknisi lapangan, cukup lakukan *restart service remote* atau periksa jalur VPN.
    *   Jika kedua sensor PING dan SNMP = **DOWN (Merah)** bersamaan: Kesimpulannya, perangkat OLT mati total fisik (mati lampu gardu atau kabel suplai utama putus). NOC wajib segera menerbitkan tiket darurat krisis.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka Zabbix Web UI, masuk ke menu *Configuration -> Hosts -> Create Host*. Masukkan nama dan nomor IP Address dari OLT atau Router target.
2.  **Langkah Inti:** Pasangkan template monitoring bawaan (*Template Net Device SNMP* atau *ICMP Ping*). Masukkan kunci kecocokan *SNMP Community String* yang sesuai dengan perangkat.
3.  **Langkah Verifikasi:** Buka menu *Monitoring -> Latest Data*. Perhatikan apakah grafik nilai ketersediaan (*Availability*), kecepatan respons (*Latency*), dan persentase kehilangan paket data (*Packet Loss*) sudah sukses meluncur masuk ke layar monitor dasbor.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Instruktur secara sengaja mensimulasikan gangguan pada perangkat OLT simulasi di mana jalur SSH/manajemennya dimatikan, namun jalur data pelanggan tetap dihidupkan. Alarm dasbor menyala.
*   **Target Kelulusan:** Siswa harus mampu membaca analisis kombinasi status sensor di dasbor Zabbix/PRTG, menarik kesimpulan yang tepat bahwa OLT tidak mati fisik melainkan hanya kehilangan akses remote manajemennya saja, dan menuliskan rekomendasi solusi penanganan yang benar dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Berhasil mendaftarkan aset perangkat jaringan baru ke dalam dasbor monitoring Zabbix atau PRTG dari nol.
- [ ] Mampu menganalisis kombinasi sensor ICMP (Ping) dan SNMP untuk membedakan kasus kerusakan sistem manajemen dengan kasus perangkat mati total fisik.
- [ ] Mahir membaca dan menginterpretasikan grafik parameter penting jaringan (*Latency*, *Packet Loss*, dan *Interface Traffic*).

---
---

## 🛠️ SKILL-17: Manajemen Alarm, Penentuan Ambang Batas (Threshold), & Notifikasi Otomatis
*   **Kategori:** Manajemen Peringatan Sistem & Konfigurasi Integrasi Bot Notifikasi
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Grafana Alerts / Zabbix Triggers, Telegram Bot API atau Discord Webhook, Smartphone.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Layar monitoring penuh grafik tidak akan berguna jika staf NOC sedang lengah atau tertidur saat *shift* malam. Sistem wajib dikonfigurasi agar bisa berteriak sendiri saat terjadi bahaya melalui sistem **Trigger & Threshold (Ambang Batas)**. NOC harus tahu cara menyetel aturan logika: *"Jika parameter Packet Loss di atas 10% selama 3 menit berturut-turut, atau CPU Router melonjak di atas 90%, ubah status menjadi WARNING/CRITICAL."* Perubahan status ini dikonfigurasi agar otomatis menembak server pesan luar (Telegram/Discord) untuk membunyikan alarm di ponsel staf NOC secara instan sebelum ada pelanggan yang menelpon marah.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Masuk ke menu pengaturan *Triggers* pada aplikasi monitoring. Buat aturan formula logika ambang batas baru untuk sensor CPU atau tautan port interface.
2.  **Langkah Inti:** Buat sebuah akun bot di Telegram via @BotFather untuk mendapatkan kode kunci *API Token* khusus, atau buat jalur link *Webhook* pada saluran grup Discord tim NOC.
3.  **Langkah Verifikasi:** Hubungkan sistem pembuat alarm monitoring (*Media Types / Action*) dengan API Token Telegram tersebut. Lakukan simulasi pemutusan jalur kabel port target, lalu pastikan ponsel Anda menerima pesan notifikasi otomatis masuk bertuliskan: `🚨 CRITICAL: CORE-ROUTER PORT 1 IS DOWN!`.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Terjadi lonjakan suhu ruangan rak server data center secara ekstrem akibat AC mati di tengah malam. Sensor suhu merekam angka naik melewati batas normal, tetapi bot alarm Telegram tidak berbunyi karena kesalahan ketik kode API token.
*   **Target Kelulusan:** Siswa wajib menelusuri letak kegagalan pengiriman notifikasi pada menu log integrasi aplikasi monitoring, memperbaiki pengetikan kode integrasi bot, dan membuktikan bot Telegram berhasil mengirimkan alarm tanda bahaya suhu panas dalam waktu < 10 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami formula logika penentuan batas peringatan (*Trigger Expression & Threshold*) pada sistem pemantauan.
- [ ] Berhasil membuat bot notifikasi otomatis menggunakan jalur Telegram Bot API atau Discord Webhook.
- [ ] Sukses mengintegrasikan sensor monitoring dengan bot pesan otomatis sehingga alarm bahaya bisa berbunyi mandiri di ponsel pintar.

---
---

## 🛠️ SKILL-18: Analisis Paket Data Menggunakan Wireshark (Packet Sniffing)
*   **Kategori:** Pembedahan Paket Data Mentah & Identifikasi Anomali Transmisi
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Perangkat lunak Wireshark (GUI), Utilitas Perintah `tcpdump` pada CLI Linux Server, Berkas Berformat `.pcap`.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Ketika grafik monitoring menunjukkan pemakaian *bandwidth* penuh, namun NetFlow tidak bisa mendeteksi asal aplikasinya, senjata pamungkas terakhir seorang NOC adalah melakukan **Packet Sniffing (Menangkap paket data mentah di udara)** menggunakan aplikasi **Wireshark** atau perintah **`tcpdump`**. Seluruh lalu lintas data yang lewat di dalam kabel disalin dan dibedah isi kepalanya (*packet header*). NOC profesional harus bisa membaca warna baris data pada Wireshark dan mahir menggunakan fitur *Filter* untuk menyaring sampah data agar bisa mendeteksi anomali seperti adanya serangan banjir data siber (*DDoS/SYN Flood*) yang menyumbat jalur pipa internet.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka Wireshark di laptop Anda, pilih kartu jaringan (*Network Interface*) aktif yang sedang menyalurkan internet, lalu klik tombol sirip hiu biru untuk mulai menangkap paket data (*Start Capture*).
2.  **Langkah Inti:** Biarkan sistem merekam ribuan baris data yang lewat. Masukkan kode penyaring pada kolom filter atas, contoh: ketik `http` untuk menyaring hanya lalu lintas web biasa, atau ketik `ip.addr == 192.168.1.50` untuk melihat aktivitas satu komputer tertentu saja.
3.  **Langkah Verifikasi:** Gunakan fitur *Follow TCP Stream* (Klik kanan pada baris paket -> *Follow -> TCP Stream*) untuk membaca isi percakapan teks asli antara komputer klien dengan server tujuan internet.

### 3. SKENARIO UJI KEMAMPUAN (UJIAN GERBANG FASE 2)
*   **Kondisi Ujian:** Jaringan internal kantor mendadak lambat total secara misterius. Diduga ada satu server lokal yang sedang dibombardir oleh serangan siber paket palsu massal dari dalam gedung sendiri. Siswa diberikan file mentah hasil tangkapan berformat `.pcap`.
*   **Target Kelulusan:** Siswa wajib membuka file tersebut menggunakan Wireshark, menggunakan fitur filter pencarian yang tepat untuk mengisolasi ribuan paket sampah, menemukan IP komputer pelaku penyerang dan mendeteksi jenis serangannya dalam waktu maksimal 15 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Memahami fungsi dasar penangkapan paket data mentah jaringan (*Packet Sniffing*) via Wireshark atau perintah `tcpdump`.
- [ ] Mahir menggunakan sintaks filter pencarian Wireshark untuk membuang lalu lintas sampah dan mempercepat isolasi masalah.
- [ ] Mampu membaca struktur data isi paket (*TCP Stream*) untuk mendeteksi anomali transmisi data atau indikasi serangan siber.
