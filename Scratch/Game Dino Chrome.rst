================================================================================
PANDUAN PEMBUATAN GAME DINO RUNNER (CHROME DINO) MENGGUNAKAN SCRATCH
================================================================================

Dokumentasi ini berisi panduan komprehensif, langkah demi langkah, dan terstruktur untuk membuat ulang game ikonik **Chrome Dino Runner** menggunakan platform pemrograman berbasis visual **Scratch**.

.. note::
   Game Dino Runner adalah game bergenre *endless runner* 2D. Karakter utama (Dino) harus melompati rintangan (Kaktus) yang bergerak mendekat secara terus-menerus. Game berakhir jika Dino menabrak kaktus.


1. PERSIAPAN SPRITE DAN STRUKTUR PROYEK
--------------------------------------------------

Sebelum menyusun logika program, kita perlu menyiapkan sprite (objek) dan latar belakang yang diperlukan.

1.1 Sprite Dino (Pemain Utama)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Buat sprite baru bernama **Dino**.
* Siapkan 2 kostum utama:
  - ``Dino_Run1`` & ``Dino_Run2``: Kostum animasi berlari (kaki bergantian).
  - ``Dino_Jump``: Kostum saat melompat.

1.2 Sprite Kaktus (Rintangan)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Buat sprite baru bernama **Kaktus**.
* Buat 2 atau 3 variasi kostum kaktus (kaktus tunggal, kaktus ganda, atau kaktus besar).

1.3 Sprite Tanah / Ground (Efek Berjalan)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Buat sprite garis tanah horizontal datar sebagai tempat Dino berdiri.

1.4 Variabel Global
~~~~~~~~~~~~~~~~~~~
Buat variabel berikut pada kategori **Variables**:

+------------------+---------------------+---------------------------------------------------------------+
| Nama Variabel    | Cakupan (*Scope*)   | Fungsi Utama                                                  |
+==================+=====================+===============================================================+
| ``Kecepatan_Y``  | For all sprites     | Mengatur kecepatan gravitasional & lompatan Dino.             |
+------------------+---------------------+---------------------------------------------------------------+
| ``Skor``         | For all sprites     | Menyimpan jumlah skor pemain berdasarkan durasi bertahan hidup|
+------------------+---------------------+---------------------------------------------------------------+
| ``Kecepatan_Game``| For all sprites    | Mengatur kecepatan gerak rintangan secara berangsur.          |
+------------------+---------------------+---------------------------------------------------------------+
| ``Status_Game``  | For all sprites     | Menyimpan status panggung (``PLAYING`` atau ``GAMEOVER``).    |
+------------------+---------------------+---------------------------------------------------------------+


2. LOGIKA UTAMA KARAKTER DINO (FISIKA MELOMPAT & GRAVITASI)
--------------------------------------------------

Karakter Dino membutuhkan simulasi fisika sederhana agar dapat melompat secara mulus saat tombol ditahan/ditekan dan kembali jatuh ke tanah karena efek gravitasi.

2.1 Penjelasan Logika Fisika
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* **Posisi Dasar Tanah (Ground Y)**: Ditetapkan pada koordinat ``Y: -100``.
* **Lompatan**: Ketika tombol *Space* atau *Panah Atas* ditekan dan Dino sedang menyentuh tanah, variabel ``Kecepatan_Y`` diberi nilai positif (misal: ``12``).
* **Gravitasi**: Setiap frame, ``Kecepatan_Y`` dikurangi sebesar ``1``, lalu posisi ``Y`` Dino ditambah dengan nilai ``Kecepatan_Y``.

