# Product Requirements Document (PRD) — NotaSteam

**Versi:** 1.0  
**Tanggal sumber:** 09 Oktober 2026  
**Disusun berdasarkan:** SRS NotaSteam versi 1.0 dan dokumen WireFrame NotaSteam  
**Proyek:** Aplikasi Web NotaSteam untuk usaha pencucian motor Petrol

---

## 1. Ringkasan Produk

NotaSteam adalah aplikasi berbasis web untuk membantu usaha pencucian motor Petrol mengelola pencatatan transaksi, pembayaran, bukti pembayaran, data jenis motor dan layanan pencucian, serta laporan pendapatan harian.

Aplikasi ini menggantikan proses pencatatan yang sebelumnya dilakukan secara manual menggunakan buku. Sistem ditujukan untuk dua peran utama, yaitu Pemilik Usaha (Owner) dan Penanggung Jawab Pencatatan/Kasir.

### 1.1 Masalah yang ingin diselesaikan

Berdasarkan hasil wawancara dengan pemilik usaha Petrol pada 09 Oktober 2026:

- Pencatatan transaksi dan rekap pendapatan masih menggunakan buku.
- Kesalahan penulisan jenis motor dan pencatatan transaksi ganda (*double entry*) masih dapat terjadi.
- Belum tersedia pendataan informasi kendaraan saat pelanggan datang.
- Perhitungan pendapatan harian saat *closing* masih dilakukan secara manual.
- Pelanggan membutuhkan bukti pembayaran setelah transaksi.

### 1.2 Tujuan produk

1. Mendigitalisasi pencatatan transaksi pencucian motor.
2. Mengurangi kesalahan pencatatan jenis motor dan transaksi ganda.
3. Mempercepat proses pencatatan kendaraan dan pembayaran.
4. Menyediakan struk sebagai bukti transaksi pelanggan.
5. Menghasilkan rekap pendapatan harian secara otomatis.
6. Memudahkan Owner memantau aktivitas dan pendapatan usaha.

### 1.3 Indikator keberhasilan bisnis

| ID | Tujuan | Indikator keberhasilan |
|---|---|---|
| KB-01 | Mengurangi kesalahan pencatatan transaksi | Kesalahan penulisan jenis motor dan pencatatan ganda ditargetkan berkurang hingga 0%. |
| KB-02 | Mempercepat rekap pendapatan harian | Rekapitulasi saat *closing* dihasilkan otomatis oleh sistem. |
| KB-03 | Menyediakan bukti transaksi | Setiap transaksi pelanggan menghasilkan struk pembayaran. |

---

## 2. Stakeholder dan Pengguna

| Pengguna | Peran | Kebutuhan utama |
|---|---|---|
| Novi Fahriza | Owner/Pemilik Usaha | Memantau pendapatan, aktivitas transaksi, laporan harian, serta mengelola data jenis motor dan layanan. |
| Ibu Ernawati | Kasir/Penanggung Jawab Pencatatan | Mencatat kendaraan masuk, memilih layanan, memproses pembayaran, memverifikasi pembayaran digital, dan mencetak struk. |
| Pelanggan | Penerima layanan | Mendapatkan layanan pencucian dan bukti pembayaran. |

### 2.1 Karakteristik pengguna

- Owner berusia 30 tahun dan terbiasa menggunakan smartphone.
- Kasir berusia 49 tahun dan memiliki pemahaman sedang dalam penggunaan smartphone.
- Antarmuka perlu sederhana, mudah dibaca, dan mudah dioperasikan melalui layar sentuh.

---

## 3. Ruang Lingkup Produk

### 3.1 Termasuk dalam ruang lingkup

- Login pengguna berdasarkan username dan password.
- Hak akses berdasarkan peran Owner dan Kasir.
- Pengelolaan data jenis motor.
- Pengelolaan layanan pencucian dan tarif.
- Input transaksi kendaraan dengan memilih jenis motor dan mengisi plat nomor.
- Pencegahan pencatatan ganda pada transaksi aktif.
- Pembayaran tunai dan digital/transfer.
- Verifikasi pembayaran digital secara manual oleh Kasir.
- Perubahan status transaksi menjadi Lunas setelah pembayaran terverifikasi.
- Pembuatan dan pencetakan/penampilan nota.
- Daftar transaksi tersimpan.
- Dashboard Owner.
- Laporan pendapatan harian dan riwayat berdasarkan tanggal.
- Rekap jumlah kendaraan serta rincian pembayaran tunai dan digital.

