#### Nama		: Riska Dwi Astia Ningrum
#### NIM		: 5311421007
#### Rombel 	: 1 (Senin 09.00)

# PRAKTIKUM 6 BEST FIRST SEARCH
# PERMAINAN TIC TAC TOE


#### Tugas
Tuliskan semua Java Code diatas, kemudian pelajari code nya, dan ubahkan beberapa bagian untuk melihat perubahannya

#### Penyelesaian
Pada praktikum 6 ini memperlihatkan bagaimana membuat sebuah permainan tic tac toe.  Ketika pemain pertama menekan salah satu ubin, maka ubin tersebut akan diberikan tanda silang. Pemain kedua harus menghalangi pemain pertama untuk membuat tanda silang berjajaran baik secara vertikal, horizontal, atau diagonal. Permainan ini akan berakhir (goal state) ketika salah seorang pemain sudah menderetkan tanda meraka masing-masing baik secara vertikal, horizontal, atau diagonal.

##### Implementasi Permainan Tic Tac Toe Menggunakan Graphical User Interface (GUI)
Permainan ini dibuatkan dengan menggunakan Java Swing yang terdiri dari 3 buah Java Class dan 3 buah pendeklarasian enumaration. Ke-enam file tersebut dituliskan secara terpisah namun disimpan pada folder yang sama yaitu folder TicTacToe seperti berikut ini. 

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/6%20file%20job%206.png)

1. GameState.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/1-6.png)

- GameState adalah file yang berisi enumerasi GameState. Enum ini digunakan untuk mengidentifikasi berbagai keadaan permainan.
- Ada empat nilai dalam enumerasi ini:
PLAYING: Menunjukkan bahwa permainan sedang berlangsung, dan belum ada pemenang atau seri.
DRAW: Menunjukkan bahwa permainan berakhir dalam keadaan seri (seri).
CROSS_WON: Menunjukkan bahwa pemain yang menggunakan simbol "CROSS" (X) telah memenangkan permainan.
NOUGHT_WON: Menunjukkan bahwa pemain yang menggunakan simbol "NOUGHT" (O) telah memenangkan permainan.


2. Seed.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/2-6.png)

- Seed adalah file yang berisi enumerasi Seed. Enum ini digunakan untuk merepresentasikan isi sel dalam papan permainan (Tic Tac Toe).
- Ada tiga nilai dalam enumerasi ini:
EMPTY: Menunjukkan bahwa sel pada papan permainan masih kosong.
CROSS: Menunjukkan bahwa sel diisi dengan simbol "CROSS" (X).
NOUGHT: Menunjukkan bahwa sel diisi dengan simbol "NOUGHT" (O).

3. State.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/3-6.png)

- Dalam kode di atas, enumerasi State yang mendefinisikan berbagai keadaan permainan dalam permainan Tic Tac Toe:
PLAYING: Menunjukkan bahwa permainan sedang berlangsung, dan belum ada pemenang.
DRAW: Menunjukkan bahwa permainan berakhir dengan seri (seri) karena tidak ada yang memenangkan.
CROSS_WON: Menunjukkan bahwa pemain yang menggunakan simbol "CROSS" (X) telah memenangkan permainan.
NOUGHT_WON: Menunjukkan bahwa pemain yang menggunakan simbol "NOUGHT" (O) telah memenangkan permainan.

4. Cell.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/4-6%20cell.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/5-6%20cell.png)
Kelas Cell dalam permainan Tic Tac Toe. Ini adalah kelas yang digunakan untuk merepresentasikan sel atau kotak pada papan permainan. Kode ini adalah bagian penting dalam permainan Tic Tac Toe karena bertanggung jawab untuk menggambar sel-sel pada papan permainan dan menunjukkan apakah sel tersebut kosong, berisi "CROSS", atau "NOUGHT". Ini membantu memvisualisasikan permainan kepada pemain dan memastikan bahwa seluruh permainan berjalan dengan baik.

- Seed content: Variabel ini digunakan untuk menyimpan isi dari sel tersebut, yang dapat berisi Seed.EMPTY, Seed.CROSS, atau Seed.NOUGHT.
- int row, col: Variabel ini digunakan untuk menyimpan baris dan kolom dari sel tersebut.
- Konstruktor Cell(int row, int col): Konstruktor ini digunakan untuk menginisialisasi sel dengan baris dan kolom yang diberikan dan kemudian mengosongkan isinya dengan memanggil metode clear().
- Metode clear(): Metode ini digunakan untuk mengosongkan sel dengan mengatur content ke Seed.EMPTY.
- Metode paint(Graphics g):Metode ini digunakan untuk menggambar sel pada papan permainan.
    - Pertama, kode menggambarkan garis simbol "CROSS" (X) jika content adalah Seed.CROSS.Ini dilakukan dengan mengatur warna menjadi merah (Color.RED) dan menggunakan Graphics2D untuk menggambar dua garis yang membentuk simbol "X".
    - Kedua, jika content adalah Seed.NOUGHT, maka kode menggambar simbol "NOUGHT" (O). Ini dilakukan dengan mengatur warna menjadi biru (Color.BLUE) dan menggambar lingkaran (oval) pada sel yang sesuai dengan ukuran simbol.

