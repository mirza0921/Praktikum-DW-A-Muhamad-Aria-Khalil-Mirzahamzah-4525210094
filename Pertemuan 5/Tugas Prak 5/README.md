# Laporan Tugas Individu – Pertemuan 5: Wireframe Portal Perpustakaan Umum

## Identitas
- **Mata kuliah:** Praktikum Desain Web (A)
- **Topik:** Wireframe Low-Fidelity dengan External CSS dan Responsive Layout
- **Nama:** Muhamad Aria Khalil Mirzahamzah
- **Semester:** 3
- **NIM:** 4525210094

## Ringkasan
Pada tugas ini saya membuat wireframe low-fidelity untuk dashboard portal perpustakaan umum. Wireframe ini hanya menampilkan struktur dan posisi elemen dengan warna abu-abu, tanpa menentukan warna brand atau font final, sehingga fokusnya ada pada tata letak. Halaman terdiri dari header dengan slot logo dan foto profil yang bisa diunggah, sidebar menu, area konten dengan lima bagian (Beranda, Daftar Buku, Peminjaman, Layanan, dan Kontak), serta footer.

Seluruh gaya berada di `css/style.css` dan dihubungkan melalui `<link>` di `index.html`. Warna dan ukuran teks dikelola dengan variabel di `:root`, sehingga nilai abu-abu bisa diubah dari satu tempat. Selector universal `*` memakai `box-sizing: border-box` dan mereset margin serta padding. Kotak-kotak wireframe memakai class `.wf-box` yang digunakan ulang di banyak elemen, dan kartu ringkasan, kartu layanan, serta kartu buku memakai class `.card` dan `.book` yang juga dapat digunakan ulang.

Layout utama memakai CSS Grid dua kolom dengan lebar sidebar 220px dan area konten `1fr`. Ringkasan buku dan layanan memakai grid tiga kolom, daftar buku memakai `repeat(auto-fill, minmax(160px, 1fr))`, dan kontak memakai dua kolom. Sidebar dibuat `position: sticky` agar tetap terlihat saat halaman digulir. Placeholder logo, cover buku, dan foto profil menggunakan border putus-putus dan `repeating-linear-gradient` agar terlihat seperti area kosong.

Untuk responsivitas, media query `max-width: 767px` mengubah layout menjadi satu kolom, sidebar menjadi deret tombol horizontal, grid kartu menjadi satu kolom, grid buku menjadi dua kolom, dan header menjadi tersusun vertikal.

Pada `index.html`, struktur memakai elemen semantik `header`, `aside`, `main`, dan `footer`. Setiap bagian diberi `id` dan class `.section`, lalu JavaScript hanya menampilkan bagian yang sesuai dengan `#hash` di URL. Foto profil dapat diganti dengan `URL.createObjectURL`, dan jika file gambar belum tersedia, `onerror` akan menghapus gambar sehingga teks placeholder tetap terlihat.

Masalah yang saya temui adalah sidebar yang tidak nyaman di layar kecil karena daftar menu panjang ke bawah. Solusinya adalah mengubah `ul` menjadi `flex-direction: row` dengan `flex-wrap: wrap` di media query. Masalah lain adalah placeholder gambar yang tetap tampil bersamaan dengan gambar asli. Saya mengatasinya dengan `onload` yang menyembunyikan teks placeholder ketika gambar berhasil dimuat dan `onerror` yang menghapus gambar jika file tidak ditemukan.

