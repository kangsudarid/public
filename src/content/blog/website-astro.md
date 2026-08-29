---
title: "Situs Web Baru Berbasis Astro"
pubDate: 2026-08-19T00:00:54+02:00
lastmod: 2026-08-19T00:00:54+02:00
share:
  enable: true
  link: true
  twitter: true
  reddit: true
  bluesky: true
  hackernews: true

draft: false
license: "MIT"

tags: [astro, vite, cloudflare, react]
categories: [Web]
description: "Setelah berkelana kesana - kemari akhirnya menjadi pilihan ngeblog adalah Framework Astro"
---

import { Image } from 'astro:assets';
import astroImg from '../../../assets/images/2026/new_website_based_on_astro/websiteku.png';

<Image src={astroImg} 
    alt="Astro Website" 
    widths={[640, 960, 1280, 1600]}
    sizes="(max-width: 768px) 100vw, 900px"
    formats={['avif', 'webp']}
    quality={80}
    loading="lazy"/>

Setalah sekian lama menjacari Framework yang cocok untuk blog kesayangan akhirnya saya menemukan yang pas untuk blog ini. Yups saya sekarang menggunakan Framework Astro dalam pengembangan website pribadi saya ini. 

Mungkin yang pernah berkunjung diblog ini tampilan nya selalu berbeda - beda? itu karena blog ini masih uji coba menggunakan Framework yang populer seperti, Nextjs, Gatsby dan Hugo. 

Dari sekian banyak nya Framework itu akhirnya saya memilih Astro ini. Saya pindah ke SSG ini pada awal tahun dan menggunakan Hugo, Awal kenal dengan AstroJS ini karena sering melihat blog yang open source memggunakan AstroJS ini. 

## Kenapa memilih Astro? 

Astro JS adalah kerangka kerja (framework) web modern sumber terbuka yang dirancang khusus untuk membangun situs web yang cepat, berkinerja tinggi, dan berfokus pada konten.

### Keunggulan Utama
- **Performa Tinggi**: Skor kecepatan bawaan yang sangat optimal karena minimnya JavaScript di sisi klien.
- **Ramah Konten**: Sangat mudah diintegrasikan dengan Markdown, MDX, atau berbagai CMS eksternal.
- **SEO Lebih Baik**: Halaman statis yang matang dirender di server sangat disukai oleh mesin pencari.

Apalagi sekarang Astro 7 sudah keluar dengan beberapa kelebihan nya, tentu membuat website akan lebih cepat dimuat, tentu dengan website cepat dimuat akan membuat pengunjung menjadi betah. 

