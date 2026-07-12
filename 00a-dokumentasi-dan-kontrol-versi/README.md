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
