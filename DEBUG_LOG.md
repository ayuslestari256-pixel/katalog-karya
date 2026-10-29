# Debug Log - Katalog Karya P10

## 1. Bug G1: Path Logo Tidak Tampil (404 Not Found)
* **Langkah Reproduksi:** Membuka halaman `index.html` di browser, lalu melihat bagian navbar atas di mana logo gambar tidak muncul.
* **Hipotesis:** Path file SVG logo pada atribut `src` salah atau tidak sesuai dengan lokasi foldernya.
* **Bukti DevTools:** Tab *Network* menunjukkan status `404 (Not Found)` pada berkas logo.
* **Perbaikan (`index.html` / `logo.svg`):** Memperbaiki nilai path pada atribut `src` agar mengarah tepat ke file logo.
* **Uji Ulang:** Logo berhasil dimuat dengan sempurna tanpa error 404.

## 2. Bug G2: Layout Kartu Tidak Responsif
* **Langkah Reproduksi:** Mengubah ukuran layar (resize window) atau membuka tampilan mobile, kartu galeri menumpuk tidak beraturan.
* **Hipotesis:** Kelas grid Bootstrap pada elemen kontainer galeri atau kartu kurang lengkap.
* **Bukti DevTools:** Elemen kartu tidak menerapkan kelas *flexbox/grid* responsif secara benar.
* **Perbaikan (`main.js`):** Menambahkan kelas Bootstrap seperti `col-12 col-sm-6 col-lg-4` pada fungsi pembuatan kartu (`kartu()`).
* **Uji Ulang:** Kartu galeri otomatis menyesuaikan ukuran layar secara responsif.

## 3. Bug G3 & G4: Penghitung Jumlah Karya Tidak Sesuai
* **Langkah Reproduksi:** Memuat halaman atau melakukan filter, teks jumlah karya menampilkan angka kosong atau salah.
* **Hipotesis:** Logika perhitungan teks `jumlah.textContent` tidak mengambil panjang array hasil saringan dengan benar.
* **Bukti DevTools:** Elemen `<p id="jumlah">` tidak terpaut dengan variabel panjang data `hasil.length`.
* **Perbaikan (`main.js`):** Memperbarui fungsi `tampil()` agar memperbarui teks penghitung menggunakan `hasil.length` dan `KARYA.length`.
* **Uji Ulang:** Teks menampilkan informasi akurat (contoh: "Menampilkan 6 dari 6 karya").

## 4. Bug G5: Tombol Detail Tidak Berfungsi
* **Langkah Reproduksi:** Mengklik tombol "Detail" pada salah satu kartu karya, tetapi kotak informasi di bawah tidak muncul.
* **Hipotesis:** *Event listener* untuk tombol detail belum dipasang atau terlewat saat galeri dirender ulang.
* **Bukti DevTools:** Tidak ada *event* klik yang terekam saat tombol detail ditekan.
* **Perbaikan (`main.js`):** Memastikan fungsi `pasangDetail()` dipanggil setiap kali fungsi `tampil()` selesai merender galeri.
* **Uji Ulang:** Kotak detail langsung muncul dengan teks informasi karya yang sesuai saat tombol diklik.

## 5. Bug G6: Pencarian dan Filter Kategori Gagal / Case-Sensitive
* **Langkah Reproduksi:** Mengetik judul dengan huruf kapital atau memilih kategori tertentu, tetapi galeri menjadi kosong (`0 hasil`).
* **Hipotesis:** Terjadi perbedaan format teks (*case-sensitive*) antara input pencarian/nilai opsi filter dengan data asli di `data.js`.
* **Bukti DevTools:** Hasil filter mengembalikan *array* kosong karena perbandingan string tidak sama persis.
* **Perbaikan (`index.html` & `main.js`):** Menyamakan nilai `value` pada opsi HTML menjadi huruf kecil dan menambahkan `.toLowerCase()` pada fungsi `saring()`.
* **Uji Ulang:** Pencarian judul dan filter kategori berhasil berfungsi secara *case-insensitive* dengan akurat.