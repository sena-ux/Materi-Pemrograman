# DOKUMENTASI LENGKAP SCRATCH: DARI KOMPONEN UTAMA HINGGA CUSTOM BLOCK

Dokumentasi ini dirancang sebagai panduan komprehensif, mendalam, dan terstruktur mengenai penggunaan platform **Scratch** untuk pengembangan game, simulasi, dan aplikasi interaktif. Panduan ini ditujukan bagi siswa SMA, mahasiswa, pengajar, maupun pemula yang ingin memahami konsep dasar pemrograman berbasis visual secara sistematis dan profesional.

---

## 1. ANATOMI DAN ANTARMUKA UTAMA SCRATCH

Scratch adalah lingkungan pemrograman berbasis blok visual (*block-based visual programming environment*) yang dikembangkan oleh MIT Media Lab. Antarmuka Scratch dirancang intuitif namun menyimpan landasan konsep pemrograman berorientasi objek (*Object-Oriented Programming* / OOP).

```
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
```

### 1.1 Sprite
* **Pengertian**: Sprite adalah objek digital dalam Scratch yang dapat bergerak, berganti kostum, bersuara, dan menerima instruksi program.
* **Peran Pemrograman (Konsep Object/Class)**: Dalam paradigma Pemrograman Berorientasi Objek (OOP), Sprite bertindak sebagai **Instance/Object**. Kostum dan posisi sprite merepresentasikan **Property/Attribute** (keadaan/state), sedangkan skrip kode yang ditempelkan padanya merepresentasikan **Method/Behavior** (perilaku).
* **Pengelolaan Sprite**:
  1. *Menambah Sprite*: Klik ikon Kucing dengan tanda plus `(+)` di pojok kanan bawah. Terdapat opsi memilih dari perpustakaan (*Choose a Sprite*), menggambar sendiri (*Paint*), memilih acak (*Surprise*), atau mengunggah berkas gambar milik sendiri (*Upload Sprite*).
  2. *Mengedit Sprite*: Melalui tab **Costumes**, pengguna dapat menggunakan editor vektor/bitmap untuk mengubah warna, menambah bentuk, menghapus bagian tertentu, atau merancang animasi antarkostum.

### 1.2 Stage & Backdrop
* **Konsep Sistem Koordinat Kartesius**: Panggung (Stage) Scratch menggunakan sistem koordinat Kartesius 2D untuk menentukan posisi presisi setiap Sprite.
  * **Sumbu X (Horizontal)**: Memiliki rentang dari `-240` (ujung kiri) hingga `+240` (ujung kanan). Total lebar: **480 piksel**.
  * **Sumbu Y (Vertikal)**: Memiliki rentang dari `-180` (ujung bawah) hingga `+180` (ujung atas). Total tinggi: **360 piksel**.
  * **Titik Pusat (Origin)**: Terletak pada titik koordinat `(X: 0, Y: 0)`.
* **Backdrop**: Merupakan gambar latar belakang dari Stage. Meskipun Stage dapat diprogram layaknya Sprite, Stage memiliki keterbatasan yaitu tidak dapat bergerak (tidak punya blok *Motion*) atau mengubah posisi koordinatnya.

```
                  +Y (Top: 180)
                        |
                        |
 -X (Left: -240) -------+------- +X (Right: 240)
                     (0,0)
                        |
                        |
                  -Y (Bottom: -180)
```

### 1.3 Block Palette Code
Block Palette adalah perpustakaan yang berisi seluruh blok perintah. Perintah-perintah dikelompokkan berdasarkan kategorinya dengan warna khas tertentu. Pengguna cukup melakukan tindakan *drag-and-drop* (seret dan lepas) dari palette ini ke dalam area kerja.

### 1.4 Workspace
Workspace adalah kanvas utama tempat pengembang menyusun, menyambungkan, dan merangkai blok-blok logika program. Setiap Sprite dan Stage memiliki Workspace tersendiri, sehingga logika program terdistribusi secara modular di masing-masing objek.

