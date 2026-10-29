# SakuQ — Product Requirements Document (PRD)

**Versi:** 1.0 — MVP  
**Status:** Rancangan implementasi awal  
**Produk:** Website pencatat uang saku dan target tabungan untuk pelajar  
**Platform awal:** Website statis, responsif, menggunakan HTML, CSS, JavaScript, dan `localStorage`

---

## 1. Ringkasan produk

SakuQ adalah website pendamping keuangan sederhana bagi pelajar SMA/SMK usia sekitar 16–19 tahun. Pengguna dapat mencatat uang yang diterima, mencatat pengeluaran, menetapkan batas pengeluaran per kategori, dan memantau target tabungan.

SakuQ **tidak menyimpan uang sungguhan, tidak terhubung ke rekening bank, dan tidak memproses pembayaran**. Angka yang tampil adalah catatan yang dimasukkan pengguna secara manual.

**Nilai utama:** membantu pelajar memahami berapa uang yang tersedia, ke mana uangnya digunakan, dan bagaimana menabung menuju tujuan yang realistis.

## 2. Masalah utama

### Pernyataan masalah
Pelajar bisa kesulitan mengingat transaksi kecil dan memperkirakan sisa uang saku. Tanpa pencatatan dan batas pengeluaran yang sederhana, mereka lebih sulit mengevaluasi kebiasaan belanja dan menyusun rencana tabungan.

### Masalah pendukung
1. Pengeluaran kecil berulang tidak selalu tercatat.
2. Uang untuk kebutuhan, hiburan, dan tabungan belum dibagi dalam rencana yang jelas.
3. Target tabungan tidak memiliki nominal, tenggat, atau indikator progres.
4. Pengguna membutuhkan cara mengevaluasi kebiasaan tanpa merasa dihakimi.

Masalah tersebut adalah hipotesis produk. Validasi melalui wawancara dan uji coba pengguna perlu dilakukan sebelum menyimpulkan bahwa masalah ini mewakili semua pelajar.

## 3. Tujuan produk

### Tujuan MVP
- Memudahkan pengguna mencatat pemasukan dan pengeluaran secara manual.
- Menghitung sisa uang tersedia secara otomatis.
- Membantu pengguna menetapkan batas pengeluaran bulanan per kategori.
- Menampilkan progres target tabungan yang mudah dipahami.
- Menyediakan ringkasan periode dan kategori pengeluaran.
- Menjaga pengalaman tetap sederhana, nyaman di ponsel, dan bisa digunakan tanpa akun.

### Bukan tujuan MVP
- Menyimpan atau memindahkan uang sungguhan.
- Menghubungkan rekening, kartu, dompet digital, atau layanan pembayaran.
- Menyediakan sistem akun atau sinkronisasi antarpiranti.
- Memberikan rekomendasi investasi atau nasihat finansial personal.
- Mengklaim pengguna pasti menjadi lebih hemat hanya karena menggunakan website.

## 4. Target pengguna dan persona

**Pengguna utama:** pelajar SMA/SMK berusia sekitar 16–19 tahun yang menerima uang saku harian, mingguan, atau bulanan.

**Persona contoh:** Dika, 17 tahun, menerima uang saku mingguan. Ia ingin menabung untuk perlengkapan sekolah, tetapi sering tidak yakin berapa uang yang aman untuk digunakan. Ia membutuhkan proses pencatatan yang singkat dan ringkasan sederhana.

### Kebutuhan pengguna
- Mengetahui uang yang masuk dan keluar.
- Menambahkan catatan transaksi tanpa formulir yang panjang.
- Mengetahui sisa uang yang tersedia setelah pengeluaran dan alokasi tabungan.
- Melihat penggunaan uang dibandingkan batas anggaran.
- Membuat satu atau beberapa target tabungan.
- Melihat kemajuan dalam nominal dan persentase.
- Mengubah atau menghapus catatan yang salah.
- Menggunakan website di ponsel maupun laptop.
- Mengetahui lokasi penyimpanan dan batasan privasi data.

## 5. Prinsip pengalaman pengguna

1. **Sederhana:** satu transaksi cukup membutuhkan jenis, nominal, kategori, tanggal, dan catatan opsional.
2. **Tidak menghakimi:** pesan ketika anggaran terlampaui bersifat informatif, bukan menyalahkan pengguna.
3. **Transparan:** rumus saldo dan tabungan dijelaskan dengan jelas.
4. **Aman secara desain:** tidak meminta kata sandi, PIN, nomor rekening, atau kredensial keuangan.
5. **Mobile-first:** navigasi, formulir, tombol, dan tabel tetap dapat digunakan pada layar kecil.
6. **Tidak mengarang data:** saat pertama kali dibuka, pengguna melihat keadaan kosong; data contoh hanya dimuat setelah pengguna memilihnya.

