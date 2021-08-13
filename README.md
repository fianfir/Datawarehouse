#Datawarehouse

##DeskripsiKasus:
Salah satu faktor kemajuan sebuah negara adalah mempunyai aplikasi transportasi seperti ojek online untuk masyarakat berpergian atau membeli suatu barang tanpa harus ketempatnya langsung.
Dimana aplikasi ojek online ini mempunyai beberapa mode yaitu car, bike, shop, dan food.
Untuk car dan bike adalah fitur penjemputan customer dari alamat customer ke tujuan yang ingin di tuju oleh customer tersebut.
Untuk shop adalah fitur untuk customer berbelanja di merchant yang terdaftar melalui onjek online.
Untuk food adalah fitur untuk customer memesan makanan atau minuman di merchant yang terdaftar melalui ojek online.
Dalam aplikasi ini sangat banyak data transaksi yang digunakan, maka dari itu ojek online membutuhkan datawarehouse untuk melakukan analisa dengan mudah guna mengambil keputusan yang tepat.
Akan tetapi dalam mengembangkan suatu data warehouse terdapat beberapa permasalahan yang memerlukan perhatian khusus, 
yaitu jumlah data yang disimpan dalam basis data bertambah dari waktu ke waktu secara signifikan sehingga terjadi penumpukan data. 
Hal ini terjadi karena peningkatan jumlah record data yang sangat pesat dengan melibatkan ribuan transaksi dalam sehari.

###DataPendukung:
Perancangan data warehouse di dukung oleh sebuah model data yang disebut model multidimensi yang memungkinkan para pengambil keputusan melakukan analisis terhadap data-data yang diperlukan. 
Pengimplementasian sistem data warehouse pada sebuah aplikasi ojek online pihak pengambil keputusan untuk menganalisa data transaksi yang digunakan dalam aplikasi ojek online.

####CaraMelakukanProsesETL
1. Mengkoneksikan ke datawarehouse
- Pertama kita melakukan connection di pentaho melalui view
- Setelah itu kita klik kanan di Database Conection lalu klik new
- Di connection name masukan uas_dw dengan port number 3308(jika masih default, maka rubah menjadi 3306 dan database name db_uas_dw)
- Lalu di connection type pilih mysql
- Lalu di bagian username isi root karena kita menggunakan Xampp dan password dikosongkan
- Jika sudah selesai maka klik test untuk memastikan sudah terhubung ke database

2. Memasukan data Excel kedalam pentaho
- kita kedesain, lalu kita masukan dengan cara drag and drop pilih microsoft excel output.
- lalu dilembar kerja klik 2 kali di bagian microsoft excel output untuk menghubungkan ke data yang ada di excel
- dibagian step name isi driver
- lalu di bagian spread sheet type pilih microsoft excel 2007
- lalu dibagian file or directory maka kita pilih file data excel yang kita ingin masukan. lalu kilik add.
- setelah itu kita ke bagian sheet
- di bagian sheet name kita pilih query_get_transaction_list_koto
- lalu dibagian Start row 0 Start column 14
- lalu kita ke fields klik get field from header row dan akan tampil row yang menjadi atribut di datawarehouse
- lakukan hal yang sama kesheet lain yang ada di excel.
- jika sudah, maka akan tampil beberapa sheet yang sudah kita buat tadi.

3. Menghubungkan data satu dengan data yang lainnya
- pilih filter rows dan lakukan drago and drop untuk mengambil id_driver.
- lalu klik 2 kali di filter rows dan masukan inputan sesuai keingingan anda.
- lakukan juga ke data customer untuk mengambil id_customer.
- setelah itu kita masukan stream lookup kedalam lembar kerja dengan cara drag and drop.
- klik 2 kali di stream lookup. gabungkan data driver dengan data table data driver, dan kita masukan inputan sesuai kebutuhan.
- lakukan juga ke data customer untuk membuat stream lookup.
- klik tombol mata untuk menjalankan projek yang sudah dibuat.
- pilih table output dan drag and drop kedalam lembar kerja.
- setting data ke dalam datawarehouse.
- jika semua telah diisi maka klik SQL pada table output.
- jalankan perintah execute untuk mengeksport data kedalam database MySQL.
- klik tombol mata lalu pilih quick launch untuk mengjalankan dan mengecek ulang projek yang sudah dibuat.
- selanjutnya kita cek di phpmyadmin dengan klik http://localhost/phpmyadmin. cari nama db_uas_dw (nama db anda).
- jika sudah ada field didalam table, maka proses export data anda sudah berhasil dibuat.

4. Membuat atau melihat ERD.
- pergi kehalaman phpmyadmin dengan klik http://localhost/phpmyadmin. cari nama db_uas_dw.
- lalu klik desainer.
- maka akan menampilkan ERD dengan settingan datawarehouse yang sudah kita input kedalam database MySQL.
