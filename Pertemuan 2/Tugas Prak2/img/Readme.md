# Website Fakultas Teknik Universitas Pancasila

Halaman web statis berbasis HTML untuk memperkenalkan Fakultas Teknik Universitas Pancasila (FTUP).

## Fitur

- Navigasi antar bagian (profil, program studi, alur pendaftaran, fasilitas, kontak)
- Daftar program studi dan alur pendaftaran mahasiswa baru
- Informasi kontak dan tautan ke website resmi

## Struktur Proyek

```
├── index.html
├── css/
│   └── style.css
└── gedung-ftup.jpg
```

## Cara Menjalankan

1. Unduh atau clone repositori ini.
2. Buka `index.html` di browser.

## Perubahan

- Struktur halaman memakai tag semantik (`header`, `nav`, `section`).
- CSS dipisah ke `css/style.css`.
- Ditambahkan gambar dengan atribut `alt` dan `title`, serta HTML entities.

## Masalah dan Solusi

| Masalah | Solusi |
|---|---|
| Tautan email tanpa `mailto:` sehingga tidak membuka aplikasi email | Gunakan `href="mailto:teknik@univpancasila.ac.id"` |
| Salah ketik "Tenik Mesin" | Ganti menjadi "Teknik Mesin" |
| Kalimat profil kurang baku dan jelas | Susun ulang kalimat agar lebih rapi |
| `<img>` berada langsung di dalam `<dl>` (tidak valid) | Pindahkan ke luar `<dl>` atau bungkus dengan `<figure>` |
| Gambar sama dipakai dua kali dan nama berkas memakai spasi | Gunakan gambar berbeda dan nama berkas tanpa spasi |

## Pembuat

Muhamad Aria Khalil Mirzahamzah, Fakultas Teknik Universitas Pancasila, 2026.