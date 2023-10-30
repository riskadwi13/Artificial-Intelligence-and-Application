#### Nama		: Riska Dwi Astia Ningrum
#### NIM		: 5311421007
#### Rombel 	: 1 (Senin 09.00)

# PRAKTIKUM 5
# TEKNIK HEURISTIC SEARCH


#### Tugas
1.	Pelajari class EightPuzzleSearch, EightPuzzleSpace, dan Node. 
2.	Ubahlah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 8. Kemudian tentukan langkah-langkah mana saja sehingga puzzlenya mencapai goal state. Analisa dan bedakan dengan solusi pada point 1. 
3.	Ubahlah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 5.9. Kemudian tentukan langkah-langkah mana saja sehingga puzzlenya mencapai goal state. Analisa dan bedakan dengan solusi pada point 1 dan 2.
4.	Ubahlah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 5.10. Kemudian tentukan langkah-langkah mana saja sehingga puzzlenya mencapai goal state. Analisa dan bedakan dengan solusi pada point 1, 2, dan 3. 
5.	Ubahlah initial dan goal state dari program dan class-class di atas sehingga bentuk initial dan goal statenya Gambar 5.11. Kemudian tentukan langkah-langkah mana saja sehingga puzzlenya mencapai goal state.


#### Penyelesaian
1.	Mempelajari class EightPuzzleSearch, EightPuzzleSpace, dan Node
##### Kelas EightPuzzleSearch:
- Kelas EightPuzzleSearch bertanggung jawab untuk melakukan pencarian solusi untuk masalah 8-puzzle.
- Kelas ini bergantung pada kelas EightPuzzleSpace untuk mendapatkan informasi tentang ruang pencarian dan menggunakan kelas Node untuk mewakili simpul dalam pencarian
- Vektor `open` digunakan untuk menyimpan simpul-simpul yang perlu dieksplorasi, dan vektor `closed` menyimpan simpul-simpul yang telah dieksplorasi.
- Kelas ini memiliki dua fungsi heuristik, yaitu `h1Cost()` dan `h2Cost()`, untuk menghitung biaya simpul berdasarkan heuristik yang berbeda.
- ##### Metode
- Metode `hCost(Node node)` digunakan untuk memilih heuristik yang akan digunakan (h1 atau h2).
- Metode `getBestNode(Vector nodes)` mengembalikan simpul dengan biaya terendah dari vektor simpul yang diberikan.
- Metode `getPreviousCost(Node node)` mengembalikan biaya simpul jika simpul tersebut ada dalam daftar `open` atau `closed`
- Metode `printPath(Vector path)` mencetak jalur dari akar ke tujuan.
- Metode `run()` adalah metode utama yang menjalankan algoritma pencarian.
##### Kelas EightPuzzleSpace:
- Kelas ini mendefinisikan keadaan awal dan tujuan dalam masalah 8-puzzle, serta menghasilkan simpul-simpul penerus.
- EightPuzzleSpace Class berperan sebagai wadah yang menangani operasi yang
berhubungan dengan ruang pencarian untuk masalah puzzle 8 angka. Kelas ini 
menyediakan metode untuk mendapatkan simpul awal (getRoot), mengambil tujuan 
(getGoal), dan menghasilkan daftar suksesor dari suatu simpul tertentu 
(getSuccessors). 
- Tugas utama kelas ini adalah mengelola konfigurasi awal dan tujuan 
dari puzzle 8 angka serta menentukan langkah-langkah yang dapat diambil dari suatu keadaan puzzle
- ##### Metode
- Metode `getRoot()` mengembalikan keadaan awal sebagai simpul.
- Metode `getGoal()` mengembalikan keadaan tujuan sebagai simpul.
- Metode `getSuccessors(Node parent)` menghasilkan simpul-simpul penerus berdasarkan perpindahan ubin kosong.
- Metode `transformState()` digunakan untuk membuat simpul baru dengan menukar dua ubin dalam keadaan.
##### Kelas Node:
- Kelas Node merepresentasikan sebuah simpul atau keadaan dalam ruang pencarian, khususnya dalam konteks penyelesaian masalah 8-puzzle.
- Setiap simpul memiliki atribut state, yang merupakan array integer dengan panjang 9, yang menggambarkan keadaan dari puzzle 8 angka.
- Kelas ini juga memiliki metode untuk mengubah simpul menjadi bentuk string, memeriksa kesetaraan, dan mengambil jalur dari simpul ke akar.
- Bidang `state` adalah array yang berisi 9 bilangan bulat yang mewakili keadaan atau posisi ubin dalam papan permainan.
- Bidang `cost` adalah biaya yang terkait dengan mencapai simpul ini.
- Bidang `parent` adalah referensi ke simpul induk dalam pohon pencarian.
- Bidang `successors` adalah vektor yang berisi simpul-simpul anak.

