# Design Document — NotaSteam

**Versi:** 1.0  
**Produk:** NotaSteam  
**Basis desain:** Dokumen WireFrame NotaSteam (11 halaman) dan SRS NotaSteam versi 1.0  
**Framework CSS:** Bootstrap 5

---

## 1. Tujuan Dokumen

Dokumen ini menjelaskan rancangan antarmuka dan pedoman implementasi UI NotaSteam. Rancangan mengikuti 11 wireframe pada dokumen sumber dan menggunakan Bootstrap 5 untuk membangun tampilan responsif.

Dokumen ini merupakan panduan desain dan implementasi front-end, bukan pengganti kebutuhan fungsional pada PRD.

## 2. Prinsip Desain

1. **Sederhana:** alur utama Kasir dibuat jelas dan tidak dipenuhi elemen yang tidak diperlukan.
2. **Mudah disentuh:** tombol dan pilihan memiliki area klik yang cukup pada smartphone.
3. **Konsisten:** warna, bentuk tombol, jarak, kartu, dan tipografi digunakan secara konsisten.
4. **Responsif:** layout menyesuaikan smartphone, tablet, dan desktop.
5. **Status mudah dikenali:** status transaksi seperti Pending/Proses dan Lunas ditampilkan dengan label yang jelas.
6. **Minim kesalahan:** pilihan jenis motor menggunakan tombol/kartu pilihan, sedangkan plat nomor menggunakan input teks dengan validasi.

## 3. Teknologi dan Framework

### 3.1 Bootstrap 5

Gunakan Bootstrap 5 sebagai framework CSS utama.

Sumber resmi:
- Dokumentasi: https://getbootstrap.com/docs/5.3/
- CDN CSS: `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css`
- CDN JavaScript Bundle: `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js`

Contoh pemasangan pada dokumen HTML:

```html
<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>NotaSteam</title>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
    rel="stylesheet">
</head>
<body>
  <!-- Konten halaman NotaSteam -->
  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js">
  </script>
</body>
</html>
```

Versi CDN di atas merupakan pilihan implementasi. Jika proyek menggunakan versi Bootstrap 5 lain, samakan versi CSS dan JavaScript.

### 3.2 Komponen Bootstrap yang disarankan

| Kebutuhan UI | Komponen / utility Bootstrap 5 |
|---|---|
| Struktur halaman | `.container`, `.container-fluid`, `.row`, `.col-*` |
| Form login dan input | `.form-control`, `.form-label`, `.input-group` |
| Tombol tindakan | `.btn`, `.btn-primary`, `.btn-dark`, `.btn-outline-secondary` |
| Kartu ringkasan | `.card`, `.card-body`, `.card-title` |
| Navigasi | `.navbar`, `.nav`, `.nav-link` |
| Daftar transaksi | `.list-group`, `.table`, `.table-responsive` |
| Status transaksi | `.badge`, `.alert` |
| Dialog konfirmasi | `.modal` |
| Tata letak | `.d-flex`, `.justify-content-between`, `.align-items-center`, `.gap-*` |
| Jarak | `.p-*`, `.m-*`, `.px-*`, `.py-*` |
| Responsif | `.d-none`, `.d-md-block`, `.col-12`, `.col-md-*` |

Gunakan CSS tambahan hanya untuk identitas visual NotaSteam dan detail yang tidak disediakan oleh Bootstrap.

---

## 4. Identitas Visual

Wireframe sumber menggunakan tampilan sederhana dengan latar terang, garis tepi gelap, kartu berwarna putih/abu-abu muda, serta aksen merah muda lembut pada beberapa pilihan dan elemen transaksi. Rekomendasi berikut mempertahankan karakter tersebut.

### 4.1 Palet warna

| Token | Warna | Kegunaan |
|---|---|---|
| `--ns-ink` | `#17252B` | Teks utama, garis tepi, judul |
| `--ns-primary` | `#202020` | Tombol aksi utama |
| `--ns-accent` | `#E8D1D2` | Pilihan aktif dan aksen lembut |
| `--ns-surface` | `#FFFFFF` | Kartu dan bidang utama |
| `--ns-background` | `#F7F4F4` | Latar halaman |
| `--ns-muted` | `#777777` | Teks sekunder |
| `--ns-border` | `#C9C3C3` | Garis pembatas |
| `--ns-success` | `#198754` | Status Lunas/berhasil |
| `--ns-warning` | `#FFC107` | Status menunggu/perlu perhatian |
| `--ns-danger` | `#DC3545` | Pesan kesalahan |

