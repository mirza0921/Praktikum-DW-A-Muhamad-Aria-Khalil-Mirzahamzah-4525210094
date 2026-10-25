# Laporan Tugas Individu – Pertemuan 4: CSS Lanjutan, Box Model, dan Responsive Layout

## Identitas
- **Mata kuliah:** Praktikum Desain Web (A)
- **Topik:** External CSS, Box Model, Div, dan Responsive Layout
- **Nama:** Muhamad Aria Khalil Mirzahamzah
- **Semester:** 3
- **NIM:** 4525210094

## Ringkasan
Pada tugas ini saya membangun ulang halaman profil menjadi landing page sederhana untuk Arunika Studio. Halaman terdiri dari header, hero, tiga layanan, dan footer. Seluruh gaya dipisahkan ke file `CSS/style.css` dan dihubungkan melalui tag `<link>` di `index.html`, sehingga kode CSS tidak tersebar di dalam HTML.

Pada bagian box model, saya mengatur `box-sizing: border-box` pada selector universal `*` agar lebar elemen sudah mencakup padding dan border. Dengan pengaturan ini, ukuran kartu dan hero lebih mudah diprediksi. Saya juga mereset `margin` dan `padding` default browser agar jarak antar elemen dikontrol sepenuhnya oleh CSS.

Header memakai Flexbox dengan `justify-content: space-between`, sehingga logo berada di kiri dan menu navigasi di kanan. Header dibuat `position: sticky` dengan `top: 0` dan `z-index: 1000` agar tetap terlihat saat halaman digulir. Layanan ditampilkan dalam CSS Grid dengan tiga kolom menggunakan `repeat(3, 1fr)`. Setiap kartu memakai class `.card` yang dapat digunakan ulang, dengan latar putih, `box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1)`, dan efek `transform: translateY(-5px)` saat hover. Tombol "Hubungi Kami" memakai class `.button` yang juga dapat digunakan ulang, dengan `border-radius: 25px` agar berbentuk pill.

Untuk responsivitas, meta viewport sudah dipasang di `index.html`. Pada media query `max-width: 767px`, grid kartu berubah menjadi satu kolom, padding header dan hero dikecilkan, dan judul hero dibuat lebih kecil agar tetap nyaman dibaca di layar ponsel.

Masalah yang saya temui adalah menyusun ulang layout tiga kartu agar tetap rapi di desktop dan ponsel tanpa membuat banyak kode berulang. Solusinya adalah memakai CSS Grid dengan `repeat(3, 1fr)` sebagai dasar, lalu cukup mengganti jumlah kolom menjadi `1fr` di dalam media query. Masalah lain adalah header yang berantakan di layar kecil ketika menu dan logo berdampingan. Saya mengatasinya dengan `flex-wrap: wrap` dan `justify-content: center` pada media query.

