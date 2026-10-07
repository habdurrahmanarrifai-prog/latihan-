JAWABAN TUGAS GIT, MERGE CONFLICT, DAN JAVASCRIPT
1. Mengapa Merge Conflict bisa terjadi?
Merge Conflict terjadi ketika Git tidak dapat menentukan perubahan mana yang harus dipertahankan saat menggabungkan dua branch.

Situasi yang dapat memicu Merge Conflict:
1. Dua orang mengubah baris yang sama pada file yang sama.
2. Satu orang mengubah atau menghapus bagian file, sementara orang lain juga mengubah bagian tersebut.

Contoh skenario nyata:
Andi dan Budi bekerja pada index.html. Andi mengubah judul menjadi warna merah, sedangkan Budi mengubah judul yang sama menjadi warna biru. Ketika branch Budi digabungkan ke branch Andi, Git tidak tahu perubahan mana yang benar sehingga terjadi Merge Conflict.
2. Penanda Merge Conflict
Kode:
<<<<<<< HEAD
<h1 style="color: red;">Selamat Datang</h1>
=======
<h1 style="color: blue;">Selamat Datang</h1>
>>>>>>> branch-teman

a. Arti masing-masing penanda:
- <<<<<<< HEAD: menandai awal perubahan dari branch yang sedang aktif.
- =======: menjadi pemisah antara dua versi kode yang mengalami konflik.
- >>>>>>> branch-teman: menandai akhir perubahan dari branch yang akan digabungkan.

b. Versi dari branch aktif:
<h1 style="color: red;">Selamat Datang</h1>

c. Versi dari branch yang datang:
<h1 style="color: blue;">Selamat Datang</h1>
3. Dua cara menyelesaikan Merge Conflict
A. Melalui Visual Studio Code
1. Buka proyek di Visual Studio Code.
2. Buka file yang mengalami konflik.
3. Pilih salah satu pilihan: Accept Current Change, Accept Incoming Change, atau Accept Both Changes.
4. Pastikan tanda konflik sudah hilang.
5. Simpan file.
6. Jalankan git add.
7. Lakukan commit untuk menyelesaikan merge.

B. Melalui editor teks manual
1. Buka file yang mengalami konflik.
2. Cari tanda <<<<<<< HEAD, =======, dan >>>>>>> branch-teman.
3. Tentukan kode yang ingin dipertahankan.
4. Hapus kode yang tidak diperlukan.
5. Hapus semua tanda konflik.
6. Simpan file.
7. Jalankan git add.
8. Lakukan commit.

VS Code direkomendasikan untuk pemula karena bagian yang konflik ditampilkan dengan jelas dan tersedia tombol untuk memilih perubahan.
4. Perintah setelah konflik diselesaikan
Urutan perintah:
git status
git add .
git commit -m "resolve merge conflict"

Fungsi:
1. git status: memeriksa file yang masih mengalami konflik dan status repository.
2. git add .: menandai file yang sudah diperbaiki sebagai konflik yang telah diselesaikan.
3. git commit -m "resolve merge conflict": mencatat hasil penyelesaian konflik ke riwayat Git.

Jika hasil merge perlu dikirim ke GitHub, dapat dilanjutkan dengan:
git push
5. Fungsi git merge --abort
git merge --abort digunakan untuk membatalkan proses merge yang sedang berlangsung dan mengembalikan repository ke kondisi sebelum merge dimulai.

Contoh situasi:
Kita sedang melakukan merge branch teman, tetapi terdapat banyak konflik pada file penting dan perubahan tersebut belum siap digunakan. Daripada menyelesaikan banyak konflik satu per satu, kita dapat membatalkan proses merge dengan:
git merge --abort
6. Praktik terbaik untuk mengurangi Merge Conflict
1. Sering melakukan git pull
Mengambil perubahan terbaru sebelum bekerja dapat mengurangi kemungkinan mengedit kode yang sudah berubah oleh anggota tim.

2. Melakukan commit secara rutin
Perubahan kecil lebih mudah dilacak dan digabungkan daripada perubahan besar dalam satu commit.

3. Menggunakan branch untuk setiap fitur
Setiap anggota dapat mengerjakan fitur masing-masing tanpa langsung mengubah branch utama.

4. Berkomunikasi dengan anggota tim
Jika dua orang akan mengubah file atau bagian kode yang sama, sebaiknya dibicarakan terlebih dahulu agar pekerjaan tidak bertabrakan.

5. Membuat pull request sebelum merge
Pull request memungkinkan anggota lain memeriksa kode sebelum masuk ke branch utama.
7. Pentingnya pesan commit yang jelas
Pesan commit yang jelas penting karena membantu anggota tim memahami perubahan yang dilakukan tanpa harus membuka seluruh kode. Pesan tersebut juga membuat riwayat proyek lebih mudah dibaca dan dilacak.

