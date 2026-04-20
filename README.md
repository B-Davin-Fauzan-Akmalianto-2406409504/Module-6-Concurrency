## Commit 1 Reflection Notes
Fungsi handle_connection membaca data dari koneksi, dan kemudian merubahnya menjadi bentuk tulisan yang bisa dibaca oleh manusia. Pertama dia menampung sinyal dulu di buffer (yang disimpan variable buf_reader), kemudian dari buf_reader itu dipecah per newline dan dicollect ke satu vector http_request, yang kemudian di print.

## Commit 2 Reflection Notes
![Commit 2 screen capture](/assets/images/commit2.png)
Pada fungsi handle_connection di commit 2, kita membuat suatu string response yang berisi status line, headers, baris kosong, serta htmlnya. Setelah itu, response dikirim ke dalam stream, yang menghasilkan page 127.0.0.1/7878 menampilkan file hello.html.

## Commit 3 Reflection Notes
![Commit 3 screen capture](/assets/images/commit3.png)
Pada commit 3, kita membuat if expression yang dimana kalau misal http_requestnya ga diawali dengan GET / HTTP/1.1 (artinya kalau linknya bukan "/"), dia bakalan nge set nama file html yang di pakai menjadi yang 404.html, sehingga bisa menampilkan page yang menunjukkan 404 not found jika tidak memakai link /.
Refactoring dilakukan karna sebelumnya itu dari dua kondisi ada yang ngulang kode yang sama, jadi biar DRY.

## Commit 4 Reflection Notes
Karena servernya berjalan di single thread, maka ketika page /sleep mendelay diri sendiri selama 10 detik, page lain harus nunggu /sleep kelar pakai threadnya dulu, baru bisa jalan.

## Commit 5 Reflection Notes
Kita membuat sebuah struct bernama ThreadPool di lib.rs, fungsinya adalah untuk membuat multi threads namun bisa dibatasi oleh sebuah angka (size). Disini, dibuatlah suatu channel yang terdiri dari sender (yang dipegang threadpoolnya) dan receiver yang dipegang masing2 worker (thread). Receiver dibungkus Arc agar bisa punya multiple clones dari receiver yang sama (agar bisa dipegang bbrp worker sekaligus), dan juga Mutex agar instruksi hanya bisa dikerjain satu worker dalam satu waktu. Kemudian, fungsi execute di ThreadPool akan mengirim "job" untuk dikerjakan salah satu worker. 
Dalam worker, jangan lupa di loop agar worker (thread) tidak sekali jalan lalu mati.