Pastikan teks dan latar memiliki kontras yang memadai. Jangan mengandalkan warna saja untuk membedakan status; sertakan label teks seperti **Lunas** atau **Menunggu Verifikasi**.

### 4.2 Tipografi

- Gunakan font sistem Bootstrap: `system-ui`, sans-serif.
- Judul halaman: tegas dan ringkas.
- Label form: jelas dan diletakkan dekat input.
- Teks isi: ukuran nyaman dibaca pada smartphone.
- Hindari teks kecil untuk nominal, status, dan informasi transaksi penting.

### 4.3 Bentuk dan jarak

- Gunakan kartu dengan sudut membulat sedang (`rounded-3`).
- Gunakan border tipis (`border`) untuk memisahkan kelompok informasi.
- Beri ruang antar tombol agar tidak mudah salah tekan.
- Tombol tindakan utama dibuat lebar pada layar smartphone bila sesuai alur.

Contoh CSS tambahan:

```css
:root {
  --ns-ink: #17252b;
  --ns-primary: #202020;
  --ns-accent: #e8d1d2;
  --ns-surface: #ffffff;
  --ns-background: #f7f4f4;
  --ns-muted: #777777;
  --ns-border: #c9c3c3;
}

body {
  background: var(--ns-background);
  color: var(--ns-ink);
  font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
}

.ns-card {
  background: var(--ns-surface);
  border: 1px solid var(--ns-border);
  border-radius: 1rem;
}

.btn-ns {
  color: #fff;
  background: var(--ns-primary);
  border-color: var(--ns-primary);
}

.btn-ns:hover {
  color: #fff;
  background: #3a3a3a;
  border-color: #3a3a3a;
}

.ns-option-active {
  background: var(--ns-accent);
  border-color: #b99b9d;
}
```

---

## 5. Struktur Navigasi dan Hak Akses

### 5.1 Navigasi Kasir

- Dashboard Kasir
- Transaksi Baru
- Transaksi Tersimpan
- Keluar

### 5.2 Navigasi Owner

- Dashboard Owner
- Laporan Pendapatan
- Jenis & Layanan Motor
- Akun Owner
- Keluar

Menu yang ditampilkan harus mengikuti peran pengguna yang sedang login. Jangan menampilkan menu pengelolaan master data kepada Kasir jika hak akses tersebut tidak diberikan.

### 5.3 Pola header

Header ringkas berisi:
- Nama/identitas NotaSteam.
- Nama halaman atau konteks halaman.
- Inisial/avatar pengguna.
- Tombol keluar.

Pada smartphone, header dibuat ringkas agar area konten tetap luas.

---

## 6. Spesifikasi 11 Halaman

### 6.1 Halaman Login

**Aktor:** Owner dan Kasir  
**Tujuan:** Memungkinkan pengguna masuk ke sistem.

Elemen:
- Nama/logo teks NotaSteam.
- Kalimat pengantar “Silakan masuk ke akun Anda”.
- Input Username.
- Input Password dengan kontrol tampil/sembunyikan jika diimplementasikan.
- Tombol Masuk.
- Tautan “Lupa Password?” sesuai wireframe.

Perilaku:
- Username dan password wajib diisi.
- Tampilkan pesan kesalahan yang mudah dipahami jika kredensial tidak valid.
- Setelah login berhasil, arahkan pengguna sesuai perannya.
- Jangan menampilkan pesan yang membocorkan apakah username atau password tertentu terdaftar.

Bootstrap:
- `.container`, `.row`, `.col`, `.card`, `.form-control`, `.form-label`, `.btn`.

### 6.2 Dashboard Kasir

**Aktor:** Kasir  
**Tujuan:** Menjadi titik awal pencatatan kendaraan.

Elemen sesuai wireframe:
- Header NotaSteam dan identitas Kasir.
- Sapaan “Halo, Kasir!”.
- Tombol **Transaksi Baru**.
- Daftar pilihan jenis motor.
- Input Nomor Plat Kendaraan.

Wireframe menampilkan contoh kategori:
- Motor Matic.
- Motor Bebek.
- Motor Sport.
- Matic Besar.

Nama kategori dan harga aktual harus mengikuti master data, bukan ditetapkan dari contoh wireframe.

Perilaku:
- Tombol Transaksi Baru membawa Kasir ke alur input transaksi.
- Pilihan motor dapat ditampilkan sebagai kartu/tombol.
- Plat nomor diisi secara manual.

