# Setup Guide

Panduan mengaktifkan semua bagian dinamis di profil ini setelah repo `febby24si-create/febby24si-create` dibuat dan file-file ini di-push.

<br/>

## 1. Struktur dasar

```
febby24si-create/
├── README.md
├── assets/
│   ├── banner.svg
│   ├── divider.svg
│   ├── logo.svg
│   └── terminal.svg
├── .github/workflows/
│   ├── snake.yml
│   ├── metrics.yml
│   └── update.yml
├── profile/
│   ├── about.md
│   ├── stack.md
│   ├── projects.md
│   ├── stats.md
│   ├── philosophy.md
│   └── contact.md
└── docs/
    └── SETUP.md
```

Push semua ini ke repo `febby24si-create/febby24si-create` (harus **public**, nama repo sama persis dengan username).

<br/>

## 2. Contribution Snake (`snake.yml`)

Tidak perlu setup token tambahan — cukup:

1. Push repo dengan workflow `.github/workflows/snake.yml`
2. Buka tab **Actions** di repo → jalankan workflow `Generate Snake Animation` sekali secara manual (`Run workflow`)
3. Workflow akan membuat branch `output` berisi file SVG snake
4. README sudah otomatis menunjuk ke:
   `https://raw.githubusercontent.com/febby24si-create/febby24si-create/output/github-contribution-grid-snake-dark.svg`

Setelah run pertama sukses, snake akan otomatis update tiap hari (cron `0 0 * * *`).

<br/>

## 3. GitHub Metrics (`metrics.yml`)

Butuh **1 token tambahan**:

1. Buat Personal Access Token (classic) di GitHub → Settings → Developer settings → scope minimal: `repo`, `read:user`
2. Di repo profil → Settings → Secrets and variables → Actions → New repository secret
3. Nama secret: `METRICS_TOKEN`, isi dengan token yang dibuat
4. Jalankan workflow `Generate Metrics` sekali manual dari tab Actions

Output otomatis tersimpan di `profile/metrics.svg` — bisa ditambahkan ke README manual kalau mau ditampilkan:

```md
<img src="./profile/metrics.svg" width="100%" />
```

<br/>

## 4. Dynamic Quote (`update.yml`)

Workflow ini jalan otomatis tiap hari, tidak perlu secret tambahan. Kalau ingin quote block ditampilkan di README, tambahkan comment marker ini di tempat yang diinginkan:

```html
<!--START_SECTION:quote-->
<!--END_SECTION:quote-->
```

<br/>

## 5. Opsional — WakaTime

Kalau mau menampilkan jam coding mingguan:

1. Daftar di [wakatime.com](https://wakatime.com), install plugin di editor
2. Setelah ada data ≥ 1 minggu, tambahkan badge ini ke README:

```md
![WakaTime](https://wakatime.com/badge/user/USER_ID.svg)
```

Ganti `USER_ID` dengan ID WakaTime kamu (ada di Settings → API Key page).

<br/>

## 6. Opsional — Spotify Now Playing

1. Fork repo `novatorem/novatorem` atau pakai layanan serupa (`spotify-github-profile`)
2. Ikuti instruksi OAuth Spotify di repo tersebut untuk dapat refresh token
3. Tambahkan badge/README embed sesuai instruksi repo tersebut

Fitur ini butuh akun Spotify aktif, jadi sengaja tidak di-hardcode di sini.

<br/>

## 7. Checklist setelah push pertama

- [ ] Repo public, nama = username
- [ ] Jalankan `snake.yml` manual sekali
- [ ] Set secret `METRICS_TOKEN`, jalankan `metrics.yml` manual sekali
- [ ] Cek semua gambar di README tampil (refresh profil GitHub)
- [ ] Ganti link LinkedIn / Instagram / Email di `profile/contact.md` dan `README.md` kalau berbeda dari pola username
