---
title: "Migrasi Blog dari Hugo ke GatsbyJs"
pubDate: 2026-08-14T00:00:54+02:00
lastmod: 2026-08-14T00:00:54+02:00
share:
  enable: true
  link: true
  twitter: true
  reddit: true
  bluesky: true
  hackernews: true

draft: false
license: "MIT"

tags: [astro, gatsbyjs, cloudflare]
categories: [Web]
description: "Bagaimana Hosting Hugo di Cloudflare?"
---
 
Setalah beberapa bulan menggunakan Hugo akhirnya pada tanggal 13 Agustus 2026 Memutuskan untuk migrasi blog ke gatsby. Sebenarnya di Hugo juga banyak pengguna nya dan merupakan CMS Populer di dunia namun ada beberapa kendala yang mana harus membuat saya memindah blog ke Gatsby ini. 

Buat yang belum tau apa sih itu GatsbyJs ini? Sebenarnya di era sekarang banyak sekali CMS blog yang bisa kalian pakai mulai dari Hugo, Astro, NextJs dan masih banyak lagi namun yang saya sebautkan ini adalah CMS populer yang banyak dipakai oleh Devoloper Dunia. 

## Apa itu GatsbyJs? 

GatsbyJS adalah framework sumber terbuka (open-source) berbasis React yang digunakan untuk membuat situs web dan aplikasi web yang sangat cepat dengan teknik [Static Site Generation](https://www.sudarblogger.com/articles/cloudflare-pages) (SSG). Framework ini menggabungkan teknologi React, GraphQL, dan Webpack untuk merender halaman menjadi berkas HTML statis demi keamanan dan performa optimal.

Itulah sedikit penjelasan mengenai Gatsby ini. 

Saya sendiri memilih GatsbyJs ini karena terinspirasi dari blog nya teguh.co dimana menggunakan GatsbyJs ini. 

Bagi pemula seperti saya ini tentu bingung ya setting nya akan tetapi enalnya memakai CMS ini sangatlah Open Source ditambah lagi Gratis karena cukup kalian hosting aja file nya di Github dan Cloudflare Pages untuk online nya. 

Namun ada beberapa juga kekurang dari GatsbyJs ini seperti

## Keunggulan dan Kekurangan GastbyJS

### Keunggulan:

- Waktu muat halaman sangat cepat karena menyajikan file statis.
- Sangat baik untuk SEO karena mesin pencari dapat membaca konten HTML dengan mudah.
- Tingkat keamanan tinggi karena tidak memiliki celah dari database atau server tradisional.

### Kekurangan:
- Waktu build (pembuatan ulang) bisa sangat lama jika situs web memiliki ribuan halaman.
- Membutuhkan kurva belajar untuk memahami ekosistem React dan GraphQL. 

[GatsbyJS](https://www.gatsbyjs.com/) ini terkenal akan speed nya karena berbasis SSG yang mana Javascript ini di generate menjadi content HTML Static. Namun di GatsbyJS ini harus mengerti coding agar bisa merombak template yang anda inginkan. 

Berikut ini beberapa perbandingan antara Hugo dan Gatsby. 

Hugo adalah generator situs statis ultra cepat yang ditulis dalam bahasa Go, terkenal karena waktu pembuatannya kurang dari satu detik. Gatsby adalah kerangka kerja web berbasis React yang tangguh yang mengambil data melalui GraphQL, dirancang untuk aplikasi web progresif dinamis yang kaya komponen dan situs konten yang kaya.

## Performa & Kecepatan
- Hugo: Sangat cepat. Membangun ribuan halaman dalam hitungan milidetik menggunakan satu biner yang telah dikompilasi tanpa penambahan dependensi yang berlebihan.
- Gatsby: Waktu build lebih lambat (berkisar dari detik hingga menit) karena menjalankan ekosistem Webpack/Node dan memproses lapisan GraphQL.

Bisa Kalian lihat Speed Test setelah saya menggunakam GastbyJs ini :

Sebenarnya saya sering otak - atik blog ini karena dari awal ingin mencari template Gastby yang open source jadi bisa dikelola setiap saat. 

Saya sendiri ngeblog masih menggunakan HP dan untuk update di blog tentu harus membuka Google Chrome ini. 

## Cara Membuat Situs Website Menggunakan GatsbyJS

Tentu bagi pemula seperti saya akan bingung bagaimana Deploy Gatsby di Cloudflare supaya blog kalian tentu nya bisa online dan aktif tentu nya.

Seblum membuat blog memggunakan Gatsby tentu pertama - tama kalian harus memiliki akun :
- Github (Sebagai Wadah atau Source kalian parkir) 
- Cloudflare (Sebagai Hosting Domain kalian nanti)

Jika kalian belum memiliki kedua ini jadi lebih baik membuat nya dulu. 

### Langkah 1 : Crea Aplication
Kalian masuk aja di Dashboard Cloidflare kemudian pilih Workers & Pages kemudian setelah itu klik Create Aplication

### Langkah 2 : Connect Github

Jika kalian sudah membuat akun github bisa langsung aja di conect aja ke akun cloudflare milik kalian nanti ini akan saling berhubungan untuk edit artikel atau template yang kalian pakai nanti nya. 


### Langkah 3 : Import Repository

Setelah kalian Conect akun kalian maka repository yang ad di akun github milik kalian akan di import ke cloudflare dengan otomatis 

Setelah itu pilih repository mana yang akan kalian buat pada blog kalian nanti. 

### Langkah 4 : Build Setting 

Nah ini yang paling penting dimana kalian harus tau setting build kalian karena di Gatsby setiap theme berbeda tergantung devoloper nya. 

Apabila salah setting maka kalian tidak bisa membuat website kalian menjadi online, jadi sebelum deploy web maka harus lihat confirgurasi dulu theme apa yang di pakai. 