Bootstrap:
- `.card`, `.btn`, `.form-control`, `.list-group`, `.row`, `.col-12`.

### 6.3 Halaman Transaksi 1 — Pilih Motor dan Input Plat

**Aktor:** Kasir  
**Tujuan:** Mencatat kendaraan yang akan dicuci.

Elemen:
- Tombol kembali.
- Judul NotaSteam.
- Daftar pilihan jenis motor.
- Input Nomor Plat Kendaraan.
- Ringkasan layanan terpilih dan tarif.
- Tombol **Simpan Transaksi**.
- Akses/tautan **Transaksi Tersimpan**.

Perilaku:
1. Kasir memilih satu jenis motor.
2. Pilihan aktif diberi penanda visual.
3. Sistem menampilkan layanan dan tarif yang terkait.
4. Kasir mengisi plat nomor.
5. Sistem memvalidasi kolom wajib.
6. Setelah disimpan, transaksi masuk ke status awal yang ditentukan sistem.

Bootstrap:
- `.card`, `.form-control`, `.btn`, `.list-group`, `.badge`.

### 6.4 Halaman Transaksi 2 — Pembayaran

**Aktor:** Kasir  
**Tujuan:** Memproses pembayaran transaksi aktif.

Elemen:
- Tombol Kembali.
- Judul **Transaksi Aktif** dan jumlah antrean.
- Ringkasan kendaraan: plat nomor, jenis motor, tarif, dan waktu.
- Bagian Pembayaran.
- Tombol **Tunai**.
- Tombol **Transfer**.
- Tombol/aksi **Verifikasi Pembayaran**.

Perilaku:
- Kasir memilih metode pembayaran.
- Untuk tunai, sistem menyediakan input nominal pembayaran sesuai kebutuhan implementasi.
- Untuk transfer, Kasir memeriksa bukti/masuknya dana di luar integrasi otomatis lalu melakukan konfirmasi manual.
- Tampilkan konfirmasi sebelum status pembayaran digital diubah menjadi Lunas.
- Pembayaran yang belum valid tidak boleh dianggap Lunas.

Bootstrap:
- `.card`, `.btn`, `.badge`, `.form-control`, `.modal`, `.alert`.

### 6.5 Halaman Transaksi 3 — Transaksi Lunas

**Aktor:** Kasir  
**Tujuan:** Memberi konfirmasi bahwa transaksi selesai dibayar.

Elemen:
- Ikon/indikator berhasil.
- Label **Pembayaran Selesai**.
- Judul **Transaksi sudah lunas**.
- Ringkasan kendaraan dan total pembayaran.
- Tombol **Transaksi Baru**.
- Tombol **Cetak/Lihat Nota**.

Perilaku:
- Halaman ini hanya muncul setelah pembayaran berhasil dan terverifikasi.
- Kasir dapat memulai transaksi berikutnya atau membuka nota.

Bootstrap:
- `.alert`, `.badge`, `.card`, `.btn`.

### 6.6 Halaman Cetak Nota

**Aktor:** Kasir  
**Tujuan:** Menampilkan bukti transaksi pelanggan.

Elemen berdasarkan wireframe:
- Judul Nota Digital dan kontrol tutup.
- Nama NotaSteam.
- Ucapan terima kasih.
- Nomor transaksi.
- Waktu.
- Nama Kasir.
- Jenis motor dan plat nomor.
- Total pembayaran.
- Metode pembayaran.
- Status LUNAS.
- Tombol **Cetak Nota**.

Perilaku:
- Data nota diambil dari transaksi yang dipilih.
- Tombol cetak memanggil fasilitas cetak browser/perangkat yang didukung.
- Jika printer tidak tersedia, nota tetap dapat ditampilkan sebagai nota digital.
- Struk hanya tersedia untuk transaksi lunas.

Bootstrap:
- `.card`, `.table`, `.badge`, `.btn`.
- Pertimbangkan CSS khusus mode cetak dengan `@media print`.

### 6.7 Halaman Transaksi Tersimpan

**Aktor:** Kasir  
**Tujuan:** Melihat transaksi yang sudah disimpan.

Elemen:
- Tombol kembali.
- Judul **Transaksi Tersimpan**.
- Jumlah transaksi.
- Daftar transaksi yang berisi plat nomor, jenis motor, nominal, waktu, dan status.

Perilaku:
- Daftar diperbarui sesuai data transaksi tersimpan.
- Status pembayaran ditampilkan sebagai teks/badge.
- Jika daftar kosong, tampilkan pesan kosong yang informatif.