### 3.2 Di luar ruang lingkup

- Pengelolaan otomatis stok solar, bensin, dan air PDAM.
- Integrasi otomatis dengan *payment gateway*.
- Verifikasi pembayaran digital melalui API bank atau penyedia pembayaran.
- SEO untuk website publik; NotaSteam merupakan aplikasi operasional internal.

### 3.3 Batasan

- Sistem diakses melalui browser dan membutuhkan koneksi internet atau jaringan lokal yang stabil.
- Pembayaran digital diperiksa dan diverifikasi manual oleh Kasir.
- Pencetakan fisik bergantung pada ketersediaan printer thermal dan koneksi perangkat.
- Antarmuka harus mudah dipahami oleh pengguna dengan literasi digital menengah.

---

## 4. Fitur dan Kebutuhan Fungsional

Prioritas **Must** berarti fitur wajib menurut daftar kebutuhan fungsional dalam SRS.

| ID | Fitur | Deskripsi kebutuhan | Prioritas |
|---|---|---|---|
| KF-01 | Autentikasi | Sistem menyediakan login menggunakan username dan password untuk membatasi akses Owner dan Kasir. | Must |
| KF-02 | Data Jenis Motor | Sistem menyimpan, menampilkan, dan mengelola daftar jenis motor. | Must |
| KF-03 | Data Layanan Pencucian | Sistem mengelola layanan pencucian, termasuk layanan cuci bersih, beserta harganya. | Must |
| KF-04 | Input Transaksi Masuk | Kasir memilih jenis motor dari daftar dan mengisi nomor plat secara manual. | Must |
| KF-05 | Pencatatan Otomatis | Sistem membantu mencegah kesalahan penulisan jenis motor dan pencatatan ganda. | Must |
| KF-06 | Pemrosesan Pembayaran | Sistem mendukung pembayaran tunai dan digital/transfer. | Must |
| KF-07 | Verifikasi Pembayaran Digital | Kasir dapat mengonfirmasi pembayaran digital secara manual. | Must |
| KF-08 | Cetak Struk | Sistem menghasilkan struk transaksi yang dapat dicetak melalui printer thermal. | Must |
| KF-09 | Laporan Pendapatan Harian | Sistem mengakumulasi transaksi lunas untuk menyajikan laporan pendapatan harian saat *closing*. | Must |

> Catatan sumber: SRS memuat sembilan baris kebutuhan fungsional pada bagian 6.1. Dokumen juga menyebut target minimal 10 kebutuhan dan pada bagian prioritas merujuk KF-10, tetapi rincian KF-10 tidak tersedia pada daftar tersebut. KF-10 perlu dikonfirmasi, bukan diasumsikan.

---

## 5. User Stories dan Kriteria Penerimaan

### US-01 — Input Transaksi Kendaraan

**Sebagai** Kasir, **saya ingin** memilih jenis motor dan memasukkan plat nomor kendaraan, **agar** transaksi tercatat cepat tanpa kesalahan penulisan atau pencatatan ganda.

Kriteria penerimaan:

1. Kasir dapat memilih jenis motor dari pilihan yang tersedia.
2. Sistem menampilkan jenis motor dan tarif layanan sesuai pilihan.
3. Kasir wajib mengisi plat nomor kendaraan.
4. Sistem menyimpan transaksi setelah data valid.
5. Sistem mencegah pendaftaran ganda untuk transaksi aktif pada waktu yang sama.

### US-02 — Pembayaran dan Cetak Struk

**Sebagai** Kasir, **saya ingin** memproses pembayaran tunai atau digital dan mencetak struk, **agar** pelanggan mendapatkan bukti transaksi.

