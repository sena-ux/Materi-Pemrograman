# Materi Khusus: VLOOKUP, HLOOKUP, dan XLOOKUP

Panduan lengkap penggunaan tiga fungsi pencarian data paling penting di Excel.

---

## 1. VLOOKUP (Vertical Lookup)

Digunakan untuk mencari data yang tersusun **secara vertikal (per kolom)**, lalu mengambil nilai dari kolom lain di baris yang sama.

### Sintaks
```
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
```

| Argumen | Keterangan |
|---|---|
| `lookup_value` | Nilai/kata kunci yang dicari |
| `table_array` | Range tabel data, kolom pertama harus berisi kata kunci pencarian |
| `col_index_num` | Nomor urut kolom (dihitung dari kolom pertama tabel = 1) yang nilainya ingin diambil |
| `range_lookup` | `FALSE`/`0` = pencocokan persis (exact match), `TRUE`/`1` = pencocokan mendekati (approximate) |

### Contoh Kasus
Tabel data siswa di `A1:C5`:

| A (NIS) | B (Nama) | C (Kelas) |
|---|---|---|
| 1001 | Made | X-1 |
| 1002 | Kadek | X-2 |
| 1003 | Komang | X-3 |

Mencari nama siswa dengan NIS 1002:
```
=VLOOKUP(1002, A2:C4, 2, FALSE)
```
Hasil: `Kadek`

### Aturan Penting
- Kolom kunci pencarian **wajib** berada di kolom paling kiri dari `table_array`.
- Selalu gunakan `FALSE` (exact match) untuk data seperti NIS, kode barang, NIP, dsb. `TRUE` hanya untuk tabel bertingkat yang sudah diurutkan naik.
- VLOOKUP **tidak bisa** mencari ke arah kiri (mengambil data dari kolom sebelum kolom kunci).
- Kunci `table_array` (misal dengan `F4` menjadi `$A$2:$C$4`) agar rumus bisa di-copy ke bawah tanpa bergeser.

### Kesalahan Umum
- `#N/A` → data tidak ditemukan, biasanya karena ada spasi tersembunyi atau format sel berbeda (angka vs teks).
- Lupa `FALSE` → hasil salah karena Excel mengambil nilai mendekati, bukan persis.

---

## 2. HLOOKUP (Horizontal Lookup)

Sama seperti VLOOKUP, tetapi digunakan jika data tersusun **secara horizontal (per baris)**.

### Sintaks
```
=HLOOKUP(lookup_value, table_array, row_index_num, [range_lookup])
```

| Argumen | Keterangan |
|---|---|
| `lookup_value` | Nilai yang dicari |
| `table_array` | Range tabel, baris pertama berisi kata kunci pencarian |
| `row_index_num` | Nomor urut baris (dihitung dari baris pertama = 1) yang nilainya diambil |
| `range_lookup` | `FALSE` = persis, `TRUE` = mendekati |

### Contoh Kasus
Data di `A1:D3`:

| | B1001 | B1002 | B1003 |
|---|---|---|---|
| Nama Barang | Pulpen | Buku | Tas |
| Harga | 3000 | 5000 | 50000 |

Mencari harga barang dengan kode B1002:
```
=HLOOKUP("B1002", B1:D3, 3, FALSE)
```
Hasil: `5000`

### Kapan Dipakai
HLOOKUP jarang digunakan dibanding VLOOKUP karena kebanyakan data tabel disusun per kolom, bukan per baris. Cocok untuk data seperti jadwal per bulan/tahun yang disusun mendatar.

---

## 3. XLOOKUP (Fungsi Modern Pengganti VLOOKUP & HLOOKUP)

Tersedia di Excel 365 dan Excel 2021 ke atas. Lebih fleksibel karena bisa mencari ke kiri/kanan, atas/bawah, dan punya penanganan error bawaan.

### Sintaks
```
=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])
```

| Argumen | Keterangan |
|---|---|
| `lookup_value` | Nilai yang dicari |
| `lookup_array` | Kolom/baris tempat mencari kata kunci |
| `return_array` | Kolom/baris tempat mengambil hasil |
| `if_not_found` | Teks/nilai pengganti jika data tidak ditemukan (opsional, pengganti IFERROR) |
| `match_mode` | 0 = persis (default), -1 = persis atau lebih kecil terdekat, 1 = persis atau lebih besar terdekat, 2 = wildcard |
| `search_mode` | 1 = dari awal (default), -1 = dari akhir, 2/-2 = binary search |

### Contoh Kasus
Menggunakan tabel siswa yang sama:
```
=XLOOKUP(1002, A2:A4, B2:B4)
```
Hasil: `Kadek`

Dengan penanganan jika data tidak ditemukan:
```
=XLOOKUP(1005, A2:A4, B2:B4, "Data tidak ada")
```
Hasil: `Data tidak ada`

### Keunggulan XLOOKUP dibanding VLOOKUP/HLOOKUP
1. **Bisa mencari ke kiri** — tidak seperti VLOOKUP yang hanya bisa ke kanan.
2. **Tidak perlu hitung nomor kolom/baris** — cukup arahkan langsung ke `return_array`, sehingga tidak error saat kolom disisipkan/dihapus.
3. **Default-nya exact match** — lebih aman untuk pemula, mengurangi risiko lupa `FALSE`.
4. **Ada parameter `if_not_found` bawaan** — tidak perlu membungkus dengan `IFERROR`.
5. **Bisa mengambil beberapa kolom sekaligus** — dengan `return_array` berupa range beberapa kolom, hasilnya otomatis "tumpah" (spill) ke beberapa sel.

Contoh mengambil Nama dan Kelas sekaligus:
```
=XLOOKUP(1002, A2:A4, B2:C4)
```
Hasil akan tumpah ke 2 sel: `Kadek` dan `X-2`.

---

## 4. Tabel Perbandingan Ringkas

| Aspek | VLOOKUP | HLOOKUP | XLOOKUP |
|---|---|---|---|
| Arah data | Vertikal (kolom) | Horizontal (baris) | Keduanya |
| Bisa cari ke kiri | Tidak | Tidak (setara: ke atas) | Bisa |
| Penunjuk hasil | Nomor indeks kolom | Nomor indeks baris | Langsung pilih range |
| Default match | Mendekati (harus set FALSE manual) | Mendekati (harus set FALSE manual) | Persis (default aman) |
| Penanganan error | Perlu IFERROR terpisah | Perlu IFERROR terpisah | Built-in (`if_not_found`) |
| Ketersediaan | Semua versi Excel | Semua versi Excel | Excel 365 / 2021+ |
| Ambil banyak kolom sekaligus | Tidak | Tidak | Bisa (spill array) |

## 5. Tips Praktis
- Untuk laporan yang dipakai di Excel versi lama (2016/2019), tetap gunakan VLOOKUP/HLOOKUP karena XLOOKUP belum tersedia di versi tersebut.
- Jika memungkinkan (Excel 365), gunakan XLOOKUP sebagai standar baru karena lebih tahan terhadap perubahan struktur tabel.
- Kombinasi `INDEX` + `MATCH` masih relevan sebagai alternatif VLOOKUP di Excel versi lama yang butuh pencarian ke kiri.
- Selalu bersihkan data dengan `TRIM()` dan pastikan format sel konsisten (angka vs teks) sebelum melakukan pencarian, untuk menghindari error `#N/A`.