---

## 2. KATEGORI BLOK KODE DAN KARAKTERISTIK WARNANYA

Setiap kategori blok di Scratch ditandai dengan kode warna yang konsisten untuk mempermudah identifikasi fungsi saat pembacaan alur program.

| Kategori | Hex Color | Kode Warna Deskriptif | Fungsi Utama |
| :--- | :--- | :--- | :--- |
| **Motion** | `#4C97FF` | Biru Tua / Bright Blue | Mengontrol posisi, pergerakan, kecepatan, dan orientasi/rotasi sprite. |
| **Looks** | `#9966FF` | Ungu / Purple | Mengatur tampilan visual, kostum, latar belakang, ukuran, efek grafik, dan dialog text box. |
| **Sound** | `#CF63CF` | Merah Muda / Pink-Magenta | Mengelola playback audio, instrumen musik, efek suara, pitch, dan volume panggung. |
| **Events** | `#FFBF00` | Kuning / Yellow-Gold | Bertindak sebagai trigger (pemicu awal) yang mengeksekusi serangkaian blok skrip. |
| **Control** | `#FFAB19` | Oranye / Orange | Mengatur alur kontrol program (percabangan, perulangan, penundaan, serta pencetakan clone). |
| **Sensing** | `#5CB1D6` | Biru Muda / Light Blue | Mendeteksi interaksi pengguna, sentuhan fisik antar-objek, masukan mouse/keyboard, dan timer. |
| **Operators** | `#59C059` | Hijau / Green | Melakukan komputasi matematika, operasi logika boolean, perbandingan nilai, dan pengolahan string. |
| **Variables** | `#FF8C1A` | Oranye Tua / Dark Orange | Mengelola nilai variabel dinamis dan variabel deret data (List/Array). |

---

### 2.1 Motion (Biru Tua - `#4C97FF`)
Mengendalikan semua transformasi mekanis ruang 2D pada Sprite.

* **Fungsi Utama**: Mengatur pergeseran titik koordinat X dan Y, sudut rotasi (*direction*), serta navigasi arah.
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `move (10) steps`: Menggerakkan sprite maju sesuai arah (*direction*) saat ini sejauh piksel yang ditentukan.
  * `go to x: (0) y: (0)`: Memindahkan sprite secara instan ke titik koordinat tertentu.
  * `point in direction (90)`: Mengubah sudut orientasi sprite (90 = Kanan, -90 = Kiri, 0 = Atas, 180 = Bawah).

**Langkah demi Langkah (Pergerakan Karakter):**
```scratch
when green flag clicked
go to x: (-100) y: (0)
point in direction (90)
repeat (10)
    move (10) steps
end
```

---

### 2.2 Looks (Ungu - `#9966FF`)
Mengatur estetika dan interaksi visual antarmuka pengguna.

* **Fungsi Utama**: Mengubah pakaian/kostum sprite, menampilkan percakapan berbentuk *speech bubble*, serta memodifikasi ukuran dan transparansi visual.
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `say [Hello!] for (2) seconds`: Menampilkan balon kata berisi teks selama durasi waktu tertentu.
  * `switch costume to [costume2]`: Mengganti Tampilan visual sprite ke kostum spesifik.
  * `change [ghost v] effect by (25)`: Memodifikasi transparansi sprite (efek `ghost` 100 membuat sprite tidak terlihat).

**Langkah demi Langkah (Animasi Berjalan dan Dialog):**
```scratch
when green flag clicked
show
set size to (100) %
say [Ayo berpetualang!] for (2) seconds
repeat (5)
    next costume
    wait (0.2) seconds
end
```

---

### 2.3 Sound (Merah Muda/Pink - `#CF63CF`)
Memberikan efek auditif yang memperkaya imersi game atau aplikasi.