## 6. Ruang lingkup fitur

### 6.1 Dashboard
**Tujuan:** memberi gambaran cepat kondisi keuangan.

**Informasi yang ditampilkan:**
- Sisa uang tersedia saat ini.
- Total pemasukan bulan ini.
- Total pengeluaran bulan ini.
- Total setoran tabungan yang tercatat.
- Progres anggaran per kategori pada bulan berjalan.
- Maksimal tiga target tabungan.
- Lima aktivitas transaksi terbaru.
- Tips keuangan singkat.

**Perilaku:** angka diperbarui setelah transaksi, setoran, atau anggaran berubah. Bila belum ada data, tampilkan keadaan kosong dan pilihan memuat data ilustrasi.

### 6.2 Transaksi
**Fungsi MVP:** tambah, lihat, cari, filter, edit, dan hapus transaksi.

**Jenis transaksi:**
- Pemasukan: uang saku, uang tambahan, hadiah, lainnya.
- Pengeluaran: makanan & minuman, transportasi, kebutuhan sekolah, hiburan & sosial, belanja pribadi, lainnya.
- Tabungan: setoran yang dialokasikan ke target tabungan.

**Kolom transaksi:** ID, jenis, nominal, kategori, tanggal, catatan opsional, dan ID target (khusus setoran tabungan).

**Validasi:** nominal harus berupa bilangan bulat positif; tanggal transaksi tidak boleh melewati hari ini; panjang catatan maksimal 80 karakter. Transaksi yang sudah ada dapat diedit jika jenisnya pemasukan atau pengeluaran. Setoran tabungan dikelola lewat target dan hanya bisa dihapus dari riwayat agar progres ikut diperbarui.

### 6.3 Anggaran
**Tujuan:** memberi batas rencana untuk pengeluaran bulanan.

**Kategori tetap:**
- Makanan & minuman
- Transportasi
- Kebutuhan sekolah
- Hiburan & sosial
- Belanja pribadi
- Lainnya

Setiap kategori memiliki batas rupiah bulanan yang bisa diubah. Nilai `0` berarti belum diberi batas. Pengeluaran aktual berasal dari transaksi bertipe pengeluaran pada bulan berjalan.

**Perilaku:** tampilkan batas, jumlah terpakai, sisa/kelebihan, dan persentase pemakaian. Jika pengeluaran melewati batas, tampilkan indikator peringatan dengan bahasa yang netral.

### 6.4 Target tabungan
**Data target:** nama target, nominal target, tanggal target opsional, tanggal pembuatan.

**Fungsi MVP:** buat target dan tambah setoran pada target.

**Aturan setoran:** setoran harus lebih besar dari nol, tidak boleh melebihi uang yang tersedia, dan tidak boleh melebihi sisa target. Setoran dibuat sebagai jenis transaksi `saving` supaya riwayat dan rumus saldo konsisten. Target yang sudah mencapai nominalnya ditandai sebagai tercapai.

**Batas MVP:** target yang sudah dibuat belum dapat diganti namanya atau dihapus dari antarmuka; setoran yang tercatat tetap bisa dihapus lewat riwayat transaksi jika salah input. Fitur pengubahan/penghapusan target dapat ditambahkan setelah model data dan perilakunya ditentukan lebih lanjut.

### 6.5 Laporan dan tips
- Pilih bulan laporan.
- Tampilkan pemasukan, pengeluaran, alokasi tabungan, dan sisa arus uang pada bulan itu.
- Tampilkan diagram batang pengeluaran berdasarkan kategori.
- Berikan ringkasan sederhana tentang kategori terbesar, anggaran yang terlampaui, dan arus uang.
- Tampilkan tips umum tentang pencatatan, target realistis, kebutuhan vs keinginan, dan evaluasi rutin.

Insight laporan bersifat deskriptif berdasarkan data yang dimasukkan, bukan rekomendasi finansial personal.

### 6.6 Penyimpanan dan reset
- Data disimpan di `localStorage` browser.
- Tidak ada akun maupun server backend pada MVP.
- Tombol reset menghapus transaksi, target, dan setoran dari penyimpanan browser setelah pengguna mengonfirmasi.
- Pengguna dapat memuat data contoh hanya ketika data masih kosong.
- Pesan privasi menyatakan bahwa data tidak tersinkron ke perangkat lain.

