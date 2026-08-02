========================================================================
DOKUMENTASI LENGKAP SCRATCH: DARI KOMPONEN UTAMA HINGGA CUSTOM BLOCK
========================================================================

Dokumentasi ini dirancang sebagai panduan komprehensif, mendalam, dan terstruktur mengenai penggunaan platform **Scratch** untuk pengembangan game, simulasi, dan aplikasi interaktif. Panduan ini ditujukan bagi siswa SMA, mahasiswa, pengajar, maupun pemula yang ingin memahami konsep dasar pemrograman berbasis visual secara sistematis dan profesional.

.. note::
   Scratch dikembangkan oleh MIT Media Lab dan dirancang untuk mengenalkan konsep-konsep pemrograman berorientasi objek (*Object-Oriented Programming*) serta pemikiran komputasional (*computational thinking*) tanpa hambatan sintaksis (*syntax error*).


1. ANATOMI DAN ANTARMUKA UTAMA SCRATCH
--------------------------------------------------

Antarmuka Scratch dirancang secara intuitif namun menyimpan landasan arsitektur perangkat lunak yang kokoh. Memahami komponen antarmuka adalah langkah awal sebelum menyusun logika program.

.. code-block:: text

   +-----------------------------------------------------------------------------------+
   |  [MenuBar] File  Edit  Tutorials  [Project Title]                     (Profile)  |
   +-------------------------------------------------------------+---------------------+
   | [Code] [Costumes] [Sounds]  |                               |                     |
   |                             |                               |       STAGE         |
   |  [Block Palette]            |          WORKSPACE            |    (Preview Area)   |
   |  - Motion                   |  (Area Pemrograman Utama)     |    (X: 0, Y: 0)     |
   |  - Looks                    |                               |                     |
   |  - Sound                    |   [When green flag clicked]   |                     |
   |  - Events                   |   [forever               ]    |                     |
   |  - Control                  |   |  [move (10) steps]   |    +---------------------+
   |  - Sensing                  |   +----------------------+    | SPRITE & BACKDROP   |
   |  - Operators                |                               | MANAGEMENT PANELS   |
   |  - Variables / My Blocks    |                               | [Sprite Info] [List]|
   +-----------------------------+-------------------------------+---------------------+


1.1 Sprite
~~~~~~~~~~

* **Pengertian**:
  Sprite adalah objek digital independen dalam panggung Scratch yang dapat berpindah tempat, mengubah tampilan, memutar suara, serta menerima instruksi skrip program.

* **Peran Pemrograman (Konsep Object & Class)**:
  Dalam paradigma Pemrograman Berorientasi Objek (*Object-Oriented Programming* / OOP):

  - Sprite bertindak sebagai **Instance / Object**.
  - Properti seperti posisi (*X, Y*), arah (*Direction*), dan Tampilan (*Costume*) bertindak sebagai **Attribute / State**.
  - Skrip blok kode yang ditempelkan padanya bertindak sebagai **Method / Behavior**.

* **Pengelolaan Sprite**:

  1. *Menambah Sprite*: Klik tombol berkepala kucing dengan tanda plus (``+``) di panel kanan bawah. Tersedia pilihan mengambil dari pustaka bawaan (*Choose a Sprite*), menggambar manual (*Paint*), memilih acak (*Surprise*), atau mengunggah berkas (*Upload Sprite*).
  2. *Mengedit Sprite*: Melalui tab **Costumes**, pengguna dapat mengedit elemen grafik vektor maupun bitmap untuk menciptakan variasi animasi atau bentuk objek.


1.2 Stage & Backdrop
~~~~~~~~~~~~~~~~~~~~

* **Konsep Sistem Koordinat Kartesius**:
  Panggung (*Stage*) Scratch diproyeksikan ke dalam bidang Kartesius dua dimensi (2D).

  - **Sumbu X (Horizontal)**: Rentang dari ``-240`` (ujung kiri) hingga ``240`` (ujung kanan). Lebar total panggung adalah **480 piksel**.
  - **Sumbu Y (Vertikal)**: Rentang dari ``-180`` (ujung bawah) hingga ``180`` (ujung atas). Tinggi total panggung adalah **360 piksel**.
  - **Titik Center (Origin)**: Berada tepat di tengah panggung pada koordinat ``(X: 0, Y: 0)``.

