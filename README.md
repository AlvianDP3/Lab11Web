# Praktikum 11: PHP Framework (Codeigniter)

# Tujuan
1. Mahasiswa mampu memahami konsep dasar Framework.
2. Mahasiswa mampu memahami konsep dasar MVC.
3. Mahasaswa mampu membuat program sederhana menggunakan Framework
Codeigniter 4.

# Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.

![1](https://user-images.githubusercontent.com/56244029/122474738-d3a5f680-cfed-11eb-8171-eeb55d0c70d2.png)

2. Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)

![2](https://user-images.githubusercontent.com/56244029/122474805-e8828a00-cfed-11eb-9c5e-f56d410aa6c8.png)

3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

# Langkah-langkah Praktikum
# Persiapan
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi
pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan
pengembangan Codeigniter 4.
Berikut beberapa ekstensi yang perlu diaktifkan:
• php-json ekstension untuk bekerja dengan JSON;
• php-mysqlnd native driver untuk MySQL;
• php-xml ekstension untuk bekerja dengan XML;
• php-intl ekstensi untuk membuat aplikasi multibahasa;
• libcurl (opsional), jika ingin pakai Curl.

Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini

![3](https://user-images.githubusercontent.com/56244029/122474979-28497180-cfee-11eb-9f0c-e92da75aefcb.png)

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.

![4](https://user-images.githubusercontent.com/56244029/122475611-1b794d80-cfef-11eb-8ae5-ffddc2bbc88c.png)

# Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara
manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara
manual.
• Unduh Codeigniter dari website https://codeigniter.com/download
• Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
• Ubah nama direktory framework-4.x.xx menjadi ci4.
• Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/

![5](https://user-images.githubusercontent.com/56244029/122476129-e8838980-cfef-11eb-9706-387731cfa5e6.png)

# Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk
mengakses CLI buka terminal/command prompt.

![6](https://user-images.githubusercontent.com/56244029/122476323-300a1580-cff0-11eb-9698-4fe10ee60ae9.png)

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)
Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:
```
php spark
```

![7](https://user-images.githubusercontent.com/56244029/122476627-bd4d6a00-cff0-11eb-9826-70edc466ee46.png)

# Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk
mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.
Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan
pesan kesalahan seperti berikut.

![8](https://user-images.githubusercontent.com/56244029/122476794-f38ae980-cff0-11eb-84c6-00de8f9768f1.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis
errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi
pada environment variable CI_ENVIRINMENT menjadi development.

![9](https://user-images.githubusercontent.com/56244029/122477056-58464400-cff1-11eb-8a13-c20b378089e5.png)

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable CI_ENVIRINMENT menjadi development.

# Struktur Direktori
Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori
dan file yang ada. Buka pada Windows Explorer atau dari Visual Studio Code ->
Open Folder.
Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya.
• .github folder ini kita butuhkan untuk konfigurasi repo github, seperti konfigurasi
untuk build dengan github action;
• app folder ini akan berisi kode dari aplikasi yang kita kembangkan;
• public folder ini berisi file yang bisa diakses oleh publik, seperti file index.php,
robots.txt, favicon.ico, ads.txt, dll;
• tests folder ini berisi kode untuk melakukan testing dengna PHPunit;
• vendor folder ini berisi library yang dibutuhkan oleh aplikasi, isinya juga termasuk
kode core dari system CI.
• writable folder ini berisi file yang ditulis oleh aplikasi. Nantinya, kita bisa pakai
untuk menyimpan file yang di-upload, logs, session, dll.
Sedangkan file-file yang berada pada root direktori CI sebagai berikut.
• .env adalah file yang berisi variabel environment yang dibutuhkan oleh aplikasi.
• .gitignore adalah file yang berisi daftar nama file dan folder yang akan diabaikan
oleh Git.
• build adalah script untuk mengubah versi codeigniter yang digunakan. Ada versi
release (stabil) dan development (labil).
• composer.json adalah file JSON yang berisi informasi tentang proyek dan daftar
library yang dibutuhkannya. File ini digunakan oleh Composer sebagai acuan.
• composer.lock adalah file yang berisi informasi versi dari libraray yang digunakan
aplikasi.
• license.txt adalah file yang berisi penjelasan tentang lisensi Codeigniter;
• phpunit.xml.dist adalah file XML yang berisi konfigurasi untuk PHPunit.
• README.md adalah file keterangan tentang codebase CI. Ini biasanya akan
dibutuhkan pada repo github atau gitlab.
• spark adalah program atau script yang berfungsi untuk menjalankan server,
generate kode, dll.

![10](https://user-images.githubusercontent.com/56244029/122477434-e6222f00-cff1-11eb-97cc-b4eb6e4d4697.png)

Fokus kita pada folder app, dimana folder tersebut adalah area kerja kita untuk membuat aplikasi. Dan folder public untuk menyimpan aset web seperti css, gambar,
javascript, dll.

# Memahami Konsep MVC
Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-Controller. MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan. Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan diletakkan pada direktori View.

Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.

Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun sumber lainnya.

View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan
dengan html dan css.

Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian diproses dengan menghubungkan bagian model dan view.

# Routing dan Controller

Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4,
routing bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. 

Controller adalah class atau script yang bertanggung jawab merespon sebuah request.

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk meudian oleh router tesebut diarahkan ke Controller. Router terletak pada file app/config/Routes.php

![11](https://user-images.githubusercontent.com/56244029/122478085-f7b80680-cff2-11eb-8288-ebbf381d26d6.png)

Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
Contoh:
```
$routes->get('/', 'Home::index');
```
Kode tersebut akan mengarahkan rute untuk halaman home.

# Membuat Route Baru.
Tambahkan kode berikut di dalam Routes.php
```
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.
```
php spark routes
```
![12](https://user-images.githubusercontent.com/56244029/122478396-86c51e80-cff3-11eb-821f-ed5e503928d2.png)

 Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about

![12](https://user-images.githubusercontent.com/56244029/122478516-baa04400-cff3-11eb-871e-2c93184cb7ef.png)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih
dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

# Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php
pada direktori Controller kemudian isi kodenya seperti berikut.
```
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
```
Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah dapat diakses.

![13](https://user-images.githubusercontent.com/56244029/122478881-634ea380-cff4-11eb-97ea-5fca31f45cf4.png)

# Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true
menjadi false.
```
$routes->setAutoRoute(true);
```
Tambahkan method baru pada Controller Page seperti berikut.
```
public function tos()
{
echo "ini halaman Term of Services";
}
```
![14](https://user-images.githubusercontent.com/56244029/122479091-bd4f6900-cff4-11eb-881e-b66e4fd0ba36.png)

# Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi
kodenya seperti berikut.
```
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
```
![15](https://user-images.githubusercontent.com/56244029/122479514-66965f00-cff5-11eb-898f-e1fb89883e8d.png)


# Membuat Layout Web dengan CSS
Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset
css dan javascript terletak pada direktori public.

Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout. Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![16](https://user-images.githubusercontent.com/56244029/122480261-b7f31e00-cff6-11eb-880c-66165e395431.png)

Kemudian buat folder template pada direktori view kemudian buat file header.php dan
footer.php

File app/view/template/header.php
```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title><?= $title; ?></title>
<link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
<div id="container">
<header>
<h1>Layout Sederhana</h1>
</header>
<nav>
<a href="<?= base_url('/');?>" class="active">Home</a>
<a href="<?= base_url('/artikel');?>">Artikel</a>
<a href="<?= base_url('/about');?>">About</a>
<a href="<?= base_url('/contact');?>">Kontak</a>
</nav>
<section id="wrapper">
<section id="main">
```
File app/view/template/footer.php
```
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
<p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada
tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis.
Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
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
Kemudian ubah file app/view/about.php seperti berikut.
```
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```
Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![17](https://user-images.githubusercontent.com/56244029/122480656-71ea8a00-cff7-11eb-8e6a-0a9044c0a614.png)

# Pertanyaan dan Tugas
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.


# Update Controller (page.php)

![page](https://user-images.githubusercontent.com/56244029/122481284-a448b700-cff8-11eb-84bf-01965a94e636.png)

# Menu About

![about](https://user-images.githubusercontent.com/56244029/122481321-b3c80000-cff8-11eb-9a62-0edbe663036c.png)

# Menu Artikel

![artikel](https://user-images.githubusercontent.com/56244029/122481352-bcb8d180-cff8-11eb-89d6-a8dbb5f63acd.png)


![18](https://user-images.githubusercontent.com/56244029/122481514-09041180-cff9-11eb-9438-05b7617f2f70.png)

# Menu Contact

![contact](https://user-images.githubusercontent.com/56244029/122481570-1c16e180-cff9-11eb-9357-82fbf20e9162.png)

![21](https://user-images.githubusercontent.com/56244029/122481779-86c81d00-cff9-11eb-8e50-45b01d8406a1.png)

# Praktikum 12: Framework Lanjutan (CRUD)

# Buat Database
```
CREATE DATABASE lab_ci4;
```
# Buat Tabel
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
# Konfigurasi koneksi database
Selanjutnya membuat konfigurasi untuk menghubungkan dengan database server.
Konfigurasi dapat dilakukan dengan du acara, yaitu pada file app/config/database.php
atau menggunakan file .env. Pada praktikum ini kita gunakan konfigurasi pada file .env.

![1](https://user-images.githubusercontent.com/56244029/123343463-061a9b00-d57c-11eb-9c01-72762f9801a0.png)

# Membuat Model
Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada
direktori app/Models dengan nama ArtikelModel.php

![2](https://user-images.githubusercontent.com/56244029/123343755-99ec6700-d57c-11eb-981d-b97c57538da3.png)

# Membuat Controller
Buat Controller baru dengan nama Artikel.php pada direktori app/Controllers.

![3](https://user-images.githubusercontent.com/56244029/123344380-ef754380-d57d-11eb-93ca-9bd5e2b65b6b.png)

# Membuat View
Buat direktori baru dengan nama artikel pada direktori app/views, kemudian buat file
baru dengan nama index.php.

![4](https://user-images.githubusercontent.com/56244029/123344527-3bc08380-d57e-11eb-8bab-2ce331288a34.png)

Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

![5](https://user-images.githubusercontent.com/56244029/123344612-6d394f00-d57e-11eb-8cbf-b81d7f0c55f1.png)

Belum ada data yang diampilkan. Kemudian coba tambahkan beberapa data pada database agar dapat ditampilkan datanya.

![9](https://user-images.githubusercontent.com/56244029/123345387-22b8d200-d580-11eb-961e-e41ab4a1b83e.png)

Refresh kembali browser, sehingga akan ditampilkan hasilnya.

![6](https://user-images.githubusercontent.com/56244029/123344920-16804500-d57f-11eb-9f1d-4532b1f2a121.png)

# Membuat Tampilan Detail Artikel
Tampilan pada saat judul berita di klik maka akan diarahkan ke halaman yang berbeda.
Tambahkan fungsi baru pada Controller Artikel dengan nama view().

![7](https://user-images.githubusercontent.com/56244029/123345193-bf2ea480-d57f-11eb-909c-4b06197595b8.png)

# Membuat View Detail
Buat view baru untuk halaman detail dengan nama app/views/artikel/detail.php.

![8](https://user-images.githubusercontent.com/56244029/123345341-0f0d6b80-d580-11eb-8341-d576b38e67bc.png)

# Membuat Routing untuk artikel detail
Buka Kembali file app/config/Routes.php, kemudian tambahkan routing untuk artikel
detail.

![10](https://user-images.githubusercontent.com/56244029/123345504-6ca1b800-d580-11eb-9d12-13e70c6b718e.png)

![11](https://user-images.githubusercontent.com/56244029/123345601-a246a100-d580-11eb-8d4b-aeb0a8999e83.png)

# Membuat Menu Admin
Menu admin adalah untuk proses CRUD data artikel. Buat method baru pada
Controller Artikel dengan nama admin_index().

dan Selanjutnya buat view untuk tampilan admin dengan nama admin_index.php

![12](https://user-images.githubusercontent.com/56244029/123346061-9f987b80-d581-11eb-8918-8042a5f8dfd9.png)

![13](https://user-images.githubusercontent.com/56244029/123346047-9a3b3100-d581-11eb-9888-78bf317e7c9a.png)

Tambahkan routing untuk menu admin seperti berikut:
```
$routes->group('admin', function($routes) {
$routes->get('artikel', 'Artikel::admin_index');
$routes->add('artikel/add', 'Artikel::add');
$routes->add('artikel/edit/(:any)', 'Artikel::edit/$1');
$routes->get('artikel/delete/(:any)', 'Artikel::delete/$1');
});
```

Setelah itu buat template header dan footer baru untuk Halaman Admin. Buat file baru dengan nama admin_header.php pada direktori app/view/template

![14](https://user-images.githubusercontent.com/56244029/123346473-9bb92900-d582-11eb-93b5-b5f80fb9102c.png)

Akses menu admin dengan url http://localhost:8080/admin/artikel

![15](https://user-images.githubusercontent.com/56244029/123346577-d622c600-d582-11eb-9eea-f2ab6c2fbd79.png)

# Menambah Data Artikel
Tambahkan fungsi/method baru pada Controller Artikel dengan nama add().
```
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
```
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

![16](https://user-images.githubusercontent.com/56244029/123346805-0b2f1880-d583-11eb-8b4b-23fcfb3adf54.png)

# Mengubah Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama edit()
```
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
```
<?= $this->include('template/admin_header'); ?>
<h2><?= $title; ?></h2>
<form action="" method="post">
<p>
<input type="text" name="judul" value="<?= $data['judul'];?>" >
</p>
<p>
<textarea name="isi" cols="50" rows="10"><?=
$data['isi'];?></textarea>
</p>
<p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>
<?= $this->include('template/admi!
n_footer'); ?>
```

![17](https://user-images.githubusercontent.com/56244029/123348247-6fea7300-d583-11eb-8d17-9ec20b92f0c2.png)

# Menghapus Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama delete().
```
public function delete($id)
{
$artikel = new ArtikelModel();
$artikel->delete($id);
return redirect('admin/artikel');
}
```
# Praktikum 13: Framework Lanjutan (Modul Login)

# Tujuan
1. Mahasiswa mampu memahami konsep dasar Auth dan Filter.
2. Mahasiswa mampu memahami konsep dasar Login System.
3. Mahasaswa mampu membuat modul login menggunakan Framework Codeigniter 4.
# Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab11_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
Langkah-langkah Praktikum
Persiapan.
Untuk memulai membuat modul Login, yang perlu disiapkan adalah database server
menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui
XAMPP.
# Membuat Tabel: User Login

![2](https://user-images.githubusercontent.com/56244029/124299875-1f2cd880-db88-11eb-95fc-b7054833f000.png)

# Membuat Tabel User
```
CREATE TABLE user (
id INT(11) auto_increment,
username VARCHAR(200) NOT NULL,
useremail VARCHAR(200),
userpassword VARCHAR(200),
PRIMARY KEY(id)
);
```

# Membuat Model User
Selanjutnya adalah membuat Model untuk memproses data Login. Buat file baru pada
direktori app/Models dengan nama UserModel.php
```
<?php
namespace App\Models;
use CodeIgniter\Model;
class UserModel extends Model
{
protected $table = 'user';
protected $primaryKey = 'id';
protected $useAutoIncrement = true;
protected $allowedFields = ['username', 'useremail', 'userpassword'];
}
```

# Membuat Controller User
Buat Controller baru dengan nama User.php pada direktori app/Controllers.
Kemudian tambahkan method index() untuk menampilkan daftar user, dan method
login() untuk proses login.
```
<?php
namespace App\Controllers;
use App\Models\UserModel;
class User extends BaseController
{
public function index()
{
$title = 'Daftar User';
$model = new UserModel();
$users = $model->findAll();
return view('user/index', compact('users', 'title'));
}
public function login()
{
helper(['form']);
$email = $this->request->getPost('email');
$password = $this->request->getPost('password');
if (!$email)
{
return view('user/login');
}
$session = session();
$model = new UserModel();
$login = $model->where('useremail', $email)->first();
if ($login)
{
$pass = $login['userpassword'];
if (password_verify($password, $pass))
{
$login_data = [
'user_id' => $login['id'],
'user_name' => $login['username'],
'user_email' => $login['useremail'],
'logged_in' => TRUE,
];
$session->set($login_data);
return redirect('admin/artikel');
}
else
{
$session->setFlashdata("flash_msg", "Password salah.");
return redirect()->to('/user/login');
}
}
else
{
$session->setFlashdata("flash_msg", "email tidak terdaftar.");
return redirect()->to('/user/login');
}
}
}
```

# Membuat View Login
Buat direktori baru dengan nama user pada direktori app/views, kemudian buat file
baru dengan nama login.php.
```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Login</title>
<link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
<div id="login-wrapper">
<h1>Sign In</h1>
<?php if(session()->getFlashdata('flash_msg')):?>
<div class="alert alert-danger"><?=
session()->getFlashdata('flash_msg') ?></div>
<?php endif;?>
<form action="" method="post">
<div class="mb-3">
<label for="InputForEmail" class="form-label">Email
address</label>
<input type="email" name="email" class="form-control"
id="InputForEmail" value="<?= set_value('email') ?>">
</div>
<div class="mb-3">
<label for="InputForPassword"
class="form-label">Password</label>
<input type="password" name="password"
class="form-control" id="InputForPassword">
</div>
<button type="submit" class="btn
btn-primary">Login</button>
</form>
</div>
</body>
</html>
```
# Membuat Database Seeder
Database seeder digunakan untuk membuat data dummy. Untuk keperluan ujicoba modul
login, kita perlu memasukkan data user dan password kedaalam database. Untuk itu buat
database seeder untuk tabel user. Buka CLI, kemudian tulis perintah berikut:
php spark make:seeder UserSeeder
Selanjutnya, buka file UserSeeder.php yang berada di lokasi direktori
/app/Database/Seeds/UserSeeder.php kemudian isi dengan kode berikut:
```
<?php
namespace App\Database\Seeds;
use CodeIgniter\Database\Seeder;
class UserSeeder extends Seeder
{
public function run()
{
$model = model('UserModel');
$model->insert([
'username' => 'admin',
'useremail' => 'admin@email.com',
'userpassword' => password_hash('admin123', PASSWORD_DEFAULT),
]);
}
}
```
Selanjutnya buka kembali CLI dan ketik perintah berikut:
```
php spark db:seed UserSeeder
```
Uji Coba Login
Selanjutnya buka url http://localhost:8080/user/login seperti berikut:

![5](https://user-images.githubusercontent.com/56244029/124300549-e6d9ca00-db88-11eb-87d1-6d0fbb18ad81.png)

# Menambahkan Auth Filter
Selanjutnya membuat filer untuk halaman admin. Buat file baru dengan nama Auth.php
pada direktori app/Filters.
```
<?php namespace App\Filters;
use CodeIgniter\HTTP\RequestInterface;
use CodeIgniter\HTTP\ResponseInterface;
use CodeIgniter\Filters\FilterInterface;
class Auth implements FilterInterface
{
public function before(RequestInterface $request, $arguments = null)
{
// jika user belum login
if(! session()->get('logged_in')){
// maka redirct ke halaman login
return redirect()->to('/user/login');
}
}
public function after(RequestInterface $request, ResponseInterface
$response, $arguments = null)
{
// Do something here
}
}
```
Selanjutnya buka file app/Config/Filters.php tambahkan kode berikut:
'auth' => App\Filters\Auth::class 

![6](https://user-images.githubusercontent.com/56244029/124301119-9020c000-db89-11eb-9024-0b4af27caa48.png)

Selanjutnya buka file app/Config/Routes.php dan sesuaikan kodenya.

![7](https://user-images.githubusercontent.com/56244029/124301428-03c2cd00-db8a-11eb-8f0b-2b9b32be96da.png)

Percobaan Akses Menu Admin
Buka url dengan alamat http://localhost:8080/admin/artikel ketika alamat tersebut
diakses maka, akan dimuculkan halaman login.

![5](https://user-images.githubusercontent.com/56244029/124301719-64520a00-db8a-11eb-8ce7-c81ff11bbe44.png)