* **Fungsi Utama**: Memutar efek suara (*sound effect*), menghentikan musik latar, mengontrol pitch suara, dan mengatur tingkatan volume audio.
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `play sound [Pebble v] until done`: Memutar file audio hingga selesai sebelum melanjutkan ke blok berikutnya.
  * `start sound [Pop v]`: Memutar audio secara asinkron tanpa menghentikan alur blok di bawahnya.
  * `set volume to (100) %`: Mengatur keras suara pada nilai persentase tertentu.

**Langkah demi Langkah (Efek Suara Melompat):**
```scratch
when [space v] key pressed
start sound [Jump v]
change y by (50)
wait (0.1) seconds
change y by (-50)
```

---

### 2.4 Events (Kuning - `#FFBF00`)
Pemicu utama (*Event Handler*) yang memulai alur eksekusi baris kode.

* **Fungsi Utama**: Menangkap kejadian luar (sistem/pengguna) untuk memicu fungsi tertentu. Blok pada kategori ini memiliki bagian atas melengkung (*Hat Blocks*).
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `when green flag clicked`: Pemicu utama saat tombol bendera hijau ditekan oleh pengguna.
  * `when [space v] key pressed`: Pemicu yang merespons penekanan tombol keyboard.
  * `broadcast [Game Over v]`: Mengirimkan sinyal global pesan inter-process ke seluruh objek/sprite.

**Langkah demi Langkah (Kirim dan Terima Sinyal):**
```scratch
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
```

---

### 2.5 Control (Oranye - `#FFAB19`)
Mengontrol struktur logika, perulangan, dan percakapan kondisi program.

* **Fungsi Utama**: Membuat keputusan (*branching*), mengulang blok instruksi (*looping*), mengatur penundaan (*delay*), serta mengelola sistem duplikasi (*cloning*).
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `forever`: Perulangan tanpa batas (*infinite loop*) yang mengeksekusi blok di dalamnya secara terus-menerus.
  * `if <condition> then ... else ...`: Percakapan dua arah berdasarkan evaluasi boolean true/false.
  * `create clone of [myself v]`: Membuat duplikat dinamis dari sprite secara otomatis saat runtime.

**Langkah demi Langkah (Sistem Hujan Peluru/Cloning):**
```scratch
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
```

---

### 2.6 Sensing (Biru Muda - `#5CB1D6`)
Fasilitas deteksi input dari pengguna maupun lingkungan fisik virtual Scratch.

* **Fungsi Utama**: Membaca posisi mouse, penekanan keyboard, kalkulasi jarak, pendeteksian tabrakan piksel/warna, dan penerimaan teks dari pengguna.
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `touching [Sprite2 v]?`: Blok kondisi Boolean yang bernilai `true` jika terjadi tumpang tindih piksel dengan objek sasaran.
  * `key [space v] pressed?`: Memeriksa apakah tombol tertentu pada keyboard sedang ditahan/ditekan.
  * `ask [Siapa namamu?] and wait`: Menampilkan kotak input teks dan menyimpan nilainya pada blok `answer`.

**Langkah demi Langkah (Input Nama Player):**
```scratch
when green flag clicked
ask [Masukkan Nama Pemain:] and wait
say (join [Selamat datang, ] (answer)) for (2) seconds
```

---

### 2.7 Operators (Hijau - `#59C059`)
Mesin komputasi matematis dan evaluasi ekspresi logika.

* **Fungsi Utama**: Mengolah perhitungan arithmetic dasar (+, -, *, /), pembuat angka acak, penyambung kata (string manipulation), serta operasi logika (`AND`, `OR`, `NOT`).
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `(pick random (1) to (10))`: Mengembalikan nilai acak bulat secara inkremental dalam rentang batas yang diberikan.
  * `< <(Skor) > [50]> and <(Nyawa) > [0]> >`: Operasi kombinasi logika yang bernilai benar jika kedua kondisi terpenuhi.
  * `(join [Skor: ] (Skor_Player))`: Menggabungkan dua atau lebih nilai string/variabel menjadi satu kalimat murni.

