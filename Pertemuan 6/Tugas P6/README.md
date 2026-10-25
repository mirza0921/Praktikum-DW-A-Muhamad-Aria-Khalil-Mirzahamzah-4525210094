# Laporan Tugas Individu – Pertemuan 6: Mockup Halaman Web (Visual Hierarchy, Warna, dan Tipografi)

## Identitas
- **Mata kuliah:** Praktikum Desain Web (A)
- **Topik:** Mockup Dashboard Profile Restoran
- **Nama:** Muhamad Aria Khalil Mirzahamzah
- **Semester:** 3
- **NIM:** 4525210094

## Ringkasan
Pada tugas ini saya membuat mockup Dashboard Profile Restoran "Rasa Nusantara" dengan mengikuti struktur dan sistem desain dari contoh landing page Pertemuan 6. Mockup ini sudah memuat detail visual berupa warna, tipografi, bayangan, dan jarak, berbeda dengan wireframe pada Pertemuan 5 yang hanya menampilkan struktur abu-abu.

Struktur HTML mengikuti studi kasus. `<header>` berisi `<nav>` dengan placeholder logo di sisi kiri dan menu horizontal di sisi kanan (Beranda, Tentang, Fasilitas, Layanan, Kontak). Slot logo memakai file `Img/Logo.jpg` dan akan menampilkan teks "LOGO" jika file belum tersedia. `<main>` berisi head banner `<section class="hero">` sebagai highlight utama restoran, lalu `<section class="section content">` yang menampilkan tiga menu andalan dalam kartu. `<footer>` berisi informasi kontak dan hak cipta.

Warna dikelola melalui design tokens di `:root`. Warna primer terracotta (`#8c2f1b`) dipakai untuk tombol utama, label, dan ikon, sedangkan kuning hangat (`#e7a72d`) dipakai pada label di area CTA yang berwarna gelap. Latar krem dipakai untuk membedakan head banner dan area fasilitas dari area putih. Badge harga memakai hijau success (`#2e7d32`) agar menonjol. Hierarki visual dibentuk oleh ukuran judul yang berjenjang (h1 52px, h2 36px, h3 21px), label kecil berhuruf kapital di atas setiap judul bagian, dan kontras antara banner dan area konten.

Tipografi memakai satu keluarga font sans-serif (Arial) dengan `line-height: 1.7` agar teks mudah dibaca. Jarak antar elemen memakai skala spasi yang konsisten (8, 16, 24, 32, 48, 64px). Kartu menu dan kartu fasilitas memakai radius dan bayangan yang sama agar seragam.

Foto highlight dan foto tiap menu dimasukkan dengan tag `<img>` di dalam kotak `.placeholder-img`. Gambar dibuat menutupi kotak dengan `object-fit: cover`, dan teks placeholder disembunyikan otomatis saat gambar berhasil dimuat. Jika file tidak ditemukan, elemen `<img>` dihapus dan teks placeholder tetap tampil.

Pada layar di bawah 900px, head banner menjadi satu kolom dan grid menjadi dua kolom. Pada layar di bawah 600px, navbar tersusun vertikal, menu turun ke bawah logo, tombol aksi menjadi satu kolom, dan semua grid menjadi satu kolom.

Masalah yang saya temui adalah gambar belum tersedia, sehingga area foto kosong terlihat rusak di tampilan awal. Solusinya adalah memakai placeholder bergaris putus-putus dengan label teks yang akan tertimpa foto ketika file sudah ada. Masalah lain adalah logo terlalu besar di navbar. Saya memperkecil kotak logo dari 48px menjadi 36px dan teks "LOGO" dari 12px menjadi 9px. Masalah ketiga adalah CSS yang tersebar setelah beberapa kali revisi, sehingga ada aturan dobel dan komentar catatan. Saya merapikan `style.css` dengan menggabungkan aturan yang sama dan menghapus semua komentar.