.. code-block:: text

                     +Y (Top: 180)
                           |
                           |
    -X (Left: -240) -------+------- +X (Right: 240)
                        (0,0)
                           |
                           |
                     -Y (Bottom: -180)

* **Backdrop**:
  Merupakan latar belakang visual dari Stage. Stage dapat diprogram dengan blok logika, tetapi memiliki keterbatasan yaitu tidak memiliki blok pergerakan (*Motion*) dan posisinya terfiksasi di latar belakang.


1.3 Block Palette Code
~~~~~~~~~~~~~~~~~~~~~~

Block Palette adalah perpustakaan perintah yang berisi seluruh blok kode Scratch. Perintah-perintah tersebut dikelompokkan berdasarkan fungsionalitasnya dan ditandai oleh warna khusus. Pengguna mengambil blok dari palette ini dengan cara menahan dan menggeser (*drag-and-drop*).


1.4 Workspace
~~~~~~~~~~~~~

Workspace adalah kanvas utama tempat merangkai dan menyusun blok-blok perintah. Setiap Sprite dan Stage memiliki Workspace terpisah, memungkinkan pemrograman yang terisolasi secara modular di masing-masing objek.


2. KATEGORI BLOK KODE DAN KARAKTERISTIK WARNANYA
--------------------------------------------------

Guna mempermudah pembacaan dan identifikasi alur program, Scratch mengelompokkan blok kode ke dalam 8 kategori utama dengan kode warna yang khas.

+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| Kategori      | Hex Code           | Deskripsi Warna          | Fungsi Utama                                                                    |
+===============+====================+==========================+=================================================================================+
| **Motion**    | ``#4C97FF``        | Biru Tua (*Bright Blue*) | Mengontrol pergerakan, posisi koordinat X/Y, arah, dan rotasi sprite.           |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Looks**     | ``#9966FF``        | Ungu (*Purple*)          | Mengatur kostum visual, teks percakapan, ukuran, dan efek grafis.              |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Sound**     | ``#CF63CF``        | Pink / Magenta           | Memutar audio, efek suara, kontrol volume, dan intonasi pitch.                  |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Events**    | ``#FFBF00``        | Kuning Emas (*Gold*)     | Pemicu eksekusi program (*Event Handlers*) saat kondisi tertentu terpenuhi.      |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Control**   | ``#FFAB19``        | Oranye (*Orange*)        | Mengendalikan alur logika (percabangan, perulangan, penundaan, kloning).        |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Sensing**   | ``#5CB1D6``        | Biru Muda (*Light Blue*) | Mendeteksi interaksi mouse, keyboard, jarak, dan sentuhan antar-objek.          |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Operators** | ``#59C059``        | Hijau (*Green*)          | Operasi matematika, ekspresi logika Boolean, dan manipulasi karakter teks.      |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+
| **Variables** | ``#FF8C1A``        | Oranye Tua (*Dark*)      | Penyimpanan data dinamis tunggal (*Variables*) dan deret data (*Lists/Arrays*). |
+---------------+--------------------+--------------------------+---------------------------------------------------------------------------------+


