# Dashboard Akademik (Bootstrap 5)
| | |
|---|---|
| **Mata Kuliah** | Praktikum Desain Web (A) |
| **Topik** | Grid System dan Table Responsif |
| **Nama** | Muhamad Aria Khalil Mirzahamzah |
| **Semester** | 3 |
| **NIM** | 4525210094 |


## Cara menjalankan

1. Buka `index.html` di browser.
2. Komputer harus terhubung internet, karena Bootstrap dan font dimuat dari CDN.
3. Untuk cek tampilan HP, buka DevTools (F12), lalu aktifkan mode perangkat (Ctrl+Shift+M).

## Struktur folder

```
dashboard-akademik/
├── index.html      # Halaman utama
├── css/
│   └── style.css   # CSS buatan sendiri (dipanggil setelah Bootstrap)
└── README.md       # Penjelasan dan catatan pengerjaan
```

## Fungsi container, row, dan column

| Lapis | Class | Fungsi pada halaman ini |
|---|---|---|
| Container | `container` | Membungkus seluruh konten header, statistik, dan tabel. Lebar dibatasi dan konten berada di tengah, sehingga tidak melebar sampai tepi layar laptop. |
| Row | `row` | Mengelompokkan kolom secara horizontal. Dipakai untuk baris header, baris 4 kartu statistik, dan baris kartu tabel. `g-3` atau `g-md-4` mengatur jarak antar kolom. |
| Column | `col-12`, `col-md-6`, `col-lg-3`, dan lainnya | Membagi lebar 12 kolom dalam satu row. Kartu statistik memakai `col-12 col-md-6 col-lg-3`, sehingga berubah dari 1 → 2 → 4 kolom. |

Hierarki yang dipakai: `container` → `row` → `col-*` → isi (card, tabel, teks). Column selalu berada di dalam row, dan row selalu berada di dalam container.

## Perubahan layout per ukuran layar

Breakpoint Bootstrap yang dipakai: `md` untuk tablet (mulai 768px) dan `lg` untuk laptop (mulai 1024px).

| Bagian | HP (< 768px) | Tablet (≥ 768px) | Laptop (≥ 1024px) |
|---|---|---|---|
| Header | Judul dan label tanggal bertumpuk (`col-12`) | Judul di kiri, label tanggal di kanan (`col-md-8` dan `col-md-4`) | Sama seperti tablet |
| Kartu statistik | 1 kolom (`col-12`) | 2 kolom (`col-md-6`) | 4 kolom (`col-lg-3`) |
| Header tabel | Judul dan tombol bertumpuk (`flex-wrap`) | Sejajar dalam satu baris | Sama seperti tablet |
| Tabel | Digeser horizontal (`table-responsive`) | Muat dalam layar, sebagian kolom tetap perlu digeser | Seluruh kolom tampil tanpa digeser |

## Utility classes yang dipakai

`bg-dark`, `text-white`, `text-white-50`, `text-secondary`, `text-success`, `text-warning-emphasis`, `text-info-emphasis`, `text-center`, `text-end`, `text-md-end`, `text-nowrap`, `py-4`, `py-md-5`, `my-4`, `my-md-5`, `mb-4`, `mb-md-5`, `mt-auto`, `p-0`, `p-4`, `shadow-sm`, `fw-semibold`, `fw-normal`, `small`, `d-flex`, `flex-wrap`, `justify-content-between`, `align-items-center`, `align-items-end`, `gap-2`, `h-100`, `border-0`, `border-bottom`, `position-relative`.

Komponen Bootstrap yang dipakai:
- Card: `card`, `card-header`, `card-body`
- Table: `table`, `table-striped`, `table-hover`, `table-dark`, `align-middle`, `table-responsive`
- Badge: `badge text-bg-success`, `text-bg-warning`, `text-bg-danger`, `text-bg-info`
- Button: `btn btn-primary btn-sm` (tombol tambah) dan `btn btn-sm btn-outline-primary` (tombol Detail)

## Catatan pengerjaan (perubahan, masalah, dan solusi)

Isi bagian ini dengan hasil pengujian Anda sendiri setelah melihat tampilan di HP dan laptop. Contoh yang perlu dicek:

| Perubahan | Masalah yang mungkin muncul | Solusi yang diterapkan |
|---|---|---|
| Kartu statistik memakai `col-12 col-md-6 col-lg-3` | Di tablet, angka statistik terlalu besar sehingga kartu terasa penuh | Ukuran angka dikecilkan di layar sangat kecil lewat `@media` di `style.css` |
| Tabel dibungkus `table-responsive` | Di HP, tabel melebar keluar layar | Tabel bisa digeser horizontal, dan `text-nowrap` menjaga kolom NIM dan header tidak terpotong |
| Kartu memakai `h-100` | Tinggi kartu tidak sama saat teks berbeda panjang | Kartu di satu baris memiliki tinggi yang sama |
| Tombol tambah memakai `d-flex flex-wrap` | Di HP, tombol keluar dari area judul | Judul dan tombol turun ke baris berikutnya secara otomatis |

Tulis masalah yang benar-benar Anda temui di sini. Jika tidak ada, hapus baris contoh di atas.

## Bukti pengumpulan

- [ ] Source code: folder `dashboard-akademik/` ini
- [ ] Screenshot desktop (laptop, lebar ≥ 1024px)
- [ ] Screenshot tablet (lebar 768px sampai 1023px)
- [ ] Screenshot HP (lebar sekitar 375px)
- [ ] Penjelasan perubahan, masalah, dan solusi (bagian di atas)