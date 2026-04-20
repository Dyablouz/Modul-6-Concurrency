# Reflection

## Commit 1
handle_connection adalah sebuah fungsi yang mengambil data stream dan ditandai dengan "mut" agar data yang sedang dibaca dapat berubah ketika masih diproses. Kemudian, kita menggunakan BufReader untuk mempercepat pembacaan line per line. Selanjutnya, kita mendeklarasi http_request sebagai vector tanpa tipe data agar compiler Rust yang akan menentukannya sendiri. Variabel http_request sendiri akan menyimpan hasil parse data yang dibaca setelah me-unwrap dan ditransform. Setelah selesai, hasilnya diprint.

## Commit 2
![Commit 2 screen capture](/assets/images/commit2.png)

## Commit 3
Mengecek request yang dikirim dari user, jika pathnya sesuai, maka refer user ke halaman hello.html dengan status "OK". Jika tidak sesuai, maka tampilkan file 404.html dan status "NOT FOUND".

![Commit 3 screen capture](/assets/images/commit3.png)

## Commit 4
Ketika kita membuka request user berupa 127.0.0.1/sleep, terdapat jeda 10 detik sampai halaman user ter-load dengan baik dikarenakan kita menambahkan "thread::sleep(Duration::from_secs(10));". Hal ini berguna untuk mengatur agar request yang diterima server ketika banyak user mengaksesnya sekaligus untuk tidak kewalahan menghandlenya karena terdapat antrian.

## Commit 5
Thread pool adalah sejumlah worker yang bekerja di backend untuk menerima tasks dari request user. Setiap worker akan bekerja masing-masing sehingga sesuai dengan perubahan yang dilakukan pada milestone 5 ini, jika user mengirim request sleep yang harus menunggu 10 detik hingga selesai, ketika ada user kedua yang juga mengirim request, seharusnya ia juga akan menunggu 10 detik tersebut hingga selesai tanpa perubahan yang dilakukan pada milestone 5. Tetapi dengan tambahan Thread pool ini, terdapat beberapa worker yang dapat bekerja dalam satu waktu sehingga request kedua tidak harus menunggu request pertama selesai terlebih dahulu untuk dikerjakan.