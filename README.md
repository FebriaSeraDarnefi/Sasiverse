<h1 align="center">SasiVerse</h1>

<p align="center">Sistem Informasi E-Commerce &amp; Digitalisasi Kain Sasirangan khas Banjar dengan integrasi Unique Product Code (UPC) QR Code, modul edukasi budaya, serta multi-tenant fulfillment untuk pemberdayaan UMKM lokal.</p>

<p align="center">
<a href="https://github.com/FebriaSeraDarnefi/Sasiverse"><img src="https://img.shields.io/badge/Laravel-13-FF2D20?logo=laravel&logoColor=white" alt="Laravel 13"></a>
<a href="https://www.php.net"><img src="https://img.shields.io/badge/PHP-8.3%2B-777BB4?logo=php&logoColor=white" alt="PHP 8.3+"></a>
<a href="https://tailwindcss.com"><img src="https://img.shields.io/badge/Tailwind%20CSS-3-06B6D4?logo=tailwindcss&logoColor=white" alt="Tailwind CSS"></a>
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License"></a>
</p>

## Tentang SasiVerse

SasiVerse adalah sistem informasi e-commerce dan digitalisasi **kain Sasirangan**, kain tradisional khas Banjar, Kalimantan Selatan. Platform ini memberdayakan UMKM lokal lewat toko online multi-tenant: setiap UMKM mengelola produk dan pengirimannya sendiri, sementara pembeli berbelanja dari banyak UMKM dalam satu keranjang. Setiap produk dilengkapi **Unique Product Code (UPC) QR Code** sebagai identitas digital, dan platform disiapkan untuk modul edukasi budaya Sasirangan. Fitur utamanya:

- Katalog produk publik dengan halaman detail berbasis slug.
- Unique Product Code (UPC) QR Code untuk setiap produk aktif, bisa dilihat dan diunduh oleh UMKM.
- Multi-tenant fulfillment: pesanan dipecah per UMKM, dan tiap UMKM mengemas serta mengirim bagiannya sendiri.
- Pendaftaran UMKM dengan verifikasi admin (setujui, tolak, nonaktifkan).
- Keranjang belanja dan checkout untuk customer.
- Pembayaran transfer bank dengan unggah bukti bayar dan verifikasi admin.
- Pengelolaan pesanan oleh UMKM: dikemas, dikirim, lalu dikonfirmasi diterima oleh customer.
- Tiga peran pengguna (`admin`, `umkm`, `customer`) dengan dashboard masing-masing.

SasiVerse dibangun dengan [Laravel](https://laravel.com), [Laravel Breeze](https://laravel.com/docs/starter-kits#laravel-breeze), Blade, [Tailwind CSS](https://tailwindcss.com), [Alpine.js](https://alpinejs.dev), dan [Vite](https://vitejs.dev).

## Peran Pengguna

| Peran | Akses |
|-------|-------|
| `admin` | Verifikasi UMKM dan pembayaran |
| `umkm` | Kelola produk, pesanan masuk, profil usaha, QR Code |
| `customer` | Keranjang, checkout, pembayaran, riwayat pesanan |

Produk hanya tampil di katalog dan bisa dibeli setelah UMKM berstatus **aktif**.

## Alur Transaksi

1. UMKM mendaftar, lalu admin menyetujui.
2. UMKM menambahkan produk.
3. Customer memasukkan produk ke keranjang dan checkout.
4. Customer transfer ke rekening toko dan mengunggah bukti bayar (JPG, JPEG, PNG, WEBP, maksimal 4 MB).
5. Admin menyetujui atau menolak pembayaran.
6. UMKM mengemas dan mengirim pesanan.
7. Customer menandai pesanan telah diterima.

## Instalasi

Prasyarat: PHP 8.3 atau lebih baru, [Composer](https://getcomposer.org), Node.js, dan npm.

```bash
git clone https://github.com/FebriaSeraDarnefi/Sasiverse.git
cd Sasiverse

composer install
npm install

cp .env.example .env
php artisan key:generate

touch database/database.sqlite   # Windows: type nul > database\database.sqlite
php artisan migrate --seed
php artisan storage:link

npm run build
```

Untuk pengembangan, jalankan server, antrean, log, dan Vite sekaligus:

```bash
composer run dev
```

Lalu buka `http://localhost:8000`.

## Konfigurasi Pembayaran

Rekening tujuan transfer dibaca dari `config/payment.php`. Tambahkan di `.env`:

```env
PAYMENT_BANK_NAME="Nama Bank"
PAYMENT_ACCOUNT_NUMBER="1234567890"
PAYMENT_ACCOUNT_HOLDER="Nama Pemilik Rekening"
```

## Akun Contoh

Setelah `php artisan migrate --seed`, tersedia akun untuk pengembangan lokal:

| Peran | Email | Kata sandi |
|-------|-------|------------|
| Admin | `admin@sasiverse.test` | `password` |
| UMKM | `umkm@sasiverse.test` | `password` |
| Customer | `customer@sasiverse.test` | `password` |

> Akun ini hanya untuk pengembangan lokal. Ganti semua kata sandi sebelum deploy ke server produksi.

## Pengujian

```bash
composer test
```

## Belajar Laravel

Laravel memiliki [dokumentasi](https://laravel.com/docs) dan pustaka video tutorial yang lengkap. [Laracasts](https://laracasts.com) berisi ribuan video tentang Laravel, PHP modern, pengujian, dan JavaScript. Kamu juga bisa belajar membangun aplikasi dari nol lewat [Laravel Learn](https://laravel.com/learn).

## Kontribusi

Terima kasih sudah tertarik berkontribusi pada SasiVerse. Silakan buka [Issue](https://github.com/FebriaSeraDarnefi/Sasiverse/issues) atau kirim Pull Request.

## Keamanan

Jika kamu menemukan celah keamanan di SasiVerse, jangan dipublikasikan. Hubungi pemilik repositori secara langsung lewat profil [FebriaSeraDarnefi](https://github.com/FebriaSeraDarnefi).

## Lisensi

SasiVerse dibangun di atas framework Laravel, perangkat lunak open-source berlisensi [MIT](https://opensource.org/licenses/MIT).
