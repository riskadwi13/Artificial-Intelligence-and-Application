#### Nama		: Riska Dwi Astia Ningrum
#### NIM		: 5311421007
#### Rombel 	: 1 (Senin 09.00)

# PRAKTIKUM 4
# TEKNIK PENCARIAN BLIND SEARCH

#### Tugas
1.	Tentukan bagaimana algoritma BFS di atas dapat menentukan node ke 8, 6, dan 7. 2. 
2.	Ubahlah method static void main sehingga bentuk tree seperti Gambar 4.5 dapat dibentuk. Kemudian tentukan bagaimana algoritma BFS dapat menemukan node 5. 
3.	Ubahlah method static void main sehingga bentuk tree seperti Gambar 4.6 dapat dibentuk. Kemudian tentukan bagaimana algoritma BFS dapat menemukan node 9. 
4.	Ubahlah kode program di atas sehingga bentuk tree seperti Gambar 4.7 dapat dibentuk. Kemudian tentukan bagaimana algoritma BFS dapat menemukan node C.

#### Penyelesaian
1.	Algoritma BFS (Breadth-First Search) merupakan salah satu algoritma pencarian dalam ilmu komputer yang berfungsi untuk menjelajahi atau mencari informasi dalam graf atau struktur data berdasarkan tingkat jarak atau kedalaman dari node awal. Algoritma Breadth-First Search (BFS) digunakan untuk menjelajahi atau mencari jalur terpendek dari satu simpul (node) ke simpul lain dalam graf. Dalam algoritma ini, node-node yang terhubung langsung dengan node awal akan dijelajahi terlebih dahulu sebelum node-node yang lebih dalam atau lebih jauh dieksplorasi.
Proses pencarian dari algoritma BFS adalah sebagai berikut:
a.	Melakukan inisialisasi node awal, yaitu node 3, dan kemudian dimasukkan ke dalam antrian. 
b.	Selanjutnya, node 3 akan mengeksplorasi node-node yang terhubung langsung dengan itu, yaitu node 2 dan node 4, karena keduanya memiliki jarak 1 dari node 3. Node 4 akan melanjutkan dengan mengeksplorasi node 1, node 6, dan node 5 yang terhubung dengannya. 
c.	Selanjutnya, node 5 akan mengeksplorasi node 8 dan node 7. 
d.	Proses ini akan terus berlanjut sampai semua node yang terhubung dengan node awal telah diperiksa. 
Oleh karena itu, node-node 8, 6, dan 7 akan ditemukan dan diproses dengan mengikuti aturan BFS.

- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/1-4.jpeg)

Berdasarkan hasil di atas, BFS dimulai dari simpul (node) ke-3 (n3). Mari kita lihat langkah-langkahnya untuk mencapai node ke-8, 6, dan 7:
- 	Node 3 (d=0): BFS dimulai dari simpul n3 dengan jarak 0.
-	Node 4 (d=1): n3 memiliki tetangga n4, sehingga BFS melanjutkan ke n4 dengan jarak 1.
-	Node 2 (d=1): n4 memiliki tetangga n2, tetapi n2 sudah diwarnai GRAY (dalam proses BFS), jadi BFS tidak melanjutkan ke n2.
-	Node 5 (d=2): n4 juga memiliki tetangga n5, yang belum diwarnai, jadi BFS melanjutkan ke n5 dengan jarak 2.
-	Node 6 (d=2):n5 memiliki tetangga n6, yang belum diwarnai, jadi BFS melanjutkan ke n6 dengan jarak 2.
-	Node 1 (d=2): n5 juga memiliki tetangga n1, yang belum diwarnai, jadi BFS melanjutkan ke n1 dengan jarak 2.
-	Node 7 (d=3): n6 memiliki tetangga n7, yang belum diwarnai, jadi BFS melanjutkan ke n7 dengan jarak 3.
-	Node 8 (d=3): n6 juga memiliki tetangga n8, yang belum diwarnai, jadi BFS melanjutkan ke n8 dengan jarak 3.