## Penjelasan Mengenai Astro 7
[Astro.js](https://astro.build/) adalah framework web modern yang terkenal dengan performa tingginya karena menggunakan pendekatan server-first dan arsitektur Islands (mengirimkan JavaScript ke klien hanya jika benar-benar dibutuhkan).

Pada Astro versi 7 (dan pembaruan terbarunya di seri 7.x), tim pengembang berfokus kuat pada peningkatan performa build secara masif, skalabilitas horizontal, dan integrasi fitur-fitur baru yang lebih modern.

Berikut adalah penjelasan mengenai pembaruan dan fitur utama yang dibawa oleh Astro versi 7:

### 1. Performa Super Cepat dengan Kompiler Rust

Astro 7 adalah versi Astro tercepat yang pernah dibuat. Peningkatan ini diraih dengan memindahkan fase bundling yang sebelumnya menjadi leher botol (bottleneck) ke dalam binary bawaan Rust.
 - Kompiler Rust Baru: Kompiler Go yang sebelumnya digunakan telah dipensiunkan, dan Rust kini menjadi satu-satunya kompiler utama.
 - Markdown & MDX: Pemrosesan Markdown dan MDX kini juga ditangani oleh Rust, membuatnya jauh lebih cepat.
 - Queued Rendering: Arsitektur antrean rendering baru membuat fase pembuatan teks HTML statis jauh lebih efisien. Fitur yang awalnya eksperimental ini kini otomatis aktif untuk semua proyek.

### 2. Integrasi Vite 8
Astro 7 berjalan di atas Vite 8, yang merupakan module bundler generasi terbaru. Integrasi ini membawa peningkatan dari sisi kecepatan hot module replacement (HMR) saat proses development dan optimasi hasil akhir build.

### 3. Pembaruan Sistem Routing (Advanced Routing)
Astro 7 memberikan kontrol penuh kepada developer atas request pipeline (alur permintaan web) dengan memperkenalkan file src/fetch.ts.
 - File ini menggunakan pola standar fetch handler yang populer digunakan pada lingkungan edge seperti Cloudflare Workers, Deno, dan Bun.
 - Jika Anda tidak membutuhkan fitur kontrol tingkat lanjut ini, Astro akan tetap bekerja seperti biasa dengan sistem routing berbasis file (file-based routing) tanpa masalah.

### 4. Peningkatan Dukungan untuk AI Agent
Menyesuaikan dengan tren pengembangan aplikasi saat ini, Astro 7 menambahkan fitur yang mempermudah interaksi antara environment development dengan AI:
 - Background Dev Server: Anda dapat menjalankan perintah astro dev `--background` untuk menjalankan server di latar belakang sebagai proses yang terkelola.
 - Deteksi AI Otomatis: Astro dapat mendeteksi ketika ia sedang dijalankan di dalam lingkungan AI agent (seperti AI coding assistant) dan secara otomatis mengaktifkan mode background ini.

### 5. Penghapusan dan Deprekasi (Breaking Changes)
Ada beberapa perubahan besar yang mengharuskan developer melakukan penyesuaian jika melakukan upgrade dari versi 6:
 - Penghapusan `@astrojs/db`: Fitur ini dihentikan. Developer disarankan bermigrasi menggunakan alternatif lain seperti `node:sqlite` (bawaan Node.js v22.5.0+) atau menggunakan ORM seperti Drizzle.
 - Beberapa API dari View Transitions lama telah dihapus atau diganti.

Namun Astro yang saat ini yang saya pakai masih menggunakan versi yang ke 6 dimana belum update ke versi yang lebih baru ini.

## Diupdate Pengembang
Di Astro juga selalu update setiap bulan nya oleh tim devoloper, ditambah lagi di Astro ini juga open source jadi bebas mau bikin website sesuka hati kalian, biasa buat leadingpage, portofolio atau toko online misalnya.

Salah satunya adalah Update [AstroJS 7](https://astro.build/blog/astro-7/) ini yang memiliki banyak fitur menarik 

### Fitur Utama Astro 7
- **Kompiler Rust**: Inti komponen dan pemrosesan ditulis ulang menggunakan Rust untuk mempercepat waktu pembuatan (build) situs hingga 61%.
- **Vite 8**: Menggunakan versi terbaru Vite untuk pengalaman pengembangan (dev server) yang lebih gesit.
- **Markdown & MDX berbasis Rust (Sätteri)**: Pipeline pemrosesan baru yang membuat fitur seperti tabel dan catatan kaki aktif secara bawaan (default) tanpa plugin tambahan.
- **Peningkatan AI & Server Latar Belakang**: Mendukung perintah seperti astro dev `--background` untuk alur kerja agen pengkodean AI.
- **Penyimpanan Cache Rute**: Menyediakan penyedia cache CDN (Netlify, Vercel, Cloudflare) dan memori cache untuk efisiensi rute.

## Performa AstroJS
Performa Astro.js sangat tinggi karena mengirimkan HTML murni ke browser secara default tanpa menyertakan kode JavaScript yang tidak penting bagi pengguna. 

Tidak hanya itu saja dari segi SEO pun Astro tidak kalah dengan yang lain, apalagi AstroJS ini sendiri menerapkan pre-reading yang mana murni HTML tanpa ada nya Javascript.

## Blog Masih Pengembangan
Karena masih belajar mengenai AstroJS jadi blog ini masih pengembangn, karena di AstroJS ini bisa otak - atik HTML sesuka kalian tanpa ada nya batasan, dalam 2 aja blog ini sudah dimodifikasi. 


