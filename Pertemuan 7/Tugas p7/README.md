# Form Registrasi Event: Tech Creative Day 2026

| | |
|---|---|
| **Mata Kuliah** | Praktikum Desain Web (A) |
| **Topik** | Input dan Pengiriman Data (Form HTML Dasar) |
| **Nama** | Muhamad Aria Khalil Mirzahamzah |
| **Semester** | 3 |
| **NIM** | 4525210094 |

---

## 1. Struktur Folder

```
registrasi-event/
├── index.html   # struktur form (HTML5)
├── style.css    # tampilan dan status validasi (CSS)
└── README.md    # dokumentasi ini
```

## 2. Cara Menjalankan

1. Unduh folder `registrasi-event`.
2. Buka `index.html` di browser (Chrome, Edge, atau Firefox versi terbaru).
3. Tidak perlu server atau instalasi tambahan. Versi ini tidak memakai JavaScript.

## 3. Pengiriman Data

- `action="#"`: tujuan pengiriman. Saat sudah ada server, isi dengan URL pemroses, misalnya `action="proses-registrasi.php"`.
- `method="post"`: data dikirim di dalam body request, bukan di URL. Dipilih karena data registrasi bersifat pribadi.
- `enctype="multipart/form-data"`: wajib ada karena form mengirim berkas (upload bukti pembayaran).

## 4. Elemen Form yang Digunakan

| Jenis | Elemen | Keterangan |
|---|---|---|
| Teks | `<input type="text">` | Nama lengkap |
| Email | `<input type="email">` | Format email |
| Telepon | `<input type="tel">` | Nomor WhatsApp dengan `pattern` |
| Select | `<select>` | Pilih sesi |
| Radio | `<input type="radio">` ×3 | Jenis tiket, satu grup `name="tiket"` |
| Checkbox | `<input type="checkbox">` ×3 | Minat tambahan (opsional) |
| Textarea | `<textarea>` | Alasan mengikuti event |
| Upload | `<input type="file">` | Bukti pembayaran (`accept` PDF/JPG/PNG) |
| Persetujuan | `<input type="checkbox" required>` | Aturan acara |
| Button | `type="submit"`, `type="reset"`, `type="button"` | Tiga jenis tombol |

## 5. Aturan Validasi

| No | Field | Aturan | Atribut HTML5 |
|---|---|---|---|
| 1 | Nama | Wajib, 3 sampai 60 karakter | `required`, `minlength`, `maxlength` |
| 2 | Email | Wajib, format email | `type="email"`, `required` |
| 3 | Telepon | Wajib, diawali 08, 10 sampai 13 digit | `required`, `pattern` |
| 4 | Sesi | Wajib pilih satu | `required` pada select |
| 5 | Jenis tiket | Wajib pilih satu | `required` pada radio |
| 6 | Alasan | Wajib, 20 sampai 200 karakter | `required`, `minlength`, `maxlength` |
| 7 | Bukti pembayaran | Wajib, dipilih dengan filter PDF/JPG/PNG | `required`, `accept` |
| 8 | Persetujuan | Wajib dicentang | `required` |

**Catatan:** HTML tidak bisa membatasi ukuran berkas. Atribut `accept` hanya menyaring di dialog pilihan file, dan pengguna masih bisa memilih "All files". Batas 2 MB dan pengecekan isi berkas harus dilakukan di server.

## 6. Fungsi Tiga Jenis Button

- **Daftar Sekarang** (`type="submit"`): mengirim form. Browser menahan pengiriman jika ada isian yang belum sesuai aturan, lalu menampilkan pesan di kolom tersebut.
- **Bersihkan** (`type="reset"`): mengembalikan semua isian ke nilai awal.
- **Lihat Ringkasan** (`type="button"`): tombol tanpa aksi bawaan. Tanpa JavaScript, tombol ini hanya contoh jenis tombol dan tidak melakukan apa pun.

## 7. Test Case Validasi

Lima skenario wajib dengan input salah, ditambah satu skenario tambahan. Kolom **Hasil Aktual** diisi setelah pengujian langsung di browser.