**Langkah demi Langkah (Pengecekan Kelulusan Skor):**
```scratch
when green flag clicked
if << (Skor) > (100) > and < (Nyawa) > (0) >> then
    say [Selamat, Anda Menang!] for (2) seconds
else
    say [Coba Lagi!] for (2) seconds
end
```

---

### 2.8 Variables (Oranye Tua - `#FF8C1A`)
Penyimpanan nilai data terstruktur yang bersifat dinamis.

* **Fungsi Utama**: Menyimpan nilai statis/dinamis yang dapat diakses, diperbarui, dan dibaca di sepanjang runtime program. Kategori ini mencakup pembuatan **Variable** tunggal dan **List** (Array 1D).
* **Contoh Blok Kunci & Cara Penggunaan**:
  * `set [Skor v] to (0)`: Inisialisasi awal nilai variabel.
  * `change [Skor v] by (1)`: Menambahkan atau mengurangi (*inkremen/dekremen*) nilai variabel.
  * `add [Item] to [Inventory v]`: Memasukkan data baru ke urutan akhir dari struktur data List.

**Langkah demi Langkah (Pengelolaan Skor dan Inventori):**
```scratch
when green flag clicked
set [Skor v] to (0)
delete all of [Inventory v]
add [Pedang Kayu] to [Inventory v]
change [Skor v] by (10)
```

---

## 3. PANDUAN KODE INTERAKSI DAN LOGIKA GAME (GAME MECHANICS)

Konstruksi game profesional membutuhkan arsitektur logika mendasar agar sistem berjalan responsif, bebas dari keterlambatan input (*input lag*), serta terkoordinasi antar komponennya.

### 3.1 Smooth Movement (Gerakan Mulus Tanpa Delay Input)
Metode standar Scratch menggunakan blok `when [key v] pressed` bawaan seringkali menyebabkan jeda (stuttering) sesaat sebelum pergerakan berulang diproses. Hal ini terjadi karena penundaan bawaan dari sistem operasi (*OS key-repeat delay*).

**Solusi Murni Logika**: Menggunakan perulangan abadi (`forever`) yang menggabungkan blok `if` dengan pengecekan kondisi `key pressed?` secara kontinu tiap frame.

```scratch
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
```

---

### 3.2 Collision Detection (Deteksi Tabrakan)
Pendeteksian tabrakan berguna untuk mendeteksi kontak antar objek (misalnya Peluru mengenai Musuh, atau Karakter menyentuh Dinding).

#### Kasus A: Tabrakan Sederhana (Player & Koin)
```scratch
when green flag clicked
forever
    if <touching [Koin v]?> then
        change [Skor v] by (1)
        start sound [Coin sound v]
        broadcast [Respawn Koin v]
    end
end
```

#### Kasus B: Physics Bouncing/Sistem Penghambat Dinding
```scratch
when green flag clicked
forever
    change x by (Kecepatan_X)
    if <touching [Dinding v]?> then
        // Membalikkan pergerakan saat menabrak dinding
        change x by ((Kecepatan_X) * (-1))
    end
end
```

---

### 3.3 Game Loop (Loop Utama Game)
Game Loop adalah arsitektur inti dari pembuatan game yang mengeksekusi tiga fase utama secara terus-menerus: **Process Input -> Update Game State -> Render Graphics**.

```
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
```

**Implementasi Kode Game Loop pada Scratch:**
```scratch
when green flag clicked
// Phase 1: Initializing State
set [Status_Game v] to [PLAYING]
set [Nyawa v] to (3)
set [Skor v] to (0)
show

// Phase 2 & 3: The Main Game Loop
forever
    if <(Status_Game) = [PLAYING]> then
        // Sub-Routine 1: Input & Logic Processing
        if <key [space v] pressed?> then
            change y by (10)
        end
        
        // Gravity Simulation
        change y by (-3)
        
        // Check Conditions
        if <touching [Bahaya v]?> then
            change [Nyawa v] by (-1)
            go to x: (-180) y: (0)
        end
        
        // Check End Condition
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
```

