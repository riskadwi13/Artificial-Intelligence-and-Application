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
   ##### Kode Program
   package TicTacToe;
import java.awt.Graphics;
import java.awt.*;
import java.awt.Graphics2D;
public final class Cell {
//content of this cell (Seed.EMPTY, Seed.CROSS, or Seed.NOUGHT)
 Seed content; 
 int row, col; // row and column of this cell
/**Constructor to initialize this cell with the specified row and col
     * @param row
     * @param col */
 public Cell(int row, int col) {
 this.row = row;
 this.col = col;
 clear(); // clear content
 }
 /** Clear this cell's content to EMPTY */
 public void clear() {
 content = Seed.EMPTY;
 }
 /**Paint itself on the graphics canvas, given the Graphics context
     * @param g */
 public void paint(Graphics g) {
 // Use Graphics2D which allows us to set the pen's stroke
 Graphics2D g2d = (Graphics2D)g;
 g2d.setStroke(new BasicStroke(GameMain.SYMBOL_STROKE_WIDTH, BasicStroke.CAP_ROUND, BasicStroke.JOIN_ROUND)); // Graphics2D only
 // Draw the Seed if it is not empty
 int x1 = col * GameMain.CELL_SIZE + GameMain.CELL_PADDING;
 int y1 = row * GameMain.CELL_SIZE + GameMain.CELL_PADDING;
 if (content == Seed.CROSS) {
 g2d.setColor(Color.RED);
 int x2 = (col + 1) * GameMain.CELL_SIZE - GameMain.CELL_PADDING;
 int y2 = (row + 1) * GameMain.CELL_SIZE - GameMain.CELL_PADDING;
 g2d.drawLine(x1, y1, x2, y2);
 g2d.drawLine(x2, y1, x1, y2);
 } else if (content == Seed.NOUGHT) {
 g2d.setColor(Color.BLUE);
 g2d.drawOval(x1, y1, GameMain.SYMBOL_SIZE, GameMain.SYMBOL_SIZE);
 }
 }
}

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
   ##### Kode Program
   package TicTacToe;
import java.awt.*;
/**
* The Board class models the ROWS-by-COLS game-board.
*/
public class Board {
 // package access
 // composes of 2D array of ROWS-by-COLS Cell instances
 Cell[][] cells; 
 /** Constructor to initialize the game board */
 public Board() {
// allocate the array
 cells = new Cell[GameMain.ROWS][GameMain.COLS]; 
 for (int row = 0; row < GameMain.ROWS; ++row) {
 for (int col = 0; col < GameMain.COLS; ++col) {
 // allocate element of array
 cells[row][col] = new Cell(row, col); 
 }
 }
 }
 /** Initialize (or re-initialize) the game board */
 public void init() {
 for (int row = 0; row < GameMain.ROWS; ++row) {
 for (int col = 0; col < GameMain.COLS; ++col) {
 // clear the cell content
 cells[row][col].clear(); 
 }
 }
 }
 /** Return true if it is a draw (i.e., no more EMPTY cell)
     * @return  */
 public boolean isDraw() {
 for (int row = 0; row < GameMain.ROWS; ++row) {
 for (int col = 0; col < GameMain.COLS; ++col) {
 if (cells[row][col].content == Seed.EMPTY) {
// an empty seed found, not a draw, exit
 return false; 
 }
 }
 }
 return true; // no empty cell, it's a draw
 }
 /** Return true if the player with "seed" has won after placing at
 (seedRow, seedCol)
     * @param seed
     * @param seedRow
     * @param seedCol
     * @return  */
 public boolean hasWon(Seed seed, int seedRow, int seedCol) {
 return (cells[seedRow][0].content == seed // 3-in-the-row
 && cells[seedRow][1].content == seed
 && cells[seedRow][2].content == seed
 || cells[0][seedCol].content == seed // 3-in-the-column
 && cells[1][seedCol].content == seed
&& cells[2][seedCol].content == seed
 || seedRow == seedCol // 3-in-the-diagonal
 && cells[0][0].content == seed
 && cells[1][1].content == seed
 && cells[2][2].content == seed
 || seedRow + seedCol == 2 // 3-in-the-opposite-diagonal
 && cells[0][2].content == seed
 && cells[1][1].content == seed
 && cells[2][0].content == seed);
 }
 /** Paint itself on the graphics canvas, given the Graphics context
     * @param g */
 public void paint(Graphics g) {
 // Draw the grid-lines
 g.setColor(Color.GRAY);
 for (int row = 1; row < GameMain.ROWS; ++row) {
 g.fillRoundRect(0, GameMain.CELL_SIZE * row -
GameMain.GRID_WIDHT_HALF,
 GameMain.CANVAS_WIDTH-1, GameMain.GRID_WIDTH,
 GameMain.GRID_WIDTH, GameMain.GRID_WIDTH);
 }
 for (int col = 1; col < GameMain.COLS; ++col) {
 g.fillRoundRect(GameMain.CELL_SIZE * col -
GameMain.GRID_WIDHT_HALF, 0,
 GameMain.GRID_WIDTH, GameMain.CANVAS_HEIGHT - 1,
 GameMain.GRID_WIDTH, GameMain.GRID_WIDTH);
 }
 // Draw all the cells
 for (int row = 0; row < GameMain.ROWS; ++row) {
 for (int col = 0; col < GameMain.COLS; ++col) {
 cells[row][col].paint(g); // ask the cell to paint itself
 }
 }
 }
}

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
   ##### Kode Program
   package TicTacToe;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*; 
/**
 * Tic-Tac-Toe: Two-player Graphic version with better OO design.
 * The Board and Cell classes are separated in their own classes.
 */ 