Kriteria penerimaan:

1. Kasir dapat memilih metode pembayaran Tunai atau Digital/Transfer.
2. Untuk pembayaran digital, Kasir memeriksa pembayaran dan melakukan verifikasi manual.
3. Setelah pembayaran terverifikasi, status transaksi berubah menjadi **Lunas**.
4. Struk hanya dapat dicetak setelah transaksi lunas.
5. Sistem dapat menampilkan nota digital jika pencetakan fisik tidak tersedia.

### US-03 — Laporan Pendapatan Harian

**Sebagai** Owner/Kasir, **saya ingin** melihat rekap pendapatan harian, **agar** proses *closing* dapat dilakukan tanpa perhitungan manual.

Kriteria penerimaan:

1. Pengguna membuka menu Laporan Pendapatan.
2. Sistem menampilkan laporan hari berjalan secara default.
3. Laporan memuat total pendapatan, jumlah kendaraan, rincian tunai dan digital, serta daftar transaksi.
4. Pengguna dapat memilih tanggal lain untuk melihat laporan periode sebelumnya.
5. Jika tidak ada transaksi pada tanggal terpilih, sistem menampilkan pesan bahwa tidak ada data transaksi.

---

## 6. Hak Akses dan Peran

| Fitur | Kasir | Owner |
|---|:---:|:---:|
| Login | Ya | Ya |
| Melihat dashboard operasional kasir | Ya | Tidak ditentukan secara khusus |
| Input transaksi kendaraan | Ya | Tidak ditentukan secara khusus |
| Memproses pembayaran | Ya | Tidak ditentukan secara khusus |
| Verifikasi pembayaran digital | Ya | Tidak ditentukan secara khusus |
| Mencetak/menampilkan nota | Ya | Tidak ditentukan secara khusus |
| Melihat transaksi tersimpan/riwayat | Ya, sesuai kebutuhan operasional | Ya |
| Melihat laporan pendapatan | Ya, disebut dalam user story | Ya |
| Mengelola jenis motor dan layanan | Tidak | Ya |
| Mengelola akun/profil Owner | Tidak | Ya |

Hak akses yang tidak dijelaskan secara eksplisit dalam SRS perlu dikonfirmasi sebelum implementasi final.

---

## 7. Alur Proses Utama

### 7.1 Alur transaksi

1. Kasir login ke NotaSteam.
2. Kasir membuka halaman Dashboard Kasir atau Transaksi Baru.
3. Kasir memilih jenis motor.
4. Sistem menampilkan layanan dan tarif yang sesuai.
5. Kasir memasukkan nomor plat kendaraan.
6. Kasir menyimpan transaksi.
7. Kasir memilih metode pembayaran: Tunai atau Transfer/Digital.
8. Untuk Tunai, Kasir memasukkan nominal pembayaran. Untuk Digital, Kasir memeriksa pembayaran dan mengonfirmasi secara manual.
9. Sistem mengubah status menjadi Lunas setelah pembayaran valid/terverifikasi.
10. Sistem menampilkan nota dan menyediakan tindakan cetak.
11. Transaksi masuk ke daftar transaksi tersimpan dan perhitungan laporan.

### 7.2 Alur Owner

1. Owner login.
2. Owner melihat ringkasan bisnis pada Dashboard Owner.
3. Owner dapat membuka aktivitas terbaru.
4. Owner membuka Laporan Pendapatan untuk melihat rekap dan memilih tanggal.
5. Owner membuka Jenis & Layanan Motor untuk menambah, mengubah, atau menonaktifkan data.
6. Owner dapat membuka halaman Akun Owner.

---

## 8. Struktur Halaman Produk

Mengacu pada 11 halaman dalam dokumen WireFrame NotaSteam:

