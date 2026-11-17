# Selaras Coffee: Company Profile Satu Halaman (Bootstrap 5)
| | |
|---|---|
| **Mata Kuliah** | Praktikum Desain Web (A) |
| **Topik** | Bootstrap Lanjutan dan Modifikasi CSS |
| **Nama** | Muhamad Aria Khalil Mirzahamzah |
| **Semester** | 3 |
| **NIM** | 4525210094 |

## Cara menjalankan

1. Buka `index.html` di browser.
2. Komputer harus terhubung internet, karena Bootstrap, font, dan Bootstrap Bundle JS dimuat dari CDN.
3. Untuk cek tampilan HP, buka DevTools (F12), lalu aktifkan mode perangkat (Ctrl+Shift+M).

## Struktur folder

```
selaras-coffee/
├── index.html      # Halaman utama
├── css/
│   └── style.css   # Stylesheet custom untuk branding (dipanggil setelah Bootstrap)
└── README.md       # Penjelasan dan catatan pengerjaan
```

## Komponen yang dipenuhi

| Ketentuan tugas | Implementasi di `index.html` |
|---|---|
| Navbar responsif | `navbar-expand-lg`, `navbar-toggler`, dan `.collapse`. Menu berubah menjadi hamburger di bawah 1024px. |
| Hero | Judul, deskripsi, dua tombol aksi, dan ilustrasi kopi berbentuk SVG. |
| Tiga card produk | Grid `col-12 col-md-6 col-lg-4`: 1 kolom di HP, 2 kolom di tablet, 3 kolom di laptop. |
| Satu alert | Alert promo `alert-dismissible` dengan tombol tutup. |
| Satu modal | Modal `#modalProduk`. Isinya berubah sesuai tombol "Detail" yang diklik. |
| Form kontak | `form-control`, `form-select`, dan `form-label`, dengan validasi sederhana di JavaScript. |
| Footer | Jam buka, akun media sosial, dan hak cipta. |
| Stylesheet custom | `css/style.css`, dipanggil setelah Bootstrap. |

## Fungsi container, row, dan column

| Lapis | Class | Fungsi pada halaman ini |
|---|---|---|
| Container | `container` | Membungkus konten setiap section, sehingga lebar dibatasi dan konten berada di tengah. |
| Row | `row` | Mengelompokkan kolom secara horizontal: hero, deretan card produk, dan bagian kontak. `g-3`, `g-4`, dan `g-5` mengatur jarak antar kolom. |
| Column | `col-12`, `col-md-6`, `col-lg-4`, dan lainnya | Membagi lebar 12 kolom dalam satu row. Card produk berubah dari 1 ke 2 ke 3 kolom. |

Hierarki yang dipakai: `container` → `row` → `col-*` → isi (card, form, teks). Column selalu berada di dalam row, dan row selalu berada di dalam container.

## Perubahan layout per ukuran layar

Breakpoint Bootstrap yang dipakai: `md` untuk tablet (mulai 768px) dan `lg` untuk laptop (mulai 1024px).

| Bagian | HP (< 768px) | Tablet (≥ 768px) | Laptop (≥ 1024px) |
|---|---|---|---|
| Navbar | Menu tersembunyi, dibuka lewat hamburger | Sama seperti HP | Menu horizontal, tombol "Pesan Sekarang" di kanan |
| Hero | Teks di atas, ilustrasi di bawah. Tombol bertumpuk (`flex-column`). | Tombol sejajar (`flex-sm-row`) | Teks di kiri, ilustrasi di kanan |
| Card produk | 1 kolom (`col-12`) | 2 kolom (`col-md-6`) | 3 kolom (`col-lg-4`) |
| Kontak | Info di atas, form di bawah | Sama seperti HP | Info di kiri, form di kanan (`col-lg-5` dan `col-lg-7`) |
| Form | 1 kolom | Nama dan email sejajar (`col-md-6`) | Sama seperti tablet |

## Override CSS dan custom theme