@SuppressWarnings("serial")
public class GameMain extends JPanel { 
   // Named-constants for the game board 
   public static final int ROWS = 3;  // ROWS by COLS cells
   public static final int COLS = 3; 
public static final String TITLE = "Tic Tac Toe";
  
   // Name-constants for the various dimensions used for graphics drawing 
   public static final int CELL_SIZE = 100; // cell width and height (square)
   public static final int CANVAS_WIDTH = CELL_SIZE * COLS;  // the drawing canvas
   public static final int CANVAS_HEIGHT = CELL_SIZE * ROWS; 
   public static final int GRID_WIDTH = 8;  // Grid-line's width 
   public static final int GRID_WIDHT_HALF = GRID_WIDTH / 2; // Grid-line's half-width 
   // Symbols (cross/nought) are displayed inside a cell, with padding from border 
   
   public static final int CELL_PADDING = CELL_SIZE / 6;
   public static final int SYMBOL_SIZE = CELL_SIZE - CELL_PADDING * 2;
   public static final int SYMBOL_STROKE_WIDTH = 8; // pen's stroke width
 
   private Board board;            // the game board
   private GameState currentState;//the current state of the game
   private Seed currentPlayer;     // the current player
   private final JLabel statusBar;     // for displaying status message
  
   /** Constructor to setup the UI and game components */ 
   public GameMain() {
  
      // This JPanel fires MouseEvent 
      this.addMouseListener(new MouseAdapter() {
         @Override
         public void mouseClicked(MouseEvent e) {  // mouse-clicked handler
            int mouseX = e.getX();
            int mouseY = e.getY(); 
            // Get the row and column clicked 
            int rowSelected = mouseY / CELL_SIZE;
            int colSelected = mouseX / CELL_SIZE;
 
            if (currentState == GameState.PLAYING) {
               if (rowSelected >= 0 && rowSelected < ROWS
                     && colSelected >= 0 && colSelected < COLS
                     && board.cells[rowSelected][colSelected].content ==
Seed.EMPTY) {
                  board.cells[rowSelected][colSelected].content =
currentPlayer; // move
                  updateGame(currentPlayer, rowSelected, colSelected); // update currentState
                  // Switch player 
                  currentPlayer = (currentPlayer == Seed.CROSS) ?
Seed.NOUGHT : Seed.CROSS;
               }
            } else {        // game over
               initGame();  // restart the game
            } 
            // Refresh the drawing canvas 
            repaint();  // Call-back paintComponent().
         }
      });
  
      // Setup the status bar (JLabel) to display status message 
      statusBar = new JLabel("         ");
      statusBar.setFont(new Font(Font.DIALOG_INPUT, Font.BOLD, 14));
      statusBar.setBorder(BorderFactory.createEmptyBorder(2, 5, 4, 5));
      statusBar.setOpaque(true);
      statusBar.setBackground(Color.LIGHT_GRAY);
 
      setLayout(new BorderLayout()); 
      add(statusBar, BorderLayout.PAGE_END); // same as SOUTH
      setPreferredSize(new Dimension(CANVAS_WIDTH, CANVAS_HEIGHT + 30)); 
            // account for statusBar in height 
 
      board = new Board();   // allocate the game-board
      initGame();  // Initialize the game variables
   }
  
   /** Initialize the game-board contents and the current-state */ 
   public void initGame() {
      for (int row = 0; row < ROWS; ++row) {
         for (int col = 0; col < COLS; ++col) {
            board.cells[row][col].content = Seed.EMPTY; // all cells empty
         }
      }
      currentState = GameState.PLAYING;  // ready to play
      currentPlayer = Seed.CROSS;        // cross plays first
   }
  
   /** Update the currentState after the player with "theSeed" has placed on (row, col) */ 
   public void updateGame(Seed theSeed, int row, int col) {
      if (board.hasWon(theSeed, row, col)) {  // check for win
         currentState = (theSeed == Seed.CROSS) ? GameState.CROSS_WON :
GameState.NOUGHT_WON;
      } else if (board.isDraw()) {  // check for draw
         currentState = GameState.DRAW;
      } 
      // Otherwise, no change to current state (PLAYING). 
   }
  
   /** Custom painting codes on this JPanel */ 
   @Override
   public void paintComponent(Graphics g){ 
      //invoke via repaint()
      super.paintComponent(g);    // fill background 
      setBackground(Color.WHITE); // set its background color
 
      board.paint(g);  // ask the game board to paint itself 
 
      // Print status-bar message 
      if (currentState == GameState.PLAYING) {
         statusBar.setForeground(Color.BLACK);
         if (currentPlayer == Seed.CROSS) {
            statusBar.setText("X's Turn");
         } else {
            statusBar.setText("O's Turn");
         }
      } else if (currentState == GameState.DRAW) {
         statusBar.setForeground(Color.RED);
         statusBar.setText("It's a Draw! Click to play again.");
      } else if (currentState == GameState.CROSS_WON) {
         statusBar.setForeground(Color.RED);
         statusBar.setText("'X' Won! Click to play again.");
      } else if (currentState == GameState.NOUGHT_WON) {
         statusBar.setForeground(Color.RED);
         statusBar.setText("'O' Won! Click to play again.");
      }
   }
  
   /** The entry "main" method
     * @param args */ 
   public static void main(String[] args) {
      // Run GUI construction codes in Event-Dispatching thread for thread safety 
      javax.swing.SwingUtilities.invokeLater(() -> {
          JFrame frame = new JFrame(TITLE);
          // Set the content-pane of the JFrame to an instance of main JPanel
          frame.setContentPane(new GameMain());
          frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          frame.pack();
          // center the application window
          frame.setLocationRelativeTo(null);
          frame.setVisible(true);   // show it
      });
   }
}

     
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

Percobaan KALAH untuk Kedua Pemain

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
