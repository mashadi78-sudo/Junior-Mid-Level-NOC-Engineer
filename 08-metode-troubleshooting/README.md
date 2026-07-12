# 📂 FASE 3: TATA KELOLA INSIDEN & LOGIKA TROUBLESHOOTING

## 🛠️ SKILL-22: Strategi Isolasi Masalah dengan Metode Divide & Conquer
*   **Kategori:** Logika Pelacakan Kerusakan & Utilitas Diagnosa Jalur Rute
*   **Estimasi Waktu Kuasai:** 2 Hari
*   **Alat Kerja (Tools):** Perintah CLI `ping -t` (Continuous Ping), `traceroute` / `tracert`, `mtr` (My Traceroute) Penganalisis Jalur Dinamis.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Saat terjadi kepanikan atau kondisi stagnan di mana Anda kebingungan tidak tahu di mana lokasi kabel yang putus atau alat yang rusak, dilarang keras menebak secara acak. Gunakan taktik militer **Divide & Conquer (Bagi dan Kuasai)**. Potong jalur arsitektur topologi jaringan menjadi dua bagian tepat di tengah-tengah untuk mempersempit area pencarian.
*   **Isolasi Jalur Rute via MTR/Traceroute:** Jalankan perintah `mtr` atau `traceroute` menuju ke alamat server tujuan internet. Alat ini akan menampilkan daftar seluruh alamat IP lompatan gerbang router (*Hops*) yang dilewati paket data. Perhatikan dengan teliti di baris nomor IP *Hop* keberpakan tanda bintang (`* * *`) atau status lompatan mulai terputus total menjadi RTO. Angka IP rute terakhir yang sukses merespons sebelum tanda bintang tersebut adalah koordinat lokasi perangkat terakhir yang hidup. Dengan data ini, NOC bisa langsung menyimpulkan dengan teliti: *"Masalah bukan di internal kita, melainkan di dalam jaringan router milik pihak ketiga/Vendor ISP eksternal."*

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Buka Command Prompt/Terminal. Ketik perintah `ping -t 8.8.8.8` untuk memantau kestabilan koneksi internet secara terus-menerus tanpa henti.
2.  **Langkah Inti:** Buka terminal baru, jalankan perintah diagnosa rute mendalam: `mtr google.com` atau `traceroute google.com`. Perhatikan persentase kolom Loss (%) pada tiap tingkatan lompatan IP gerbang (*Hop*).
3.  **Langkah Verifikasi:** Jika terjadi putus koneksi, analisis baris angka IP terakhir yang masih memberikan respons milidetik (ms). Segera buka dokumen peta topologi untuk mencocokkan siapa pemilik alat dengan IP tersebut untuk langsung diisolasi masalahnya.

### 3. SKENARIO UJI KEMAMPUAN
*   **Kondisi Ujian:** Instruktur secara sengaja merusak konfigurasi sistem tabel routing pada salah satu switch core di jalur tengah simulator tersembunyi sehingga koneksi internet mati total. Siswa tidak diberikan gambar peta jaringan.
*   **Target Kelulusan:** Siswa wajib menembakkan perintah `traceroute/mtr` dari komputer klien, melacak pergerakan urutan lompatan paket data, menganalisis baris angka IP terakhir, menemukan dengan tepat di perangkat nomor berapa jaringan tersebut mengalami putus rute, dan menunjukkannya kepada instruktur dalam waktu < 10 menit.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Menguasai logika berpikir strategi pelacakan masalah menggunakan metode pemotongan jalur tengah (*Divide & Conquer*).
- [ ] Mahir membaca dan menginterpretasikan hasil output lompatan data (*Hops Analysis*) pada perintah `traceroute` atau `tracert`.
- [ ] Berhasil menggunakan alat diagnosa dinamis `mtr (My Traceroute)` untuk mendeteksi letak lokasi penurunan performa kehilangan paket data (*Packet Loss Intermittent*).

---
---

## 🛠️ SKILL-23: Analisis Perubahan (Rollback) & Penentuan Matriks Eskalasi (Aturan 15 Menit)
*   **Kategori:** Manajemen Pemulihan Konfigurasi & Batas Waktu Operasional L1 ke L2
*   **Estimasi Waktu Kuasai:** 1 Hari
*   **Alat Kerja (Tools):** Berkas Salinan Cadangan Konfigurasi Sistem (`.backup` / `.cfg` text file), Dokumen Matriks Daftar Kontak Vendor/ISP & Senior Engineer L2/L3.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
*   **Taktik Rollback Konfigurasi:** 90% gangguan jaringan terjadi bukan karena alat tua atau tersambar petir, melainkan akibat adanya kesalahan manusia (*Human Error* seperti salah mengetik aturan perintah di router) yang dilakukan oleh teknisi sejam yang lalu. Saat jaringan mendadak mati pasca-konfigurasi, hentikan tebakan rumit. Segera lakukan **Rollback** (Kembalikan ke berkas salinan konfigurasi terakhir yang terbukti berjalan normal 100%).
*   **Aturan Eskalasi 15 Menit:** Staf NOC tingkatan dasar (L1) bertindak sebagai garda terdepan penahan badai. Anda memiliki batas kemampuan. Kontrak SLA terus berjalan mendesak mundur. Industri menerapkan **Aturan 15 Menit**: Jika dalam waktu 15 menit Anda sudah mencoba melacak masalah secara mandiri dan otak Anda mengalami *stagnan / buntu / bingung* tidak menemukan solusi, **Anda dilarang keras mendiamkannya saja karena takut**. Anda wajib menyerahkan tiket tersebut ke tingkatan di atas Anda (**Eskalasi ke Network Engineer L2/L3 atau Vendor ISP**). Saat melapor eskalasi, laporkan secara profesional beserta data pembuktian awal yang sudah Anda kumpulkan agar tim L2 bisa langsung mengeksekusi perbaikan tanpa mengulang pertanyaan dari nol.

