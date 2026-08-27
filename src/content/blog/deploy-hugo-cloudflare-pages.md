---
title: "Deploy Hugo to Cloudflare Pages"
pubDate: 2026-01-30T21:27:55+02:00
lastmod: 2026-01-30T21:27:55+02:00
share:
  enable: true
  link: true
  twitter: true
  reddit: true
  bluesky: true
  hackernews: true

draft: false
license: "MIT"

tags: [cloudflare, hugo, themes]
categories: [Web]
description: "Cara Hosting Hugo di Cloudflate Pages 2026"
---

Hugo adalah CMS Blog yang populer dikalangan devoloper, saya saat pindah ke Static Site Generator juga menggunakan Hugo ini, bahkan Mas Sugeng pun memakai Hugo untuk blog nya. 

Ada yang sudah tau mengenai Hugo ini? Jika belum tau atau belum akan jelaskan sedikit mengenai Hugo ini. 

## Apa Itu Hugo? 

Hugo adalah generator situs statis (static site generator) sumber terbuka yang ditulis dalam bahasa pemrograman Go (Golang). Alat ini mengubah berkas konten Markdown dan template menjadi halaman web HTML statis yang sangat cepat, aman, dan tidak memerlukan basis data (database). 

## Apa itu Clouflare Pages? 

Cloudflare Pages adalah platform hosting berbasis JAMstack yang disediakan oleh Cloudflare. Platform ini memungkinkan para pengembang web untuk membuat, menguji, dan menyebarkan (deploy) situs web statis maupun aplikasi front-end secara cepat, aman, dan gratis melalui jaringan global edge network milik Cloudflare.

Sebenarnya tidak hanya cloudflare pages aja yang populer ada juga vercel, Netlify yang bisa kalian gunakan untuk hosting, tapi bagi saya yang mudah itu di Cloudflate selain itu masih ribet untuk deploy nya. 

## Deploy Hugo di Cloudflare Pages

Karena disini saya memakai Handphone untuk deploy Hugo jadi sebelum nya sudah memiliki theme hugo ini dahulu, theme hugo yang pernah saya pakai ini merupakaan theme karya ardiantara.

> Atau bisa clone git dibawah ini :

```bash
git clone --depth 1 https://github.com/ardianta/blog.git ardianta-blog
```

Karena ada beberapa alasan maka dari itu pindah atau migrasi blog, sebenarnya CMS banyak sekali untuk ngeblog ada AstroJS, NextJS, GatsbyJS dan masih banyak lagi. 

- Masuk ke Cloudflare
- Pilih Workers and Pages
- Connect Akun Git Milik Kalian
- Setelah Connect Pilih Repository yang sudah di simpan tadi
- Pilih Hugo untuk Build nya `hugo --minify`
- Build Directory nya pilih aja `Public`
- Klik Save and Deploy

Tunggu beberapa menit hingga proses selesai biasanya membutuhkan waktu 5 menitan untuk deplay nya. 

Apabila sudah selesai pilih aja `Continue Project`. 

### Konfigurasi Hugo

```bash
baseurl: 'https://www.ardianta.com'
title: Ahmad Muhardian
theme: ardianta
disqusShortname: ardianta
services:
  googleAnalytics:
  ID: UA-80537197-1
  disqus:
    shortname: ardianta
permalinks:
  page: '/:slug/'
params:
  author: Dian
  email: web@ardianta.com
  description: 'Hello, saya Dian. Blog ini belum jadi. Sabar ya...'
  social:
    github: https://github.com/ardianta
    linkedin: https://linkedin.com/in/ardianta
    dribbble: https://dribbble.com/ardianta
frontmatter:
  date:
    - date
    - publishDate
    - lastmod
  lastmod:
    - ':git'
    - lastmod
    - date
    - publishDate
  publishDate:
    - publishDate
    - date
  expiryDate:
    - expiryDate
menu:
  main:
    - identifier: about
      name: About
      url: /about/
      weight: 1
    - identifier: art
      name: Art
      url: 'https://ardiantapargo.deviantart.com/'
      weight: 2
    - identifier: twitter
      name: Twitter
      url: 'https://twitter.com/ardiantapargo'
      weight: 3
    - identifier: github
      name: Github
      url: 'https://github.com/ardianta'
      weight: 4
    - identifier: rss
      name: RSS
      url: 'http://feeds.feedburner.com/ardianta'
      weight: 5
privacy:
  youTube:
    disable: false
    privacyEnhanced: false
  instagram:
    disable: false
    simple: fals
markup:
  goldmark:
    renderer:
      unsafe: true
```

### Cara Posting Arikel Hugo

``` bash
title: "1 Day 1 Draw Challenge!"
slug: 1d1d
date: 2019-06-06T19:44:01+08:00
draft: false
type: post
tags:
    - Drawing
image: "/img/1d1d/08.webp"
description: "Iseng-iseng aja!"
```

> Apa darisini masih ada yang kebingungan? 

Kedepan nya blog ini akan berbagi tutorial mengenai AstroJS, Hugo dan NextJS sesuai pengalaman saya dapat waktu otak atik blog ini. 
