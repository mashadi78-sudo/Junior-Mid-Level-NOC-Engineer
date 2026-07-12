# 📂 FASE 0: FONDASI UTAMA & EKOSISTEM KERJA

## 🛠️ SKILL-00: Pengenalan Alat Kerja Jaringan & Segitiga Komunikasi (NOC - CS - Teknisi)
*   **Kategori:** Wawasan Operasional & Koordinasi Ekosistem Jaringan
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Lembar Alur Kerja (Flowchart Koordinasi), Skenario Krisis Lapangan.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Seorang staf NOC tidak bekerja sendirian di dalam menara gading. NOC adalah pusat komando yang menghubungkan **Tim Depan (CS Admin)** dan **Tim Lapangan (Teknisi)**. NOC wajib memahami fungsi alat kerja mitra mereka agar koordinasi berjalan presisi:

*   **Ekosistem Mitra Teknisi Lapangan (Fisik):** 
    *   **Fusion Splicer:** Alat untuk menyambung inti kaca kabel Fiber Optic (FO) yang putus dengan cara dilelehkan menggunakan busur api listrik. NOC wajib tahu bahwa sambungan yang baik harus menghasilkan redaman (*loss*) **di bawah 0.02 dB**.
    *   **OTDR (Optical Time Domain Reflectometer):** Alat radar untuk mengukur jarak kabel FO. Jika kabel putus di tengah jalan, teknisi menembakkan alat ini, dan layarnya akan menampilkan jarak pasti titik putus tersebut (misal: "Putus di kilometer 3.2"). NOC menggunakan data kilometer ini untuk mencocokkannya dengan peta jalur kabel.
*   **Ekosistem Mitra CS Admin / Helpdesk (Garda Depan):**
    *   **CRM (Customer Relationship Management):** Aplikasi tempat CS menerima ribuan keluhan dan telepon panik pelanggan saat internet mati.
    *   **Peran NOC:** Saat krisis, CS Admin mengalami tekanan mental tinggi dari pelanggan. Tugas NOC adalah mengirimkan informasi teknis yang padat dan jelas (contoh: *"Terjadi kabel putus akibat proyek jalan di KM 3, estimasi perbaikan 2 jam"*). Informasi ini disebut **Broadcast Ready Ticket**, yang bisa langsung disalin CS untuk menjawab komplain massal agar jawaban ke pelanggan seragam dan tidak ada janji palsu.

---

### 2. TAHAP DEMI TAHAP PRAKTIK (Langkah Mandiri Siswa)
1.  **Langkah Awal:** Siswa mempelajari diagram alur komunikasi segitiga: `Keluhan Pelanggan -> Masuk CRM CS -> Diisolasi oleh NOC -> Perbaikan oleh Teknisi Lapangan -> Verifikasi Akhir oleh NOC`.
2.  **Langkah Inti:** Siswa berlatih mensimulasikan peran sebagai NOC yang menerima laporan dari teknisi di lapangan: *"Mas, saya sudah tembak pakai OTDR, kabel putus di jarak 1.5 KM ke arah gardu B. Tim lapangan sedang siap-siap bawa Fusion Splicer ke lokasi."*
3.  **Langkah Verifikasi:** Siswa sebagai NOC harus mengonversi laporan teknisi tersebut menjadi kalimat singkat, lalu mengirimkannya ke tim CS Admin sebagai pemberitahuan resmi agar CS bisa meredam komplain pelanggan yang terdampak di area Gardu B.

---

### 3. SKENARIO UJI KEMAMPUAN (Ujian Kelulusan Gerbang)
*   **Kondisi Ujian:** Instruktur memberikan skenario krisis darurat: *"Kabel utama ke arah Cluster Perumahan A putus total karena tersangkut alat berat proyek. CS Admin mulai dihujani 50 telepon komplain dalam waktu 5 menit."*
*   **Target Kelulusan:** Siswa wajib menyusun instruksi kerja dengan durasi maksimal 5 menit:
    1. Alat apa yang harus diperintahkan NOC untuk dibawa oleh teknisi lapangan? (Jawaban wajib: *OTDR dan Fusion Splicer*).
    2. Buatkan 2 baris kalimat teks *Broadcast Ready* yang harus segera dikirimkan NOC ke grup CS Admin agar mereka tahu apa yang harus dijawab ke pelanggan perumahan tersebut.

---

### 📊 LEMBAR CHECKLIST PROGRES (Kriteria Centang Kelulusan)
- [ ] Mampu menjelaskan alur koordinasi 3 arah antara NOC, CS Admin, dan Teknisi Lapangan tanpa tertukar peran.
- [ ] Memahami fungsi alat kerja lapangan (Fusion Splicer & OTDR) serta standar nilai redaman sambungan yang layak (< 0.02 dB).
- [ ] Berhasil menyusun teks informasi krisis jaringan (*Broadcast Ticket*) yang siap pakai untuk membantu tugas CS Admin di gardu depan.