2.1 Motion (Biru Tua - ``#4C97FF``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini mengendalikan transformasi posisi dan rotasi Sprite di panggung 2D.

* **Fungsi Utama**: Mengubah koordinat X/Y, mengarahkan sudut pergerakan, dan mengatur mode rotasi.
* **Contoh Blok Kunci**:
  - ``move (10) steps``: Menggerakkan sprite sejauh nilai piksel tertentu sesuai arah (*direction*).
  - ``go to x: (0) y: (0)``: Memindahkan sprite secara instan ke koordinat spesifik.
  - ``point in direction (90)``: Mengatur orientasi sudut sprite (90=Kanan, -90=Kiri, 0=Atas, 180=Bawah).

**Langkah demi Langkah (Pergerakan Karakter)**:

.. code-block:: text

   when green flag clicked
   go to x: (-100) y: (0)
   point in direction (90)
   repeat (10)
       move (10) steps
   end


2.2 Looks (Ungu - ``#9966FF``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini mengatur tampilan visual dan antarmuka teks pada Sprite.

* **Fungsi Utama**: Mengganti kostum, menampilkan balon dialog, serta mengatur transparansi dan ukuran.
* **Contoh Blok Kunci**:
  - ``say [Halo!] for (2) seconds``: Menampilkan dialog balon kata selama durasi tertentu.
  - ``switch costume to [costume2]``: Mengubah tampilan kostum visual sprite.
  - ``change [ghost v] effect by (25)``: Mengubah tingkat transparansi sprite.

**Langkah demi Langkah (Animasi Berjalan dan Dialog)**:

.. code-block:: text

   when green flag clicked
   show
   set size to (100) %
   say [Ayo mulai petualangan!] for (2) seconds
   repeat (5)
       next costume
       wait (0.2) seconds
   end


2.3 Sound (Merah Muda/Pink - ``#CF63CF``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini mengelola pemutaran efek audio dan musik latar.

* **Fungsi Utama**: Memutar suara, menghentikan audio, serta mengubah pitch dan volume panggung.
* **Contoh Blok Kunci**:
  - ``play sound [Pop v] until done``: Memutar audio hingga selesai sebelum melangkah ke blok berikutnya.
  - ``start sound [Coin v]``: Memutar audio secara asinkron tanpa menahan alur eksekusi skrip.
  - ``set volume to (100) %``: Mengatur intensitas volume suara.

**Langkah demi Langkah (Efek Suara Melompat)**:

.. code-block:: text

   when [space v] key pressed
   start sound [Jump v]
   change y by (50)
   wait (0.1) seconds
   change y by (-50)


2.4 Events (Kuning - ``#FFBF00``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini bertindak sebagai pemicu (*Hat Blocks*) yang mengawali eksekusi skrip.

* **Fungsi Utama**: Menangkap masukan sistem/pengguna untuk memicu eksekusi serangkaian blok kode.
* **Contoh Blok Kunci**:
  - ``when green flag clicked``: Pemicu utama saat tombol bendera hijau ditekan.
  - ``when [space v] key pressed``: Pemicu saat tombol papan ketik tertentu ditekan.
  - ``broadcast [Start Game v]``: Mengirim sinyal pesan global ke seluruh objek program.

**Langkah demi Langkah (Sistem Kirim dan Terima Sinyal)**:

.. code-block:: text

   // Pada Sprite Musuh
   when green flag clicked
   forever
       if <touching [Player v]?> then
           broadcast [Game Over v]
           stop [this script v]
       end
   end

   // Pada Sprite UI Game Over
   when I receive [Game Over v]
   show
   go to x: (0) y: (0)


2.5 Control (Oranye - ``#FFAB19``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini mengatur alur eksekusi program (*control flow*).

* **Fungsi Utama**: Membuat struktur perulangan (*loops*), pengondisian (*branching*), penundaan (*delay*), dan penggandaan (*cloning*).
* **Contoh Blok Kunci**:
  - ``forever``: Perulangan abadi yang mengeksekusi skrip di dalamnya terus-menerus.
  - ``if <condition> then ... else ...``: Percabangan kondisi dua arah.
  - ``create clone of [myself v]``: Memproduksi salinan duplikat sprite secara dinamis saat program berjalan.

**Langkah demi Langkah (Sistem Hujan Objek / Kloning)**:

.. code-block:: text

   when green flag clicked
   hide
   forever
       wait (1) seconds
       create clone of [myself v]
   end

   when I start as a clone
   show
   go to x: (pick random (-200) to (200)) y: (180)
   repeat until <(y position) < (-170)>
       change y by (-5)
   end
   delete this clone


2.6 Sensing (Biru Muda - ``#5CB1D6``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini bertugas mengindera lingkungan fisik virtual panggung Scratch.

* **Fungsi Utama**: Membaca input kursor mouse, tombol keyboard, jarak antar-sprite, dan kordinasi warna.
* **Contoh Blok Kunci**:
  - ``touching [Sprite2 v]?``: Mengembalikan nilai `true` jika terjadi persinggungan piksel.
  - ``key [space v] pressed?``: Mengembalikan nilai `true` selama tombol keyboard ditahan.
  - ``ask [Siapa namamu?] and wait``: Membuka dialog input teks dan menyimpan hasilnya pada blok ``answer``.

**Langkah demi Langkah (Input Nama Pemain)**:

.. code-block:: text

   when green flag clicked
   ask [Masukkan nama pemain:] and wait
   say (join [Selamat datang, ] (answer)) for (2) seconds


2.7 Operators (Hijau - ``#59C059``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini merupakan pusat komputasi matematis dan perbandingan logika.

* **Fungsi Utama**: Perhitungan aritmatika dasar, pengolahan string, operasi logika (`AND`, `OR`, `NOT`), dan pencetakan angka acak.
* **Contoh Blok Kunci**:
  - ``(pick random (1) to (10))``: Menghasilkan bilangan bulat acak dalam rentang specified.
  - ``< <(Skor) > [50]> and <(Nyawa) > [0]> >``: Pengondisian majemuk dengan operator logika `AND`.
  - ``(join [Skor: ] (Skor_Player))``: Menggabungkan dua nilai string menjadi satu pesan.

**Langkah demi Langkah (Pengecekan Kemenangan)**:

.. code-block:: text

   when green flag clicked
   if << (Skor) > (100) > and < (Nyawa) > (0) >> then
       say [Anda Menang!] for (2) seconds
   else
       say [Coba Lagi!] for (2) seconds
   end


2.8 Variables (Oranye Tua - ``#FF8C1A``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kategori ini mengelola alokasi memori tempat menyimpan nilai data program.

* **Fungsi Utama**: Membaca, menginisialisasi, dan mengoperasikan nilai variabel tunggal maupun deret data (*List/Array*).
* **Contoh Blok Kunci**:
  - ``set [Skor v] to (0)``: Menginisialisasi nilai awal variabel.
  - ``change [Skor v] by (1)``: Menambah atau mengurangi nilai variabel secara inkremental.
  - ``add [Pedang] to [Inventory v]``: Menambahkan elemen baru ke dalam struktur data List.

**Langkah demi Langkah (Sistem Skor dan Inventori)**:

.. code-block:: text

   when green flag clicked
   set [Skor v] to (0)
   delete all of [Inventory v]
   add [Pedang Kayu] to [Inventory v]
   change [Skor v] by (10)


3. PANDUAN KODE INTERAKSI DAN LOGIKA GAME (GAME MECHANICS)
--------------------------------------------------

Arsitektur game yang solid membutuhkan implementasi mekanisme dasar yang responsif dan terbebas dari kendala input.


3.1 Smooth Movement (Gerakan Mulus Tanpa Delay)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Penggunaan blok bawaan ``when [key v] pressed`` sering kali menimbulkan penundaan (*input lag*) akibat *OS key-repeat delay*.

.. warning::
   Jangan gunakan blok ``when [key v] pressed`` untuk menggerakkan karakter dalam game aksi atau platformer karena akan terjadi *stuttering* pada detik pertama pergerakan.

**Solusi Murni Logika**: Menggabungkan blok ``forever``, ``if``, dan pemindaian status kondisi ``key pressed?`` pada setiap frame.

.. code-block:: text

   when green flag clicked
   forever
       if <key [arrow right v] pressed?> then
           point in direction (90)
           change x by (5)
       end
       if <key [arrow left v] pressed?> then
           point in direction (-90)
           change x by (-5)
       end
       if <key [arrow up v] pressed?> then
           change y by (5)
       end
       if <key [arrow down v] pressed?> then
           change y by (-5)
       end
   end


3.2 Collision Detection (Deteksi Tabrakan)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mekanisme ini mendeteksi interaksi fisik antar-objek seperti karakter dengan koin atau dinding rintangan.

**A. Tabrakan Karakter dengan Koin**:

.. code-block:: text

   when green flag clicked
   forever
       if <touching [Koin v]?> then
           change [Skor v] by (1)
           start sound [Coin v]
           broadcast [Respawn Koin v]
       end
   end

**B. Tabrakan dengan Dinding (Physics Rebound)**:

.. code-block:: text

   when green flag clicked
   forever
       change x by (Kecepatan_X)
       if <touching [Dinding v]?> then
           change x by ((Kecepatan_X) * (-1))
       end
   end


3.3 Game Loop (Siklus Utama Game)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Game Loop adalah arsitektur terpusat yang mengatur tiga fase utama secara kontinu: **Input Processing -> State Update -> Screen Rendering**.

.. code-block:: text

      +-------------------------------------------------------+
      |                      START                            |
      +-------------------------------------------------------+
                                  |
                                  v
                        [ Inisialisasi Data ]
                        (Skor=0, Nyawa=3, Posisi)
                                  |
                                  v
   +---> [ 1. Read Input ]  (Keyboard / Mouse)
   |              |
   |              v
   |     [ 2. Update State ] (Hitung Pergerakan, Tabrakan, Fisika)
   |              |
   |              v
   |     [ 3. Render ]       (Ganti Kostum, Efek Visual, Suara)
   |              |
   +--------------+--- Status Game Active? (Nyawa > 0)
                  |
                  | (TIDAK)
                  v
        +-------------------+
        |  BROADCAST GAMEOVER|
        +-------------------+

**Implementasi Kode Game Loop pada Scratch**:

.. code-block:: text

   when green flag clicked
   // Phase 1: Inisialisasi Data
   set [Status_Game v] to [PLAYING]
   set [Nyawa v] to (3)
   set [Skor v] to (0)
   show

   // Phase 2 & 3: Game Loop Utama
   forever
       if <(Status_Game) = [PLAYING]> then
           // Update Posisi & Fisika
           if <key [space v] pressed?> then
               change y by (10)
           end
           change y by (-3) // Simulasi Gravitasi
           
           // Evaluasi Kontak Tabrakan
           if <touching [Bahaya v]?> then
               change [Nyawa v] by (-1)
               go to x: (-180) y: (0)
           end
           
           // Evaluasi Kondisi Akhir Game
           if <(Nyawa) <= (0)> then
               set [Status_Game v] to [GAMEOVER]
           end
       else
           if <(Status_Game) = [GAMEOVER]> then
               broadcast [Trigger_Game_Over v]
               hide
               stop [this script v]
           end
       end
   end


3.4 Event Broadcasting (Kirim dan Terima Sinyal)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sistem pesan asinkron yang memungkinkan decoupling komunikasi antar-sprite secara independen.

.. code-block:: text

   // --- SCRIPT 1: Pada Sprite Player ---
   when green flag clicked
   forever
       if <touching [Musuh v]?> then
           broadcast [Game Over v]
           stop [other scripts in sprite v]
           stop [this script v]
       end
   end

   // --- SCRIPT 2: Pada Sprite UI Game Over ---
   when green flag clicked
   hide

   when I receive [Game Over v]
   go to x: (0) y: (0)
   show
   start sound [Lose v]

   // --- SCRIPT 3: Pada Sprite Musuh ---
   when I receive [Game Over v]
   stop [other scripts in sprite v]
   hide


4. PANDUAN MEMBUAT & MENGGUNAKAN CUSTOM BLOCK (MY BLOCKS)
--------------------------------------------------

Custom Block pada Scratch sepadan dengan konsep **Fungsi / Prosedur / Method** dalam bahasa pemrograman berbasis teks seperti Python atau Java.


4.1 Mengapa Custom Block Penting?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Prinsip DRY (*Don't Repeat Yourself*)**: Menghindari redundansi penulisan kumpulan blok yang sama secara berulang-ulang.
2. **Modularisasi Kode**: Memecah arsitektur program yang kompleks menjadi sub-rutin kecil berfokus tunggal.
3. **Kemudahan Maintenance & Debugging**: Isolasi bug program dapat ditangani langsung dari definisi blok tanpa mengganggu alur utama.
4. **Peningkatan Performa**: Fitur khusus Scratch dapat mengabaikan rendering visual antar-frame untuk perhitungan instan.


4.2 Cara Membuat Custom Block
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Buka tab **Code**, lalu pilih kategori **My Blocks** (Merah Muda).
2. Klik tombol **Make a Block**.
3. Masukkan nama fungsi utama.
4. Tambahkan parameter yang dibutuhkan (*number/text*, *boolean*, atau *label*).
5. Centang opsi *Run without screen refresh* bila diperlukan.
6. Klik **OK**, lalu susun baris instruksi di bawah blok ``define``.

.. code-block:: text

   +---------------------------------------------+
   |               Make a Block                  |
   +---------------------------------------------+
   |  [ Buat_Karakter_Lompat                   ] |
   |                                             |
   |  (+ Add an input)  (+ Add an input)  (+ Add) |
   |      number/text       boolean       label  |
   |                                             |
   |  [x] Run without screen refresh             |
   |                                             |
   |             [ Cancel ]  [ OK ]              |
   +---------------------------------------------+


4.3 Anatomi Parameter pada Custom Block
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* **Input Angka / Teks (*Value Parameter*)**:
  Menerima nilai data numerik atau string seperti kecepatan, durasi, atau jarak.
  *Bentuk Visual*: Oval / Rounded.

* **Input Boolean (*Condition Parameter*)**:
  Menerima argumen pernyataan logika bernilai `true` atau `false`.
  *Bentuk Visual*: Hexagonal / Tepi Runcing.

* **Teks Label (*Static Label*)**:
  Teks dekoratif statis untuk memperjelas konteks pembacaan nama fungsi bagi pemrogram.


4.4 Fitur Khusus: "Run Without Screen Refresh"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Secara alami, Scratch mengeksekusi animasi panggung pada kecepatan **30 Frame Per Second (FPS)**. Setiap perulangan (*loop*) standar menunda eksekusi selama ~33 milidetik untuk menggambar perubahan pada layar.

.. note::
   Jika opsi **Run without screen refresh** diaktifkan pada Custom Block, seluruh perintah logika di dalam blok tersebut akan dieksekusi **secara instan dalam 1 frame tunggal** (kurang dari 1 milidetik).

**Kapan Harus Digunakan?**

- Kalkulasi matematika rumit (misalnya perbandingan matriks atau array sorting).
- Menggambar objek detail menggunakan extension *Pen*.
- Sistem deteksi landasan platformer (*Ground Alignment Check*) agar tidak terlihat membal di layar.

.. warning::
   Jangan meletakkan perulangan abadi (``forever``) di dalam Custom Block yang mengaktifkan *Run without screen refresh*, karena akan menyebabkan sistem program membeku (*freeze/crash*).


4.5 Studi Kasus Penggunaan Custom Block
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Studi Kasus 1: Mekanisme Fisika Melompat (Platformer Jump)**

.. code-block:: text

   // Definisi Custom Block dengan Parameter
   define Lompat dengan ketinggian (Tinggi) dan kecepatan (Kecepatan)
   set [Kecepatan_Y v] to (Kecepatan)
   repeat (Tinggi)
       change y by (Kecepatan_Y)
       change [Kecepatan_Y v] by (-1)
   end

   // Eksekusi Pemanggilan pada Loop Utama
   when green flag clicked
   go to x: (-150) y: (-100)
   forever
       if <key [space v] pressed?> then
           Lompat dengan ketinggian (15) dan kecepatan (10)
       end
   end

**Studi Kasus 2: Generator Rintangan Otomatis (Procedural Spawner)**

.. code-block:: text

   // Definisi Custom Block Spawner
   define Buat Rintangan di X: (Pos_X) Tipe: (Kostum_Ke)
   create clone of [myself v]

   when I start as a clone
   go to x: (Pos_X) y: (-120)
   switch costume to (Kostum_Ke)
   show
   repeat until <(x position) < (-230)>
       change x by (-6)
   end
   delete this clone

   // Pemanggilan Fungsi pada Main Handler
   when green flag clicked
   hide
   forever
       wait (pick random (1) to (3)) seconds
       Buat Rintangan di X: (240) Tipe: (pick random (1) to (3))
   end


5. RANGKUMAN BEST PRACTICES PEMROGRAMAN SCRATCH
--------------------------------------------------

1. **Gunakan Penamaan Variabel yang Jelas**: Gunakan nama variabel eksplisit seperti ``Skor_Pemain`` atau ``Kecepatan_Atas`` alih-alih nama standar ``variable1``.
2. **Inisialisasi Nilai Awal (*Reset State*)**: Selalu tentukan titik koordinat awal, kostum, transparansi, dan nilai variabel saat event ``when green flag clicked`` dijalankan.
3. **Dekopel Logika dengan Broadcasting**: Pisahkan logika interaksi karakter utama dengan UI/HUD menggunakan pesan broadcast.
4. **Optimalkan Struktur dengan Custom Block**: Kelompokkan urutan instruksi repetitif ke dalam Custom Block untuk keterbacaan kode yang bersih dan terstruktur.