- ##### Metode:
- Konstruktor `Node(int s[], Node parent)` menginisialisasi sebuah simpul dengan keadaan tertentu dan simpul induk.
- Metode `toString()` mengembalikan representasi string dari keadaan simpul.
- Metode `equals(Object node)` membandingkan dua simpul untuk memeriksa apakah mereka memiliki keadaan yang sama.
- Metode `getPath(Vector<Node> v)` mengembalikan jalur dari akar ke simpul saat ini dalam bentuk vektor.
- Metode `getPath()` mengembalikan jalur dalam vektor baru.

Kode dalam class-class tersebut mengimplementasikan algoritma heuristic search untuk mencari solusi dalam masalah 8-puzzle dengan mengeksplorasi kemungkinan keadaan, mengevaluasi biaya berdasarkan heuristik, dan memilih simpul-simpul yang paling menjanjikan untuk dieksplorasi lebih lanjut. Pencarian berlanjut sampai solusi ditemukan atau semua kemungkinan telah dieksplorasi.
- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/1-5.png)

-	Keadaan Awal 
3 1 2
4 7 5
6 8 0
Papan puzzle terdiri dari sembilan ubin diatur dalam bentuk matriks 3x3. Angka 0 mewakili ubin kosong yang dapat digeser ke arah atas, bawah, kiri, atau kanan untuk mencapai keadaan tujuan.
- Langkah 1: Dalam langkah pertama, ubin kosong digeser dari posisi (3,3) ke posisi (2,3) sehingga menghasilkan keadaan baru:
3 1 2
4 7 5
6 0 8
- Langkah 2: Kemudian, ubin kosong digeser dari posisi (2,3) ke posisi (2,2):
3 1 2
4 0 5
6 7 8
- Langkah 3: Ubin kosong digeser dari posisi (2,2) ke posisi (1,2):
3 1 2
0 4 5
6 7 8
- Langkah 4 (Tujuan Tercapai): Pada langkah terakhir, ubin kosong digeser dari posisi (1,2) ke posisi (1,1), sehingga mencapai keadaan tujuan yang diinginkan:
0 1 2
3 4 5
6 7 8
Dengan demikian, masalah 8-puzzle telah terselesaikandari keadaan awal ke keadaan tujuan dalam lima langkah. Setiap langkah perpindahan ubin kosong mengarah pada perubahan keadaan menuju tujuan, dan dengan mencapai keadaan tujuan yang benar.

2.	Mengubah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 8.

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/2-5.png)

- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/3-5.png)

- Keadaan Awal (Initial State):
3 1 2
4 7 5
6 8 0
- Langkah 1: Menggeser ubin kosong dari (3,3) ke (3,2)
3 1 2
4 7 5
6 0 8
- Langkah 2: Menggeser ubin kosong dari (3,2) ke (3,1)
3 1 2
4 0 5
6 7 8
- Langkah 3: Menggeser ubin kosong dari (3,1) ke (2,1)
3 1 2
0 4 5
6 7 8
- Langkah 4: Menggeser ubin kosong dari (2,1) ke (2,2)
0 1 2
3 4 5
6 7 8
- Langkah 5: Menggeser ubin kosong dari (2,2) ke (1,2)
1 0 2
3 4 5
6 7 8
- Langkah 6: Menggeser ubin kosong dari (1,2) ke (1,3)
1 2 0
3 4 5
6 7 8
- Langkah 7: Menggeser ubin kosong dari (1,3) ke (2,3)
1 2 5
3 4 0
6 7 8
- Langkah 8: Menggeser ubin kosong dari (2,3) ke (2,2)
1 2 5
3 0 4
6 7 8
- Langkah 9: Menggeser ubin kosong dari (2,2) ke (2,1)
1 2 5
0 3 4
6 7 8
- Langkah 10: Menggeser ubin kosong dari (2,1) ke (1,1)
0 2 5 
1 3 4
6 7 8
- Langkah 11: Menggeser ubin kosong dari (1,1) ke (1,2)
2 0 5 
1 3 4 
6 7 8 
- Langkah 12: Menggeser ubin kosong dari (1,2) ke (1,3)
2 3 5 
1 0 4 
6 7 8 
- Langkah 13: Menggeser ubin kosong dari (1,3) ke (2,3)
2 3 5 
1 4 0 
6 7 8
- Langkah 14: Menggeser ubin kosong dari (2,3) ke (2,2)
2 3 0 
1 4 5 
6 7 8
- Langkah 15: Menggeser ubin kosong dari (2,2) ke (2,1)
2 0 3 
1 4 5 
6 7 8
- Langkah 16: Menggeser ubin kosong dari (2,1) ke (1,1)
0 2 3 
1 4 5 
6 7 8
- Langkah 17: Menggeser ubin kosong dari (1,1) ke (1,2)
1 2 3 
0 4 5 
6 7 8 
- Langkah 18 (Tujuan Tercapai): Menggeser ubin kosong dari (1,2) ke (1,3), sehingga mencapai keadaan tujuan yang diinginkan:
1 2 3
4 0 5
6 7 8
##### Analisa perbandingan dengan solusi poin 1
##### Jumlah Langkah:
-	Solusi pada poin 1: Dalam solusi pertama, dibutuhkan 5 langkah untuk mencapai keadaan tujuan.
-	Solusi pada poin 2: Dalam solusi kedua, dibutuhkan 18 langkah untuk mencapai keadaan tujuan.
##### Kompleksitas:
-	Solusi pada poin 1: Solusi pertama adalah solusi yang lebih sederhana dan efisien, karena memerlukan lebih sedikit langkah.
-	Solusi pada poin 2: Solusi kedua lebih kompleks dan memerlukan lebih banyak langkah untuk mencapai tujuan. Ini karena keadaan awal yang berbeda mengharuskan pencarian jalur yang lebih panjang.