Bootstrap:
- `.list-group`, `.card`, `.badge`, `.container`.

### 6.8 Dashboard Owner

**Aktor:** Owner  
**Tujuan:** Menyajikan ringkasan kondisi usaha.

Elemen yang tampak pada wireframe:
- Header Panel Pemilik dan avatar Owner.
- Judul Ringkasan Bisnis.
- Kartu Pendapatan Hari Ini.
- Kartu Motor Tercuci.
- Kartu Pembayaran Tunai.
- Kartu Pembayaran Digital.
- Bagian Aktivitas Terbaru.
- Aksi untuk melihat semua aktivitas.
- Bagian kesiapan *closing*.
- Tombol **Lihat Laporan Hari Ini**.

Perilaku:
- Nilai ringkasan dihitung dari data transaksi sesuai tanggal dan status yang berlaku.
- Aktivitas terbaru menampilkan daftar transaksi.
- Informasi *closing* mengarahkan Owner ke laporan harian.

Bootstrap:
- `.row`, `.col-12`, `.col-md-6`, `.col-lg-3`, `.card`, `.list-group`, `.btn`.

### 6.9 Halaman Laporan Pendapatan

**Aktor:** Owner  
**Tujuan:** Melihat rekap pendapatan dan transaksi berdasarkan tanggal.

Elemen:
- Header Panel Pemilik.
- Judul **Laporan Pendapatan**.
- Bagian Rekap Hari Ini.
- Pemilih tanggal.
- Tombol **Cetak Laporan**.
- Ringkasan total pendapatan.
- Ringkasan jumlah kendaraan.
- Ringkasan pembayaran Tunai/Digital.
- Daftar transaksi dengan nomor nota, plat nomor, nominal, serta aksi yang tersedia.

Perilaku:
- Tanggal hari ini digunakan sebagai nilai awal.
- Owner dapat memilih tanggal lain.
- Laporan hanya mengakumulasi transaksi berstatus Lunas.
- Jika tidak ada transaksi, tampilkan pesan “Tidak ada data transaksi pada tanggal ini”.
- Aksi edit/hapus pada daftar hanya boleh disediakan jika aturan dan otorisasi datanya sudah ditetapkan.

Bootstrap:
- `.form-control`, `.input-group`, `.row`, `.card`, `.table-responsive`, `.table`, `.btn`.

### 6.10 Halaman Jenis & Layanan Motor

**Aktor:** Owner  
**Tujuan:** Mengelola master jenis motor dan tarif layanan.

Elemen:
- Header Panel Pemilik.
- Judul **Jenis Motor & Layanan**.
- Kartu Master Layanan.
- Keterangan jenis motor aktif.
- Tombol **Tambah Data**.
- Daftar jenis motor, deskripsi/contoh kategori, dan harga.
- Label status aktif.
- Tombol **Edit**.

Perilaku:
- Owner dapat menambah data.
- Owner dapat mengubah nama jenis motor, layanan, dan harga.
- Owner dapat menonaktifkan/menghapus data dengan konfirmasi.
- Data yang tidak aktif tidak tersedia untuk transaksi baru.
- Validasi harga harus menerima nilai numerik yang valid dan menolak nilai negatif.

Bootstrap:
- `.card`, `.list-group`, `.badge`, `.btn`, `.modal`, `.form-control`.

### 6.11 Halaman Akun Owner

**Aktor:** Owner  
**Tujuan:** Menampilkan informasi profil Owner.

Elemen:
- Header Panel Pemilik.
- Judul **Akun Owner**.
- Avatar/inisial.
- Nama Novi Fahriza.
- Keterangan Owner NotaSteam.
- Tombol **Edit nama profil**.
- Tombol **Keluar dari akun**.

Perilaku:
- Owner dapat mengubah nama profil sesuai kemampuan yang disediakan.
- Keluar akun mengakhiri sesi dan mengarahkan kembali ke Login.
- Aksi keluar sebaiknya meminta konfirmasi jika ada proses yang belum disimpan.

Bootstrap:
- `.card`, `.btn`, `.modal`, `.form-control`.

---

## 7. Alur Navigasi

```text
LOGIN
├── Peran Kasir
│   └── Dashboard Kasir
│       ├── Transaksi Baru
│       │   ├── Transaksi 1: Pilih Motor & Plat
│       │   ├── Transaksi 2: Pembayaran
│       │   ├── Transaksi 3: Lunas
│       │   └── Cetak/Lihat Nota
│       └── Transaksi Tersimpan
│
└── Peran Owner
    └── Dashboard Owner
        ├── Laporan Pendapatan
        ├── Jenis & Layanan Motor
        └── Akun Owner
```

