JAWABAN TUGAS GIT, GITHUB, DAN PULL REQUEST

1. Dua arah aliran kode antara komputer lokal dan GitHub
Ada dua arah utama:
• Push → mengirim perubahan dari komputer lokal ke GitHub.
• Pull → mengambil perubahan terbaru dari GitHub ke komputer lokal.

Contoh push:
Saya selesai membuat fitur login di komputer dan sudah melakukan commit. Saya ingin menyimpan perubahan tersebut ke repository GitHub agar bisa dilihat oleh anggota tim. Maka saya menjalankan git push.

Contoh pull:
Teman satu tim sudah memperbarui style.css di GitHub. Sebelum saya melanjutkan pekerjaan, saya perlu mengambil perubahan terbaru tersebut ke komputer dengan git pull.
2. Fungsi perintah git push
git push digunakan untuk mengirim commit yang ada di repository lokal ke repository remote, misalnya GitHub.

a. Fungsi opsi -u pada git push -u origin main
Opsi -u atau --set-upstream digunakan untuk menghubungkan branch lokal main dengan branch main pada remote origin.

b. Jika -u tidak digunakan pada push pertama
Perubahan tetap dapat dikirim ke GitHub menggunakan git push origin main. Namun, hubungan antara branch lokal dan remote belum ditetapkan sebagai upstream/tracking branch. Akibatnya, pada push berikutnya Git mungkin masih meminta kita menentukan tujuan branch.

c. Mengapa setelah -u ditetapkan cukup menjalankan git push?
Karena Git sudah mengetahui bahwa branch lokal main harus dikirim ke origin/main. Jadi selanjutnya cukup menjalankan git push.
3. Perbedaan git clone dan git init
git clone digunakan untuk menyalin repository yang sudah ada, termasuk file proyek, riwayat commit, branch, dan konfigurasi remote.

Contoh:
git clone https://github.com/andi/proyek.git

Sedangkan git init digunakan untuk membuat repository Git baru pada folder yang sebelumnya belum menjadi repository Git.

Contoh:
mkdir proyek
cd proyek
git init

Setelah git clone tidak perlu menjalankan git init lagi karena git clone sudah otomatis membuat repository Git lokal beserta folder .git.
4. Fungsi git pull
git pull digunakan untuk mengambil perubahan terbaru dari repository remote dan menggabungkannya ke branch lokal.

Perintah ini sangat penting dalam kerja tim karena anggota tim mungkin sudah melakukan perubahan dan push ke GitHub. Dengan git pull, kita mendapatkan perubahan terbaru sehingga pekerjaan kita tidak menggunakan kode yang sudah ketinggalan.

Dua momen sebaiknya menjalankan git pull:
1. Sebelum mulai bekerja pada pagi hari, agar kode lokal sudah mengikuti perkembangan terbaru dari anggota tim.
2. Sebelum mulai mengerjakan fitur setelah cukup lama tidak melakukan update, agar perubahan anggota tim terlebih dahulu masuk ke komputer kita.
5. Alur kerja harian yang direkomendasikan
Urutan command:
git pull
git status
# melakukan perubahan kode
git add .
git commit -m "Menjelaskan perubahan"
git push

Penjelasan:
1. git pull — mengambil perubahan terbaru dari GitHub agar pekerjaan tidak menggunakan kode lama.
2. git status — memeriksa kondisi repository, misalnya file yang berubah, file baru, atau file yang belum masuk staging.
3. Melakukan perubahan kode — mengedit, menambah, atau memperbaiki program sesuai tugas.
4. git add . — memasukkan perubahan ke staging area agar siap di-commit.
5. git commit -m "Menjelaskan perubahan" — menyimpan perubahan ke riwayat Git secara lokal.
6. git push — mengirim commit dari komputer lokal ke GitHub agar dapat disimpan di repository remote dan dilihat anggota tim.
6. Apa itu Fork?
Fork adalah membuat salinan repository milik orang atau organisasi lain ke dalam akun GitHub kita sendiri.

Situasi nyata melakukan fork:
1. Berkontribusi pada proyek open source. Jika kita ingin memperbaiki proyek yang bukan milik kita, kita dapat melakukan fork terlebih dahulu.
2. Mengembangkan perubahan tanpa mengganggu repository asli. Kita dapat mencoba fitur baru pada repository hasil fork milik sendiri.

Perbedaan Fork dan Clone:
• Fork dilakukan di GitHub dan membuat salinan repository ke akun GitHub sendiri.
• Clone dilakukan untuk menyalin repository ke komputer lokal.
• Fork biasanya digunakan untuk bekerja pada repository orang lain.
• Clone digunakan agar repository dapat diedit dan dijalankan secara lokal.

Alur sederhananya:
Repository asli → Fork → Repository milik kita → Clone → Komputer lokal
7. Enam langkah kontribusi open source menggunakan Fork + Pull Request
1. Fork repository
Tujuan: mendapatkan repository sendiri sehingga kita dapat melakukan perubahan tanpa langsung mengubah repository asli.

2. Clone repository hasil fork
Contoh: git clone https://github.com/hanif/proyek.git
Tujuan: mengunduh repository hasil fork ke komputer sehingga dapat dikerjakan secara lokal.

3. Membuat branch baru
Contoh: git switch -c perbaikan-bug
Tujuan: memisahkan pekerjaan dari branch main sehingga perubahan lebih aman dan mudah dikelola.