## 7. Aturan perhitungan

Semua nominal disimpan sebagai bilangan bulat rupiah. Penghitungan tidak menggunakan angka desimal.

### 7.1 Definisi
- `Pemasukan total`: jumlah semua transaksi bertipe `income`.
- `Pengeluaran total`: jumlah semua transaksi bertipe `expense`.
- `Setoran tabungan total`: jumlah semua transaksi bertipe `saving`.

### 7.2 Sisa uang tersedia
`Sisa uang tersedia = Pemasukan total − Pengeluaran total − Setoran tabungan total`

Rumus menggunakan seluruh transaksi yang tersimpan. Setoran tabungan mengurangi uang tersedia karena uang tersebut telah dialokasikan untuk tujuan tabungan. Setoran tidak dihitung sebagai pengeluaran konsumsi dan tidak masuk grafik kategori pengeluaran.

Sisa uang bisa menjadi negatif jika catatan menunjukkan pengeluaran dan setoran lebih besar daripada pemasukan. Dalam kondisi ini, aplikasi menunjukkan peringatan, tidak mengubah angka secara otomatis.

### 7.3 Ringkasan per bulan
- Pemasukan bulan = jumlah transaksi `income` dengan tanggal pada bulan terpilih.
- Pengeluaran bulan = jumlah transaksi `expense` dengan tanggal pada bulan terpilih.
- Setoran tabungan bulan = jumlah transaksi `saving` dengan tanggal pada bulan terpilih.
- Sisa arus uang bulan = pemasukan bulan − pengeluaran bulan − setoran tabungan bulan.

Sisa arus uang bulanan berbeda dari sisa uang tersedia keseluruhan karena ruang lingkup periodenya berbeda.

### 7.4 Target tabungan
- Terkumpul per target = jumlah transaksi `saving` yang `goalId`-nya sama dengan ID target.
- Sisa target = nilai maksimum dari `(Nominal target − Terkumpul)` dan `0`.
- Persentase progres = `Terkumpul ÷ Nominal target × 100`, ditampilkan paling tinggi 100%.
- Target tercapai jika terkumpul sama dengan atau lebih besar dari nominal target.
- Setoran baru dibatasi oleh nilai terkecil antara sisa uang tersedia dan sisa target.

### 7.5 Anggaran
- Terpakai per kategori = jumlah transaksi `expense` pada bulan berjalan dengan kategori tersebut.
- Sisa anggaran = batas anggaran − terpakai.
- Persentase pemakaian = terpakai ÷ batas anggaran × 100, jika batas lebih besar dari 0.
- Jika batas = 0, kategori dianggap belum diatur; persentase tidak dihitung.
- Lebih anggaran terjadi hanya saat batas > 0 dan terpakai > batas.

### 7.6 Grafik kategori
Grafik laporan menjumlah pengeluaran untuk setiap kategori pada bulan yang dipilih. Lebar setiap batang adalah nilai kategori dibagi nilai pengeluaran tertinggi pada kategori yang tampil. Jika belum ada pengeluaran, tampilkan pesan kosong.

## 8. Struktur halaman dan navigasi

1. **Dashboard** — ringkasan, anggaran, target, transaksi terbaru, dan tips.
2. **Transaksi** — statistik periode berjalan, pencarian, filter, tabel riwayat, tambah/edit/hapus.
3. **Anggaran** — ringkasan batas bulanan dan formulir pengubahan batas kategori.
4. **Target tabungan** — ringkasan target dan daftar kartu target, termasuk tindakan tambah setoran.
5. **Laporan & tips** — pemilih bulan, ringkasan, diagram kategori, insight, dan tips.

Dialog formulir digunakan untuk tambah/edit transaksi, membuat target, dan mencatat setoran. Navigasi utama berubah menjadi menu geser pada layar kecil.

## 9. Model data lokal

```json
{
  "transactions": [
    {
      "id": "tx_unique_id",
      "type": "income | expense | saving",
      "amount": 15000,
      "category": "Makanan & minuman",
      "date": "2026-10-28",
      "note": "Makan siang",
      "goalId": ""
    }
  ],
  "goals": [
    {
      "id": "goal_unique_id",
      "name": "Perlengkapan sekolah",
      "targetAmount": 300000,
      "targetDate": "2026-12-27",
      "createdAt": "2026-10-28"
    }
  ],
  "budgets": {
    "Makanan & minuman": 300000,
    "Transportasi": 200000,
    "Kebutuhan sekolah": 150000,
    "Hiburan & sosial": 100000,
    "Belanja pribadi": 100000,
    "Lainnya": 100000
  }
}
```