Diagram ini menggambarkan navigasi konseptual berdasarkan wireframe. Detail menu final mengikuti keputusan hak akses dan implementasi.

---

## 8. Responsivitas

Desain sumber terutama memperlihatkan komposisi layar smartphone. Implementasi perlu mempertahankan kenyamanan tersebut pada ukuran layar berbeda.

| Ukuran | Perilaku desain |
|---|---|
| Smartphone (<576px) | Satu kolom; tombol utama dapat selebar kontainer; kartu ditumpuk vertikal; tabel dapat digulir horizontal atau diubah menjadi daftar. |
| Tablet (≥768px) | Ringkasan dapat menjadi dua kolom; form tetap mudah disentuh. |
| Desktop (≥992px) | Dashboard menggunakan beberapa kolom; konten dibatasi lebar yang nyaman; daftar transaksi dapat menggunakan tabel. |

Contoh grid:

```html
<div class="container py-4">
  <div class="row g-3">
    <div class="col-12 col-md-6 col-lg-3">
      <div class="card h-100">
        <div class="card-body">
          <h2 class="h6">Pendapatan Hari Ini</h2>
          <p class="fs-4 fw-bold mb-0">Rp 60.000</p>
        </div>
      </div>
    </div>
  </div>
</div>
```

Nominal pada contoh di atas hanya ilustrasi tampilan dari wireframe, bukan tarif atau data produksi.

---

## 9. Form, Validasi, dan Pesan Sistem

### 9.1 Validasi input

| Input | Validasi |
|---|---|
| Username | Wajib diisi. |
| Password | Wajib diisi. |
| Jenis motor | Harus memilih salah satu data aktif. |
| Plat nomor | Wajib diisi; lakukan normalisasi spasi/huruf sesuai aturan yang ditetapkan. |
| Harga layanan | Harus numerik dan tidak negatif. |
| Nominal pembayaran tunai | Tidak boleh kurang dari total pembayaran. |
| Pembayaran digital | Harus dikonfirmasi manual sebelum status menjadi Lunas. |
| Tanggal laporan | Harus berupa tanggal yang valid. |

### 9.2 Pesan yang disebut dalam SRS

- “Plat nomor kendaraan wajib diisi”.
- “Nominal pembayaran kurang”.
- “Harga layanan tidak valid”.
- “Tidak ada data transaksi pada tanggal ini”.

Gunakan `.invalid-feedback`, `.alert`, atau pesan inline Bootstrap untuk menampilkan kesalahan.

---

## 10. Aksesibilitas dan Kemudahan Penggunaan

- Setiap input memiliki label yang terlihat dan terhubung dengan input.
- Tombol memiliki teks tindakan yang jelas, bukan hanya ikon.
- Ikon penting disertai label atau teks aksesibel.
- Status transaksi ditampilkan sebagai teks selain warna.
- Kontras warna mengikuti prinsip WCAG 2.1 AA sebagaimana dirujuk SRS.
- Ukuran tombol dan jarak antar kontrol cukup untuk layar sentuh.
- Fokus keyboard terlihat pada tombol, tautan, dan input.
- Pesan validasi menjelaskan cara memperbaiki kesalahan.

---

## 11. Komponen UI yang Dapat Digunakan Ulang

| Komponen | Penggunaan |
|---|---|
| `AppHeader` | Nama aplikasi, halaman, avatar, tombol keluar. |
| `PageContainer` | Menjaga lebar dan jarak konten. |
| `MotorTypeOption` | Pilihan kategori motor. |
| `ServiceSummary` | Ringkasan layanan dan tarif. |
| `TransactionSummary` | Plat nomor, jenis motor, tanggal/waktu, total. |
| `PaymentMethodSelector` | Pilihan Tunai dan Transfer. |
| `PaymentStatusBadge` | Status Pending/Proses/Lunas. |
| `RevenueSummaryCard` | Ringkasan pendapatan dan jumlah kendaraan. |
| `TransactionListItem` | Ringkasan transaksi dalam daftar. |
| `ReceiptView` | Nota digital dan tampilan cetak. |
| `ConfirmModal` | Konfirmasi pembayaran, hapus/nonaktifkan data, dan keluar. |
| `EmptyState` | Tampilan saat belum ada transaksi/data. |

---

## 12. Rancangan Tampilan Cetak Nota

