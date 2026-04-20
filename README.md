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