## Commit 1 Reflection Notes
Fungsi handle_connection membaca data dari koneksi, dan kemudian merubahnya menjadi bentuk tulisan yang bisa dibaca oleh manusia. Pertama dia menampung sinyal dulu di buffer (yang disimpan variable buf_reader), kemudian dari buf_reader itu dipecah per newline dan dicollect ke satu vector http_request, yang kemudian di print.

## Commit 2 Reflection Notes
![Commit 2 screen capture](/assets/images/commit2.png)
Pada fungsi handle_connection di commit 2, kita membuat suatu string response yang berisi status line, headers, baris kosong, serta htmlnya. Setelah itu, response dikirim ke dalam stream, yang menghasilkan page 127.0.0.1/7878 menampilkan file hello.html.