# Cheatsheet & Materi Ringkas Rumus Pengolahan Data MS Excel

Dokumen ini berisi panduan ringkas dan praktis rumus-rumus yang paling sering digunakan dalam pengolahan data di Microsoft Excel, mulai dari pengolahan angka/nilai, logika bersyarat, hingga pencarian data.

---

## 1. Rumus Pengolahan Nilai & Angka (Basic Stat & Aggregation)

Digunakan untuk merekapitulasi, menghitung, dan mengolah data numerik.

| Rumus | Fungsi | Contoh Sintaks |
| :--- | :--- | :--- |
| **`SUM`** | Menjumlahkan seluruh angka dalam *range*. | `=SUM(A2:A10)` |
| **`AVERAGE`** | Menghitung rata-rata dari sekelompok nilai. | `=AVERAGE(B2:B10)` |
| **`COUNT`** | Menhitung jumlah sel yang berisi **angka saja**. | `=COUNT(C2:C10)` |
| **`COUNTA`** | Menhitung jumlah sel yang **tidak kosong** (angka + teks). | `=COUNTA(A2:A10)` |
| **`MAX` / `MIN`** | Mencari nilai tertinggi / terendah. | `=MAX(B2:B10)` / `=MIN(B2:B10)` |
| **`ROUND`** | Membulatkan angka ke jumlah desimal tertentu. | `=ROUND(C2, 2)` |

---

## 2. Rumus Logika & Kondisi (IF - ELSE & Variant)

Digunakan untuk membuat keputusan otomatis atau pengolahan data bersyarat.

### A. Fungsi Logika Dasar
* **`IF` Single (Kondisi Tunggal):**
  ```excel
  =IF(C2>=75, "Lulus", "Tidak Lulus")
  ```
* **`IF` Nested / Bertingkat (Kondisi Banyak):**
  ```excel
  =IF(C2>=85, "A", IF(C2>=75, "B", IF(C2>=60, "C", "D")))
  ```
* **`AND` & `OR` (Kombinasi Syarat):**
  ```excel
  =IF(AND(B2>70, C2>75), "Lulus", "Gagal")
  =IF(OR(B2>90, C2>90), "Beasiswa", "Reguler")
  ```

### B. Rumus Hitung Bersyarat (Conditional Aggregation)
* **`COUNTIF`**: Menghitung jumlah sel sesuai 1 kriteria.
  ```excel
  =COUNTIF(D2:D100, "Lulus")
  ```
* **`SUMIF`**: Menjumlahkan nilai berdasarkan 1 kriteria.
  ```excel
  =SUMIF(C2:C100, "Elektronik", E2:E100)
  ```
* **`SUMIFS`**: Menjumlahkan nilai berdasarkan **banyak** kriteria.
  ```excel
  =SUMIFS(E2:E100, C2:C100, "Elektronik", D2:D100, "Lunas")
  ```

---

## 3. Rumus Pencarian & Referensi (Lookup Formulas)

Digunakan untuk mengambil data dari tabel referensi berdasarkan pencarian kunci (*lookup value*).

### A. `VLOOKUP` (Vertical Lookup)
Mencari data secara **vertikal** (dari atas ke bawah). Kolom pencarian harus berada di **kolom pertama** pada tabel referensi.

```excel
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
```
* **Contoh:**
  ```excel
  =VLOOKUP(A2, F2:H10, 2, FALSE)
  ```
  *Penjelasan:* Cari ID di sel `A2`, lihat di area `F2:H10`, ambil nilai pada **kolom ke-2**, gunakan `FALSE` (pencarian persis/exact match).

### B. `HLOOKUP` (Horizontal Lookup)
Mencari data secara **horizontal** (dari kiri ke kanan).

```excel
=HLOOKUP(A2, F1:J3, 2, FALSE)
```

### C. `XLOOKUP` (Fitur Modern - Direkomendasikan)
Fungsi pencarian terbaru yang lebih fleksibel, cepat, dan aman dibanding VLOOKUP.
* Tidak terbatas urutan kolom (bisa cari ke kiri maupun ke kanan).
* Otomatis *exact match* tanpa perlu mengetik `FALSE`.
* Memiliki fitur penanganan error bawaan (*if_not_found*).

```excel
=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found])
```
* **Contoh:**
  ```excel
  =XLOOKUP(A2, F2:F10, H2:H10, "Tidak Ditemukan")
  ```
  *Penjelasan:* Cari nilai `A2` pada kolom `F2:F10`, lalu kembalikan nilai yang sejajar dari kolom `H2:H10`. Jika data tidak ada, tampilkan pesan `"Tidak Ditemukan"`.

---

## 4. Rumus Pendukung & Penanganan Error

* **`IFERROR`**: Mengubah tampilan pesan error (seperti `#N/A`, `#VALUE!`) menjadi teks rapi.
  ```excel
  =IFERROR(VLOOKUP(A2, F2:H10, 2, FALSE), "Data Kosong")
  ```
* **`TEXT` / `TRIM`**: Merapikan teks kunci sebelum pencarian.
  ```excel
  =TRIM(A2)
  ```