2.2 Skrip Utama Dino
~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

   when green flag clicked
   // Inisialisasi Posisi Awal Dino
   go to x: (-160) y: (-100)
   set [Kecepatan_Y v] to (0)
   switch costume to [Dino_Run1 v]
   show

   forever
       if <(Status_Game) = [PLAYING]> then
           // Modifikasi Posisi Y berdasarkan Kecepatan_Y
           change y by (Kecepatan_Y)
           
           // Pengecekan Ketinggian Tanah
           if <(y position) < (-100)> then
               set y to (-100)
               set [Kecepatan_Y v] to (0)
           end
           
           // Input Melompat (Hanya saat berada di tanah)
           if <<key [space v] pressed?> or <key [up arrow v] pressed?>> then
               if <(y position) = (-100)> then
                   set [Kecepatan_Y v] to (13)
                   start sound [Jump v]
               end
           end
           
           // Efek Gravitasi (Hanya saat di udara)
           if <(y position) > (-100)> then
               change [Kecepatan_Y v] by (-1)
               switch costume to [Dino_Jump v]
           else
               // Animasi Berlari di Tanah
               next costume
               wait (0.05) seconds
           end
       end
   end


3. LOGIKA RINTANGAN KAKTUS (GENERATOR KLONING & PERGERAKAN)
--------------------------------------------------

Guna menciptakan efek pergerakan tanpa batas (*endless runner*), sprite Kaktus akan dimanfaatkan sebagai induk yang memproduksi duplikat (*cloning*) secara otomatis dari sisi kanan layar panggung.

3.1 Skrip Induk Kaktus (Spawner)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

   when green flag clicked
   hide
   forever
       if <(Status_Game) = [PLAYING]> then
           // Penundaan acak munculnya rintangan berikutnya
           wait (pick random (1.2) to (2.5)) seconds
           create clone of [myself v]
       end
   end

3.2 Skrip Kloning Kaktus (Pergerakan & Collision)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

   when I start as a clone
   // Penentuan Kostum Acak dan Posisi Awal Kanan Panggung
   switch costume to (pick random (1) to (3))
   go to x: (240) y: (-100)
   show

   // Pergerakan Rintangan ke Kiri
   repeat until <<(x position) < (-230)> or <(Status_Game) = [GAMEOVER]>>
       change x by ((Kecepatan_Game) * (-1))
       
       // Deteksi Tabrakan dengan Dino
       if <touching [Dino v]?> then
           broadcast [Game Over v]
       end
   end

   // Hapus Kloning setelah Melewati Ujung Kiri
   delete this clone


4. SISTEM KONTROL GAME, SKOR, DAN BROADCASTING
--------------------------------------------------

Sistem pusat mengelola status *Game Loop*, peningkatan kesulitan game secara bertahap, serta penanganan kondisi *Game Over*.

4.1 Skrip Pengendali Utama (Stage / Controller)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

   when green flag clicked
   // Inisialisasi Status Game
   set [Status_Game v] to [PLAYING]
   set [Skor v] to (0)
   set [Kecepatan_Game v] to (7)

   // Loop Penambahan Skor dan Kesulitan
   forever
       if <(Status_Game) = [PLAYING]> then
           wait (0.1) seconds
           change [Skor v] by (1)
           
           // Setiap kelipatan skor tertentu, tingkatkan kecepatan game
           if <((Skor) mod (100)) = [0]> then
               change [Kecepatan_Game v] by (0.5)
               start sound [Score Milestone v]
           end
       end
   end

4.2 Handling Sinyal Game Over
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

   when I receive [Game Over v]
   set [Status_Game v] to [GAMEOVER]
   start sound [Die v]
   stop [other scripts in sprite v]


5. FITUR OPTIMASI & PENGEMBANGAN LEBIH LANJUT
--------------------------------------------------

Guna meningkatkan kualitas game, beberapa fitur berikut dapat ditambahkan:

1. **Efek Crouch (Munduk)**: Menambahkan input tombol *Panah Bawah* untuk mengubah bentuk hit-box Dino menjadi lebih pendek guna menghindari rintangan burung (Pterodactyl).
2. **Backdrop Parallax Scrolling**: Membuat objek awan di latar belakang bergerak lebih lambat dibanding tanah untuk menciptakan efek kedalaman 3D (*depth of field*).
3. **Penyimpanan High Score**: Menggunakan *Cloud Variable* atau variabel penampung untuk menyimpan rekor skor tertinggi pemain.

.. warning::
   Pastikan nilai koordinat ``Y`` pada deteksi pendaratan tanah Dino konsisten antara kalkulasi lompatan dan posisi kemunculan Kaktus agar tidak terjadi pemicuan tabrakan palsu (*false collision*).