Dengan demikian, kedua solusi berhasil mencapai keadaan tujuan, mereka memiliki perbedaan dalam kompleksitas dan jumlah langkah yang diperlukan. Solusi pertama adalah solusi yang lebih sederhana dan lebih efisien, sementara solusi kedua memerlukan lebih banyak langkah karena keadaan awal yang berbeda. Kedua solusi ini memperlihatkan bagaimana perbedaan dalam keadaan awal dapat memengaruhi jalur pencarian dalam masalah 8-puzzle.

3.	Mengubah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 5.9

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/4-5.png)
- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/5-5.png)

- Keadaan Awal (Initial State)
1 5 3
4 6 8
2 7 0
Penggeseran setiap langkah dalam solusi ini adalah sebagai berikut:
- Awalnya, ubin kosong (0) berada di posisi (3, 1), dan langkah pertama adalah menggesernya ke kanan, sehingga ubin 0 berada di posisi (3, 2).
- Selanjutnya, ubin 0 digeser ke kanan lagi ke posisi (3, 3).
- Langkah ketiga menggeser ubin 0 ke atas ke posisi (2, 3).
- Langkah berikutnya menggeser ubin 0 ke kiri ke posisi (2, 2).
- Ubin 0 digeser ke atas lagi ke posisi (1, 2).
- Langkah selanjutnya menggeser ubin 0 ke kiri ke posisi (1, 1).
- Ubin 0 digeser ke atas lagi ke posisi (2, 1).
- Langkah berikutnya menggeser ubin 0 ke kanan ke posisi (2, 2).
- Ubin 0 digeser ke bawah ke posisi (2, 3).
- Langkah selanjutnya menggeser ubin 0 ke kanan ke posisi (2, 2).
- Ubin 0 digeser ke atas ke posisi (1, 2).
- Langkah berikutnya menggeser ubin 0 ke kiri ke posisi (1, 1).
- Ubin 0 digeser ke atas lagi ke posisi (2, 1).
- Langkah selanjutnya menggeser ubin 0 ke kanan ke posisi (2, 2).
- Ubin 0 digeser ke atas ke posisi (1, 2).
- Langkah berikutnya menggeser ubin 0 ke kiri ke posisi (1, 1).
- Ubin 0 digeser ke atas lagi ke posisi (1, 2).
- Terakhir, ubin 0 digeser ke kanan ke posisi (1, 3), sehingga mencapai tujuan akhir.

##### Analisa Perbandingan dengan Solusi 1 dan 2
Solusi 1:
-	Solusi pertama adalah solusi yang paling sederhana dan hanya memerlukan 18 langkah untuk mencapai tujuan.
-	Proses penyelesaian berlangsung sangat cepat, dengan total waktu eksekusi sekitar 1 detik.
Solusi 2:
-	Solusi kedua juga memerlukan 18 langkah untuk mencapai tujuan dan memiliki prinsip urutan langkah yang sama dengan solusi pertama.
-	Waktu eksekusi yang singkat, dengan total waktu sekitar 1 detik.
Solusi 3:
-	Solusi ketiga adalah yang paling kompleks dengan 38 langkah untuk mencapai tujuan.
-	Waktu eksekusi yang jauh lebih lama dibandingkan dengan solusi sebelumnya, dengan total waktu sekitar 52 menit.
##### Analisa:
Solusi pertama dan solusi kedua adalah solusi yang efisien dan relatif sederhana. Kedua solusi memiliki jumlah langkah yang sama dan dapat mencapai tujuan dengan cepat. Solusi ketiga, meskipun mencapai tujuan, memerlukan lebih banyak langkah dan waktu yang signifikan untuk diselesaikan. Keadaan awal dan tujuan yang berbeda mungkin mempengaruhi kompleksitas puzzle.

