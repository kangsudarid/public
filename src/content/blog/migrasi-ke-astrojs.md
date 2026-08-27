---
title: "Migrasi dari GatsbyJs ke AstroJS"
pubDate: 2026-08-26T00:25:54+02:00
lastmod: 2026-08-26T00:25:54+02:00
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
description: "AstroJS membaut blog menjadi cepat karena meminimalkan Javascript"
---


Setelah beberapa hari memggunakan [GastbyJS](https://www.sudarblogger.com/blog/gatsbyjs/) akhir saya pindah lagi ke AstroJS sebagai piliham Platfrom blog saya saat ini, mungkin kalian berfikir nih orang kenapa gonta - ganti mulu ya? hehehe

Dari segi SEO aku akui kalau GatsbyJS ini saat cocok apalagi saat memindah blog banyak artikel dalam hitungan jam ke index oleh Google, bahkan hampir semua artikel saya sudah ke index semua oleh Google. 

> Lalu kenpaa pindah mas? bukannya sayang banget artikelnya sudah terindex lalu akan terjadi error di mesin pencari! 

Mungkin kalian berfikir seperti itu, karena melihat dari blog mas sugeng juga memindah blog nya jadi tidak ada salahnya untuk mencoba, kalaupun link nya nanti error mungkin hanya beberapa saja. 

## Apa sih AstroJS? 

Astro.js adalah sebuah web framework modern yang dirancang khusus untuk membangun situs web yang cepat dan berfokus pada konten dengan mengirimkan JavaScript minimal ke browser.

Apabila menggunakan AstroJS ini tentu akan meminimalkan penggunaan Javascript dan akan membuat blog menjadi kecang saat di akses. 

Alsan mengapa saya memilih AstoJS ini :
- **Arsitektur Pulau** (Islands Architecture): Astro merender sebagian besar halaman menjadi HTML statis yang ringan. Bagian halaman yang butuh interaksi (seperti tombol interaktif atau kolom komentar) dipisahkan menjadi "pulau" kecil yang hanya memuat JavaScript saat benar-benar diperlukan.
- **Bebas Memilih Framework UI** (Bring Your Own Framework): Anda tetap bisa menggunakan komponen dari library populer seperti React, Vue, Svelte, atau Solid.js di dalam proyek Astro Anda.
- **Performa Tinggi Secara Bawaan** (Zero JavaScript by Default): Tanpa konfigurasi tambahan, Astro menghapus semua kode JavaScript yang tidak diperlukan di sisi klien sehingga halaman termuat dengan sangat cepat dan ramah SEO.

## Hosting di Clouflare Pages
Sebenarnya ada banyak pilihan hlating yang populer seperti Vercel, Akan tetapi saya tetap milih Cloudflare sebagai hosting blog saya ini, Ada beberapa alasan mengapa saya tetap milih Cloudflare : 

- **Biaya Lebih Rendah**: Paket gratis Cloudflare Pages sudah sangat memadai untuk kebutuhan saya.
- **Integrasi DNS & Proxy**: Integrasi lancar dengan layanan DNS dan proxy Cloudflare yang sudah saya gunakan.
- **Cloudflare Rules**: Memudahkan pengaturan redirect dan transformasi.
- **Point of Presence (POP) di Indonesia**: Kehadiran server Cloudflare di Indonesia menjamin kecepatan loading yang lebih baik untuk pengunjung lokal.
- **Kompatibilitas**: Vercel dan Netlify tidak merekomendasikan penggunaan proxy Cloudflare, sementara saya ingin tetap menggunakan layanan Cloudflare lainnya.
- **Uptime yang Andal**: Tidak perlu diragukan lagi, uptime Cloudflare sangat bisa diandalkan, memberikan keamanan bahwa website akan selalu tersedia bagi pengunjung.

## AstroJS vs GatsbyJS
Agar tidak salah pilih CMS maka disini mari kita badingkan Astrojs dengan GatsbyJs ini :

**​Keunggulan Astro.js:**

- Multi-Framework: Bebas menggunakan komponen dari React, Svelte, atau Vue dalam satu proyek secara bersamaan.
- Kurva Belajar Rendah: Menggunakan sintaks mirip HTML (.astro) yang intuitif dan mudah dipahami.
- Optimasi Konten: Sangat efisien untuk situs berbasis teks seperti blog, dokumentasi, dan portofolio.
- ​Islands Architecture: Mengirimkan HTML murni ke browser dan hanya mengunduh JavaScript pada komponen interaktif tertentu.

**​Keunggulan Gatsby.js:**
​
- Ekosistem React yang Luas: Memanfaatkan penuh pustaka, alur kerja, dan tooling dari ekosistem React.
- ​Ekosistem Plugin Melimpah: Menyediakan ribuan plugin siap pakai untuk integrasi CMS, SEO, dan manipulasi gambar.
- GraphQL Terintegrasi: Memudahkan pengelolaan dan penggabungan data dari berbagai headless CMS secara terstruktur.
- Rendering Hibrida: Mendukung Deferred Static Generation (DSG) dan SSR untuk menangani ribuan halaman dinamis.


## Theme Apa Yang di Pakai? 

Tentu yang berkunjung di blog ini pada bertanya template apa yang saya pakai, disini saya menggunakan template karya devoloper Vuk1lis, dimana theme nya sesuai yang saya harapkan ditambah tidak terlalu wah juga, karena ini blog nya bersifat personal jadi tidak perlu lah memiliki banyak fitur yang wah cukup sewajar nya aja. 

## Deploy Astro ke Cloudflare

Karena masih menggunakan Cloudflare Pages maka saya akan share cara naya deploy AstroJS ini kepada kalian semua, jika bingung langsung tanyakan di kolom komentar aja. 

### Stup Cloudfalre Page
- Log in ke akun [Cloudflare](https://dash.cloudflare.com/login) milik kalian
- Pilih menu Workers & Pages, kemudian `klik Create` application
- Pilih Lagi `Get Started`
- Pilih Import an existing Git repository klik `Get Started`
- Kemudian pilih **Connect Git** milik kalian
- Setelah Selesai, selanjutnya pilih Theme AstroJS milik kalian
- Pastikan untuk Freamwork Preset nya pilih yang **Astro** jangan pilih yang lain, karena yang mau kita build itu adalah AstroJS. 

### Build Configurasi
```bash
Build command: npm run build
Build output directory: dist
Root directory: /
```
> Note : Apabila kalian menemukan **build pnpm** berarti template yang digunakan itu memakai lokal server jadi tidak bisa dibuild di cloudflare

### Tunggu Build
Setelah memgikuti langkah diatas tinggal tunggu aja, prosesnya membutuhkan waktu sekitar 5 atau 10 menit saja jadi tetap tunggu saja proses nya.

## Setting Theme AstroJs
Setiap theme astrojs ini sangatlah berbeda - beda cara setting nya seperti theme yang saya pakai ini dimana sedikit ribet, akan tetapi theme AstroJS ini pasti ada `astro.config.mjs` untuk konfirmasi website kita. 

```bash
import { defineConfig } from 'astro/config';
import remarkToc from 'remark-toc';
import rehypeSlug from 'rehype-slug';
import rehypeAutolinkHeadings from 'rehype-autolink-headings';
import sitemap from '@astrojs/sitemap';
import { visit } from 'unist-util-visit';
import mdx from '@astrojs/mdx';
import expressiveCode from 'astro-expressive-code';
import { unified } from '@astrojs/markdown-remark';

function rehypeLazyImages() {
  return (tree) => {
    visit(tree, 'element', (node) => {
      if (node.tagName === 'img' && !node.properties.loading) {
        node.properties.loading = 'lazy';
        node.properties.decoding = 'async';
      }
    });
  };
}

export default defineConfig({
  site: 'https://www.sudarblogger.com',
  trailingSlash: 'always',

  markdown: unified({
    remarkPlugins: [[remarkToc, { heading: 'contents' }]],
    rehypePlugins: [rehypeSlug, rehypeLazyImages, [rehypeAutolinkHeadings, { behavior: 'append' }]],
  }),

  prefetch: false,

  integrations: [expressiveCode(), sitemap(), mdx()],
});
```
diatas adalah konfigurasi AstroJS ini jadi apabila kalian sudah mengganti domain milik kalian, harus diganti juga konfigurasi dengan domain kalian. 

Setelah setting configurasi astro selanjutnya kita setting title blog, seperti saya bilang di awal themes astro ini sangatlah ribet biasa nya kalau astro itu setting title serta descripsi nya berada di `content.config.ts` namun kali ini berada di 'index.astro'

```bash title="index.astro"
<BaseLayout title="Sudar Blogger | Personal Website & Portofolio" description="Vuk1lis is a DevOps engineer, Linux enthusiast, and VibeCoder crafting immersive digital experiences where dark aesthetics meet surgical performance." keywords="vukilis, portfolio, creative developer, devops engineer, linux enthusiast, immersive experiences, dark aesthetics, web development, personal website, tech blog, coding, automation, frontend, backend, open source, github, projects, skills, recent posts, vuk1lis, v for vendetta">
  <Navigation />

  <!-- Page-wide themed atmosphere -->
  <div class="vendetta-bg" aria-hidden="true">
    <div class="vendetta-vendetta-v v-monogram">
      <span>V</span>
    </div>
  </div>
```

Tinggal setting Meta data agar blog mudah di temukan oleh mesin pencari, mulai dari setting icon, pasang kode [Google Adsense](https://www.sudarblogger.com/blog/google-adsense/) misalnya. 

```bash title="BaseLayout.Astro"
const base = import.meta.env.BASE_URL;
const {
  title = 'Sudar Blogger | Catatan Harian Kang Sudar',
  description = 'My work sits at the intersection of art and technology. I build immersive digital experiences where dark aesthetics meet surgical performance. Every deployment is a revolution. Every animation is a statement.',
  keywords = 'sudar blogger, portfolio, creative developer, immersive experiences, dark aesthetics',
  hideFooter = false,
} = Astro.props;
---
```
Nah sekarang sudah selesai, Apabila kalian masih bingung bisa langsung aja tanyakan di kolom komentar yang ada di bawah ini. 
