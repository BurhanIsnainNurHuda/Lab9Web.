# Lab 9 - PHP Modular

    Nama: Burhan Isnain Nur Huda  
    NIM: 312410226  
    Kelas: TI.24.A.2  
    Mata Kuliah: Pemrograman Web 1

##  Tujuan Praktikum
1. Memahami konsep dasar Modularisasi Program
2. Memahami konsep dasar Fungsi pada PHP
3. Mampu membuat program Modular sederhana menggunakan PHP
4. Mampu mengimplementasikan penggunaan fungsi pada PHP

##  Langkah-Langkah Praktikum

### 1. Persiapan Environment
- Menginstall XAMPP sebagai web server
- Membuat folder `lab9_php_modular` di dalam `htdocs`
- Menyiapkan Visual Studio Code sebagai text editor

### 2. Membuat Struktur Folder Modular
lab9_php_modular/
├── index.php
├── .htaccess
├── config/
│ └── database.php
├── functions/
│ └── helpers.php
├── views/
│ ├── header.php
│ ├── footer.php
│ └── dashboard.php
├── modules/
│ ├── user/
│ │ ├── list.php
│ │ └── add.php
│ └── auth/
│ ├── login.php
│ └── logout.php
└── assets/
├── css/
└── js/


### 3. Implementasi Routing System
Membuat file `index.php` sebagai router utama yang menangani semua request:

    php
    <?php
    error_reporting(E_ALL);
    ini_set('display_errors', 1);
    session_start();

    $base_dir = __DIR__;
    $page = $_GET['page'] ?? 'dashboard';

    $allowed_routes = [
    'dashboard' => 'views/dashboard.php',
    'user/list' => 'modules/user/list.php',
    'user/add' => 'modules/user/add.php',
    'auth/login' => 'modules/auth/login.php',
    'auth/logout' => 'modules/auth/logout.php'
    ];

    if (array_key_exists($page, $allowed_routes)) {
    require $base_dir . '/' . $allowed_routes[$page];
    } else {
    http_response_code(404);
    echo "Halaman tidak ditemukan";
    }
    ?>

### 4. Membuat Template Header dan Footer
File: `views/header.php`

Berisi struktur HTML head dan navigation bar

Menggunakan Bootstrap 5 untuk styling

Responsive design

File: `views/footer.php`

Berisi footer dan script dependencies

Copyright information

### 5. Implementasi Modular Pages
Dashboard (`views/dashboard.php`)

Halaman utama dengan statistik

Navigation cards dengan informasi

User Management (`modules/user/list.php dan modules/user/add.php`)

CRUD interface untuk manajemen user

Form validation dan table display

Authentication (`modules/auth/login.php dan modules/auth/logout.php`)

Login system dengan session management

Logout functionality
