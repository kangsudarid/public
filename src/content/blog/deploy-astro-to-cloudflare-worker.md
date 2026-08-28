---
title: "Cara Deploy Astro di Cloudflare Worker"
pubDate: 2026-08-28T18:27:55+02:00
lastmod: 2026-08-28T18:27:55+02:00
share:
  enable: true
  link: true
  twitter: true
  reddit: true
  bluesky: true
  hackernews: true

draft: false
license: "MIT"

tags: [astro, hugo, adsense]
categories: [Web, Tutorial]
description: "Bagaimana Deploy Astro di Cloudflare Worker, apakah itu populer di kalangan devoloper?"
---

Mencoba hal baru di website ini, kali ini mencoba menggunakan Cloudflare Worker yang mana populer di kalangan devoloper luar, saya sendiri sering mencari themes yang pas untuk website ini. 

Seperti kalian tau kalau beberapa hari lalu saya [Migrasi ke Astro](https://www.sudarblogger.com/blog/migrasi-ke-astrojs/) oleh karena itu saya akan berbagi tutorial bagaimana deploy Astro di cloudflare ini. 

Buat yang belum tau apa sih yang itu Cloudflare Worker beda kah dengan Cloudflare Pages, tentu itu jadi pertanyaan menurut saya pribadi dan rekan - rekan yang baru terjun di dunia blogger. 

## Apa itu Cloudflare Worker? 
Cloudflare Workers adalah platform eksekusi kode serverless (tanpa server) yang memungkinkan pengembang menjalankan kode di jaringan global (edge network) milik Cloudflare.  

​Berbeda dari server tradisional atau cloud provider biasa yang menempatkan kode di satu lokasi pusat data, Cloudflare Workers mengeksekusi kode di server edge yang paling dekat dengan lokasi pengguna.
​
### Keunggulan & Cara Kerja Utama
- ​**Latensi Sangat Rendah**: Karena kode berjalan di ratusan pusat data Cloudflare di seluruh dunia, permintaan (request) dari pengguna langsung diproses di kota/negara terdekat tanpa perlu memutar ke server asal.  
- **​Berbasis V8 Isolate**: Workers tidak menggunakan virtual machine atau kontainer Docker yang berat. Workers menggunakan V8 Isolate (teknologi yang sama di Google Chrome), membuat waktu mulai (cold start) nyaris 0 milidetik.
- **​Otomatis Berskala (Auto-scaling)**: Dapat menangani puluhan hingga jutaan permintaan secara otomatis tanpa perlu mengonfigurasi atau mengelola server.
- **Bahasa Utama**: Mendukung JavaScript, TypeScript, Rust, C/C++, dan WebAssembly. 

Apa beda nya Cloudflare Pages sama Cloudflare Worker? Tentu itu juga yang menjadi pertanyaan kalian. Oke kali ini saya akan jelaskan kepada kalian supaya lebih paham

## Perbedaan Cloudflare Pages dan Clouflare Worker
Keduanya sama-sama bagus, tetapi dirancang untuk tujuan utama yang berbeda. Pages lebih baik untuk situs web/aplikasi visual, sedangkan Workers lebih baik untuk logika backend/API.

​Pilihan tergantung pada apa yang ingin Anda bangun:

| Fitur/Pertimbangan | Clouflare Pages | Clouflare Worker |
| :--- | :--- | :--- |
| Fokus Utama | Aplikasi Frontend, Situs Statis, & Full-Stack (Jamstack). | Backend API, Middleware, & Edge Computing. |
| Pengembangan (DX) | Sangat mudah. Hubungkan repository GitHub/GitLab, otomatis deploy saat `git push`. | Menggunakan CLI (wrangler) untuk menulis dan mengunggah kode backend secara langsung. |
| Frameworks | Sangat cocok untuk React, Next.js, Vue, Nuxt, Astro, Svelte, dll. | Tidak ideal untuk rendering UI framework rumit secara langsung (kecuali API backend-nya). |
| Routing | Berbasis file/folder (seperti folder `/public` atau functions/). | Berbasis kode (programmatic routing menggunakan kode JavaScript/TypeScript). |
| Fitur Serverless | Mendukung Pages Functions (di balik layar memanfaatkan Workers). | Menggunakan Workers murni. |

Nah Sekarang sudah tau kan perbedaan nya. Oke sekarang kita lanjut ke intinya yaitu Deploy Astro di Cloflare Worker

Jika kalian ingin deploy Astro dengan theme mirip yang saya pakai kalian bisa langsing aja copy git aja di bawah ini

## Git Github Project

```bash title="git"
git clone git@github.com:vukilis/website.git
```
Tunggu hingga proses selesai clone nya sekarang akan pergi ke Cloudflare untuk membuat website nya

## Konfirmasi Wangler.toml

```bash title="wrangler.toml"
name = "website"
compatibility_date = "2026-08-20"
compatibility_flags = ["nodejs_compat"]


[assets]
directory = "./dist"
not_found_handling = "404-page"

[placement]
mode = "smart"

[observability]
enabled = false
head_sampling_rate = 1

[observability.logs]
enabled = true
head_sampling_rate = 1
persist = true
invocation_logs = true

[observability.traces]
enabled = false
persist = true
head_sampling_rate = 1
```

Pastikan nama ini sama url `website.sudarblogger.worker.dev` agar saat build tidak ada yang error. 

## Building
Untuk yang ingin menggunakan local host maka untuk build nya seperti ini

```bash
pnpm build
```
## Previewing
Atau kalian ingin review website kalian disitus local host bisa lakukan seperti ini untuk build nya. 
```bash
pnpm preview --host 0.0.0.0
```
## Alur Kerja Worker

Berikut ini adalah alur kerja proses worker

```bash
git clone https://github.com/kpab/website-v2.git
cd website
nix develop                   # enter the Nix shell
pnpm install                  # install dependencies
pnpm dev --host 0.0.0.0       # start developing
# ... make changes ...
pnpm build                    # verify the build works
pnpm preview --host 0.0.0.0   # preview production build locally
```
Tunggu hingga prosesnya maka website kalian bisa tampil langsung dengan server local. 

Apakah di Clouflare Worker bisa custom domain? Jawabanya tentu bisa dan proses nya itu sangatlah gampang. 

## Custom Domain di Cloudflare Worker

Berikut ini adalah tutorial custome domain di worker cloudflare
- Masuk Worker & Page
- Setelah itu pilih Project Worker kalian klik View Setting pada titik tiga di kanan
- Pilih Domain,  klik Add Domain
- Selanjutnya pilih domain yang ingin di Custom
- Tunggu Prosesnya selesai

## Penutup
Dengan tutorial ini apa masih bingung, jika kebingungan bisa langsung tanyakan aja di kolom komentar yang ada di bawah ya. 

