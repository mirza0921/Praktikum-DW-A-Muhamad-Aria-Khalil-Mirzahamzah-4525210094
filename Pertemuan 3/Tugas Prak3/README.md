# Laporan Tugas Individu – Pertemuan 5: External CSS pada Website CV

## Identitas
- **Mata kuliah:** Praktikum Desain Web (A)
- **Topik:** External CSS, Selector, dan Struktur Multi-Halaman
- **Nama:** Muhamad Aria Khalil Mirzahamzah
- **Semester:** 3
- **NPM:** 4525210094

## Ringkasan
Pada tugas ini saya membuat website CV yang terdiri dari tiga halaman, yaitu `index.html` (Beranda), `pendidikan.html` (Pendidikan), dan `kontak.html` (Kontak). Seluruh tampilan dipisahkan ke satu file eksternal `css/style.css` dan dihubungkan ke setiap halaman melalui tag `<link>`. Dengan cara ini, perubahan warna atau font cukup dilakukan di satu tempat dan langsung berlaku di ketiga halaman.

Di dalam CSS, saya membagi kode menjadi beberapa bagian. Bagian pertama berisi variabel warna dan font di `:root`, yaitu palet biru laut, tosca, dan kuning, sehingga mudah diubah. Element selector digunakan untuk tag umum seperti `body`, `header`, `h2`, `p`, `a`, `table`, dan `footer`. ID selector `#judul` dipakai untuk nama pemilik CV di header. Class selector `.foto`, `.jabatan`, `.biodata`, `.catatan`, dan `.aktif` dipakai untuk elemen yang butuh gaya khusus, misalnya foto profil berbentuk lingkaran dengan bingkai kuning dan menu yang sedang dibuka. Tampilan untuk layar HP diatur dengan media query `max-width: 600px`, sehingga header berubah menjadi kolom dan judul diperkecil.

Setiap halaman memiliki header dan menu navigasi yang sama. Pada menu, halaman yang sedang dibuka diberi class `aktif` dan `aria-current="page"` agar pengguna tahu posisinya. Konten utama memakai tabel untuk data diri, riwayat pendidikan, dan keahlian.

Masalah yang saya temui adalah menjaga agar header dan menu tetap sama di setiap halaman, karena perubahan kecil pada satu file bisa membuat halaman lain tidak konsisten. Solusinya adalah menyalin struktur header dan nav dengan teliti, serta menyimpan semua gaya di satu file CSS sehingga tampilan tidak perlu diatur ulang di setiap halaman. Masalah lain adalah path gambar dan CSS yang harus sesuai dengan struktur folder. Saya menyelesaikannya dengan menempatkan `css/style.css` dan `img/khalil.jpeg` dalam subfolder yang sama dengan halaman HTML, lalu memastikan penulisan path dan huruf besar-kecil nama file sudah sama.

## Struktur Folder
```
CV/
├── index.html
├── pendidikan.html
├── kontak.html
├── css/
│   └── style.css
└── img/
    └── khalil.jpeg
```

