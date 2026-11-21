# -Eiga-Ya---Streaming-Film-
🎬 Eiga-Ya 映画屋 — Katalog &amp; pemutar film pribadi bergaya Jepang dalam satu file HTML. Serial, Mode Cinema, lanjut menonton, tema gelap. Tanpa server.

<div align="center">

# 映画屋 Eiga-Ya

**Katalog & pemutar film pribadi bergaya Jepang — satu file HTML, tanpa server, tanpa instalasi.**

![HTML5](https://img.shields.io/badge/HTML5-single%20file-e8869b)
![JavaScript](https://img.shields.io/badge/Vanilla-JavaScript-d9a441)
![Dependencies](https://img.shields.io/badge/dependencies-0-7fae93)
![License](https://img.shields.io/badge/license-MIT-3d4a7a)

</div>

---

## ✨ Tentang

**Eiga-Ya** (映画屋, "toko film") adalah aplikasi web ringan untuk mengelola dan menonton koleksi film serta serial pribadi Anda. Seluruh aplikasi ada dalam **satu file `index.html`** — tanpa framework, tanpa build, tanpa backend. Data katalog disimpan di browser (`localStorage`), sehingga cukup buka file-nya dan langsung dipakai.

Tampilan terinspirasi estetika Jepang: palet **sakura** (merah muda), **indigo**, dan **matcha**, poster otomatis bergradasi dengan **kanji** sebagai ikon, serta dukungan **tema terang/gelap**.

## 🎯 Fitur

### Katalog
- 🔍 **Pencarian** instan berdasarkan judul, tag, tahun, deskripsi, hingga judul episode
- 🏷️ **Tag** dengan filter satu klik, plus penambahan tag massal
- ♥ **Favorit** dan ⭐ **rating** 1–5 bintang
- ↕️ **Urutkan**: terbaru ditambah, A–Z / Z–A, tahun, rating tertinggi, durasi terpanjang
- 🎞️ **Filter jenis**: Film atau Serial
- 📄 **Pagination** (6/12/24/48/96 per halaman) dengan lompat ke halaman tertentu
- ☑️ **Aksi massal**: pilih beberapa film lalu favoritkan, beri tag, atau hapus sekaligus
- 🖼️ **Thumbnail kustom** — gambar otomatis diperkecil (rasio 2:3) dan disimpan sebagai data URI

### Serial TV
- 📺 Manajemen **musim & episode** (tambah beberapa episode berurutan sekaligus)
- ✓ Tandai episode **sudah ditonton**
- ⏭️ **Auto-play episode berikutnya** saat episode selesai

### Pemutar
- ▶️ Pemutar video HTML5 bawaan (MP4/WebM)
- 🎬 **Mode Cinema** layar penuh dengan suasana bioskop
- 🎯 **Mode Fokus** untuk menyembunyikan semua gangguan
- ⏱️ **Lanjut menonton** — posisi terakhir diingat otomatis
- 🚀 Kecepatan putar 0.75× – 2×
- 💡 Mencegah layar mati saat menonton (Screen Wake Lock, bila didukung)
- 📂 **Putar file lokal** langsung dari komputer tanpa mengetik URL

### Data
- 💾 **Backup & restore** katalog dalam format JSON (salin, unduh, atau unggah)
- ♻️ **Reset** ke data contoh kapan saja
- 🔒 Semua data tetap di perangkat Anda, tidak dikirim ke mana pun

## ⌨️ Pintasan Keyboard (Mode Cinema)

| Tombol | Fungsi |
|---|---|
| `Spasi` | Putar / jeda |
| `←` / `→` | Mundur / maju 10 detik |
| `↑` / `↓` | Volume naik / turun |
| `M` | Bisukan / aktifkan suara |
| `D` | Mode fokus |
| `F` | Layar penuh |
| `N` | Episode berikutnya (serial) |
| `Esc` | Keluar dari Mode Cinema |

## 🚀 Cara Pakai

### Opsi 1 — Langsung buka
1. Unduh atau *clone* repo ini
2. Buka `index.html` di browser (Chrome, Edge, Firefox, Safari)

```bash
git clone https://github.com/USERNAME/eiga-ya.git
cd eiga-ya
# buka index.html di browser
```

### Opsi 2 — Server lokal (opsional)
```bash
python -m http.server 8000
# lalu buka http://localhost:8000
```

### Opsi 3 — GitHub Pages
1. Buka **Settings → Pages**
2. Pada *Source*, pilih branch `main` dan folder `/ (root)`
3. Aplikasi akan tersedia di `https://USERNAME.github.io/eiga-ya/`

## 🎥 Menambahkan Video

Eiga-Ya **tidak menyertakan atau menyediakan film apa pun**. Anda menautkan sendiri file video milik Anda:

| Sumber | Contoh alamat | Catatan |
|---|---|---|
| 🌐 Internet | `https://domain.com/film.mp4` | Harus tautan **langsung** ke file video (bukan halaman YouTube/Google Drive), dan server harus mengizinkan akses lintas situs (CORS) |
| 💻 File lokal | `file:///D:/Film/film.mp4` | Hanya berfungsi jika `index.html` dibuka langsung dari komputer (`file://`). Path Windows seperti `C:\Film\a.mp4` otomatis dikonversi |
| 📁 Folder proyek | `./video/film.mp4` | Relatif terhadap `index.html`; cocok untuk server lokal |
| 📂 Tanpa alamat | — | Gunakan tombol **Putar file lokal** di jendela detail (hanya untuk sesi itu) |

**Format yang disarankan:** MP4 (H.264 + AAC) atau WebM.

> ⚠️ `localStorage` hanya menyimpan **data katalog** (teks & thumbnail), bukan file video.

## 🗂️ Struktur Repo

```
eiga-ya/
├── index.html      # seluruh aplikasi (HTML + CSS + JS)
├── README.md
├── LICENSE
├── CHANGELOG.md
└── .gitignore
```

## 🧱 Teknologi

- HTML5, CSS3 (CSS variables, `color-mix`, grid, `backdrop-filter`)
- JavaScript murni (ES6+), tanpa library atau framework
- Web Storage API, FileReader, Canvas, Fullscreen API, Screen Wake Lock API

## 💾 Format Backup

```json
{
  "app": "eiga-ya",
  "version": 1,
  "films": [
    {
      "id": "abc123",
      "title": "Sakura no Yoru",
      "kanji": "桜",
      "year": 2021,
      "dur": 108,
      "desc": "…",
      "tags": ["romansa", "drama"],
      "url": "https://…/film.mp4",
      "rating": 4,
      "fav": true,
      "type": "movie",
      "eps": [],
      "thumb": "data:image/jpeg;base64,…",
      "added": 1700000000000
    }
  ]
}
```

## ⚠️ Batasan

- Data tersimpan **per browser & per alamat** — membuka dari `file://` dan dari GitHub Pages berarti dua penyimpanan terpisah. Gunakan fitur **Backup/Restore** untuk memindahkan data.
- Kapasitas `localStorage` terbatas (~5 MB); terlalu banyak thumbnail dapat memenuhinya.
- Alamat `file:///` diblokir browser bila aplikasi dibuka dari situs online.

## ⚖️ Disclaimer

Eiga-Ya hanyalah **alat katalog dan pemutar** untuk konten yang Anda miliki atau berhak Anda akses. Proyek ini tidak menyediakan, meng-host, atau mendistribusikan konten berhak cipta. Pengguna bertanggung jawab penuh atas konten yang ditautkan. Film contoh bawaan bersifat fiktif dan memakai video demo domain publik (CC0) dari MDN.

## 🤝 Kontribusi

Saran, laporan bug, dan pull request sangat diterima!

1. Fork repo ini
2. Buat branch fitur: `git checkout -b fitur/nama-fitur`
3. Commit perubahan: `git commit -m "Tambah fitur …"`
4. Push dan buka Pull Request

## 📄 Lisensi

Dirilis di bawah [Lisensi MIT](LICENSE).

---

<div align="center">

映画を楽しもう 🌸 — *Selamat menonton!*

</div>