### 2. TAHAP DEMI TAHAP PRAKTIK
1.  **Langkah Awal:** Biasakan melakukan pembuatan berkas cadangan harian otomatis pada router sebelum mengubah sistem via perintah `/system backup save name=konfigurasi_aman`.
2.  **Langkah Inti:** Jika terjadi error pasca-ketik, langsung lakukan pemulihan instan via perintah `/system backup load name=konfigurasi_aman` untuk mengembalikan jaringan ke kondisi normal asal dalam hitungan detik.
3.  **Langkah Verifikasi:** Jika masalah di luar kendali Anda, buka dokumen *Escalation Matrix Contact List*. Hubungi Senior L2 via telepon/pesan internal menggunakan format pelaporan baku, contoh:
    > *"Mas, internet Gedung B putus total (SLA tersisa 45 menit). Saya sudah cek fisik switch lokal aman, hasil traceroute mentok berhenti di IP Router Utama luar. Saya stagnan di rute eksternal tersebut, mohon bantuan eskalasi penanganan L2."*

### 3. SKENARIO UJI KEMAMPUAN (UJIAN AKHIR KELULUSAN / BLIND TEST)
*   **Kondisi Ujian:** Instruktur merusak 3 buah titik konfigurasi krusial yang berbeda secara acak pada jaringan lab tanpa memberi tahu siswa. Jam timer SLA digital dinyalakan selama 30 menit mundur. Suasana disimulasikan penuh tekanan suara alarm berbunyi merah.
*   **Target Kelulusan:** Siswa wajib bekerja tenang menggunakan logika deduktif: menyelesaikan masalah yang mampu diselesaikan lewat metode uji lokal pertama atau rollback, dan mendemonstrasikan tindakan eskalasi yang cepat dan tepat ke tim L2/Vendor ISP saat pelacakan menemui jalan buntu dalam batas waktu total 30 menit sebelum status SLA pecah melanggar kontrak bisnis.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Mahir melakukan pembuatan berkas cadangan (*Backup*) dan pemulihan konfigurasi (*Rollback*) secara cepat saat terjadi kesalahan ketik sistem.
- [ ] Memahami batas waktu penanganan mandiri dan patuh menerapkan Aturan 15 Menit eskalasi demi menyelamatkan kontrak waktu SLA perusahaan.
- [ ] Mampu menyusun dan menyampaikan laporan eskalasi gangguan ke tingkat Senior Engineer (L2/L3) atau pihak ketiga Vendor ISP secara taktis, padat data, dan profesional.

---
---

## 🛠️ SKILL-24 & 25: Soft-Skills: Manajemen Krisis Tekanan & Etika Kerja Shift
*   **Kategori:** Ketahanan Mental Ruang Monitor & Kedisiplinan Operasional 24/7
*   **Estimasi Waktu Kuasai:** Sepanjang Pelatihan
*   **Alat Kerja (Tools):** Buku Panduan Darurat Krisis Jaringan (*Incident Response Playbook*), Aplikasi Presensi Kehadiran Geofencing.

### 1. APA YANG HARUS DIPAHAMI? (Kedalaman Materi)
Keahlian mengetik baris kode tercanggih di dunia tidak akan berguna jika staf NOC mentalnya mudah panik, berteriak, atau stres saat ruang monitor dihujani ratusan alarm menyala merah tua secara bersamaan. NOC profesional dilatih untuk memiliki ketahanan mental tinggi (*Stress Management*). Saat kondisi krisis darurat massal terjadi, tenangkan pikiran, tarik napas, buka dokumen **Incident Response Playbook**, lalu ikuti instruksi tertulis di sana langkah demi langkah dengan kepala dingin tanpa melibatkan emosi panik. Selain itu, pilar utama ruang NOC 24/7 adalah **Disiplin Waktu Hadir**. Datang terlambat 10 menit saat pergantian kerja shift bukan sekadar masalah pelanggaran absen biasa, melainkan tindakan melanggar etika profesi yang membuat rekan kerja *shift* sebelumnya kelelahan dan merusak konsentrasi pengawasan infrastruktur vital negara.

### 📊 LEMBAR CHECKLIST PROGRES
- [ ] Mampu menjaga kestabilan emosi, tetap tenang, fokus mencari solusi, dan tidak ikut panik saat menghadapi rentetan alarm gangguan massal.
- [ ] Patuh mengikuti instruksi baku dokumen langkah darurat tertulis (*Playbook Guidelines*) tanpa mengambil tindakan tebakan berisiko sendiri.
- [ ] Menjaga kedisiplinan tinggi waktu kehadiran serah terima kerja *shift* demi menjaga kelancaran operasional ruang komando NOC tanpa celah kekosongan pengawasan.
