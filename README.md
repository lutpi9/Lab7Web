# Pertemuan ke 1-3 <img src=https://seeklogo.com/images/E/elephpant-mascot-php-logo-4C78D1AC4E-seeklogo.com.png width="120px" >

## Profil
|  |  |
| -------- | --- |
| **Nama** | Lutpiah Ainus Shiddik |
| **Kelas** | TI.23.A.5 |
| **Mata Kuliah** | Pemrograman Web 2 |

# Praktikum 1: PHP Framework (Codeigniter)

## Langkah-langkah Praktikum
## Persiapan
Langkah-langkah Praktikum
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada
webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan
Codeigniter 4.
Berikut beberapa ekstensi yang perlu diaktifkan:
• php-json ekstension untuk bekerja dengan JSON;
• php-mysqlnd native driver untuk MySQL;
• php-xml ekstension untuk bekerja dengan XML;
• php-intl ekstensi untuk membuat aplikasi multibahasa;
• libcurl (opsional), jika ingin pakai Curl.
Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache
klik Config -> PHP.ini

### Catatan : mulai dari PHP 7.0, ekstensi JSON biasanya sudah termasuk secara bawaan.

<img width="675" alt="cmd1" src="https://github.com/user-attachments/assets/c58ce11f-8f12-4425-be47-32cb3209315a" />

Selanjutnya, kalian dapat mencari ekstensi yang diperlukan. Jika ada ekstensi yang belum aktif, kalian bisa mengaktifkannya melalui XAMPP Control Panel. Pada bagian Apache, klik Config lalu pilih PHP.ini.


