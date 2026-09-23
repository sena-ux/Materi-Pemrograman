# Daftar Rumus-Rumus Excel

Kumpulan rumus (fungsi) Excel yang dikelompokkan berdasarkan kategori penggunaan.

## 1. Matematika & Statistik Dasar

| Rumus | Fungsi |
|---|---|
| `=SUM(range)` | Menjumlahkan angka |
| `=AVERAGE(range)` | Rata-rata |
| `=MIN(range)` | Nilai terkecil |
| `=MAX(range)` | Nilai terbesar |
| `=COUNT(range)` | Menghitung sel berisi angka |
| `=COUNTA(range)` | Menghitung sel yang tidak kosong |
| `=COUNTBLANK(range)` | Menghitung sel kosong |
| `=MEDIAN(range)` | Nilai tengah |
| `=MODE.SNGL(range)` | Nilai yang paling sering muncul |
| `=ROUND(number, digit)` | Membulatkan angka |
| `=ROUNDUP(number, digit)` | Membulatkan ke atas |
| `=ROUNDDOWN(number, digit)` | Membulatkan ke bawah |
| `=ABS(number)` | Nilai absolut |
| `=SQRT(number)` | Akar kuadrat |
| `=POWER(number, power)` | Pangkat |
| `=MOD(number, divisor)` | Sisa bagi |
| `=SUMPRODUCT(range1, range2)` | Perkalian antar array lalu dijumlahkan |
| `=SUBTOTAL(function_num, range)` | Subtotal yang mengabaikan baris tersembunyi/filter |

## 2. Fungsi Kondisional (Logika)

| Rumus | Fungsi |
|---|---|
| `=IF(kondisi, jika_benar, jika_salah)` | Percabangan logika |
| `=IFS(kondisi1, hasil1, kondisi2, hasil2, ...)` | Banyak kondisi tanpa nested IF |
| `=AND(kondisi1, kondisi2, ...)` | Benar jika semua kondisi benar |
| `=OR(kondisi1, kondisi2, ...)` | Benar jika salah satu kondisi benar |
| `=NOT(kondisi)` | Membalik nilai logika |
| `=IFERROR(value, value_if_error)` | Menangani error dengan nilai pengganti |
| `=IFNA(value, value_if_na)` | Menangani error #N/A khusus |
| `=SWITCH(expression, value1, result1, ...)` | Mencocokkan nilai ke beberapa hasil |

## 3. Fungsi Pencarian & Referensi (Lookup)

| Rumus | Fungsi |
|---|---|
| `=VLOOKUP(lookup_value, table_array, col_index, [range_lookup])` | Cari data secara vertikal |
| `=HLOOKUP(lookup_value, table_array, row_index, [range_lookup])` | Cari data secara horizontal |
| `=XLOOKUP(lookup_value, lookup_array, return_array, ...)` | Pencarian modern, dua arah |
| `=INDEX(array, row_num, [col_num])` | Ambil nilai berdasarkan posisi |
| `=MATCH(lookup_value, lookup_array, [match_type])` | Cari posisi/urutan data |
| `=INDEX(...)+MATCH(...)` | Kombinasi pencarian fleksibel (pengganti VLOOKUP klasik) |
| `=LOOKUP(lookup_value, lookup_vector, result_vector)` | Pencarian sederhana satu arah |
| `=OFFSET(reference, rows, cols, [height], [width])` | Referensi sel bergeser dari titik acuan |
| `=INDIRECT(ref_text)` | Mengubah teks menjadi referensi sel |
| `=CHOOSE(index_num, value1, value2, ...)` | Memilih nilai berdasarkan urutan |
| `=ADDRESS(row_num, column_num)` | Menghasilkan alamat sel dalam bentuk teks |
| `=ROW()` / `=COLUMN()` | Mengambil nomor baris/kolom |
| `=ROWS(range)` / `=COLUMNS(range)` | Menghitung jumlah baris/kolom |

## 4. Fungsi Teks (Text)

