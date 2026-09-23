# Materi Khusus: Mail Merge — Menggabungkan Data Excel ke Word Secara Otomatis

Mail Merge adalah fitur di Microsoft Word untuk membuat dokumen massal (surat, sertifikat, undangan, kartu ujian, dll) secara otomatis dengan mengambil data dari sumber seperti Excel, tanpa perlu mengetik satu per satu.

---

## 1. Konsep Dasar

Ada 3 komponen utama dalam Mail Merge:

1. **Main Document** — Dokumen Word berisi template tetap (misal: format surat/sertifikat) dengan area kosong yang akan diisi otomatis.
2. **Data Source** — File Excel berisi data yang akan dimasukkan (misal: daftar nama, NIS, kelas, nilai).
3. **Merge Fields** — Penanda di dalam dokumen Word yang menunjukkan di mana data dari Excel akan dimasukkan.

---

## 2. Persiapan Data di Excel

Sebelum memulai, siapkan data dengan aturan berikut:

- Data harus berbentuk **tabel** dengan **baris pertama sebagai judul kolom** (header), contoh: `Nama`, `NIS`, `Kelas`, `Nilai`.
- **Tidak boleh ada baris/kolom kosong** di tengah data.
- Setiap kolom harus **konsisten formatnya** (misal kolom Nilai semua berupa angka, bukan campuran angka dan teks).
- Simpan file Excel dan **jangan dibuka bersamaan** saat proses mail merge berlangsung di Word (sebaiknya ditutup dulu).

Contoh struktur data di Excel (`data_siswa.xlsx`, sheet `Sheet1`):

| Nama | NIS | Kelas | Nilai |
|---|---|---|---|
| Made Ayu | 1001 | X-1 | 90 |
| Kadek Dwi | 1002 | X-2 | 85 |
| Komang Tri | 1003 | X-3 | 88 |

---

## 3. Langkah-Langkah Mail Merge di Word

### Langkah 1 — Buka Dokumen Word & Buat Template
Buat/buka dokumen Word yang akan dijadikan template (misalnya format surat panggilan orang tua atau sertifikat), lalu ketik teks tetap sesuai kebutuhan.