![xampp](https://github.com/user-attachments/assets/366e5646-19d9-46ba-8352-8f40df7f62cc)


<img width="675" alt="cmd1" src="https://github.com/user-attachments/assets/2fe0daf6-9de8-4cd7-84f6-02234cb6aba6" />
* Sebagai contoh, jika ekstensi extension=intl belum aktif, cara mengaktifkannya adalah dengan menghapus tanda titik koma (;) di depan nama ekstensi tersebut. Setelah itu, simpan file tersebut dan lakukan restart pada Apache web server.

## Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual
dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.
* Unduh Codeigniter dari website https://codeigniter.com/download
* Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
* Ubah nama direktory codeigniter4-framework-v4.x.xx menjadi ci4.
* Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/


<img width="959" alt="codelnigter" src="https://github.com/user-attachments/assets/91e3bf8a-d115-423d-9127-4771344d433a" />

## Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka Shell pada XAMPP.


<img width="674" alt="xamppphpini" src="https://github.com/user-attachments/assets/d80ab5eb-6805-441c-893d-2760cafedc16" />

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (Contoh : cd htdocs/lab11_ci/ci4)

Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

### php spark

<img width="676" alt="spark" src="https://github.com/user-attachments/assets/9b879a64-160b-46b3-bfe8-8ef7b1a1ae45" />

## Mengaktifkan Mode Debugging

CodeIgniter 4 memiliki fitur debugging yang berguna untuk membantu developer dalam melihat pesan error ketika terjadi kesalahan dalam penulisan kode program.

Secara bawaan, fitur ini belum diaktifkan. Saat terjadi error pada aplikasi, akan muncul pesan kesalahan seperti contoh berikut.

![WhatsApp Image 2025-03-13 at 14 41 11](https://github.com/user-attachments/assets/d85309b9-a6d5-402b-bbab-0aab9ef76ece)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya,
maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment
variable CI_ENVIRONMENT menjadi development.

<img width="458" alt="image" src="https://github.com/user-attachments/assets/e6aedccb-3a11-44db-a34b-1d919b889a4f" />


Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable
CI_ENVIRONMENT menjadi development.
#### Catatan : Kadang, CodeIgniter tidak membaca file .env karena masih dikomentari, pastikan tidak ada tanda # di depan CI_ENVIRONMENT.


![pasteerror](https://github.com/user-attachments/assets/4c32f46a-b725-4b20-abec-035c38c88dfd)

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
app/Controller/Home.php hilangkan titik koma pada akhir kode return view('welcome_message').

![coba](https://github.com/user-attachments/assets/0cf96233-3011-4419-96b5-996d0c1c8e54)

## Memahami konsep MVC
CodeIgniter mengadopsi konsep MVC, yang merupakan singkatan dari Model-View-Controller. MVC adalah pola arsitektur yang banyak digunakan dalam pengembangan aplikasi. Tujuan utama dari konsep ini adalah memisahkan kode program berdasarkan proses logika, pengelolaan data, dan tampilan.
Logika proses ditempatkan di dalam direktori Controller, data dikelola melalui direktori Model, dan tampilan desain antarmuka diletakkan pada direktori View.

CodeIgniter menerapkan paradigma object-oriented programming (OOP) dalam penerapan konsep MVC ini.

Model berisi kode program yang merepresentasikan pemodelan data. Data tersebut bisa berasal dari database maupun sumber lainnya.

View merupakan bagian kode yang mengatur tampilan antarmuka pengguna. Dalam aplikasi web, bagian ini umumnya berkaitan dengan HTML dan CSS.

Controller adalah bagian kode yang mengatur logika proses serta menjembatani antara View dan Model. Fungsinya adalah menerima request dan data dari pengguna, lalu memprosesnya dengan melibatkan Model dan View.

## Routing dan Controller
Routing adalah proses pengaturan jalur atau rute dari sebuah request untuk menentukan bagian mana dari aplikasi yang akan menanganinya. Dalam framework CodeIgniter 4, routing digunakan untuk menentukan Controller mana yang akan merespons suatu request.
Controller sendiri adalah class atau script yang memiliki tanggung jawab dalam menangani request tersebut.

Di CodeIgniter, setiap request yang masuk melalui file index.php akan diteruskan ke Router. Selanjutnya, Router akan mengarahkan request tersebut ke Controller yang sesuai.

File konfigurasi Router dapat ditemukan di: app/Config/Routes.php.

Router terletak pada file app/config/Routes.php
![Routes](https://github.com/user-attachments/assets/59e66513-f7ad-4bf0-a3ef-83e6e701639e)

Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
Contoh:
```` python
$routes->get('/', 'Home::index');
````
Kode tersebut akan mengarahkan rute untuk halaman home.

#### Membuat Route Baru.
Tambahkan kode berikut di dalam Routes.php
```` python
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
````
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

php spark routes

![spark routes](https://github.com/user-attachments/assets/f59fb602-6a7b-4686-b4b9-5d9d5238a981)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about

![404](https://github.com/user-attachments/assets/4d45c2c3-a64e-4017-b0fa-25db27815f13)

Ketika halaman diakses namun muncul pesan error 404 file not found, itu berarti file atau halaman yang diminta tidak tersedia. Agar halaman tersebut dapat diakses, perlu dibuat terlebih dahulu Controller yang sesuai dengan routing yang telah ditentukan, yaitu Controller dengan nama Page.


#### Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.

```` python
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "Ini halaman About";
    }
    public function contact()
    {
        echo "Ini halaman Contact";
    }
    public function faqs()
    {
        echo "Ini halaman FAQ";
    }
}
````


![about (1)](https://github.com/user-attachments/assets/09512980-1530-43c5-920a-cce000b1d6c8)

#### Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.

```` python
$routes->get('page/tos', 'Page::tos');
$routes->setAutoRoute(true);
````

Tambahkan method baru pada Controller Page seperti berikut.
```` python
public function tos()
{
    echo "ini halaman Term of Services";
}
````

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos

![tos](https://github.com/user-attachments/assets/ab692c57-15ef-44af-ae7b-1624548a44dc)

### Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori Views (app/Views/about.php) kemudian isi kodenya seperti berikut.
```` python
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>

<body>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
</body>

</html>
````

Ubah method about pada class Controller Page menjadi seperti berikut:
``` python
    public function about()
    {
        return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }
```

Kemudian lakukan refresh pada halaman tersebut.


![About2 (1)](https://github.com/user-attachments/assets/d2a6c9fa-ee7a-45cf-8788-a6d638e2ec10)

### Membuat Layout Web dengan CSS
Pada dasarnya, penerapan layout web menggunakan CSS dapat dilakukan dengan mudah di CodeIgniter. Hal yang perlu diperhatikan adalah bahwa pada CodeIgniter 4, file yang berisi aset seperti CSS dan JavaScript disimpan di dalam direktori public.

Buat file css pada direktori public dengan nama style.css


![style](https://github.com/user-attachments/assets/03dedcf2-8336-486a-ac22-254b7fc81e16)

Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php

File app/Views/template/header.php
```python
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css'); ?>">
</head>

<body>
    <div id="container">
        <header>
            <h1>Layout Sederhana</h1>
        </header>
        <nav>
            <a href="<?= base_url('/'); ?>" class="active">Home</a>
            <a href="<?= base_url('/artikel'); ?>">Artikel</a>
            <a href="<?= base_url('/about'); ?>">About</a>
            <a href="<?= base_url('/contact'); ?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main"></section>
```

File app/Views/template/footer.php
```python
</section>
<aside id="sidebar">
    <div class="widget-box">
        <h3 class="title">Widget Header</h3>
        <ul>
            <li><a href="#">Widget Link</a></li>
            <li><a href="#">Widget Link</a></li>
        </ul>
    </div>
    <div class="widget-box">
        <h3 class="title">Widget Text</h3>
        <p>Vestibulum lorem elit, iaculis in nisl volutpat,
            malesuada tincidunt arcu. Proin in leo fringilla, vestibulum mi porta,
            faucibus felis. Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
    </div>
</aside>
</section>
<footer>
    <p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>

</html>
```

Kemudian ubah file app/Views/about.php seperti berikut.
```python
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![layout (2)](https://github.com/user-attachments/assets/025f198b-3c53-44f5-bbc3-a5c8b9be2685)

