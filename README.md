# LANGIT BIRU — Premium Colorful E-Commerce Platform

Website toko online statis berbahasa Indonesia dengan desain colorful, sidebar kiri pada storefront dan admin, katalog, pencarian, filter, pengurutan, detail produk, wishlist, keranjang, checkout WhatsApp, riwayat lokal, dashboard admin, manajemen produk/kategori, pengaturan, dan cadangan JSON.

## Mulai cepat

1. Ekstrak ZIP proyek.
2. Unggah isi folder `langit-biru/` ke repository GitHub bernama `langit-biru`.
3. Aktifkan GitHub Pages pada **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.
4. Setelah deployment selesai, buka URL yang ditampilkan GitHub Pages.
5. Halaman toko berada di root; halaman admin ada di `/admin/`.

## Fitur yang tersedia

- **Storefront:** beranda, kategori, katalog, pencarian, filter kategori/harga/stok/diskon, pengurutan, halaman detail, wishlist, keranjang, validasi stok, dan tema terang/gelap.
- **Checkout:** membuat referensi pesanan lokal dan ringkasan yang dibuka melalui WhatsApp. Nomor WhatsApp harus diisi lebih dulu di admin. Pengguna perlu meninjau dan mengirim pesan sendiri.
- **Admin:** gerbang kode akses demo yang dibuat saat penggunaan pertama, dashboard dengan angka aktual, tambah/edit/hapus dan publikasi produk, kategori CRUD dengan perlindungan kategori yang masih dipakai, daftar dan perubahan status pesanan lokal, pengaturan toko, serta ekspor/impor JSON.
- **Aset:** logo/favicon dan ilustrasi produk SVG disertakan secara lokal. Tidak membutuhkan framework atau proses build.
- **Identitas developer:** MUSYAFFA HANIF SUNNI · JURUSAN TJKT · SMK NEGERI 1 ADIWERNA.

## Batasan penting

- **LocalStorage hanya berlaku untuk browser/perangkat yang sama.** Perubahan produk, pesanan, kategori, wishlist, dan pengaturan tidak tersinkron ke browser atau perangkat lain.
- **Gerbang admin bukan autentikasi aman.** Kode akses disimpan sebagai hash pada browser, tetapi JavaScript dan LocalStorage dapat diperiksa atau diubah oleh pengguna yang memiliki akses teknis. Jangan simpan data rahasia atau gunakan ini sebagai perlindungan admin produksi.
- **Checkout WhatsApp bukan pemrosesan pesanan otomatis.** Situs menyimpan salinan lokal dan membuka pesan yang sudah disiapkan. Pesanan baru dikonfirmasi setelah pembeli mengirim pesan dan toko menanggapinya.
- **Tidak ada payment gateway atau kalkulasi ongkir bawaan.** Ongkir dan instruksi pembayaran dikonfirmasi secara manual. Tidak ada biaya fiktif yang ditambahkan ke total produk.
- Data awal berisi contoh katalog untuk membantu melihat desain. Sesuaikan harga, stok, deskripsi, serta pengaturan sebelum dipakai untuk toko sungguhan.
- Fitur berbasis JavaScript module biasanya lebih tepat diuji melalui HTTP/GitHub Pages daripada dengan membuka file HTML langsung melalui `file://`.

## Atur WhatsApp toko

1. Buka halaman `admin/` pada browser.
2. Pada kunjungan pertama, buat kode akses demo minimal 8 karakter. Tidak ada kode akses bawaan.
3. Buka **Pengaturan Toko**.
4. Isi nomor WhatsApp aktif. Format `08...` atau `62...` diterima; simpan dalam format kode negara bila memungkinkan, contoh format `6281234567890`.
5. Simpan. Nomor ini akan dipakai sebagai tujuan link WhatsApp pada checkout.

Sesi login demo berada di tab/browser yang sedang digunakan. Jika sesi berakhir, masuk kembali menggunakan kode akses tersebut. Karena tidak ada backend, login tersebut bukan pengamanan tingkat server.

## Struktur proyek