| ID | Field | Input Uji | Hasil yang Diharapkan | Hasil Aktual |
|---|---|---|---|---|
| TC-01 | Nama | `Al` (2 karakter) | Form tidak terkirim. Browser menampilkan pesan minimal 3 karakter. | |
| TC-02 | Email | `rina@` (tanpa domain) | Form tidak terkirim. Browser menampilkan pesan format email tidak valid. | |
| TC-03 | Telepon | `0812345` (7 digit) | Form tidak terkirim. Browser menampilkan pesan format tidak sesuai. | |
| TC-04 | Alasan | `Ingin ikut` (9 karakter) | Form tidak terkirim. Browser menampilkan pesan minimal 20 karakter. | |
| TC-05 | Jenis tiket | Tidak ada radio yang dipilih | Form tidak terkirim. Browser menampilkan pesan wajib memilih salah satu. | |
| TC-06 | Bukti pembayaran | File `.docx` dipilih lewat opsi "All files" | Form tetap bisa terkirim, karena HTML tidak memeriksa tipe berkas yang dipilih secara paksa. Ini kelemahan yang harus ditangani server. | |

**Cara menguji:** isi semua kolom dengan data yang benar, ubah satu kolom menjadi input uji dari tabel, lalu klik **Daftar Sekarang**. Catat apa yang muncul di layar.

**Bukti tambahan:** ambil screenshot setiap test case di desktop dan mobile (lebar layar di bawah 480 px). Beri nama `TC-01-desktop.png`, `TC-01-mobile.png`, dan seterusnya.

## 8. Validasi yang Wajib Dilakukan di Server

Validasi HTML hanya untuk pengalaman pengguna. Pengguna dapat melewatinya lewat Developer Tools atau dengan mengirim request langsung. Karena itu, server wajib memeriksa ulang:

1. **Kelengkapan dan nilai field.** Sesi dan jenis tiket harus sesuai daftar yang tersedia di database, bukan sekadar nilai yang dikirim browser.
2. **Format email dan telepon.** Pattern di browser bisa diabaikan, jadi server memeriksa ulang dengan aturan yang sama.
3. **Panjang teks.** Server membatasi panjang nama dan alasan, karena `maxlength` bisa dihapus.
4. **Tipe dan ukuran berkas.** Ekstensi dan `Content-Type` bisa dipalsukan, jadi server memeriksa isi berkas (magic bytes) dan memastikan ukurannya maksimal 2 MB.
5. **Penyimpanan berkas.** Berkas diberi nama acak dan disimpan di luar folder publik agar tidak bisa dieksekusi.
6. **Sanitasi input.** Teks dibersihkan dari karakter berbahaya sebelum disimpan atau ditampilkan, untuk mencegah XSS dan SQL injection.
7. **Kuota tiket.** Jumlah peserta per jenis tiket dan kapasitas aula harus dicek di server, karena browser tidak tahu kondisi terkini.
8. **Duplikasi pendaftaran.** Email atau nomor WhatsApp yang sama tidak boleh mendaftar dua kali untuk event yang sama.
9. **Persetujuan.** Checkbox persetujuan harus diperiksa di server dan dicatat sebagai bukti.
10. **Token CSRF.** Mencegah form dikirim dari situs lain atas nama pengguna.

## 9. Perubahan, Masalah, dan Solusi

| Masalah | Solusi |
|---|---|
| Ukuran berkas tidak bisa dibatasi dengan HTML. | Batas 2 MB dinyatakan di teks bantuan, lalu dicek di server. |
| `accept` tidak mencegah pengguna memilih berkas lain. | Diterima sebagai keterbatasan HTML. Tipe berkas diperiksa ulang di server. |
| Pesan error bawaan browser berbeda-beda di tiap browser. | Diterima sebagai keterbatasan HTML. Pesan tetap muncul dan terbaca di browser modern. |
| Status valid dan tidak valid perlu terlihat tanpa JavaScript. | Memakai pseudo-class CSS `:user-invalid` dan `:user-valid`, sehingga warna muncul setelah pengguna mengisi. |
| Form perlu tampil menarik sebagai poster event. | Header berbentuk poster dengan gradasi, pilihan radio dan checkbox dibuat seperti chip, dan kartu form sedikit naik ke atas header. |
| Pada layar kecil tombol terlalu sempit. | Di bawah 480 px, setiap tombol memenuhi lebar form. |