4. Mengedit kode, add, dan commit
Contoh:
git add .
git commit -m "Memperbaiki bug validasi"
Tujuan: menyimpan perubahan yang dibuat ke dalam riwayat Git.

5. Push branch ke repository hasil fork
Contoh: git push origin perbaikan-bug
Tujuan: mengirim branch dan perubahan ke GitHub agar dapat digunakan untuk mengajukan kontribusi.

6. Membuat Pull Request
Tujuan: meminta pemilik atau maintainer proyek memeriksa dan mempertimbangkan perubahan agar dapat digabungkan ke proyek utama.
8. Apa yang dimaksud dengan Pull Request?
Pull Request (PR) adalah permintaan untuk menggabungkan perubahan dari satu branch atau repository ke branch lain.

PR penting dalam kerja tim karena perubahan tidak langsung masuk ke main. Perubahan dapat diperiksa terlebih dahulu oleh anggota tim.

Mengapa tidak langsung merge?
• Perubahan mungkin mengandung bug.
• Perubahan dapat menyebabkan konflik.
• Kode mungkin tidak sesuai standar.
• Perubahan dapat merusak fitur yang sudah ada.
• Pengujian mungkin belum cukup.

Keuntungan menggunakan PR:
1. Code review — anggota tim dapat memeriksa kode sebelum digabungkan.
2. Diskusi — anggota tim dapat memberikan komentar dan meminta perubahan.
3. Mengurangi kesalahan — bug dapat ditemukan sebelum kode masuk ke branch utama.
4. Dokumentasi — PR menjadi catatan mengenai perubahan yang pernah dilakukan dalam proyek.
9. Studi kasus Andi dan Budi
a. Apa yang kemungkinan terjadi?
Kemungkinan besar Budi mendapatkan rejected/non-fast-forward error ketika menjalankan git push, misalnya:
! [rejected] main -> main (fetch first)

Artinya branch remote sudah memiliki commit yang belum dimiliki Budi.

b. Mengapa hal tersebut terjadi?
Repository GitHub sudah berubah setelah Budi terakhir melakukan pull. Andi melakukan push, sehingga GitHub memiliki perubahan baru sementara Budi belum mengambil perubahan tersebut. Git mencegah Budi menimpa perubahan Andi begitu saja.

c. Apa yang seharusnya dilakukan Budi sebelum mulai mengedit?
Budi sebaiknya menjalankan git pull terlebih dahulu agar kode lokal mendapatkan perubahan terbaru dari Andi.

d. Urutan perintah Budi sejak pagi hari:
git pull
git status
Kemudian mengedit style.css.

Setelah selesai:
git status
git add style.css
git commit -m "Memperbarui tampilan CSS"
git push

Jika ketika git pull terjadi conflict, Budi harus menyelesaikan conflict terlebih dahulu sebelum melakukan commit dan push.
10. Studi Kasus — Alur Kerja Lengkap
Urutan perintah:
git clone https://github.com/andi/proyek.git
cd proyek
git switch -c perbaikan-bug
touch fix.js
git add fix.js
git commit -m "Memperbaiki bug pada validasi form"
git push origin perbaikan-bug

a. Apa yang dilakukan git clone?
Perintah tersebut mengunduh repository proyek dari GitHub ke komputer lokal. Selain file proyek, Git juga mengambil riwayat repository dan konfigurasi remote.

b. Mengapa membuat branch perbaikan-bug?
git switch -c perbaikan-bug membuat branch baru dan langsung berpindah ke branch tersebut. Tujuannya agar pekerjaan memperbaiki bug tidak langsung dilakukan pada main. Dengan cara ini, branch main tetap lebih aman dan perubahan dapat diperiksa terlebih dahulu.

c. Tujuan git push origin perbaikan-bug
Perintah tersebut mengirim branch perbaikan-bug dari komputer lokal ke remote bernama origin. Branch baru belum tentu memiliki upstream branch, sehingga tujuan push ditentukan secara jelas. Alternatif yang sekaligus menetapkan upstream adalah:
git push -u origin perbaikan-bug
Setelah itu, push berikutnya cukup menggunakan git push.

d. Langkah di GitHub setelah push
1. Buka repository di GitHub.
2. Klik Compare & pull request jika tersedia.
3. Pastikan branch sumber adalah perbaikan-bug.
4. Pastikan branch tujuan adalah main.
5. Tulis judul dan penjelasan perubahan.
6. Periksa perubahan jika diperlukan.
7. Klik Create pull request.
Setelah itu pemilik atau maintainer repository dapat melakukan review.

e. Jika pemilik repo meminta revisi
Pengguna tidak perlu membuat Pull Request baru selama masih menggunakan branch yang sama. Pengguna kembali ke komputer, memperbaiki kode sesuai permintaan, kemudian menjalankan:
git switch perbaikan-bug
git add .
git commit -m "Memperbaiki revisi validasi form"
git push

Karena branch tersebut sudah terhubung dengan PR, commit baru yang di-push ke branch perbaikan-bug akan otomatis muncul pada Pull Request yang sama.

Alur lengkap:
Fork/Clone → Buat branch → Edit kode → git add → git commit → git push → Buat Pull Request → Code Review → Diminta revisi → Edit kode lagi → git add → git commit → git push → PR diperbarui → Review ulang → Merge ke main.