```text
langit-biru/
├── index.html
├── README.md
├── favicon.svg
├── assets/
│   ├── icons/logo.svg
│   └── images/             # Ilustrasi produk SVG lokal
├── css/
│   ├── style.css
│   ├── components.css
│   └── responsive.css
├── js/
│   ├── app.js
│   ├── storage.js
│   ├── cart.js
│   ├── wishlist.js
│   └── theme.js
└── admin/
    ├── index.html
    ├── admin.css
    └── admin.js
```

Logika katalog, detail produk, dan checkout dikelola di `js/app.js`; penyimpanan, keranjang, wishlist, dan tema dipisahkan dalam modul tersendiri.

## Tutorial Termux di HP Android

### 1. Siapkan Termux

```bash
termux-setup-storage
pkg update && pkg install git unzip -y
```

Izinkan akses penyimpanan jika diminta. Letakkan `Langit_Biru_GitHub_Pages.zip` pada folder **Download**.

### 2. Ekstrak ZIP

```bash
mkdir -p ~/langit-biru
unzip -o ~/storage/downloads/Langit_Biru_GitHub_Pages.zip -d ~/langit-biru
cd ~/langit-biru/langit-biru
ls -la
ls index.html
```

ZIP ini berisi folder proyek bernama `langit-biru/`, sehingga setelah diekstrak folder proyek berada di `~/langit-biru/langit-biru`. Pastikan perintah `ls index.html` menampilkan file tersebut sebelum melanjutkan.

### 3. Siapkan identitas Git

Ganti nilai contoh di bawah dengan nama dan email yang ingin ditampilkan pada commit Git:

```bash
git config --global user.name "NAMA_GITHUB_KAMU"
git config --global user.email "EMAIL_GITHUB_KAMU"
```

### 4. Commit dan upload ke GitHub

Buat repository kosong bernama **langit-biru** pada akun GitHub. Tidak perlu menambahkan README dari GitHub ketika membuat repository karena README sudah ada di proyek. Kemudian jalankan:

```bash
git init
git branch -M main
git add .
git commit -m "Initial Langit Biru website"
git remote add origin https://github.com/USERNAME/langit-biru.git
git push -u origin main
```

Ganti `USERNAME` dengan username GitHub milikmu. Jika sebelumnya remote sudah ditambahkan, jangan ulangi `git remote add origin`; periksa dengan `git remote -v` atau ubah alamat remote memakai `git remote set-url origin https://github.com/USERNAME/langit-biru.git`.

Jika GitHub meminta autentikasi, ikuti metode resmi GitHub, misalnya login melalui browser atau token yang memiliki izin yang diperlukan. **Jangan masukkan password akun GitHub langsung sebagai password Git.** Jangan membagikan token kepada orang lain.

### 5. Aktifkan GitHub Pages

1. Buka repository `langit-biru` di GitHub.
2. Pilih **Settings**.
3. Buka menu **Pages**.
4. Pada bagian publikasi, pilih **Deploy from a branch** bila opsi tersedia.
5. Pilih branch `main` dan folder `/ (root)`.
6. Tekan **Save**.
7. Tunggu sampai status deployment berhasil, lalu buka URL yang ditampilkan GitHub Pages. Pola URL project page biasanya `https://USERNAME.github.io/langit-biru/`; URL aktual bergantung pada username dan status deployment.

### 6. Memperbarui website

Setelah mengubah file di folder proyek yang sama:

```bash
cd ~/langit-biru/langit-biru
git add .
git commit -m "Update Langit Biru"
git push
```

## Pemeriksaan sebelum dipakai

- Pastikan storefront dan admin dibuka melalui URL GitHub Pages setelah deploy.
- Atur kode akses demo dan nomor WhatsApp toko.
- Uji tambah/edit produk, kategori, filter katalog, keranjang, checkout, dan ekspor cadangan.
- Buat file cadangan JSON sebelum mencoba impor yang menimpa data.
- Jangan menganggap statistik admin sebagai laporan bisnis lintas perangkat karena semuanya dihitung dari LocalStorage lokal.

Versi proyek: **1.0.0**.
