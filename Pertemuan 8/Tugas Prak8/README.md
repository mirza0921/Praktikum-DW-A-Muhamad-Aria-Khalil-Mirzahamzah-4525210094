# Form Pendaftaran Kursus

| | |
|---|---|
| **Mata Kuliah** | Praktikum Desain Web (A) |
| **Topik** | Pilihan, Upload, Textarea, dan Validasi HTML |
| **Nama** | Muhamad Aria Khalil Mirzahamzah |
| **Semester** | 3 |
| **NIM** | 4525210094 |

---

## 1. Struktur Folder

```
pendaftaran-kursus/
├── index.html   # struktur form (HTML5)
├── style.css    # tampilan dan status validasi (CSS)
└── README.md    # dokumentasi ini
```

## 2. Cara Menjalankan

1. Unduh folder `pendaftaran-kursus`.
2. Buka `index.html` di browser (Chrome, Edge, atau Firefox versi terbaru).
3. Tidak perlu server atau instalasi tambahan.

## 3. Elemen Form yang Digunakan

| Jenis | Elemen | Keterangan |
|---|---|---|
| Teks | `<input type="text">` | Nama lengkap |
| Email | `<input type="email">` | Format email |
| Telepon | `<input type="tel">` | Pola angka dengan `pattern` |
| Select | `<select>` | Pilih kursus |
| Radio | `<input type="radio">` ×3 | Jenis kelas (Online, Offline, Hybrid), satu grup `name="kelas"` |
| Checkbox | `<input type="checkbox">` ×3 | Fasilitas tambahan (opsional) |
| Textarea | `<textarea>` | Tujuan belajar |
| Upload | `<input type="file">` | Bukti pembayaran (`accept` PDF/JPG/PNG) |
| Persetujuan | `<input type="checkbox" required>` | Syarat dan ketentuan |
| Button | `type="submit"`, `type="reset"`, `type="button"` | Tiga jenis tombol |

## 4. Aturan Validasi

| No | Field | Aturan | Atribut HTML5 |
|---|---|---|---|
| 1 | Nama | Wajib, 3 sampai 60 karakter | `required`, `minlength`, `maxlength` |
| 2 | Email | Wajib, format email | `type="email"`, `required` |
| 3 | Telepon | Wajib, diawali 08, 10 sampai 13 digit | `pattern="08[0-9]{8,11}"`, `required` |
| 4 | Kursus | Wajib pilih satu | `required` pada select |
| 5 | Jenis kelas | Wajib pilih satu | `required` pada radio |
| 6 | Tujuan belajar | Wajib, 20 sampai 200 karakter | `required`, `minlength`, `maxlength` |
| 7 | Bukti bayar | Wajib, dipilih dengan filter PDF/JPG/PNG | `required`, `accept` |
| 8 | Persetujuan | Wajib dicentang | `required` |

**Catatan:** HTML murni tidak bisa membatasi ukuran berkas. Atribut `accept` hanya menyaring di dialog pilihan file, dan pengguna masih bisa memilih "All files". Batas 2 MB dan pengecekan isi berkas harus dilakukan di server.

## 5. Fungsi Tiga Jenis Button

- **Daftar Sekarang** (`type="submit"`): mengirim form. Browser menahan pengiriman jika ada isian yang belum sesuai aturan, lalu menampilkan pesan di kolom tersebut.
- **Bersihkan** (`type="reset"`): mengembalikan semua isian ke nilai awal.
- **Batal** (`type="button"`): tombol tanpa aksi bawaan. Tanpa JavaScript, tombol ini hanya contoh jenis tombol dan tidak melakukan apa pun.

## 6. Test Case Validasi

Lima skenario wajib dengan input salah, ditambah satu skenario tambahan. Kolom **Hasil Aktual** diisi setelah pengujian langsung di browser.

