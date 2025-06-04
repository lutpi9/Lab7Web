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



# Praktikum 2: Framework Lanjutan (CRUD) - CodeIgniter 4

# Tujuan
1. mampu memahami konsep dasar Model.
2. mampu memahami konsep dasar CRUD.
3. mampu membuat program sederhana menggunakan Framework Codeigniter4.

   
# Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

   
# Langkah-langkah Praktikum
Persiapan.
Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database
server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui
XAMPP.
Membuat Database: Studi Kasus Data Artikel

<img width="598" alt="TABEL DATABASE" src="https://github.com/user-attachments/assets/7b055f63-88d8-47c5-b221-70062091366c" />


```
CREATE DATABASE lab_ci4;
```

```
CREATE TABLE artikel (
  id INT(11) auto_increment,
  judul VARCHAR(200) NOT NULL,
  isi TEXT,
  gambar VARCHAR(200),
  status TINYINT(1) DEFAULT 0,
  slug VARCHAR(200),
  PRIMARY KEY(id)
);
```

# Konfigurasi Koneksi Database

- Gunakan file .env dan atur parameter koneksi database sesuai kebutuhan.

  ![Konfigurasi database](https://github.com/user-attachments/assets/7fa61b8c-fb13-431b-b158-743aee838aac)

# Membuat Model
- Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada direktori app/Models dengan nama ArtikelModel.php


```php
<?php
namespace App\Models;

use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}
```


# Membuat Controller
- Buat Controller baru dengan nama Artikel.php pada direktori app/Controllers.

```php
<?php

namespace App\Controllers;

use App\Models\ArtikelModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/index', compact('artikel', 'title'));
    }
}
```

# Membuat View
- Buat direktori baru dengan nama artikel pada direktori app/views, kemudian buat file baru dengan nama index.php.


```php
<?= $this->include('template/header'); ?>

<?php if($artikel): foreach($artikel as $row): ?>
<article class="entry">
    <h2<a href="<?= base_url('/artikel/' . $row['slug']);?>"><?= $row['judul']; ?></a>
</h2>
    <img src="<?= base_url('/gambar/' . $row['gambar']);?>" alt="<?= $row['judul']; ?>">
    <p><?= substr($row['isi'], 0, 200); ?></p>
</article>
<hr class="divider" />
<?php endforeach; else: ?>
<article class="entry">
    <h2>Belum ada data.</h2>
</article>
<?php endif; ?>

<?= $this->include('template/footer'); ?>
```


Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

![view_1](https://github.com/user-attachments/assets/d26e459b-ffbe-4f2b-855a-220f04a57381)


Belum ada data yang diampilkan. Kemudian coba tambahkan beberapa data pada database agar dapat ditampilkan datanya.

```php
INSERT INTO artikel (judul, isi, slug) VALUE
('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah buku contoh huruf.','artikel-pertama'),
('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih dari 2000 tahun.', 'artikel-kedua');
```

Lakukan refresh pada browser untuk menampilkan hasilnya.

![view_2](https://github.com/user-attachments/assets/f8554219-52a7-4255-b348-fcfc0d47bbed)

Saat judul berita diklik, pengguna akan diarahkan ke halaman yang berbeda. Untuk itu, tambahkan sebuah fungsi baru pada Controller Artikel dengan nama view().


```php
public function view($slug)
{
    $model = new ArtikelModel();
    $artikel = $model->where([
        'slug' => $slug
    ])->first();

    // Menampilkan error apabila data tidak ada.
    if (!$artikel)
    {
        throw PageNotFoundException::forPageNotFound();
    }

    $title = $artikel['judul'];
    return view('artikel/detail', compact('artikel', 'title'));
}
```


# Membuat View Detail
- Buat view baru untuk halaman detail dengan nama app/views/artikel/detail.php.

```php
<?= $this->include('template/header'); ?>

<article class="entry">
    <h2><?= $artikel['judul']; ?></h2>
    <img src="<?= base_url('/gambar/' . $artikel['gambar']);?>" alt="<?=
$artikel['judul']; ?>">
    <p><?= $row['isi']; ?></p>
</article>

<?= $this->include('template/footer'); ?>
```

# Membuat Routing untuk artikel detail
- Buka Kembali file app/config/Routes.php, kemudian tambahkan routing untuk artikel detail.

```php
$routes->get('/artikel/(:any)', 'Artikel::view/$1');
```


![Artikel_2](https://github.com/user-attachments/assets/74f1e203-7c04-434d-86bb-2a4bfb62bcb6)

# Membuat menu admin
- Menu admin adalah untuk proses CRUD data artikel. Buat method baru pada Controller Artikel dengan nama admin_index().

```php
public function admin_index()
{
    $title = 'Daftar Artikel';
    $model = new ArtikelModel();
    $artikel = $model->findAll();
    return view('artikel/admin_index', compact('artikel', 'title'));
}
```

Selanjutnya buat view untuk tampilan admin dengan nama admin_index.php

```php
<?= $this->include('template/admin_header'); ?>

<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>AKsi</th>
        </tr>
    </thead>
    <tbody>
    <?php if($artikel): foreach($artikel as $row): ?>
    <tr>
        <td><?= $row['id']; ?></td>
        <td>
            <b><?= $row['judul']; ?></b>
            <p><small><?= substr($row['isi'], 0, 50); ?></small></p>
        </td>
        <td><?= $row['status']; ?></td>
        <td>
            <a class="btn" href="<?= base_url('/admin/artikel/edit/' . $row['id']);?>">Ubah</a>
            <a class="btn btn-danger" onclick="return confirm('Yakin menghapus data?');" href="<?= base_url('/admin/artikel/delete/' . $row['id']);?>">Hapus</a>
        </td>
    </tr>
    <?php endforeach; else: ?>
    <tr>
        <td colspan="4">Belum ada data.</td>
    </tr>
    <?php endif; ?>
    </tbody>
    <tfoot>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>AKsi</th>
        </tr>
    </tfoot>
</table>

<?= $this->include('template/admin_footer'); ?>
```

Tambahkan routing untuk menu admin seperti berikut:

```php
$routes->group('admin', function($routes) {
    $routes->get('artikel', 'Artikel::admin_index');
    $routes->add('artikel/add', 'Artikel::add');
    $routes->add('artikel/edit/(:any)', 'Artikel::edit/$1');
    $routes->get('artikel/delete/(:any)', 'Artikel::delete/$1');
});

```

akses menu admin dengan URL  http://localhost:8080/admin/artikel

![admin_1](https://github.com/user-attachments/assets/6c4a4168-05d5-4d78-ac71-bc1743750c2e)

# Menambah Data Artikel
Tambahkan fungsi/method baru pada Controller Artikel dengan nama add().

```php
public function add()
{
    // validasi data.
    $validation = \Config\Services::validation();
    $validation->setRules(['judul' => 'required']);
    $isDataValid = $validation->withRequest($this->request)->run();

    if ($isDataValid)
    {
        $artikel = new ArtikelModel();
        $artikel->insert([
            'judul' => $this->request->getPost('judul'),
            'isi' => $this->request->getPost('isi'),
            'slug' => url_title($this->request->getPost('judul')),
        ]);
        return redirect('admin/artikel');
    }
    $title = "Tambah Artikel";
    return view('artikel/form_add', compact('title'));
}
```

Kemudian buat view untuk form tambah dengan nama form_add.php

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <input type="text" name="judul">
    </p>
    <p>
        <textarea name="isi" cols="50" rows="10"></textarea>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

![formadd1](https://github.com/user-attachments/assets/8429c420-8342-49ab-9f3e-71dcfb9bee51)

# Mengubah Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama edit().

```php
public function edit($id)
{
    $artikel = new ArtikelModel();

    // validasi data.
    $validation = \Config\Services::validation();
    $validation->setRules(['judul' => 'required']);
    $isDataValid = $validation->withRequest($this->request)->run();

    if ($isDataValid)
    {
        $artikel->update($id, [
            'judul' => $this->request->getPost('judul'),
            'isi' => $this->request->getPost('isi'),
        ]);
        return redirect('admin/artikel');
    }

    // ambil data lama
    $data = $artikel->where('id', $id)->first();
    $title = "Edit Artikel";
    return view('artikel/form_edit', compact('title', 'data'));
}
```

Kemudian buat view untuk form tambah dengan nama form_edit.php

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <input type="text" name="judul" value="<?= $data['judul'];?>" >
    </p>
    <p>
        <textarea name="isi" cols="50" rows="10"><?=$data['isi'];?></textarea>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

![formedit_](https://github.com/user-attachments/assets/145b898f-1e58-4132-92df-db95418822f8)

# Menghapus Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama delete().

```php
public function delete($id)
{
    $artikel = new ArtikelModel();
    $artikel->delete($id);
    return redirect('admin/artikel');
}
```


# Praktikum 3: View Layout dan View Cell

# Tujuan
Setelah menyelesaikan praktikum ini, mahasiswa diharapkan dapat:
1. Memahami konsep View Layout di CodeIgniter 4.
2. Menggunakan View Layout untuk membuat template tampilan.
3. Memahami dan mengimplementasikan View Cell dalam CodeIgniter 4.
4. Menggunakan View Cell untuk memanggil komponen UI secara modular.

# Langkah-langkah Praktikum
Persiapan
1. Akses folder lab7_php_ci yang telah digunakan pada sesi praktikum sebelumnya.
2. Gunakan editor teks seperti Visual Studio Code (VSCode) untuk membuka proyek tersebut.

# Membuat Layout Utama
Buat folder layout di dalam app/Views/
Buat file main.php di dalam folder layout dengan kode berikut:

Buat file main.php di dalam folder layout dengan kode berikut:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title ?? 'My Website' ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>"> 
</head>
<body>
    <div id="container">
        <header><h1>Layout Sederhana</h1></header>
        <nav>
            <a href="<?= base_url('/');?>" class="active">Home</a>
            <a href="<?= base_url('/artikel');?>">Artikel</a>
            <a href="<?= base_url('/about');?>">About</a>
            <a href="<?= base_url('/contact');?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main">
                <?= $this->renderSection('content') ?>
            </section>
            <aside id="sidebar">
                <?= view_cell('App\\Cells\\ArtikelTerkini::render') ?>
                <!-- Widget lainnya -->
            </aside>
        </section>
        <footer><p>&copy; 2021 - Universitas Pelita Bangsa</p></footer>
    </div>
</body>
</html>
```

# Modifikasi File View
Ubah app/Views/home.php agar sesuai dengan layout baru:
```php
<?= $this->extend('layout/main') ?>

<?= $this->section('content') ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>

<?= $this->endSection() ?>
```

View Cell merupakan fitur yang memungkinkan tampilan dipanggil dalam bentuk komponen terpisah yang dapat digunakan kembali. Fitur ini sangat sesuai untuk elemen-elemen yang sering tampil di banyak halaman, seperti menu navigasi, widget, atau sidebar.

# Membuat class View Cell
- Buat folder Cells di dalam app/.
- Buat file ArtikelTerkini.php di dalam app/Cells/ dengan kode berikut:

```php
namespace App\Cells;

use CodeIgniter\View\Cell;
use App\Models\ArtikelModel;

class ArtikelTerkini extends Cell
{
    public function render()
    {
        $model = new ArtikelModel();
        $artikel = $model->orderBy('created_at', 'DESC')->limit(5)->findAll();
        return view('components/artikel_terkini', ['artikel' => $artikel]);
    }
}
```
# Membuat View untuk View Cell
- Buat folder components di dalam app/Views/.
- Buat file artikel_terkini.php:

```php
<h3>Artikel Terkini</h3>
<ul>
<?php foreach ($artikel as $row): ?>
    <li><a href="<?= base_url('/artikel/' . $row['slug']) ?>"><?= $row['judul'] ?></a></li>
<?php endforeach; ?>
</ul>
```

# *Pertanyaan dan Tugas*
1. Sesuaikan data dengan praktikum sebelumnya, perlu melakukan perubahan field pada database dengan menambahkan tanggal agar dapat mengambil data artikel terbaru.
   ```
   ALTER TABLE artikel ADD COLUMN created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP;
   ```
   ![(1)](https://github.com/user-attachments/assets/f52c4be6-9116-4bf6-9312-7ec3160a4b26)

2. Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi.
   
3.  Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi?
   
    View Layout menyediakan metode untuk membangun struktur tampilan yang seragam di seluruh bagian aplikasi. Dengan menggunakan layout, kita cukup membuat satu file sebagai kerangka utama HTML (berisi elemen seperti         header, sidebar, dan footer), lalu konten tiap halaman dapat disisipkan ke dalam kerangka tersebut. Keuntungannya antara lain:
    - Menghemat waktu pengembangan
    - Mempermudah pengelolaan tampilan
    - Mengurangi pengulangan kode

 4. Jelaskan perbedaan antara View Cell dan View biasa.
| Fitur          | View Layout                                     | View Cell                                                |
|----------------|-------------------------------------------------|-----------------------------------------------------------|
| Fungsi         | Template utama untuk struktur tampilan aplikasi | Komponen kecil yang dapat dipanggil di dalam view         |
| Fleksibilitas  | Digunakan untuk keseluruhan halaman             | Digunakan untuk bagian kecil seperti sidebar atau widget  |
| Pemakaian      | `extend()` dan `renderSection()`                | `view_cell()`                                             |
| Contoh         | Struktur website lengkap                        | Widget pencarian, daftar artikel terbaru, dll             |

   5. Ubah View Cell agar hanya menampilkan post dengan kategori tertentu.
      # Langkah:
        Tambahkan kolom kategori pada tabel artikel.
        ```
        ALTER TABLE artikel ADD kategori VARCHAR(50);
        ```
        



  