| Rumus | Fungsi |
|---|---|
| `=LEFT(text, num_chars)` | Ambil karakter dari kiri |
| `=RIGHT(text, num_chars)` | Ambil karakter dari kanan |
| `=MID(text, start_num, num_chars)` | Ambil karakter dari tengah |
| `=LEN(text)` | Menghitung jumlah karakter |
| `=TRIM(text)` | Menghapus spasi berlebih |
| `=UPPER(text)` / `=LOWER(text)` | Ubah huruf besar/kecil |
| `=PROPER(text)` | Huruf kapital di awal kata |
| `=CONCAT(text1, text2, ...)` / `=CONCATENATE(...)` | Menggabungkan teks |
| `=TEXTJOIN(delimiter, ignore_empty, text1, ...)` | Menggabungkan teks dengan pemisah |
| `=SUBSTITUTE(text, old_text, new_text)` | Mengganti bagian teks tertentu |
| `=REPLACE(old_text, start_num, num_chars, new_text)` | Mengganti teks berdasarkan posisi |
| `=FIND(find_text, within_text)` | Mencari posisi teks (case sensitive) |
| `=SEARCH(find_text, within_text)` | Mencari posisi teks (tidak case sensitive) |
| `=TEXT(value, format_text)` | Mengubah angka/tanggal ke format teks tertentu |
| `=VALUE(text)` | Mengubah teks angka menjadi angka |
| `=REPT(text, number_times)` | Mengulang teks |
| `=TEXTSPLIT(text, delimiter)` | Memecah teks menjadi beberapa sel (Excel 365) |

## 5. Fungsi Tanggal & Waktu

| Rumus | Fungsi |
|---|---|
| `=TODAY()` | Tanggal hari ini |
| `=NOW()` | Tanggal & waktu saat ini |
| `=DATE(year, month, day)` | Membuat tanggal |
| `=DAY(date)` / `=MONTH(date)` / `=YEAR(date)` | Mengambil bagian tanggal |
| `=DATEDIF(start_date, end_date, unit)` | Selisih dua tanggal |
| `=NETWORKDAYS(start_date, end_date)` | Jumlah hari kerja |
| `=WORKDAY(start_date, days)` | Tanggal setelah sejumlah hari kerja |
| `=WEEKDAY(date)` | Nomor hari dalam seminggu |
| `=EOMONTH(start_date, months)` | Tanggal akhir bulan |
| `=EDATE(start_date, months)` | Tanggal setelah sejumlah bulan |

## 6. Fungsi Statistik Kondisional (Conditional)

| Rumus | Fungsi |
|---|---|
| `=SUMIF(range, criteria, [sum_range])` | Jumlah dengan satu kriteria |
| `=SUMIFS(sum_range, criteria_range1, criteria1, ...)` | Jumlah dengan banyak kriteria |
| `=COUNTIF(range, criteria)` | Hitung dengan satu kriteria |
| `=COUNTIFS(criteria_range1, criteria1, ...)` | Hitung dengan banyak kriteria |
| `=AVERAGEIF(range, criteria, [average_range])` | Rata-rata dengan satu kriteria |
| `=AVERAGEIFS(average_range, criteria_range1, criteria1, ...)` | Rata-rata dengan banyak kriteria |
| `=MAXIFS(max_range, criteria_range1, criteria1, ...)` | Nilai maksimum bersyarat |
| `=MINIFS(min_range, criteria_range1, criteria1, ...)` | Nilai minimum bersyarat |

## 7. Fungsi Excel 365 (Dynamic Array)

| Rumus | Fungsi |
|---|---|
| `=UNIQUE(range)` | Mengambil nilai unik |
| `=SORT(range, [sort_index], [sort_order])` | Mengurutkan data |
| `=SORTBY(array, by_array, [order])` | Mengurutkan berdasarkan kolom lain |
| `=FILTER(array, include, [if_empty])` | Menyaring data sesuai kondisi |
| `=SEQUENCE(rows, [cols], [start], [step])` | Membuat deret angka otomatis |
| `=RANDARRAY(rows, cols)` | Membuat array angka acak |
| `=LET(name1, value1, calculation)` | Membuat variabel dalam rumus |
| `=LAMBDA(parameter, calculation)` | Membuat fungsi kustom sendiri |

## 8. Fungsi Keuangan Dasar

| Rumus | Fungsi |
|---|---|
| `=PMT(rate, nper, pv)` | Menghitung cicilan pinjaman |
| `=FV(rate, nper, pmt, pv)` | Nilai masa depan investasi |
| `=PV(rate, nper, pmt)` | Nilai sekarang investasi |
| `=RATE(nper, pmt, pv)` | Menghitung suku bunga |
| `=NPER(rate, pmt, pv)` | Jumlah periode pembayaran |

## 9. Fungsi Informasi (Error/Type Checking)

| Rumus | Fungsi |
|---|---|
| `=ISERROR(value)` | Cek apakah hasil error |
| `=ISNA(value)` | Cek apakah hasil #N/A |
| `=ISBLANK(value)` | Cek apakah sel kosong |
| `=ISNUMBER(value)` | Cek apakah nilai berupa angka |
| `=ISTEXT(value)` | Cek apakah nilai berupa teks |
| `=CELL(info_type, reference)` | Informasi tentang sel |