| ID | Field | Input Uji | Hasil yang Diharapkan | Hasil Aktual |
|---|---|---|---|---|
| TC-01 | Nama | `Al` (2 karakter) | Form tidak terkirim. Browser menampilkan pesan minimal 3 karakter. | |
| TC-02 | Telepon | `0812345` (7 digit) | Form tidak terkirim. Browser menampilkan pesan format tidak sesuai. | |
| TC-03 | Email | `budi@` (tanpa domain) | Form tidak terkirim. Browser menampilkan pesan format email tidak valid. | |
| TC-04 | Tujuan belajar | `Ingin belajar` (12 karakter) | Form tidak terkirim. Browser menampilkan pesan minimal 20 karakter. | |
| TC-05 | Bukti bayar | File `.docx` dipilih lewat opsi "All files" | Form tetap bisa terkirim, karena HTML tidak memeriksa tipe berkas yang dipilih secara paksa. Ini kelemahan yang harus ditangani server. | |
| TC-06 | Persetujuan | Checkbox tidak dicentang | Form tidak terkirim. Browser menampilkan pesan wajib dicentang. | |

**Cara menguji:** isi semua kolom dengan data yang benar, ubah satu kolom menjadi input uji dari tabel, lalu klik **Daftar Sekarang**. Catat apa yang muncul di layar.

**Bukti tambahan:** ambil screenshot setiap test case di desktop dan mobile (lebar layar di bawah 480 px). Beri nama `TC-01-desktop.png`, `TC-01-mobile.png`, dan seterusnya.

## 7. Validasi yang Wajib Dilakukan di Server

Validasi HTML hanya untuk pengalaman pengguna. Pengguna dapat melewatinya lewat Developer Tools atau dengan mengirim request langsung. Karena itu, server wajib memeriksa ulang:

1. **Kelengkapan dan tipe data semua field.** Nilai select dan radio harus sesuai daftar yang diizinkan.
2. **Format email dan telepon.** Pattern di browser bisa diabaikan, jadi server memeriksa ulang dengan aturan yang sama.
3. **Panjang teks.** Server membatasi panjang nama dan tujuan belajar, karena `maxlength` bisa dihapus.
4. **Tipe dan ukuran berkas bukti pembayaran.** Ekstensi dan `Content-Type` bisa dipalsukan, jadi server memeriksa isi berkas (magic bytes) dan memastikan ukurannya maksimal 2 MB.
5. **Penamaan dan penyimpanan berkas.** Berkas diberi nama acak dan disimpan di luar folder publik agar tidak bisa dieksekusi.
6. **Sanitasi input.** Teks dibersihkan dari karakter berbahaya sebelum disimpan atau ditampilkan, untuk mencegah XSS dan SQL injection.
7. **Duplikasi pendaftaran.** Email atau nomor telepon yang sama tidak boleh mendaftar dua kali untuk kursus yang sama.
8. **Kuota kursus.** Jumlah peserta harus dicek di server.
9. **Persetujuan.** Checkbox setuju harus diperiksa di server dan dicatat sebagai bukti.
10. **Token CSRF.** Mencegah form dikirim dari situs lain atas nama pengguna.

## 8. Perubahan, Masalah, dan Solusi

| Masalah | Solusi |
|---|---|
| Ukuran berkas tidak bisa dibatasi dengan HTML. | Batas 2 MB dinyatakan di teks bantuan, lalu dicek di server. |
| `accept` tidak mencegah pengguna memilih berkas lain. | Diterima sebagai keterbatasan HTML. Tipe berkas diperiksa ulang di server. |
| Pesan error bawaan browser berbeda-beda di tiap browser. | Diterima sebagai keterbatasan HTML. Pesan tetap muncul dan terbaca di browser modern. |
| Status valid dan tidak valid perlu terlihat tanpa JavaScript. | Memakai pseudo-class CSS `:user-invalid` dan `:user-valid`, sehingga warna muncul setelah pengguna mengisi. |
| Pada layar kecil tombol terlalu sempit. | Di bawah 480 px, setiap tombol memenuhi lebar form. |
| Tombol "Periksa Data" membutuhkan JavaScript. | Dihapus dan diganti tombol "Batal" (`type="button"`) sebagai contoh jenis tombol tanpa aksi. |