Contoh pesan commit buruk:
- update
- fix
- perubahan

Contoh pesan commit baik:
- feat: menambahkan fitur pencarian produk
- fix: memperbaiki tombol login yang tidak berfungsi
- style: memperbaiki tampilan navbar pada perangkat mobile
8. Format Conventional Commits
Format dasar:
type: deskripsi perubahan

Beberapa tipe yang umum:
1. feat: menambahkan fitur baru.
Contoh: feat: menambahkan fitur pencarian produk

2. fix: memperbaiki bug.
Contoh: fix: memperbaiki tombol login

3. docs: perubahan dokumentasi.
Contoh: docs: memperbarui README

4. style: perubahan tampilan atau format kode.
Contoh: style: memperbaiki tampilan navbar

5. refactor: mengubah struktur kode tanpa mengubah fungsi.
Contoh: refactor: merapikan struktur fungsi login

6. test: menambah atau memperbaiki pengujian.
Contoh: test: menambahkan test untuk login
9. Pesan commit yang paling baik
Dari tiga pesan berikut:
- git commit -m "update"
- git commit -m "fix bug tombol"
- git commit -m "feat: menambahkan fitur pencarian produk di navbar"

Yang paling baik adalah:
git commit -m "feat: menambahkan fitur pencarian produk di navbar"

Alasannya:
- Menggunakan tipe Conventional Commit, yaitu feat.
- Menjelaskan perubahan yang dilakukan.
- Menjelaskan fitur secara spesifik.
- Mudah dipahami ketika melihat riwayat commit.

Pesan "update" terlalu umum, sedangkan "fix bug tombol" sudah lebih jelas tetapi belum menggunakan format Conventional Commits dan masih kurang spesifik.
10. Fungsi file .gitignore
.gitignore digunakan untuk memberitahu Git file atau folder apa yang tidak perlu dilacak dan dikirim ke repository.

Contoh yang sebaiknya dimasukkan:
1. .env — dapat berisi API key, password, token, atau informasi rahasia.
2. node_modules/ — ukurannya dapat sangat besar dan dapat dibuat kembali dengan package manager.
3. dist/ — berisi hasil build yang dapat dihasilkan kembali secara otomatis.
4. .vscode/ — dapat berisi konfigurasi pribadi untuk komputer masing-masing.
5. *.log — berisi informasi sementara yang biasanya tidak diperlukan dalam repository.

Contoh .gitignore:
.env
node_modules/
dist/
*.log
.vscode/
11. Standar penamaan branch
Penamaan branch sebaiknya konsisten, singkat, dan menjelaskan tujuan branch.

Format yang umum:
jenis/nama-perubahan

Contoh:
1. feature/login — untuk membuat fitur login.
2. feature/search-product — untuk membuat fitur pencarian produk.
3. fix/navbar-mobile — untuk memperbaiki navbar pada perangkat mobile.

Format ini lebih baik daripada penamaan bebas seperti branch1, punya-saya, atau coba karena nama branch langsung menunjukkan jenis dan tujuan pekerjaan.
12. Peran HTML, CSS, dan JavaScript
HTML (HyperText Markup Language) digunakan untuk membuat struktur dan isi halaman website.

CSS (Cascading Style Sheets) digunakan untuk mengatur tampilan dan desain website, seperti warna, ukuran, posisi, layout, dan responsivitas.

JavaScript digunakan untuk memberikan interaksi dan perilaku dinamis pada website.

Secara sederhana:
HTML = struktur
CSS = tampilan
JavaScript = interaksi/perilaku
13. Dua lingkungan tempat JavaScript dijalankan
1. Browser
JavaScript dapat dijalankan langsung di browser seperti Chrome, Edge, Firefox, dan Safari. Contohnya digunakan untuk mengubah isi HTML atau merespons interaksi pengguna.

2. Server
JavaScript dapat dijalankan di server menggunakan runtime seperti Node.js. JavaScript dapat digunakan untuk membuat server, API, membaca file, dan mengakses database.
14. Perbedaan JavaScript dan ECMAScript (ES)
JavaScript adalah bahasa pemrograman yang digunakan untuk membuat website menjadi interaktif.

ECMAScript (ES) adalah standar atau spesifikasi yang mendefinisikan bagaimana bahasa JavaScript bekerja. JavaScript merupakan salah satu implementasi dari standar ECMAScript.

Sederhananya:
ECMAScript = standar
JavaScript = bahasa yang mengimplementasikan standar tersebut

Contoh gaya lama:
var nama = "Hanif";

function sapa(nama) {
    return "Halo " + nama;
}

Contoh gaya modern:
const nama = "Hanif";

const sapa = (nama) => {
    return `Halo ${nama}`;
};

Pada gaya modern digunakan fitur seperti const, arrow function, dan template literal. Perkembangan ECMAScript membuat JavaScript memiliki fitur baru yang lebih praktis dan mudah dibaca.
