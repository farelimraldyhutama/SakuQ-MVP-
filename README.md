# SakuQ — Website pengelola uang saku

Prototipe SakuQ membantu pelajar mencatat pemasukan/pengeluaran, membuat anggaran, dan memantau target tabungan.

## File
- `index.html` — struktur halaman dan dialog formulir.
- `style.css` — layout, tema visual, responsivitas, dan komponen antarmuka.
- `script.js` — perhitungan, validasi, navigasi, dan penyimpanan `localStorage`.
- `PRD.md` — dokumen kebutuhan produk, rumus, model data, serta kriteria keberhasilan.
- `manifest.webmanifest` dan `icon.svg` — metadata untuk pemasangan di perangkat.
- `service-worker.js` — cache file inti agar website dapat dibuka kembali saat offline.

## Menjalankan di komputer
1. Unduh atau ekstrak semua file ke satu folder.
2. Buka `index.html` dengan browser modern, atau gunakan ekstensi Live Server di editor kode.
3. Coba tambah pemasukan, pengeluaran, anggaran, dan target tabungan.
4. Data tersimpan di `localStorage` browser yang sedang digunakan.

Tombol **Coba data contoh** di dashboard mengisi data ilustrasi agar fitur dapat dicoba. Gunakan **Reset semua data** di sidebar untuk menghapus semua catatan lokal setelah konfirmasi.

## Rumus saldo
`Sisa uang tersedia = total pemasukan − total pengeluaran − total setoran tabungan`.

Setoran tabungan bukan pengeluaran konsumsi, tetapi mengurangi uang tersedia karena dicatat sebagai uang yang telah dialokasikan untuk tujuan tabungan.

## Menerbitkan melalui GitHub Pages
1. Buat repositori GitHub baru.
2. Unggah `index.html`, `style.css`, `script.js`, `README.md`, dan `PRD.md` ke root repositori.
3. Buka **Settings → Pages**.
4. Di bagian build/deployment, pilih sumber dari branch (misalnya `main`) dan folder root (`/`).
5. Simpan pengaturan dan tunggu proses publikasi selesai. Buka URL yang ditampilkan GitHub Pages.

## Batasan prototipe
- Tidak ada login atau database server.
- Data hanya tersimpan di browser/perangkat terkait; tidak tersinkron antarperangkat.
- Jangan memasukkan PIN, kata sandi, nomor rekening, atau informasi finansial sensitif.
- SakuQ bukan layanan bank dan tidak memproses uang sungguhan.


## Tampilan responsif

SakuQ menggunakan layout responsif untuk desktop, tablet, dan ponsel. Navigasi berubah menjadi menu samping yang dapat dibuka di layar kecil; kartu dan formulir menyesuaikan lebar layar; tabel transaksi dapat digeser secara horizontal. Untuk mencoba, buka `index.html` atau gunakan Live Server di VS Code.


## Mini games offline
- **Memori Hemat** — cari 6 pasangan kartu; ada penghitung langkah dan waktu.
- **Kuis Duit Pintar** — lima soal edukasi keuangan dengan penjelasan.
- **Tantangan Anggaran** — simulasi keputusan keuangan sehari-hari.

Mini games ditulis langsung di `script.js`, tanpa database, login, paket eksternal, atau permintaan jaringan saat dimainkan. Skor hanya berada di memori sesi dan tidak tersimpan setelah halaman dimuat ulang.

## Responsif dan animasi
Navigasi bawah untuk ponsel, drawer menu, kartu adaptif, safe-area spacing, animasi hover/transisi, dan dukungan `prefers-reduced-motion` disediakan di `style.css`.


## Akses offline dan pemasangan di ponsel
SakuQ mendaftarkan service worker pada HTTPS (termasuk GitHub Pages) untuk menyimpan app shell. Buka situs ketika online dan tunggu sampai halaman selesai dimuat agar cache awal terisi. Setelah file berhasil di-cache, dashboard dan mini games dapat dibuka kembali tanpa koneksi. Browser mungkin perlu satu pemuatan online awal untuk mengunduh file dan service worker.

Di Android, buka situs SakuQ melalui Chrome, buka menu browser, lalu pilih **Install app** atau **Add to Home screen** jika opsi tersebut tersedia. Penginstalan bergantung pada dukungan browser dan status service worker.