### Langkah 2 — Mulai Mail Merge
1. Buka tab **Mailings** pada Ribbon Word.
2. Klik **Start Mail Merge** → pilih jenis dokumen (misal: **Letters** untuk surat, atau **Labels**/**Envelopes** sesuai kebutuhan).

### Langkah 3 — Hubungkan ke Data Excel
1. Klik **Select Recipients** → pilih **Use an Existing List...**
2. Cari dan pilih file Excel yang sudah disiapkan (`data_siswa.xlsx`).
3. Word akan menampilkan daftar sheet — pilih sheet yang berisi data (misal `Sheet1$`), lalu klik **OK**.
4. Centang/hilangkan centang **"First row of data contains column headers"** jika baris pertama adalah judul kolom (biasanya sudah otomatis tercentang).

### Langkah 4 — Edit Recipient List (Opsional)
- Klik **Edit Recipient List** untuk menyaring data (misalnya hanya mencetak surat untuk kelas tertentu) menggunakan fitur **Filter**, atau mengurutkan data dengan **Sort**.

### Langkah 5 — Masukkan Merge Field ke Dokumen
1. Letakkan kursor di posisi yang ingin diisi data otomatis (misal setelah tulisan "Nama Siswa:").
2. Klik **Insert Merge Field** pada tab Mailings.
3. Pilih nama kolom yang sesuai dari daftar (misal `Nama`, `NIS`, `Kelas`, `Nilai`).
4. Ulangi untuk setiap bagian dokumen yang perlu diisi data otomatis.

Contoh hasil template di Word:
```
Kepada Yth. Orang Tua/Wali dari «Nama»
NIS: «NIS»   Kelas: «Kelas»
Dengan ini kami sampaikan bahwa nilai ujian ananda adalah «Nilai».
```
(Tanda `« »` adalah tampilan merge field di Word, bukan diketik manual — muncul otomatis setelah insert field.)

### Langkah 6 — Preview Hasil
- Klik **Preview Results** pada tab Mailings untuk melihat bagaimana data akan tampil satu per satu (gunakan tombol panah untuk berpindah antar data/record).
- Periksa apakah data sudah tampil dengan benar, termasuk format angka dan tanggal.

### Langkah 7 — Selesaikan Mail Merge
Ada dua pilihan:
- **Finish & Merge → Edit Individual Documents** — menghasilkan satu file Word baru berisi semua dokumen (satu dokumen per baris data), cocok jika ingin diedit manual sebelum dicetak.
- **Finish & Merge → Print Documents** — langsung mencetak semua dokumen ke printer.

---

## 4. Mengatasi Masalah Format Angka/Tanggal yang Berubah

Sering terjadi angka (misal nilai desimal) atau tanggal berubah format aneh saat dimasukkan ke Word. Solusinya menggunakan **Field Switch**:

1. Klik kanan pada merge field yang bermasalah → pilih **Toggle Field Codes** (atau tekan `Alt + F9`).
2. Field akan terlihat seperti: `{ MERGEFIELD Nilai }`
3. Tambahkan switch format, contoh:
   - Format angka 2 desimal: `{ MERGEFIELD Nilai \# "0.00" }`
   - Format angka ribuan: `{ MERGEFIELD Nilai \# "#,##0" }`
   - Format tanggal Indonesia: `{ MERGEFIELD Tanggal \@ "dd MMMM yyyy" }`
4. Tekan `Alt + F9` lagi untuk kembali ke tampilan normal, lalu klik kanan → **Update Field**.

---

## 5. Menambahkan Kondisi (IF) dalam Mail Merge

Word mendukung field kondisional untuk menampilkan teks berbeda tergantung data, contoh menampilkan keterangan "LULUS" atau "TIDAK LULUS" berdasarkan nilai:

1. Tab **Mailings** → **Rules** → **If...Then...Else...**
2. Atur:
   - Field name: `Nilai`
   - Comparison: `Greater than or equal to`
   - Compare to: `75`
   - Insert this text: `LULUS`
   - Otherwise insert this text: `TIDAK LULUS`

---

## 6. Studi Kasus: Kartu Ujian / Sertifikat Otomatis

Alur umum untuk membuat kartu ujian atau sertifikat massal:

1. Siapkan data peserta di Excel (Nama, No. Peserta, Ruang, Kelas).
2. Buat desain kartu/sertifikat di Word (bisa 1 kartu per halaman, atau gunakan tabel untuk beberapa kartu per halaman menggunakan fitur **Labels** dengan ukuran custom).
3. Hubungkan data source dan masukkan merge field sesuai desain.
4. Untuk mode banyak kartu per halaman: gunakan tombol **Update Labels** setelah field pertama diisi, agar seluruh sel label ikut menerapkan pola yang sama.
5. Jalankan **Finish & Merge** untuk menghasilkan seluruh kartu sekaligus.

---

## 7. Tips & Troubleshooting

| Masalah | Solusi |
|---|---|
| Muncul huruf/simbol aneh seperti `«»` tidak terganti data | Pastikan sudah menjalankan **Preview Results**, bukan hanya insert field |
| Data Excel tidak update di Word meski sudah diedit | Data source hanya dibaca saat proses merge; edit ulang lewat **Edit Recipient List** atau buka ulang koneksi data |
| Sebagian data tidak muncul (terlewat) | Cek apakah ada baris kosong di tengah data Excel, hapus baris kosong tersebut |
| Format angka desimal berubah jadi banyak digit | Gunakan Field Switch `\#` seperti dijelaskan pada bagian 4 |
| Ingin hanya mencetak sebagian data (misal 1 kelas saja) | Gunakan **Edit Recipient List → Filter** sebelum Finish & Merge |
| File Excel terkunci/tidak bisa dibuka saat proses merge | Tutup file Excel sebelum membuka/mengedit koneksi mail merge di Word |

---

## 8. Ringkasan Alur Kerja

```
[Excel: Data Sumber] 
        ↓  (Select Recipients → Use Existing List)
[Word: Template Dokumen + Merge Fields]
        ↓  (Preview Results untuk cek)
[Finish & Merge]
        ↓
[Dokumen jadi: banyak surat/sertifikat/kartu otomatis]
```

Dengan Mail Merge, satu template Word dapat menghasilkan ratusan dokumen personal secara otomatis hanya dengan satu kali proses, sangat berguna untuk kebutuhan surat massal, kartu ujian, sertifikat, maupun rapor di lingkungan sekolah.