| No. | Halaman | Pengguna | Tujuan |
|---:|---|---|---|
| 1 | Login | Owner dan Kasir | Autentikasi pengguna. |
| 2 | Dashboard Kasir | Kasir | Memulai transaksi dan mengakses pilihan jenis motor. |
| 3 | Transaksi 1 | Kasir | Memilih jenis motor, memasukkan plat nomor, dan menyimpan transaksi. |
| 4 | Transaksi 2 | Kasir | Menampilkan transaksi aktif dan memilih metode pembayaran. |
| 5 | Transaksi 3 | Kasir | Menampilkan status transaksi sudah lunas. |
| 6 | Cetak Nota | Kasir | Menampilkan rincian nota dan tombol cetak. |
| 7 | Transaksi Tersimpan | Kasir | Melihat daftar transaksi yang sudah tersimpan. |
| 8 | Dashboard Owner | Owner | Melihat ringkasan pendapatan, jumlah motor, pembayaran, dan aktivitas terbaru. |
| 9 | Laporan Pendapatan | Owner | Melihat rekap harian, memilih tanggal, dan mencetak laporan. |
| 10 | Jenis & Layanan Motor | Owner | Mengelola master jenis motor dan tarif layanan. |
| 11 | Akun Owner | Owner | Melihat dan mengubah nama profil serta keluar dari akun. |

---

## 9. Kebutuhan Non-Fungsional

| ID | Kategori | Kebutuhan |
|---|---|---|
| KNF-01 | Kinerja | Halaman transaksi dan pencarian jenis motor harus dimuat dengan cepat pada koneksi standar. SRS menyebut pengujian melalui Lighthouse atau Network Tab, tetapi angka target waktu belum tercantum. |
| KNF-02 | Keamanan | Password disimpan dalam bentuk hash, menggunakan HTTPS, dan menerapkan kontrol akses berdasarkan peran. |
| KNF-03 | Kegunaan | Kasir dapat menyelesaikan pencatatan transaksi dengan langkah klik/input yang ringkas. |
| KNF-04 | Aksesibilitas | Kontras warna dan ukuran teks/tombol harus memadai; acuan yang disebut adalah WCAG 2.1 AA. |
| KNF-05 | Kompatibilitas | Sistem dapat digunakan pada Chrome, Safari, dan Firefox di smartphone. |
| KNF-06 | Ketersediaan | Sistem dapat diakses selama jam operasional Petrol. Nilai target uptime belum dicantumkan. |
| KNF-07 | Skalabilitas | Sistem ditargetkan mendukung hingga 10 pengguna secara bersamaan. |
| KNF-08 | Keterpeliharaan | Kode terorganisasi secara modular, menggunakan version control Git, dan memiliki dokumentasi API sederhana. |
| KNF-09 | Privasi | Riwayat transaksi dan nomor plat kendaraan disimpan dengan aman dan tidak disebarluaskan. |

**Catatan:** SRS juga mencantumkan KNF-10 SEO sebagai Won't Have. Karena SEO tidak menjadi kebutuhan aplikasi internal, fitur tersebut tidak termasuk ruang lingkup saat ini.

---

## 10. Data dan Entitas Utama

SRS mendefinisikan empat entitas konseptual:

### 10.1 Pengguna

- `id_user`
- `username`
- `password`
- `nama_lengkap`
- `peran`

Menyimpan data akun Owner dan Kasir.

### 10.2 Jenis Motor

- `id_jenis_motor`
- `nama_jenis`

Menyimpan daftar kategori/jenis motor.

### 10.3 Layanan

- `id_layanan`
- `id_jenis_motor`
- `nama_layanan`
- `harga`

Menyimpan layanan pencucian dan tarif yang terkait dengan jenis motor.

### 10.4 Transaksi

- `id_transaksi`
- `no_nota`
- `tanggal`
- `plat_nomor`
- `id_jenis_motor`
- `id_layanan`
- `metode_pembayaran`
- `status_pembayaran`
- `total_bayar`
- `id_user`

Menyimpan transaksi pencucian, kendaraan, pembayaran, dan data penerbitan nota.

---

## 11. Aturan Bisnis

