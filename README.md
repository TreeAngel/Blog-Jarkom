# Blog Jarkom Kelompok 3

Blog tugas mata kuliah Jaringan Komputer menggunakan Hugo dengan tema PaperMod.

## Cara Menjalankan Lokal

Clone dengan submodule kemudian jalankan:
  hugo server -D

Buka http://localhost:1313 di browser.

## Cara Menambah Artikel Baru

Gunakan Page Bundle agar gambar bisa disimpan bersama artikel:
  hugo new posts/nama-artikel/index.md

Struktur hasil:
  content/posts/
    nama-artikel/
      index.md       <- konten artikel
      cover.png      <- gambar cover
      gambar1.png    <- gambar lain

### Menambahkan Gambar Cover

Di front matter index.md:

  cover:
    image: "cover.png"
    alt: "Deskripsi gambar"
    caption: "Keterangan gambar (opsional)"
    relative: true

### Menyisipkan Gambar di Dalam Artikel

Sintaks Markdown:
  ![Alt text](nama-gambar.png)

Atau shortcode Hugo:
  {{< figure src="nama-gambar.png" alt="Alt text" caption="Keterangan" >}}

## Deploy ke Cloudflare Pages

1. Push repo ke GitHub (termasuk submodule).
2. Cloudflare Dashboard -> Workers & Pages -> Create -> Pages -> Connect to Git.
3. Pilih repo ini.
4. Cloudflare otomatis mendeteksi dari wrangler.toml:
   - Build command: hugo --minify
   - Output directory: public
   - Hugo version: 0.168.0
5. Klik Save and Deploy.

## Struktur Proyek

  archetypes/    - Template front matter
  content/
    posts/       - Artikel (Page Bundle)
    search.md    - Halaman pencarian
  layouts/       - Override template tema
  static/
    images/      - OG image default dan aset statis
  themes/
    PaperMod/    - Tema (Git submodule)
  hugo.yaml      - Konfigurasi Hugo
  wrangler.toml  - Konfigurasi Cloudflare Pages
