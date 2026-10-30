SOAL PRE-TEST

1.	Jelaskan secara singkat tujuan penggunaan klausa JOIN pada basis data relasional dan apa kelemahannya jika digunakan pada tabel dengan jutaan baris data!

Jawab:
Tujuan utama penggunaan klausa JOIN adalah untuk menggabungkan data dari dua tabel atau lebih yang saling berelasi berdasarkan kolom kunci yang sama, namun kelemahannya jika diterapkan pada tabel dengan jutaan baris adalah performa kueri akan menjadi sangat lambat dan membebani sumber daya server karena proses pencocokan data (nested loop atau merge join) memakan waktu komputasi yang besar.

2.	Apa yang dimaksud dengan redundansi data, dan mengapa dalam konsep "Denormalisasi" redundansi ini sengaja diciptakan?   

Jawab:
Redundansi data adalah kondisi duplikasi atau pengulangan penyimpanan data yang sama pada beberapa tempat di dalam basis data, dan sengaja diciptakan dalam konsep "Denormalisasi" untuk mempercepat performa pembacaan data (read performance) tanpa harus sering melakukan operasi JOIN yang rumit.

3.	Berikan satu contoh konkret bagaimana sebuah atribut turunan dapat menghindari penggunaan fungsi agregasi (seperti SUM) dalam query!  
 
Jawab:
Contoh konkretnya adalah alih-alih menggunakan fungsi agregasi seperti SUM(total_harga) pada tabel transaksi setiap kali ingin menampilkan total belanja pelanggan, kita dapat membuat atribut turunan berupa kolom fisik bernama total_belanja langsung pada tabel pelanggan yang nilainya diperbarui secara otomatis setiap kali terjadi transaksi baru.

