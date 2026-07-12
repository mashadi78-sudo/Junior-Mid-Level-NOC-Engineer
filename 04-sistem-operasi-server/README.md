# 📂 FASE 2: TELEMETRI & PERANGKAT MONITORING

## 🛠️ SKILL-12: Navigasi Dasar Server melalui Linux Command Line (CLI)
*   **Kategori:** Administrasi Sistem Operasi Server & Navigasi Teks
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** SSH Client (Putty / Terminal MacOS/Linux), Server Ubuntu / Debian Virtual (VirtualBox).

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Layanan pemantauan server (*Monitoring Tools*) mayoritas diinstal di atas sistem operasi Linux Server tanpa tampilan gambar grafis (GUI murni teks). Seorang NOC wajib lincah mengoperasikan terminal perintah hitam-putih (CLI) untuk memeriksa kesehatan internal mesin server pemantau itu sendiri agar sistem tidak buta. NOC harus paham cara memeriksa sisa ruang penyimpanan harddisk (karena jika harddisk server monitoring penuh, data grafik pemantauan akan mendadak berhenti merekam) serta melihat daftar aplikasi yang memakan memori terbesar.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka Putty, lakukan koneksi SSH menuju IP Linux Server. Gunakan perintah navigasi dasar `cd /var/log` untuk berpindah direktori dan `ls -la` untuk melihat daftar file tersembunyi beserta hak aksesnya.
2.  **Langkah Inti:** Jalankan perintah `df -h` untuk memeriksa kapasitas ruang penyimpanan harddisk (*disk space*). Jalankan perintah `free -m` untuk melihat sisa RAM server dalam satuan Megabytes.
3.  **Langkah Verifikasi:** Jalankan perintah `top` atau `htop` pada terminal untuk memantau aplikasi atau layanan (*process id*) apa saja yang sedang memakan utilitas memori dan CPU server tertinggi secara *real-time*.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Dasbor aplikasi pemantauan mendadak macet total tidak merekam data baru. Diduga sistem operasi server Linux mengalami kelebihan beban data sampah.
*   **Target Kelulusan:** Siswa wajib masuk via SSH, menemukan direktori mana yang kapasitas penyimpanannya sudah menyentuh angka 100% menggunakan perintah `df -h`, mencari file sampah terbesar, dan membersihkannya via CLI dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Lancar menggunakan perintah dasar navigasi berkas Linux CLI (`cd`, `ls`, `mkdir`, `rm`, `nano`) tanpa kesalahan.
- [ ] Berhasil membaca status kesehatan kapasitas penyimpanan harddisk (`df -h`) dan sisa memori RAM (`free -m`) pada Linux Server.
- [ ] Mampu mengidentifikasi proses sistem yang membebani server menggunakan utilitas perintah `top` atau `htop`.

---
---

## 🛠️ SKILL-13: Manajemen File Log Sistem & Pembacaan Syslog Severity Levels
*   **Kategori:** Analisis Catatan Sistem & Klasifikasi Tingkat Kedaruratan
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Perintah Linux CLI (`tail -f`, `grep`, `less`), File Direktori `/var/log/syslog`.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Setiap ada kejadian penting, error, atau pergantian status koneksi, sistem operasi dan perangkat jaringan akan menulis "buku harian" digital otomatis yang disebut **Syslog**. NOC wajib bisa membaca baris log ini langsung dari pusat data server untuk menemukan akar masalah kerusakan secara cepat. NOC wajib menghafal standar tingkat tingkat kedaruratan pesan log (*Syslog Severity Levels*):
*   `Level 0 - Emergency`: Sistem hancur/tidak bisa dipakai sama sekali.
*   `Level 1 - Alert`: Tindakan harus segera diambil saat itu juga.
*   `Level 2 - Critical`: Kondisi kritis pada aplikasi/perangkat keras.
*   `Level 3 - Error`: Terjadi kesalahan fungsi sistem (layanan web mati, dll).
*   `Level 4 - Warning`: Peringatan awal sebelum terjadi kerusakan sistem.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Masuk ke server Linux, navigasikan ke folder log utama menggunakan perintah `cd /var/log`.
2.  **Langkah Inti:** Jalankan perintah keramat `tail -f /var/log/syslog` untuk memantau aktivitas catatan sistem yang terus berjalan masuk secara *real-time*.
3.  **Langkah Verifikasi:** Gunakan kombinasi perintah penapis kata kunci, contoh: `grep -i "error" /var/log/syslog` atau `tail -n 100 /var/log/syslog | grep "interface"` untuk menyaring hanya baris pesan kesalahan tertentu yang ingin dilacak.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Instruktur secara sengaja mematikan layanan server web (Apache/Nginx) di latar belakang. Pengguna melaporkan aplikasi web bertuliskan error.
*   **Target Kelulusan:** Siswa harus mampu melacak penyebab matinya layanan tersebut dengan membaca baris pesan kegagalan (*failed/error message*) yang tertulis di dalam file Syslog via perintah `tail/grep` dan menyalakan kembali layanan tersebut dalam waktu < 5 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Mampu membedakan klasifikasi urgensi pesan berdasarkan standar tingkatan *Syslog Severity Levels* (0 s.d 7).
- [ ] Mahir menggunakan perintah pembaca teks dinamis (`tail -f`) untuk memantau aktivitas sistem jaringan secara langsung.
- [ ] Berhasil menggunakan perintah penyaring kata kunci (`grep`) untuk mempercepat pencarian baris pesan error pada file log yang tebal.