---

### 3.4 Event Broadcasting (Komunikasi Antar-Sprite)
Sistem *Publish-Subscribe* yang memungkinkan suatu Sprite mengirimkan sinyal global untuk memicu respons skrip pada Sprite lain secara terdekopel (*decoupled architecture*).

**Elemen Utama Broadcasting:**
1. `broadcast [Pesan]`: Mengirim sinyal dan langsung melanjutkan eksekusi blok berikutnya.
2. `broadcast [Pesan] and wait`: Mengirim sinyal dan menunda eksekusi blok selanjutnya sampai seluruh skrip penerima selesai dijalankan.
3. `when I receive [Pesan]`: Event handler penerima sinyal.

```scratch
// --- SCRIPT 1: Pada Sprite Player ---
when green flag clicked
forever
    if <touching [Musuh v]?> then
        broadcast [Game Over v]
        stop [other scripts in sprite v]
        stop [this script v]
    end
end

// --- SCRIPT 2: Pada Sprite Game Over Screen (UI) ---
when green flag clicked
hide

when I receive [Game Over v]
go to x: (0) y: (0)
show
start sound [Lose Sound v]

// --- SCRIPT 3: Pada Sprite Musuh ---
when I receive [Game Over v]
stop [other scripts in sprite v]
hide
```

---

## 4. PANDUAN MEMBUAT & MENGGUNAKAN CUSTOM BLOCK (MY BLOCKS)

Fitur **Custom Block** pada Scratch merepresentasikan modulasi **Fungsi / Prosedur / Method** pada bahasa pemrograman modern berbasis teks seperti Python, C++, atau Java.