4.	Mengubah initial dan goal state dari program di atas sehingga bentuk initial dan goal statenya Gambar 5.10. Kemudian tentukan langkah-langkah mana saja sehingga puzzlenya mencapai goal state.

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/6-5.png)
- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/7-5.png)

Penggeseran setiap langkah dalam solusi ini adalah sebagai berikut:
- Awalnya, ubin kosong (0) berada di posisi (3, 3), yang terletak di sudut kanan bawah papan permainan.
- Langkah pertama menggeser ubin 0 ke kiri, sehingga berada di posisi (3, 2).
- Selanjutnya, ubin 0 digeser ke kiri lagi ke posisi (3, 1).
- Langkah keempat menggeser ubin 0 ke atas, sehingga berada di posisi (2, 1).
- Ubin 0 digeser ke kanan ke posisi (2, 2).
- Langkah berikutnya menggeser ubin 0 ke atas lagi, sehingga berada di posisi (1, 2).
- Ubin 0 digeser ke kiri ke posisi (1, 1).
- Langkah ke-8 menggeser ubin 0 ke atas lagi ke posisi (2, 1).
- Ubin 0 digeser ke kanan ke posisi (2, 2).
- Langkah selanjutnya menggeser ubin 0 ke atas lagi ke posisi (1, 2).
- Ubin 0 digeser ke kiri ke posisi (1, 1).
- Langkah ke-12 menggeser ubin 0 ke atas lagi ke posisi (2, 1).
- Ubin 0 digeser ke kanan ke posisi (2, 2).
- Langkah berikutnya menggeser ubin 0 ke atas lagi ke posisi (1, 2).
- Ubin 0 digeser ke kanan ke posisi (1, 3).\
- Terakhir, ubin 0 digeser ke kanan lagi ke posisi (2, 3) sehingga mencapai tujuan akhir yang merupakan urutan yang sesuai.

##### Analisa Perbandingan dengan Solusi 1, 2, dan 3
Dalam semua solusi yang diberikan, tujuannya adalah mencapai keadaan tujuan (goal state) dari keadaan awal (root state) dalam beberapa langkah. Mari kita bandingkan keempat solusi tersebut:
Solusi 1:
•	Root: 3 1 2 4 7 5 6 8 0 = keadaan awal
•	Keadaan tujuan : 0 1 2 3 4 5 6 7 8
•	Total waktu: 0 detik
•	Total langkah: 4

Solusi 2:
•	Root: 3 1 2 4 7 5 6 8 0 = keadaan awal
•	Keadaan tujuan : 1 2 3 4 0 5 6 7 8
•	Total waktu: 1 detik
•	Total langkah: 18

Solusi 3:
•	Root: 1 5 3 4 6 8 2 7 0 = keadaan awal
•	Keadaan tujuan : 7 6 5 8 0 4 1 2 3
•	Total waktu: 52 menit 23 detik
•	Total langkah: 20

Solusi 4:
•	Root: 1 2 3 4 5 6 7 8 0
•	Keadaan tujuan : 1 2 3 4 0 5 6 7 8
•	Total waktu: 0 detik
•	Total langkah: 16

##### Analisa :
-	Solusi 1 dan 4 mencapai tujuan dengan jumlah langkah yang lebih sedikit dan dalam waktu yang sangat singkat (kurang dari 1 detik).
-	Solusi 2 dan 3 memerlukan lebih banyak langkah dan waktu yang signifikan untuk mencapai tujuan.
-	Solusi 2 adalah yang terpanjang dalam hal jumlah langkah.
-	Solusi 3 memerlukan waktu yang sangat lama (52 menit) untuk menyelesaikan masalah, bahkan jika jumlah langkahnya mirip dengan Solusi 2.
- Dari analisis ini, dapat disimpulkan bahwa Solusi 1 dan Solusi 4 adalah yang paling efisien, sementara Solusi 3 adalah yang paling lambat dan memerlukan waktu yang sangat lama. Solusi 2 berada di tengah-tengah dalam hal jumlah langkah, tetapi masih memerlukan waktu yang signifikan dibandingkan dengan Solusi 1 dan Solusi 4.

5.	 Mengubah initial dan goal state dari program dan class-class di atas sehingga bentuk initial dan goal statenya Gambar 5.11.
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/8-5.png)
Mengubah Initial State dan Goal State pada kode program
int ex[] = {D, B, E, A, F, G, H, C, 0}; // initial state 
int state[] = {A, H, G, B, 0, F, C, D, E}; // goal state