2.	Membuat tree seperti pada gambar 4.5 dengan mengubah method static void main, seperti berikut ini.
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/2-4.jpeg)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/3-4.jpeg)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/4-4..jpg)
- ##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/5-4.jpg)
- Hasil tersebut mengkonfirmasi kesesuaian hasil tree yang dihasilkan oleh program dengan gambar 4.5. 
a.	Dalam mencari node 5, pertama-tama algoritma BFS memulai dengan langkah memasukkan node 1 ke dalam antrian. 
b.	Kemudian, node 1 akan mengeksplorasi node 2 dan node 3, yang secara langsung terhubung dengan node 1 atau memiliki kedalaman tingkat 1. 
c.	Setelah itu, node 3 akan melanjutkan dengan mengeksplorasi node yang memiliki jarak atau kedalaman 2, yang dimulai dengan mengecek node 4, node 5, node 6, dan node 7. 
d.	Setelah node 5 ditemukan, proses akan terus berlanjut hingga semua node yang terhubung dengan node awal telah diperiksa. 
Oleh karena itu, node 5 akan ditemukan dan diproses sesuai dengan ketentuan algoritma BFS.



3. Membuat tree seperti pada gambar 4.6 dengan mengubah method static void main, seperti berikut ini.
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/6-4.jpg)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/7-4.jpg)
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/8-4.jpg)
- ###### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/9-4.jpg)
- Hasil tersebut sudah menunjukkan bahwa hasil tree yg diperoleh dari program sudah sesuai dengan gambar 4.6. 
a.	Dalam menemukan node 9 algoritma BFS memulainya dengan memasukkan node 1 ke dalam antrian. 
b.	Selanjutnya, node 1 akan memeriksa node 2, node 3, dan node 4 yang terhubung langsung dengan node 1 atau node yang memiliki tingkat kedalaman 1. 
c.	Kemudian, node 4 akan memeriksa node yang memiliki tingkat kedalaman 2 dimulai dari memeriksa node 5, node 6, node 7, dan node 8. 
d.	Dilanjutkan node 8 yang akan memeriksa node 9, dimana setelah menemukan node 9 maka proses akan terus berlanjut untuk memeriksa node 10, node 11, dan node 12 sampai semua node yang terhubung dengan node awal telah diperiksa. 
Dengan demikian, pada akhir proses BFS, node 9 akan ditemukan dan diproses sesuai dengan aturan algoritma BFS.


4.	Membuat tree seperti pada gambar 4.7 yang akan dilakukan beberapa perubahan pada kode program.
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/10-4.jpg)

a.	Pada kelas Node, untuk dapat menerima huruf maka harus mengganti tipe data variabel ’data’ dari yang awalnya ’int’ menjadi ’String’.

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/11-4.jpg)

b.	Kemudian pada Metode main, memasukkan nilai node dengan tipe data string sebagai berikut.
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/12-4.jpg)

c.	Selanjutnya pada Metode addEdge dan bfs, memasukkan logika pemrosesan data untuk tipe data String sebagai berikut.

![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/13-4.jpg)

d.	Kemudian Run untuk mendapatkan hasil.
##### Hasil Program
![alt text](https://github.com/riskadwi13/Artificial-Intelligence-and-Application/blob/main/14-4.jpg)
Hasil tersebut sudah menunjukkan bahwa hasil tree yg diperoleh dari program sudah sesuai dengan gambar 4.7. 
-	Dalam menemukan node 3 (C) algoritma BFS memulainya dengan memasukkan node 6 (F) ke dalam antrian. 
-	Kemudian, dilanjutkan node 6 yang akan memeriksa node 2 (B), dan node 7 (G) yang terhubung langsung dengan node 6 atau node yang memiliki tingkat kedalaman 1. 
