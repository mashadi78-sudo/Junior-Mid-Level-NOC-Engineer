# 📂 FASE 0: FONDASI UTAMA & EKOSISTEM KERJA

## 🛠️ SKILL-01: Penguasaan Standar Dokumentasi dengan Markdown (`.md`)
*   **Kategori:** Perangkat Lunak & Standarisasi Dokumentasi Teknis
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Editor VS Code (Markdown Preview), Berkas Mentah Logbook Lapangan.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Saat terjadi gangguan jaringan, staf NOC wajib mencatat kronologi perbaikan dengan format yang cepat diketik namun sangat mudah dibaca oleh manajemen. Markdown (`.md`) dipilih karena tidak membutuhkan *mouse* untuk mengatur ukuran huruf atau menebalkan teks. Staf NOC cukup menghafal beberapa simbol teks ("simbol keramat") berikut:

*   **Judul & Sub-Judul:** Menggunakan simbol pagar (`#`). Jumlah pagar menentukan ukuran (contoh: `#` untuk Judul Utama Modul, `##` untuk Nama Skill, `###` untuk Sub-Bab).
*   **Penekanan Penting:** Menggunakan tanda bintang ganda (`**teks**`) untuk menghasilkan cetak **Tebal**. Sangat vital untuk menandai status krusial seperti kata **CRITICAL** atau **DOWN**.
*   **Format Tabel:** Menggunakan garis tegak (`|`) dan garis hubung (`-`) untuk merapikan daftar parameter redaman atau alamat IP perangkat agar terlihat presisi.
*   **Blok Perintah CLI:** Menggunakan tanda petik terbalik sebanyak tiga buah (```) untuk mengurung baris teks perintah konfigurasi dari router/switch agar tidak bercampur dengan teks penjelasan biasa.
*   **Kotak Centang (Checklist):** Menggunakan format `- [ ]` untuk kotak kosong, dan `- [x]` untuk kotak yang sudah terisi silang (tanda lulus).

---

### 2. TAHAP DEMI TAHAP PRAKTIK (Langkah Mandiri Siswa)
1.  **Langkah Awal:** Siswa membuka teks editor **VS Code** di laptop masing-masing, membuat file baru bernama `latihan-markdown.md`, lalu mengaktifkan fitur *Markdown Preview* (tombol ikon belah ketupat/layar di pojok kanan atas VS Code) untuk melihat hasil visualnya secara langsung.
2.  **Langkah Inti:** Siswa berlatih mengetik teks laporan tiruan dengan menyertakan format kombinasi: membuat judul gangguan, menebalkan status perangkat yang mati, memasukkan tabel pembagian IP, dan menyalin contoh baris perintah teks dari terminal router.
3.  **Langkah Verifikasi:** Siswa memeriksa layar *Preview* untuk memastikan seluruh kode simbol pagar, bintang, dan tabel yang diketik manual di layar kiri sudah berubah menjadi dokumen visual yang rapi di layar kanan tanpa ada kode simbol yang bocor atau hancur formatnya.

---

### 3. SKENARIO UJI KEMAMPUAN (Ujian Kelulusan Gerbang)
*   **Kondisi Ujian:** Instruktur memberikan selembar teks ketikan WhatsApp berantakan dari teknisi lapangan: 
    > *"Laporan gangguan mas jumat jam 10 pagi internet putus di router core 1 gara-gara sfp overheat suhu 85 derajat celcius tindakan lapangan ganti sfp baru merek cisco panjang gelombang 1310nm status jam 11 siang link sudah up kembali redaman normal di angka -18dbm"*
*   **Target Kelulusan:** Siswa wajib menyusun kembali pesan berantakan di atas ke dalam format file Markdown resmi dalam waktu < 10 menit dengan ketentuan: wajib menggunakan judul waktu kejadian, menggunakan tabel parameter teknis untuk SFP baru, dan status akhir wajib dicetak tebal (**LINK UP**).

---

### 📊 LEMBAR CHECKLIST PROGRES (Kriteria Centang Kelulusan)
- [ ] Mampu menuliskan struktur Judul (`#`), Sub-Judul (`##`), dan penekanan teks tebal (`**`) tanpa melihat panduan catatan.
- [ ] Berhasil membuat format tabel parameter dan blok kode teks CLI secara rapi dan presisi menggunakan sintaks Markdown.
- [ ] Sukses lulus ujian mengubah teks logbook berantakan menjadi laporan insiden terstruktur yang siap dibaca oleh pihak manajemen perusahaan.



---

## 🛠️ SKILL-02: Manajemen Kode dan Kontrol Versi dengan Git & GitHub
*   **Kategori:** Perangkat Lunak & Sistem Kontrol Versi (*Version Control System*)
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Aplikasi Git CLI (Terminal), Akun GitHub Pribadi Peserta, Editor VS Code.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Di dunia nyata, seorang staf NOC sering kali harus memperbarui naskah otomatisasi (*script automation*) atau berkas konfigurasi secara bersamaan dengan tim lain. Agar file tersebut tidak saling menimpa atau hilang, jika dikerjakan bersama, industri menggunakan sistem bernama **Git**. GitHub adalah pelayan *cloud* terpusatnya. Peserta wajib memahami 5 perintah "keramat" Git berikut beserta fungsinya secara mendalam:

*   **`git clone [link]`**: Perintah untuk mendownload/menyalin folder proyek utama dari GitHub instruktur ke laptop lokal peserta (cukup dilakukan 1 kali di awal pelatihan).
*   **`git status`**: Alat pemeriksa layar. Digunakan untuk melihat berkas apa saja yang baru dibuat atau diubah di laptop peserta sebelum dikirim ke pusat.
*   **`git add [nama_file]`**: Memasukkan file ke dalam "antrean" (*staging area*). Mengindikasikan bahwa file tersebut siap dibungkus untuk dikirim.
*   **`git commit -m "[pesan]"`**: Membungkus antrean file dan memberikan label catatan permanen tentang apa perubahan yang dilakukan.
*   **`git push origin main`**: Gerbang pengiriman utama. Menembakkan dan mengunggah berkas yang sudah dibungkus dari laptop lokal peserta menuju server GitHub terpusat milik instruktur.

---

### 2. TAHAP DEMI TAHAP PRAKTIK (Langkah Mandiri Siswa)
1.  **Langkah Awal**: Siswa membuka Terminal/Command Prompt di laptopnya yang sudah terinstal Git, lalu mengetik perintah `git clone https://github.com` untuk menyalin repositori kelas Anda ke komputer mereka.
2.  **Langkah Inti**: Siswa masuk ke folder tersebut via VS Code. Di dalam folder `peserta/`, siswa membuat satu file mandiri menggunakan nama mereka sendiri (contoh: `peserta/budi-setiawan.md`) dan mengisi checklist kemajuan mereka di sana.
3.  **Langkah Verifikasi**: Siswa membuka Terminal VS Code mereka, lalu mengetikkan rentetan perintah keramat secara berurutan:
    ```bash
    git status
    git add .
    git commit -m "Menambahkan file progress atas nama Budi"
    git push origin main
    ```
    Siswa membuka browser dan memastikan file nama mereka sudah muncul di server GitHub instruktur tanpa ada pesan error di terminal.

---

### 3. SKENARIO UJI KEMAMPUAN (Ujian Kelulusan Gerbang)
*   **Kondisi Ujian**: Siswa diminta melakukan simulasi pembaruan data secara langsung di lab. Mereka harus membuka kembali file nama mereka masing-masing di laptop lokal, mengubah satu tanda centang kotak kosong `[ ]` menjadi `[x]`, lalu mengirimkannya ulang ke server GitHub pusat.
*   **Target Kelulusan**: Berkas pembaruan tersebut wajib terunggah ke repositori GitHub instruktur dalam waktu < 3 menit tanpa memicu error otentikasi perizinan (*permission error*) atau konflik kode (*merge conflict*).

---

### 📊 LEMBAR CHECKLIST PROGRES (Kriteria Centang Kelulusan)
- [ ] Memahami fungsi alur kerja berkas Git (*Working Directory* -> *Staging Area* -> *Local Repository* -> *Remote Repository*).
- [ ] Mampu mengesekusi perintah `git clone`, `git status`, `git add`, dan `git commit` melalui terminal teks (CLI) tanpa bantuan grafik (GUI).
- [ ] Sukses melakukan `git push` tugas mandiri dari komputer lokal dan berhasil muncul di dasbor repositori pusat instruktur dengan aman.