Gunakan area nota yang terpisah dari navigasi aplikasi saat dicetak. Informasi minimum mengikuti wireframe:

- Nama NotaSteam.
- Ucapan terima kasih.
- Nomor transaksi.
- Waktu transaksi.
- Nama Kasir.
- Jenis motor.
- Plat nomor.
- Total.
- Metode pembayaran.
- Status LUNAS.

Contoh CSS mode cetak:

```css
@media print {
  body {
    background: #fff !important;
  }

  .no-print,
  nav,
  header .app-actions {
    display: none !important;
  }

  .receipt {
    width: 100%;
    max-width: 80mm;
    margin: 0 auto;
    border: 0;
    box-shadow: none;
  }
}
```

Lebar 80 mm adalah contoh umum untuk layout thermal dan perlu disesuaikan dengan printer yang benar-benar digunakan.

---

## 13. Keadaan UI yang Harus Dirancang

Setiap halaman perlu mempertimbangkan keadaan berikut:

1. **Normal:** data berhasil ditampilkan.
2. **Loading:** sistem sedang mengambil atau menyimpan data.
3. **Kosong:** belum ada transaksi atau data.
4. **Error:** data gagal dimuat atau disimpan.
5. **Validasi:** input belum sesuai.
6. **Berhasil:** transaksi tersimpan atau pembayaran lunas.
7. **Konfirmasi:** tindakan penting seperti verifikasi pembayaran atau penghapusan data membutuhkan persetujuan.

---

## 14. Catatan Implementasi dan Hal yang Perlu Dikonfirmasi

1. Wireframe memperlihatkan 11 halaman; penamaan route dan apakah beberapa halaman digabung perlu diputuskan saat implementasi.
2. Hak akses laporan untuk Kasir perlu dikonfirmasi karena SRS menyebut Owner/Kasir pada user story, tetapi hak akses utama lebih menekankan Owner.
3. Mekanisme cetak dari smartphone melalui Bluetooth/USB bergantung pada perangkat, browser, dan printer. Uji pada perangkat target sebelum menetapkan pengalaman cetak final.
4. SRS menyebut pembayaran digital diverifikasi manual; jangan membuat alur seolah-olah ada integrasi payment gateway otomatis.
5. SRS menyebut status Pending/Proses dan Lunas. Label status antara tahap transaksi perlu disepakati.
6. Tombol Edit/Hapus yang terlihat pada wireframe Laporan Pendapatan tidak dijelaskan rinci dalam kebutuhan fungsional; implementasinya perlu dikonfirmasi.
7. Angka, nama motor, harga, dan transaksi yang tampil pada wireframe merupakan contoh visual sampai dikonfirmasi sebagai data operasional.
8. Bootstrap 5 menangani layout dan komponen visual; autentikasi, validasi server, hak akses, penyimpanan transaksi, serta perhitungan pendapatan tetap harus diterapkan pada sisi aplikasi/server.

---

## 15. Checklist Implementasi UI

- [ ] Bootstrap 5 terpasang dengan viewport responsif.
- [ ] Warna, tipografi, border, dan tombol konsisten.
- [ ] Header dan navigasi menyesuaikan peran.
- [ ] Semua 11 halaman wireframe sudah dipetakan.
- [ ] Form memiliki label dan validasi.
- [ ] Pilihan motor memiliki kondisi aktif yang jelas.
- [ ] Metode pembayaran dan verifikasi manual mudah dipahami.
- [ ] Status Lunas hanya tampil setelah pembayaran terverifikasi.
- [ ] Nota memiliki tampilan layar dan tampilan cetak.
- [ ] Dashboard dan laporan memiliki kondisi data kosong/loading/error.
- [ ] Tampilan diuji pada smartphone, tablet, dan desktop.
- [ ] Kontras dan ukuran kontrol diperiksa untuk aksesibilitas.

---

## 16. Referensi

1. **WireFrame NotaSteam**, 3 halaman, berisi rancangan 11 layar: Login, Dashboard Kasir, tiga tahap Transaksi, Cetak Nota, Transaksi Tersimpan, Dashboard Owner, Laporan Pendapatan, Jenis & Layanan Motor, dan Akun Owner.
2. **SRS — NotaSteam, Versi 1.0**, khususnya bagian ruang lingkup, stakeholder, hak akses, kebutuhan fungsional, use case, model data, dan kebutuhan non-fungsional.
3. **Bootstrap 5.3 Documentation:** https://getbootstrap.com/docs/5.3/