### 4.1 Mengapa Custom Block Penting?
1. **Prinsip DRY (Don't Repeat Yourself)**: Menghindari penulisan blok kode berseri yang repetitif.
2. **Modularisasi Kode**: Memecah program besar yang kompleks menjadi fungsi-fungsi kecil yang berfokus pada satu tugas spesifik.
3. **Kemudahan Maintenance & Debugging**: Jika terjadi kesalahan logika, pembenahan hanya perlu dilakukan pada definisi Custom Block terkait tanpa harus merombak seluruh alur program.
4. **Peningkatan Performa Execution**: Fasilitas opsional Scratch memungkinkan instruksi dijalankan secara langsung tanpa kalkulasi animasi visual per-frame.

---

### 4.2 Cara Membuat Custom Block
1. Buka tab **Code**, pilih kategori warna merah muda/pink **My Blocks**.
2. Klik tombol **Make a Block**.
3. Ketikkan nama fungsi utama pada jendela dialog.
4. Tambahkan argumen parameter yang dibutuhkan.
5. Tentukan pilihan centang opsi *Run without screen refresh*.
6. Klik **OK**.
7. Rangkai baris perintah logika di bawah blok utama `define [Nama Block]`.

```
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
```

---

### 4.3 Anatomi Parameter pada Custom Block
Saat merancang Custom Block, kita dapat melampirkan parameter data yang fleksibel:

1. **Input Angka/Teks (Value Parameter / String / Number)**:
   * Menerima variabel nilai seperti kecepatan, durasi, jarak, nama, atau indeks.
   * *Bentuk Visual*: Oval / Rounded Box.
2. **Input Boolean (Condition Parameter / True-False)**:
   * Menerima ekspresi operasi perbandingan logika.
   * *Bentuk Visual*: Hexagonal / Tepi Runcing.
3. **Teks Label (Static Text Decorator)**:
   * Digunakan sebagai pembatas deskriptif visual agar nama blok lebih intuitif dibaca oleh manusia.

---

### 4.4 Fitur Khusus: "Run Without Screen Refresh"
Scratch secara alami mengeksekusi logika visual dengan memunculkan pembaruan layar (*frame rendering*) sebesar **30 Frame Per Second (FPS)**. Setiap perulangan (*loop*) secara default menunda eksekusi selama ~33 milidetik untuk menggambar tampilan baru di layar.

* **Fungsi "Run without screen refresh"**: Jika opsi ini diaktifkan pada Custom Block, Scratch akan mengeksekusi seluruh baris perintah logika di dalam perulangan tersebut **secara instan dalam satu frame tunggal** (kurang dari 1 milidetik), tanpa menunggu antrean pembaruan animasi layar.
* **Kapan Harus Digunakan**:
  * Perhitungan kalkulasi kompleks (seperti pencarian rute, operasi matematika matriks, array sorting).
  * Penggambaran pola rumit dengan Extension *Pen*.
  * Deteksi collision kompleks atau penyesuaian posisi karakter (*Raycasting / Platformer Ground Check*).
* **Peringatan**: Jika perulangan tanpa akhir (*infinite loop*) ditaruh di dalam blok yang centang *Run without screen refresh*-nya aktif, Scratch akan mengalami pembekuan sistem (*freeze/crash*) karena CPU terjebak dalam loop tanpa batas.

---

### 4.5 Studi Kasus Penggunaan Custom Block

#### Studi Kasus 1: Mekanisme Fisika Melompat (Platformer Jump)
Mengisolasikan logika mekanis lompatan yang dipengaruhi oleh gravitasi dan ketinggian ke dalam Custom Block yang reusable.

```scratch
// Definisi Custom Block dengan Parameter Ketinggian & Kecepatan
define Lompat dengan ketinggian (Tinggi) dan kecepatan (Kecepatan)
set [Kecepatan_Y v] to (Kecepatan)
repeat (Tinggi)
    change y by (Kecepatan_Y)
    change [Kecepatan_Y v] by (-1)
end

// Implementasi Pemanggilan Blok pada Main Loop
when green flag clicked
go to x: (-150) y: (-100)
forever
    if <key [space v] pressed?> then
        Lompat dengan ketinggian (15) dan kecepatan (10)
    end
end
```

#### Studi Kasus 2: Generator Rintangan Otomatis (Procedural Generation)
Membuat fungsi terpusat untuk mencetak spawner rintangan secara dinamis menggunakan *Run Without Screen Refresh* agar inisialisasi awal tidak berbayang (*lagging*).

```scratch
// Definisi Custom Block untuk Pembuatan Obstacle
define Buat Rintangan di X: (Pos_X) Tipe: (Kostum_Ke)
create clone of [myself v]

when I start as a clone
// Blok ini menerima instruksi dari pemanggilan Custom Block
go to x: (Pos_X) y: (-120)
switch costume to (Kostum_Ke)
show
repeat until <(x position) < (-230)>
    change x by (-6)
end
delete this clone

// Implementasi Utama Spawner
when green flag clicked
hide
forever
    wait (pick random (1) to (3)) seconds
    Buat Rintangan di X: (240) Tipe: (pick random (1) to (3))
end
```

---

## 5. RANGKUMAN BEST PRACTICES PEMROGRAMAN SCRATCH

1. **Gunakan Penamaan Variabel yang Deskriptif**: Hindari variabel default seperti `variable1`. Gunakan nama lugas seperti `Skor_Pemain`, `Kecepatan_Musuh`, atau `Status_Selesai`.
2. **Inisialisasi Nilai Awal (Reset State)**: Selalu gunakan event `when green flag clicked` pada sprite utama untuk menentukan titik awal (Posisi X/Y, Kostum, Visibility `show`/`hide`, dan Variabel) agar tidak membawa sisa kondisi dari sesi play sebelumnya.
3. **Gunakan Broadcast untuk Manajemen Alur Game**: Pisahkan antara logika gameplay, UI/HUD, dan layar Game Over menggunakan Broadcast System.
4. **Optimalkan dengan Custom Block**: Jika ada 3 atau lebih blok bernilai sama yang ditulis berulang kali, bungkuslah ke dalam fungsi `My Blocks` agar proyek lebih tertata, bersih, dan mudah dirawat.
