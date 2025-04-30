# UTS_Pemrograman Web
## Artikel SQL Injection
| UTS  |  Pemrograman Web 2   |
|-------|--------- |
| Nama   | Habib Suprayoga |
| Nim  | 312310608 |
| Kelas | TI.23.A6 |
| **Mata Kuliah**    |     Pemrograman Web 2    |
| **Dosen Pengampu** |Agung Nugroho, S.Kom., M.Kom  |
| **Tautan Artikel** |https://thelifeofhabib.blogspot.com/2025/04/memahami-sql-injection-menunjukan-dan.html |

## Pendahuluan
Salah satu kerentanan yang paling umum dan berbahaya adalah Injeksi SQL. Jenis eksploitasi ini terjadi ketika kode SQL jahat dapat masuk ke dalam input yang diterima oleh basis data aplikasi web. Injeksi SQL telah diketahui selama lebih dari dua puluh tahun, dan hingga kini, masih menjadi salah satu ancaman paling kuat bagi aplikasi web modern. Laporan yang dikeluarkan oleh OWASP (Open Web Application Security Project) pada 2021 masih mencantumkan Injeksi SQL sebagai salah satu dari sepuluh kerentanan keamanan teratas mereka.

Tujuan artikel ini adalah untuk menyajikan penjelasan mendalam tentang konsep injeksi SQL, mendemonstrasikan cara kerjanya secara praktis, menganalisis dampaknya, dan mengusulkan rencana pencegahan yang efektif. Pengembang perlu mengetahui cara membangun aplikasi yang aman, dan oleh karena itu, mereka harus diberi pendidikan mengenai kerentanan ini. 

## Pembahasan
Apa itu Injeksi SQL?

Injeksi SQL adalah Teknik Serangan di mana seorang penyerang menyisipkan atau ‘menusukkan’ perintah serangan SQL ke dalam formulir input aplikasi Website. Jika input ini diproses tanpa validasi atau sanitasi, aplikasi dapat mengubah struktur kueri sistem manajemen basis data relasional (RDBMS) dan menghasilkan informasi yang tidak sah, manipulasi data, penghapusan, atau pembajakan server. Berdasarkan penelitian yang saya lakukan, SQL Injection dapat dibagi menjadi beberapa jenis:

  1. In-band SQL Injection: Penyerang memperoleh hasil serangan melalui saluran komunikasi yang sama dengan yang digunakan untuk meluncurkan serangan. 

     o Berbasis kesalahan: Menggunakan pesan kesalahan yang ditampilkan oleh database untuk mengetahui struktur database. 

      o Union-based: Menggunakan operator UNION SQL untuk menggabungkan hasil query berbahaya dengan query asli.

     2. Blind SQL Injection: Penyerang tidak dapat melihat hasil serangan secara langsung.

         o Boolean-based: Mengirim query dan menganalisis perbedaan dalam respons aplikasi.
        o Time-based: Mengirim query yang menyebabkan database menunda responsnya untuk beberapa waktu jika kondisi tertentu terpenuhi.

     4. Out-of-band SQL Injection: Penyerang menggunakan saluran alternatif untuk mendapatkan hasil (misalnya melalui DNS atau HTTP requests). 

Eksperimen SQL Injection

 Untuk memahami SQL Injection secara lebih mendalam, saya telah melakukan serangkaian eksperimen dalam lingkungan terkontrol. Berikut adalah penjelasan langkah demi langkah dari eksperimen tersebut. 

## Dokumentasi Hasil Eksperimen Artikel
berikut adalah code pemrograman yang digunakan

1. Saya membuat aplikasi web sederhana menggunakan: 

    o PHP 8.0 sebagai bahasa pemrograman server    
    o MySQL 8.0 sebagai database 
    o HTML dan CSS untuk frontend 
   o XAMPP sebagai server lokal 

 2. Saya membuat database users dengan struktur berikut:

CREATE TABLE users (

  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50) NOT NULL,
  password  VARCHAR(255) NOT NULL,
  email  VARCHAR(100) NOT NULL,
  is_admin BOOLEAN DEFAULT FALSE

);



INSERT INTO users (username, password, email, is_admin) VALUES

('admin', 'admin123', 'admin@example.com', TRUE),

('john', 'password123', 'john@example.com', FALSE),

('jane', 'secret123', 'jane@example.com', FALSE),



  3. Saya membuat halaman login sederhana dengan kode PHP yang rentan:

Dalam eksperimen pertama, saya mencoba melakukan bypass pada form login. 

Langkah-langkah: 

    1. Saya membuka halaman login 

    2. Pada kolom username, saya memasukkan: ' OR '1'='1 

    3. Pada kolom password, saya memasukkan: ' OR '1'='1 
    

## code halaman Beranda

![image](https://github.com/user-attachments/assets/a325171e-cda9-40ae-8da4-6407386ede09)

## code halaman login yang rentan

![image](https://github.com/user-attachments/assets/aad35513-9b63-4f82-a48f-3492d4064171)

## code halaman yang aman

![image](https://github.com/user-attachments/assets/25629ac5-4290-44c9-b367-8128406f0956)


## Hasilnya Seperti Berikut

## hasil halaman Beranda
![image](https://github.com/user-attachments/assets/20306bec-45c9-4620-b023-d792479f69f9)

## hasil halaman login yang rentan
![image](https://github.com/user-attachments/assets/5a4100dc-922c-4997-ac92-f747d15900e7)

## hasil halaman login yang aman
![image](https://github.com/user-attachments/assets/7047b56b-c1f8-4918-bff9-cf0bcc3397df)


## Kesimpulan
 SQL Injection tetap menjadi ancaman serius bagi aplikasi web modern meskipun solusinya relatif sederhana. Melalui eksperimen dalam artikel ini, kita dapat melihat betapa mudahnya bagi penyerang untuk mengeksploitasi aplikasi yang tidak diproteksi dengan baik, dan betapa luas dampak yang dapat ditimbulkan. 

 Kunci untuk mencegah SQL Injection adalah menggunakan prepared statements secara konsisten, melakukan validasi input, dan menerapkan prinsip keamanan berlapis. Dengan pemahaman yang baik tentang bagaimana serangan ini bekerja dan strategi mitigasi yang tepat, pengembang dapat membangun aplikasi web yang lebih aman dan melindungi data pengguna mereka. 

 Sebagai pengembang web, kita memiliki tanggung jawab untuk memahami kerentanan keamanan dan menerapkan praktik terbaik dalam kode kita. Pengamanan terhadap SQL Injection bukan hanya tentang melindungi data, tetapi juga tentang membangun kepercayaan dengan pengguna aplikasi kita.

 ## Referensi
1. OWASP. (2021). OWASP Top Ten. https://owasp.org/www-project-top-ten/ 
2. Stuttard, D., & Pinto, M. (2018). The Web Application Hacker's Handbook: Finding and Exploiting Security Flaws (2nd ed.). Wiley. 
3. Clarke, J. (2020). SQL Injection Attacks and Defense (2nd ed.). Syngress. 
4. Litchfield, D. (2005). The Database Hacker's Handbook: Defending Database Servers. Wiley. 
5. PHP Manual. (2022). Prepared Statements. https://www.php.net/manual/en/mysqli.quickstart.prepared-statements.php

## Sekian yang bisa saya tampilkan kurang lebihnya mohon maaf. 