Contoh di atas hanya menjelaskan struktur. Website tidak mengharuskan tanggal atau nominal contoh tersebut dipakai pengguna.

## 10. Keamanan, privasi, dan keterbatasan

- Jangan meminta PIN, kata sandi, nomor rekening, detail kartu, atau data perbankan.
- `localStorage` bukan brankas terenkripsi; orang lain yang memakai browser/profil yang sama dapat melihat data aplikasi.
- Data tidak otomatis berpindah antarperangkat dan dapat hilang jika data situs dibersihkan.
- Pada versi statis ini, tidak ada autentikasi atau backend.
- Pengguna sebaiknya tidak mencatat informasi sensitif di kolom catatan.
- Website perlu diuji di browser modern dan layar ponsel sebelum dibagikan.

## 11. Kriteria keberhasilan dan acceptance criteria

### Kriteria keberhasilan uji pengguna
MVP dapat dianggap layak untuk tahap uji terbatas ketika:
1. Minimal 8–12 pelajar diwawancarai sebelum atau selama validasi, dengan hasil wawancara dicatat.
2. Dalam pengujian prototipe, setidaknya 80% peserta dapat mencatat satu pemasukan dan satu pengeluaran tanpa bantuan langsung.
3. Setidaknya 80% peserta dapat membuat target dan memahami progresnya.
4. Tidak ada kesalahan perhitungan pada skenario pengujian nominal dan tanggal.
5. Peserta uji dapat menjelaskan bahwa data disimpan secara lokal dan tidak tersinkron lintas perangkat.
6. Tombol dan formulir inti berfungsi pada viewport ponsel sekitar 360 px dan desktop.

Angka tersebut merupakan target internal awal, bukan klaim hasil yang sudah dicapai. Untuk menilai apakah produk membantu membangun kebiasaan, lakukan uji coba lanjutan selama 1–2 minggu dan amati apakah peserta kembali mencatat transaksi.

### Acceptance criteria fungsional
- [ ] Pengguna bisa menambahkan pemasukan dan pengeluaran dengan nominal positif.
- [ ] Transaksi tersimpan setelah halaman dimuat ulang pada browser yang sama.
- [ ] Pengguna bisa mengedit atau menghapus transaksi pemasukan/pengeluaran.
- [ ] Pengguna bisa mencari dan memfilter daftar transaksi.
- [ ] Sisa uang sama dengan total pemasukan dikurangi pengeluaran dan setoran tabungan.
- [ ] Pengeluaran kategori memperbarui indikator anggaran pada bulan yang sesuai.
- [ ] Anggaran kategori bisa diubah dan tetap tersimpan setelah refresh.
- [ ] Pengguna bisa membuat target dengan nominal positif dan tanggal target opsional.
- [ ] Setoran tidak bisa melebihi sisa uang tersedia atau sisa target.
- [ ] Penghapusan catatan setoran memperbarui saldo dan progres target.
- [ ] Laporan bulanan menghitung pemasukan, pengeluaran, setoran, arus uang, dan kategori berdasarkan bulan terpilih.
- [ ] Data contoh hanya bisa dimuat saat belum ada transaksi maupun target.
- [ ] Reset meminta konfirmasi sebelum menghapus data lokal.
- [ ] Navigasi, dialog, dan formulir dapat digunakan di layar kecil.

### Skenario uji perhitungan dasar
1. Pemasukan Rp150.000, pengeluaran Rp55.000, setoran Rp20.000 → sisa uang Rp75.000.
2. Target Rp300.000 dengan setoran Rp20.000 → progres 6,67% (ditampilkan sekitar 7%), sisa target Rp280.000.
3. Anggaran makanan Rp100.000, pengeluaran makanan Rp120.000 → kelebihan anggaran Rp20.000 dan indikator peringatan aktif.
4. Batas anggaran Rp0 → status kategori belum diatur, bukan persentase tak terhingga.
5. Menghapus setoran Rp20.000 dari skenario pertama → sisa uang meningkat menjadi Rp95.000 dan progres target berkurang sesuai setoran yang dihapus.

## 12. Tahapan implementasi

