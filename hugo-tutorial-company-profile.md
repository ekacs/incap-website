# Tutorial Lengkap: Membangun Website Company Profile dengan Hugo dan Tema "Hugo Up Business"

## Daftar Isi
- [Pendahuluan](#pendahuluan)
- [Langkah 1: Persiapan Lingkungan (Prasyarat)](#langkah-1-persiapan-lingkungan-prasyarat)
- [Langkah 2: Inisialisasi Proyek Hugo](#langkah-2-inisialisasi-proyek-hugo)
- [Langkah 3: Instalasi dan Konfigurasi Tema](#langkah-3-instalasi-dan-konfigurasi-tema)
- [Langkah 4: Kustomisasi Konfigurasi Utama](#langkah-4-kustomisasi-konfigurasi-utama)
- [Langkah 5: Membuat Konten Halaman](#langkah-5-membuat-konten-halaman)
- [Langkah 6: Menjalankan & Menguji Situs](#langkah-6-menjalankan--menguji-situs)
- [Langkah 7: Tips Kustomisasi Tambahan](#langkah-7-tips-kustomisasi-tambahan)

## Pendahuluan

Hugo adalah static site generator yang sangat cepat dan efisien yang ditulis dalam bahasa Go. Berikut adalah beberapa alasan mengapa Hugo menjadi pilihan yang sangat baik untuk website company profile:

### Keunggulan Hugo:
1. **Kecepatan Tinggi**: Hugo dapat membangun situs dengan ribuan halaman dalam hitungan detik
2. **SEO-Friendly**: Secara otomatis menghasilkan struktur URL yang bersih dan mendukung meta tag
3. **Keamanan**: Tidak memerlukan database atau server-side processing, sehingga lebih aman
4. **Deployment Mudah**: Dapat di-deploy ke berbagai platform seperti Netlify, Vercel, atau GitHub Pages
5. **Markdown Support**: Konten dapat ditulis dalam format Markdown yang mudah dipelajari
6. **Live Reload**: Fitur development yang memungkinkan preview perubahan secara real-time

### Tema "Hugo Up Business"
Tema "Hugo Up Business" adalah tema modern dan profesional yang dirancang khusus untuk company profile. Keunggulannya meliputi:

- **Desain Responsif**: Tampilan yang optimal di desktop, tablet, dan mobile
- **Komponen Lengkap**: Hero section, about, services, portfolio, testimonials, dan contact form
- **Bootstrap Integration**: Menggunakan Bootstrap 5 untuk styling yang konsisten
- **Font Awesome Icons**: Koleksi icon yang lengkap untuk mempercantik tampilan
- **Google Fonts**: Typography yang profesional dan mudah dibaca
- **Contact Form**: Form kontak yang siap pakai dengan Formspree integration
- **SEO Optimized**: Meta tags dan structured data yang sudah teroptimasi

## Langkah 1: Persiapan Lingkungan (Prasyarat)

Sebelum memulai, kita perlu menginstal beberapa software yang diperlukan:

### Software yang Diperlukan:

1. **Hugo**: Static site generator utama
2. **Git**: Version control system untuk mengelola kode dan tema

### Instalasi Hugo dan Git:

#### Windows (menggunakan Chocolatey):
```bash
# Instal Chocolatey jika belum ada
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Instal Hugo dan Git
choco install hugo git
```

#### Windows (menggunakan Scoop):
```bash
# Instal Scoop jika belum ada
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex

# Instal Hugo dan Git
scoop install hugo git
```

#### macOS (menggunakan Homebrew):
```bash
# Instal Homebrew jika belum ada
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instal Hugo dan Git
brew install hugo git
```

#### Linux (Ubuntu/Debian menggunakan APT):
```bash
# Update package list
sudo apt update

# Instal Hugo dan Git
sudo apt install hugo git
```

#### Linux (menggunakan Snap):
```bash
# Instal Hugo dan Git via Snap
sudo snap install hugo
sudo apt install git
```

### Verifikasi Instalasi:
```bash
# Cek versi Hugo
hugo version

# Cek versi Git
git --version
```

**Penjelasan:**
- **Hugo**: Digunakan untuk membuat dan membangun situs web statis dari file Markdown dan template
- **Git**: Diperlukan untuk mengunduh tema dan version control proyek website

## Langkah 2: Inisialisasi Proyek Hugo

Setelah software terinstal, kita akan membuat proyek Hugo baru.

### Membuat Direktori Proyek:
```bash
# Buat direktori untuk proyek company profile
mkdir incap
cd incap

# Inisialisasi situs Hugo baru
hugo new site . --force
```

**Penjelasan:**
- `mkdir company-profile-hugo`: Membuat direktori baru untuk proyek
- `cd company-profile-hugo`: Masuk ke direktori proyek
- `hugo new site . --force`: Membuat situs Hugo baru di direktori saat ini (`.` menunjukkan direktori saat ini)

### Struktur Folder yang Dihasilkan:
Setelah menjalankan perintah di atas, Hugo akan membuat struktur folder sebagai berikut:

```
company-profile-hugo/
├── archetypes/
│   └── default.md          # Template untuk konten baru
├── assets/                 # File asset (CSS, JS, gambar)
├── content/                # Konten situs dalam format Markdown
├── data/                   # File data (YAML, JSON, TOML)
├── layouts/                # Template HTML custom
├── public/                 # Output hasil build (auto-generated)
├── static/                 # File statis (gambar, CSS, JS)
├── themes/                 # Tema Hugo
└── hugo.toml              # File konfigurasi utama
```

## Langkah 3: Instalasi dan Konfigurasi Tema

Tema "Hugo Up Business" akan kita instal sebagai Git submodule untuk kemudahan maintenance.

### Instalasi Tema sebagai Git Submodule:
```bash
# Tambahkan tema sebagai submodule
git init
git submodule add https://github.com/writeonlycode/hugo-up-business.git themes/hugo-up-business

# Inisialisasi dan update submodule
git submodule update --init --recursive
```

**Mengapa Git Submodule?**
- Memudahkan update tema di masa depan
- Tema tersimpan sebagai referensi Git, bukan copy lokal
- Memungkinkan tracking versi tema yang digunakan
- Tidak perlu mengunduh ulang saat clone proyek

### Menyalin File Konfigurasi Tema:
```bash
# Salin file konfigurasi contoh dari tema
cp themes/hugo-up/hugo.toml hugo.toml
```

**Penjelasan:**
- `cp themes/hugo-up-business/hugo.toml hugo.toml`: Menyalin file konfigurasi contoh dari tema ke root direktori proyek
- File ini berisi semua konfigurasi default tema yang bisa kita kustomisasi

## Langkah 4: Kustomisasi Konfigurasi Utama

Sekarang kita akan mengedit file `hugo.toml` untuk menyesuaikan dengan company profile kita.

### Contoh File `hugo.toml` yang Dikustomisasi:

```toml
# -- Basic Site Configuration --
baseURL = "https://example.com"
languageCode = "id-ID"
title = "Nama Perusahaan Anda"
theme = "hugo-up-business"

# -- Site Meta Information --
[params]
  siteName = "Nama Perusahaan Anda"
  siteDescription = "Deskripsi singkat tentang perusahaan Anda"
  siteKeywords = "kata kunci, company profile, bisnis"

# -- Author Information --
[author]
  name = "Nama Perusahaan"

# -- Menu Navigation --
[[menu.main]]
  name = "Beranda"
  url = "/"
  weight = 1

[[menu.main]]
  name = "Tentang Kami"
  url = "/about/"
  weight = 2

[[menu.main]]
  name = "Layanan"
  url = "/services/"
  weight = 3

[[menu.main]]
  name = "Kontak"
  url = "/contact/"
  weight = 4

# -- Theme Parameters --
[params.hero]
  title = "Selamat Datang di"
  subtitle = "Nama Perusahaan Anda"
  description = "Deskripsi singkat tentang perusahaan dan layanan yang ditawarkan"
  buttonText = "Pelajari Lebih Lanjut"
  buttonURL = "/about/"

[params.about]
  title = "Tentang Kami"
  description = "Deskripsi lengkap tentang perusahaan, visi, misi, dan nilai-nilai perusahaan"

[params.services]
  title = "Layanan Kami"

[params.contact]
  title = "Hubungi Kami"
  description = "Jangan ragu untuk menghubungi kami jika ada pertanyaan"

# -- Contact Information --
[params.contactInfo]
  address = "Alamat lengkap perusahaan"
  phone = "+62-XXX-XXXX-XXXX"
  email = "info@perusahaan.com"
  hours = "Senin - Jumat: 08:00 - 17:00"

# -- Social Media Links --
[params.social]
  facebook = "https://facebook.com/username"
  twitter = "https://twitter.com/username"
  instagram = "https://instagram.com/username"
  linkedin = "https://linkedin.com/company/username"

# -- Footer Information --
[params.footer]
  copyright = "© 2024 Nama Perusahaan Anda. Hak cipta dilindungi."
  poweredBy = true
  poweredByURL = "https://gohugo.io"
```

### Penjelasan Parameter Penting:

1. **baseURL**: URL utama situs web (ganti dengan domain asli)
2. **languageCode**: Kode bahasa situs (id-ID untuk Bahasa Indonesia)
3. **title**: Judul situs yang akan muncul di browser tab
4. **[[menu.main]]**: Konfigurasi menu navigasi utama
5. **[params.hero]**: Konten untuk section hero/utama di homepage
6. **[params.contactInfo]**: Informasi kontak perusahaan
7. **[params.social]**: Link ke sosial media perusahaan
8. **[params.footer]**: Informasi footer dan copyright

## Langkah 5: Membuat Konten Halaman

Sekarang kita akan membuat konten untuk berbagai halaman menggunakan Markdown.

### 1. Halaman Beranda (Homepage)
Homepage akan menggunakan `content/_index.md`:

```bash
# Buat direktori dan file homepage
mkdir -p content
```

```markdown
---
title: "Beranda"
---
```

**Catatan**: Homepage biasanya tidak memerlukan konten khusus karena menggunakan konfigurasi dari `hugo.toml`.

### 2. Halaman Tentang Kami
```bash
# Buat direktori dan file tentang kami
mkdir -p content/about
```

File: `content/about/_index.md`:
```markdown
---
title: "Tentang Kami"
description: "Pelajari lebih lanjut tentang perusahaan kami"
keywords: "tentang kami, company profile, visi misi"
---

# Tentang Kami

## Visi Kami
Jelaskan visi perusahaan Anda di sini...

## Misi Kami
Jelaskan misi perusahaan Anda di sini...

## Nilai-Nilai Kami
- **Inovasi**: Selalu mencari cara baru untuk melayani pelanggan
- **Integritas**: Menjaga kejujuran dalam setiap aspek bisnis
- **Kualitas**: Memberikan layanan terbaik untuk kepuasan pelanggan

## Tim Kami
Kami memiliki tim profesional yang berpengalaman di bidangnya masing-masing...

## Mengapa Memilih Kami?
1. Pengalaman lebih dari 10 tahun
2. Tim profesional dan terlatih
3. Teknologi terdepan
4. Pelayanan prima
```

### 3. Halaman Layanan
```bash
# Buat direktori layanan
mkdir -p content/services
```

File: `content/services/_index.md`:
```markdown
---
title: "Layanan Kami"
description: "Berbagai layanan yang kami tawarkan"
keywords: "layanan, jasa, konsultasi"
---

# Layanan Kami

Kami menawarkan berbagai layanan berkualitas tinggi untuk memenuhi kebutuhan bisnis Anda.
```

File: `content/services/konsultasi-bisnis.md`:
```markdown
---
title: "Konsultasi Bisnis"
description: "Layanan konsultasi bisnis profesional"
keywords: "konsultasi bisnis, strategi bisnis"
---

# Konsultasi Bisnis

## Apa yang Kami Tawarkan?

Kami menyediakan layanan konsultasi bisnis komprehensif untuk membantu perusahaan Anda berkembang pesat.

### Area Konsultasi:
- **Strategi Bisnis**: Pengembangan strategi jangka panjang
- **Manajemen Operasional**: Optimasi proses bisnis
- **Pengembangan SDM**: Pengelolaan sumber daya manusia
- **Analisis Pasar**: Riset dan analisis kompetitor

## Keunggulan Layanan Kami:
- Konsultan berpengalaman lebih dari 10 tahun
- Metodologi terbukti dan terstruktur
- Solusi yang disesuaikan dengan kebutuhan spesifik
- Follow-up dan evaluasi berkelanjutan

## Hubungi Kami
Untuk informasi lebih lanjut tentang layanan konsultasi bisnis kami, silakan hubungi tim kami.
```

File: `content/services/pengembangan-web.md`:
```markdown
---
title: "Pengembangan Website"
description: "Jasa pembuatan website profesional"
keywords: "web development, website company profile"
---

# Pengembangan Website

## Layanan Pengembangan Website

Kami menyediakan jasa pembuatan website modern dan responsif untuk berbagai kebutuhan bisnis.

### Teknologi yang Kami Gunakan:
- **Hugo Static Site Generator**: Website cepat dan SEO-friendly
- **Bootstrap 5**: Framework CSS modern dan responsif
- **JavaScript Modern**: Interaktivitas dan user experience yang baik
- **Responsive Design**: Optimal di semua device

### Paket Layanan:
1. **Company Profile**: Website profil perusahaan profesional
2. **Portfolio**: Showcase karya dan project
3. **Blog/Artikel**: Platform content marketing
4. **E-commerce**: Toko online dengan fitur lengkap

## Proses Pengembangan:
1. Konsultasi dan perencanaan
2. Design dan prototyping
3. Development dan testing
4. Launch dan maintenance

## Portofolio Kami
Berikut adalah beberapa project website yang telah kami kerjakan...
```

### 4. Halaman Kontak
```bash
# Buat direktori dan file kontak
mkdir -p content/contact
```

File: `content/contact/_index.md`:
```markdown
---
title: "Hubungi Kami"
description: "Kontak kami untuk informasi lebih lanjut"
keywords: "kontak, hubungi kami, alamat"
---

# Hubungi Kami

Kami siap membantu Anda! Jangan ragu untuk menghubungi kami melalui berbagai cara di bawah ini.

## Informasi Kontak

**Alamat:**
Nama Perusahaan Anda
Jl. Contoh No. 123
Jakarta Pusat 12345
Indonesia

**Telepon:**
+62-21-XXXX-XXXX
+62-8XX-XXXX-XXXX

**Email:**
info@perusahaan.com
marketing@perusahaan.com

**Jam Operasional:**
Senin - Jumat: 08:00 - 17:00 WIB
Sabtu: 08:00 - 12:00 WIB
Minggu: Tutup

## Kirim Pesan

Silakan isi form di bawah ini untuk mengirim pesan kepada kami. Kami akan merespons dalam waktu 1x24 jam pada hari kerja.

<form action="https://formspree.io/f/your-form-id" method="POST">
  <div class="form-group">
    <label for="name">Nama Lengkap:</label>
    <input type="text" id="name" name="name" required>
  </div>

  <div class="form-group">
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
  </div>

  <div class="form-group">
    <label for="subject">Subjek:</label>
    <input type="text" id="subject" name="subject" required>
  </div>

  <div class="form-group">
    <label for="message">Pesan:</label>
    <textarea id="message" name="message" rows="5" required></textarea>
  </div>

  <button type="submit">Kirim Pesan</button>
</form>
```

## Langkah 6: Menjalankan & Menguji Situs

Setelah semua konten dan konfigurasi selesai, saatnya menjalankan situs untuk melihat hasilnya.

### Menjalankan Development Server:
```bash
# Jalankan Hugo development server
hugo server -D
```

**Output yang Diharapkan:**
```
Start building sites …
hugo v0.120.0+extended darwin/amd64 BuildDate=unknown

                   | EN
-------------------+-----
  Pages            | 8
  Paginator pages  | 0
  Non-page files   | 0
  Static files     | 0
  Processed images | 0
  Aliases          | 0
  Sitemaps         | 1

Built in 123 ms

Watching for changes in /path/to/company-profile-hugo/{archetypes,assets,content,data,layouts,static,themes}
Watching for config changes in /path/to/company-profile-hugo/hugo.toml
Web Server is available at http://localhost:4000/ (bind address 0.0.0.0)
Press Ctrl+C to stop.
```

### Mengakses Situs di Browser:
1. Buka browser web (Chrome, Firefox, Safari, dll)
2. Ketik `http://localhost:4000` di address bar
3. Tekan Enter

### Fitur Live Reload:
- Setiap perubahan pada file konten atau konfigurasi akan otomatis terdeteksi
- Browser akan secara otomatis refresh untuk menampilkan perubahan
- Tidak perlu restart server development

**Tips Development:**
- Gunakan `-D` flag untuk melihat konten dengan `draft: true` di front matter
- Tanpa `-D`, hanya konten dengan `draft: false` atau tanpa draft status yang akan tampil
- Untuk production build, gunakan `hugo` tanpa parameter server

## Langkah 7: Tips Kustomisasi Tambahan

### Mengubah Warna Tema:
Buat file CSS custom di `assets/css/custom.css`:

```css
/* assets/css/custom.css */
:root {
  --primary-color: #your-primary-color;
  --secondary-color: #your-secondary-color;
  --accent-color: #your-accent-color;
}

/* Custom styling untuk komponen tertentu */
.hero-section {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
}

.btn-primary {
  background-color: var(--accent-color);
  border-color: var(--accent-color);
}

.btn-primary:hover {
  background-color: var(--primary-color);
  border-color: var(--primary-color);
}
```

Kemudian tambahkan referensi CSS ini ke `hugo.toml`:
```toml
# Tambahkan di bagian [params]
customCSS = ["css/custom.css"]
```

### Mengubah Font:
Tambahkan Google Fonts ke `hugo.toml`:
```toml
# Di bagian [params]
googleFonts = ["Open+Sans:400,600,700", "Roboto:300,400,500,700"]
```

### Menambahkan Gambar:
1. Letakkan gambar di folder `static/images/` atau `assets/images/`
2. Untuk Hugo >= v0.120.0, gunakan `assets/` untuk optimasi otomatis
3. Akses gambar dengan path relatif dari static root

### Optimasi SEO:
1. **Meta Description**: Pastikan setiap halaman memiliki description yang unik
2. **Open Graph Tags**: Tema sudah menyertakan Open Graph untuk social media
3. **Sitemap**: Hugo otomatis generate sitemap.xml
4. **Robots.txt**: Buat file `static/robots.txt` jika diperlukan

### Deployment:
Setelah development selesai, build untuk production:
```bash
# Build untuk production
hugo

# Hasil build ada di folder public/
```

Folder `public/` siap di-deploy ke berbagai platform seperti:
- **Netlify**: Drag & drop folder public atau connect dengan Git
- **Vercel**: Connect dengan Git repository
- **GitHub Pages**: Push folder public ke branch gh-pages
- **Firebase Hosting**: `firebase deploy`

---

**Kesimpulan:**

Dengan mengikuti tutorial ini, Anda telah berhasil membuat website company profile profesional menggunakan Hugo dan tema "Hugo Up Business". Website yang dihasilkan memiliki:

✅ Desain modern dan responsif
✅ Konten yang mudah dikelola dengan Markdown
✅ SEO-friendly dan cepat loading
✅ Siap untuk deployment ke berbagai platform
✅ Mudah untuk dikustomisasi dan dikembangkan lebih lanjut

Selamat! Website company profile Anda siap untuk digunakan dan dapat dikembangkan lebih lanjut sesuai kebutuhan bisnis.