- **Urutan pemanggilan:** `bootstrap.min.css` dipanggil lebih dulu, lalu `css/style.css`, sehingga aturan custom menimpa gaya bawaan.
- **Design tokens:** warna merek disimpan di `:root` sebagai `--brand-primary` (espresso), `--brand-accent` (crema), `--brand-paper`, `--brand-sage`, dan `--brand-card`. Mengganti warna cukup dilakukan di satu tempat.
- **Custom class:** `.custom-navbar`, `.custom-link`, `.brand-logo`, `.btn-brand`, `.btn-outline-brand`, `.product-card`, `.hero-art`, `.form-control-brand`, dan `.modal-brand`.
- **Tanpa `!important` yang berlebihan:** tombol memakai variabel `--bs-btn-*` Bootstrap. Satu-satunya `!important` ada di blok `prefers-reduced-motion`, yang memang diperlukan untuk mematikan animasi.

## Utility classes yang dipakai

`bg-*` dan `text-*` dari token custom, `py-3`, `py-5`, `py-lg-0`, `px-3`, `px-4`, `p-4`, `p-md-5`, `mb-0` sampai `mb-5`, `mt-2`, `mt-3`, `mt-auto`, `mt-lg-0`, `mx-auto`, `my-4`, `ms-auto`, `ms-lg-2`, `pt-0`, `pt-2`, `pb-0`, `gap-2`, `gap-3`, `gap-lg-2`, `g-3`, `g-4`, `g-5`, `order-1`, `order-2`, `order-lg-1`, `order-lg-2`, `text-center`, `text-lg-start`, `text-muted`, `fw-bold`, `fw-semibold`, `small`, `lead`, `d-flex`, `d-none`, `flex-column`, `flex-sm-row`, `justify-content-center`, `justify-content-between`, `justify-content-lg-start`, `align-items-center`, `align-items-lg-center`, `align-items-start`, `h-100`, `w-100`, `list-unstyled`, `border-0`, dan `shadow`.

Komponen Bootstrap yang dipakai:
- Navbar: `navbar`, `navbar-expand-lg`, `navbar-brand`, `navbar-toggler`, `navbar-collapse`, `navbar-nav`
- Card: `card`, `card-body`
- Alert: `alert`, `alert-dismissible`, `alert-success`, `btn-close`
- Button: `btn`, `btn-lg`, `btn-sm`
- Form: `form-control`, `form-select`, `form-label`
- Modal: `modal`, `modal-dialog`, `modal-dialog-centered`, `modal-content`, `modal-header`, `modal-body`, `modal-footer`

## Catatan pengerjaan (perubahan, masalah, dan solusi)

Isi bagian ini dengan hasil pengujian Anda sendiri setelah melihat tampilan di HP, tablet, dan laptop. Contoh yang perlu dicek:

| Perubahan | Masalah yang mungkin muncul | Solusi yang diterapkan |
|---|---|---|
| Navbar memakai `sticky-top` | Judul section tertutup navbar saat dituju lewat link menu | `scroll-margin-top: 90px` pada `section[id]` di `style.css` |
| Card produk memakai `h-100` dan `mt-auto` | Tinggi card tidak sama, atau harga tidak sejajar | Card dibuat setinggi baris, dan bagian harga didorong ke bawah dengan `mt-auto` |
| Modal diisi lewat `data-*` | Modal menampilkan isi produk sebelumnya | Event `show.bs.modal` mengisi ulang judul, harga, dan deskripsi setiap kali dibuka |
| Ilustrasi hero dibuat dengan SVG | Gambar terlalu besar di HP | `max-width` diperkecil di layar kecil lewat `@media (max-width: 575.98px)` |
| Hero memakai `py-lg-6` | Class tersebut tidak ada di Bootstrap, sehingga spacing tidak berlaku | Diganti menjadi `py-5` |

Tulis masalah yang benar-benar Anda temui, atau hapus baris contoh di atas.

## Catatan teknis

- Form kontak hanya simulasi di sisi klien. Tidak ada data yang dikirim ke server.
- Tidak ada gambar eksternal. Ilustrasi dibuat dengan SVG di dalam HTML.