1. Kasir dan Owner harus login untuk mengakses sistem.
2. Jenis motor dipilih dari master data; tidak diketik bebas pada transaksi.
3. Plat nomor kendaraan wajib diisi secara manual.
4. Jenis motor yang dapat dipilih Kasir adalah data yang aktif.
5. Tarif transaksi mengikuti data layanan yang dipilih.
6. Metode pembayaran yang didukung adalah Tunai dan Digital/Transfer.
7. Pembayaran digital diverifikasi secara manual oleh Kasir.
8. Transaksi hanya berstatus Lunas setelah pembayaran dinyatakan valid/terverifikasi.
9. Nota hanya dapat dicetak setelah transaksi lunas.
10. Laporan pendapatan mengakumulasi transaksi dengan status Lunas.

---

## 12. Risiko dan Mitigasi

| Risiko | Dampak | Mitigasi yang disebut dalam SRS |
|---|---|---|
| Koneksi internet terputus | Transaksi terganggu | SRS mengusulkan penyimpanan sementara lokal/PWA dan sinkronisasi saat koneksi kembali. |
| Printer thermal tidak terhubung atau kehabisan kertas | Struk fisik tidak dapat dicetak | Sediakan cetak ulang dan nota digital di layar. |
| Kesalahan verifikasi pembayaran digital | Status transaksi dapat keliru | Tampilkan konfirmasi sebelum status pembayaran diubah menjadi Lunas. |

---

## 13. Asumsi dan Hal yang Perlu Dikonfirmasi

Bagian ini sengaja memisahkan hal yang belum lengkap/seragam dalam sumber agar tidak dianggap sebagai keputusan final.

1. **Jumlah kebutuhan fungsional:** daftar 6.1 memuat KF-01 sampai KF-09, sedangkan dokumen menyebut minimal 10 kebutuhan dan tabel prioritas merujuk KF-10.
2. **Hak akses laporan:** user story menyebut Owner/Kasir dapat melihat laporan, sedangkan tabel hak akses utama menekankan laporan pada Owner.
3. **Dashboard Kasir:** wireframe menampilkan pilihan jenis motor dan input plat nomor, sedangkan SRS juga mendeskripsikan halaman Transaksi Baru. Perlu dipastikan apakah dashboard dan halaman transaksi merupakan satu alur atau halaman terpisah.
4. **Status transaksi:** SRS menggunakan istilah Pending/Proses dan Lunas. Definisi status per tahap perlu ditetapkan.
5. **Pencegahan transaksi ganda:** aturan teknis untuk menentukan transaksi aktif dan kondisi duplikasi plat nomor perlu dirinci.
6. **Nilai target kinerja dan uptime:** KNF-01 dan KNF-06 belum memiliki angka target terukur.
7. **Nota digital dan printer:** mekanisme cetak dari smartphone serta dukungan Bluetooth/USB perlu diuji pada perangkat yang akan digunakan.
8. **Layanan dan harga:** wireframe menampilkan beberapa kategori motor dan harga contoh Rp15.000; nilai tersebut perlu dikonfirmasi sebagai data contoh atau tarif operasional sebenarnya.

---

## 14. Kriteria Rilis Minimum (MVP)

Produk minimum dapat dinyatakan siap diuji apabila:

- Owner dan Kasir dapat login dengan hak akses yang sesuai.
- Owner dapat mengelola data jenis motor dan layanan beserta tarif.
- Kasir dapat membuat transaksi dengan memilih jenis motor dan mengisi plat nomor.
- Sistem menyimpan transaksi dan mengurangi kemungkinan pencatatan ganda.
- Kasir dapat memproses pembayaran tunai dan memverifikasi transfer secara manual.
- Status transaksi berubah menjadi Lunas setelah pembayaran terverifikasi.
- Nota dapat ditampilkan dan dicetak.
- Dashboard dan laporan menampilkan transaksi serta pendapatan berdasarkan transaksi lunas.
- Tampilan dapat digunakan pada smartphone dan desktop dengan nyaman.

---

## 15. Referensi Dokumen

1. **SRS — NotaSteam, Versi 1.0**, Requirements Engineering, tanggal 09/10/2026. Termasuk hasil wawancara usaha pencucian motor Petrol pada 09 Oktober 2026.
2. **WireFrame NotaSteam**, dokumen desain berisi 11 rancangan halaman aplikasi.
