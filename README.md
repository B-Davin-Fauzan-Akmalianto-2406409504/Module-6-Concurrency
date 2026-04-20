## Commit 1 Reflection Notes
Fungsi handle_connection membaca data dari koneksi, dan kemudian merubahnya menjadi bentuk tulisan yang bisa dibaca oleh manusia. Pertama dia menampung sinyal dulu di buffer (yang disimpan variable buf_reader), kemudian dari buf_reader itu dipecah per newline dan dicollect ke satu vector http_request, yang kemudian di print.

## Commit 2 Reflection Notes
![Commit 2 screen capture](/assets/images/commit2.png)
Pada fungsi handle_connection di commit 2, kita membuat suatu string response yang berisi status line, headers, baris kosong, serta htmlnya. Setelah itu, response dikirim ke dalam stream, yang menghasilkan page 127.0.0.1/7878 menampilkan file hello.html.

## Commit 3 Reflection Notes
![Commit 3 screen capture](/assets/images/commit3.png)
Pada commit 3, kita membuat if expression yang dimana kalau misal http_requestnya ga diawali dengan GET / HTTP/1.1 (artinya kalau linknya bukan "/"), dia bakalan nge set nama file html yang di pakai menjadi yang 404.html, sehingga bisa menampilkan page yang menunjukkan 404 not found jika tidak memakai link /.
Refactoring dilakukan karna sebelumnya itu dari dua kondisi ada yang ngulang kode yang sama, jadi biar DRY.