1. **Validasi masalah:** wawancara pelajar dan merangkum pola jawaban tanpa mengumpulkan data keuangan yang sensitif.
2. **Rancangan:** uji sketsa dashboard, formulir transaksi, anggaran, dan target.
3. **MVP:** bangun HTML, CSS responsif, JavaScript, penyimpanan lokal, dan validasi input.
4. **Pengujian:** uji hitungan, edit/hapus, refresh, tanggal, data kosong, dan viewport ponsel.
5. **Publikasi:** masukkan file ke repositori GitHub dan aktifkan GitHub Pages.
6. **Evaluasi:** kumpulkan masukan pengguna; prioritaskan perbaikan pada kemudahan pencatatan dan kejelasan ringkasan.

## 13. Risiko dan mitigasi

| Risiko | Mitigasi |
|---|---|
| Pengguna lupa mencatat transaksi | Form singkat, akses cepat, dan pengingat kebiasaan secara edukatif. |
| Pengguna memasukkan data keliru | Validasi nominal/tanggal dan dukungan edit/hapus untuk transaksi. |
| Pengguna mengira website menyimpan uang sungguhan | Gunakan istilah “catatan” dan “alokasi tabungan”; tampilkan disclaimer. |
| Data hilang saat browser dibersihkan | Jelaskan bahwa data lokal tidak sama dengan backup; ekspor data menjadi kandidat fitur berikutnya. |
| Fitur bertambah terlalu cepat | Utamakan MVP dan evaluasi berdasarkan penggunaan. |
| Tampilan sulit dipakai di ponsel | Uji ukuran layar 360 px, tombol besar, navigasi geser, dan tabel yang dapat digulir. |

---

**Keputusan MVP:** prioritaskan pencatatan, perhitungan saldo yang transparan, batas anggaran, dan target tabungan. Sinkronisasi akun, pengingat lanjutan, ekspor laporan, dan fitur sosial berada di luar lingkup versi pertama.

## Addendum — Responsivitas dan mini games

### Pengalaman lintas perangkat
- Navigasi desktop menggunakan sidebar; di layar ponsel ditambahkan navigasi bawah untuk halaman utama.
- Komponen, kartu, formulir, tombol, dan ruang antarbagian menyesuaikan lebar layar serta safe area perangkat.
- Animasi transisi halaman, hover, dekorasi hero, dan feedback mini games digunakan secara ringan.
- `prefers-reduced-motion` dihormati agar pengguna dapat mengurangi animasi melalui pengaturan sistem.

### Mini games offline
Mini games merupakan fitur edukasi opsional dan tidak terhubung dengan saldo maupun transaksi pengguna.
1. **Memori Hemat:** mencocokkan enam pasangan kartu, dengan penghitung langkah dan waktu.
2. **Kuis Duit Pintar:** lima pertanyaan pilihan ganda per ronde dengan penjelasan jawaban.
3. **Tantangan Anggaran:** lima skenario pengambilan keputusan keuangan sehari-hari dengan feedback.

Semua soal dan logika game berada di `script.js`. Permainan tidak memerlukan database, akun, paket eksternal, layanan jaringan, atau skor tersimpan. Skor berlangsung di memori sesi dan tidak mengubah catatan finansial. Tidak terdapat uang sungguhan, taruhan, atau hadiah berbayar.

### Kriteria penerimaan tambahan
- Navigasi utama dapat diakses melalui sidebar desktop dan navigasi bawah ponsel.
- Pada lebar layar 320 px dan lebih besar, halaman tidak menimbulkan scroll horizontal yang tidak disengaja.
- Ketiga mini games dapat dimainkan menggunakan klik/tap dan tombol ulangi.
- Kuis dan tantangan menampilkan feedback serta skor ronde.
- Game berfungsi tanpa request jaringan tambahan setelah file website dimuat.
- Animasi dikurangi jika preferensi `prefers-reduced-motion` pengguna aktif.


### Dukungan akses offline dan instalasi (tambahan)
- App shell inti (`index.html`, `style.css`, `script.js`, manifest, dan ikon) disimpan oleh service worker pada origin HTTPS.
- Setelah kunjungan online pertama berhasil mengisi cache, dashboard dan mini games dapat dibuka kembali tanpa koneksi selama file cache tidak dihapus oleh browser.
- Website menyediakan manifest untuk mendukung opsi pemasangan ke layar utama pada browser yang kompatibel.
- Mode offline bukan penyimpanan cloud: catatan finansial tetap ada di `localStorage` perangkat dan tidak disinkronkan.