5. Board.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/6-6%20board.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/7-6%20board.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/8-6%20board.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/9-6%20board.png)
Kelas Board dalam permainan Tic Tac Toe. Kelas ini digunakan untuk merepresentasikan papan permainan dan mengelola sel-selnya. Kelas Board bertanggung jawab untuk mengelola seluruh papan permainan dan memastikan bahwa sel-selnya digambar dengan benar, serta memeriksa apakah permainan telah berakhir dalam keadaan seri atau ada pemenang.

- Cell[][] cells: Variabel ini adalah array 2D yang berisi sel-sel dalam papan permainan. Seluruh papan permainan terdiri dari sel-sel ini.
- Konstruktor Board(): Konstruktor ini digunakan untuk menginisialisasi papan permainan. Ini mengalokasikan array 2D untuk sel-sel papan dan menginisialisasi masing-masing sel dengan baris dan kolom yang sesuai menggunakan objek Cell.
-Metode init():Metode ini digunakan untuk menginisialisasi ulang papan permainan dengan mengosongkan isi semua sel. Ini digunakan untuk memulai permainan baru.
- Metode isDraw():Metode ini mengembalikan true jika permainan berakhir dalam keadaan seri (seri) karena tidak ada sel kosong tersisa di papan permainan. Ini memeriksa semua sel pada papan dan memeriksa apakah ada sel kosong (Seed.EMPTY) yang tersisa.
- Metode hasWon(Seed seed, int seedRow, int seedCol): Metode ini mengembalikan true jika pemain dengan seed (simbol) yang diberikan telah memenangkan permainan setelah meletakkan simbolnya di sel (seedRow, seedCol). Ini memeriksa apakah pemain telah mencapai tiga simbol yang sama secara berurutan dalam baris, kolom, atau diagonal yang melalui sel yang ditentukan.
- Metode paint(Graphics g): Metode ini digunakan untuk menggambar papan permainan dan sel-selnya.
    - Pertama, kode menggambar garis grid pada papan dengan warna abu-abu (Color.GRAY).
    - Selanjutnya, kode mengiterasi seluruh sel pada papan dan memanggil metode paint() pada masing-masing sel untuk menggambar simbolnya.

6. GameMain.Java
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/10-6%20gamemain.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/11-6.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/12-6.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/13-6.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/14-6.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/15-6.png)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/16-6.png)
Kelas GameMain dalam permainan Tic Tac Toe yang berfungsi sebagai GUI untuk permainan. Kelas GameMain ini adalah bagian penting dalam implementasi permainan Tic Tac Toe. Ini menggabungkan berbagai komponen permainan, mengelola logika permainan, dan menangani tampilan GUI. Ketika pemain melakukan klik pada papan permainan, permainan akan bereaksi sesuai, menggambarkan perubahan pada layar, dan memberikan pesan status.
- Kode ini mendefinisikan berbagai konstanta yang digunakan dalam permainan, seperti jumlah baris dan kolom pada papan permainan, ukuran sel, lebar garis grid, dan lain-lain.
- Konstruktor ini digunakan untuk menginisialisasi UI dan komponen permainan.
- Mendefinisikan MouseListener untuk menangani klik mouse pada papan permainan.
- Menginisialisasi status bar (JLabel) untuk menampilkan pesan status permainan.
- Mengatur tata letak dan dimensi panel permainan.
- Menginisialisasi papan permainan dengan memanggil initGame().
- Metode initGame(): Metode ini digunakan untuk menginisialisasi ulang konten papan permainan dan mengatur currentState menjadi PLAYING.
Seluruh sel pada papan diatur sebagai kosong (EMPTY).
Pemain pertama adalah "CROSS."
- Metode updateGame(Seed theSeed, int row, int col): Metode ini digunakan untuk memperbarui keadaan permainan setelah pemain dengan simbol "theSeed" telah meletakkan simbolnya di sel (row, col).
Memeriksa apakah pemain tersebut telah memenangkan permainan atau apakah permainan berakhir seri. Jika ya, currentState diubah sesuai.
- Metode paintComponent(Graphics g): Metode ini digunakan untuk menggambar komponen permainan di panel.
Meminta papan permainan (board) untuk menggambar dirinya sendiri.
Menampilkan pesan status di status bar sesuai dengan currentState.
- Metode main(String[] args):Metode main yang menjadi titik masuk program.
Menjalankan GUI construction codes dalam thread Event-Dispatching untuk keamanan thread.
Membuat dan menampilkan frame permainan.

##### Hasil Program dan Percobaan
Percobaan pemain pertama "CROSS" (X) = MENANG

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/menang%20x.png)

Percobaan pemain kedua "NOUGHT" (O) = MENANG

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/menang%200.png)

Percobaan Kedua Pemaian KALAH

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/kalah%20job%206.png)

##### Analisa Hasil Percobaan
Dalam permainan Tic Tac Toe, goal state adalah keadaan di mana salah satu pemain telah memenangkan permainan atau permainan berakhir dengan seri (draw). Berikut adalah deskripsi goal state dalam permainan Tic Tac Toe:
- Goal State (Pemenang): Goal state tercapai ketika salah satu pemain berhasil menempatkan tiga simbol (X atau O) secara berurutan dalam satu baris, satu kolom, atau salah satu dari dua diagonal. Goal state ini akan menghasilkan kemenangan bagi pemain yang mencapainya. Dalam kasus ini, GameState akan diatur ke CROSS_WON atau NOUGHT_WON, tergantung pada pemain yang memenangkan permainan.
- Goal State (Seri): Goal state juga tercapai jika seluruh sel di papan permainan terisi dan tidak ada pemain yang memenangkan permainan. Ini menunjukkan bahwa permainan berakhir dalam keadaan seri (draw), dan GameState akan diatur ke DRAW.

Jadi, dalam permainan Tic Tac Toe, ada dua goal state utama: pemain memenangkan permainan atau permainan berakhir dengan seri. Tujuan pemain adalah mencapai goal state pertama, sementara tujuan lainnya adalah menghindari goal state kedua saat bermain agar tidak berakhir seri.

##### Analisa Algoritma Best First Search dalam Permainan Tic Tac Toe 
Tic Tac Toe dan algoritma pencarian Best-First Search (BFS) memiliki hubungan dalam konteks kecerdasan buatan dan permainan. Di bawah ini, saya akan menjelaskan hubungannya:
- Tic Tac Toe adalah permainan papan dua pemain yang bersifat deterministik, artinya setiap langkah yang diambil oleh pemain akan menghasilkan keadaan permainan yang dapat diprediksi. Oleh karena itu, permainan ini dapat dimodelkan sebagai pohon pencarian, di mana setiap simpul dalam pohon adalah keadaan permainan yang mungkin.
- Best-First Search dalam Pencarian Game: Best First Search adalah salah satu algoritma pencarian yang digunakan dalam permainan untuk mencari langkah terbaik. Algoritma ini mencoba untuk mengeksplorasi pohon pencarian dengan memilih simpul yang paling menjanjikan berdasarkan fungsi evaluasi atau heuristik tertentu. Dalam konteks Tic Tac Toe, fungsi evaluasi biasanya akan mempertimbangkan seberapa baik keadaan saat ini untuk pemain, seberapa buruk untuk lawan, dan sejauh mana keadaan saat ini menuju goal state (kemenangan atau seri).
- Penerapan Best-First Search dalam Tic Tac Toe: Dalam implementasi Best-First Search dalam permainan Tic Tac Toe, algoritma tersebut akan menjelajahi pohon pencarian untuk menentukan langkah terbaik yang harus diambil oleh pemain saat ini. Ini melibatkan pemilihan simpul dengan nilai evaluasi terbaik, yang dapat mencapai kemenangan atau menghindari kekalahan.
- Heuristik: Heuristik dalam Best-First Search untuk Tic Tac Toe adalah kunci. Ini adalah fungsi evaluasi yang memberikan nilai pada setiap keadaan permainan yang dievaluasi. Fungsi ini harus dirancang sedemikian rupa sehingga dapat membedakan antara keadaan yang menguntungkan dan merugikan untuk pemain, sehingga Best-First Search dapat memutuskan langkah yang optimal.
- Pohon Pencarian: Pohon pencarian dalam Tic Tac Toe akan tumbuh seiring berjalannya permainan. Pemain akan mencoba langkah-langkah berbeda dan menjelajahi berbagai cabang pohon pencarian untuk mencapai goal state yang menguntungkan. 
