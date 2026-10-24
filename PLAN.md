# PLAN.md — Universal 2D Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade 2D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: *(Menunggu sesi brainstorming ide game bersama siswa)*
- **Genre**: 2D Arcade Game
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal
- **Platform**: Web Browser (Desktop & Mobile Responsive)
- **Audio**: Web Audio API Sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `main`, path `/`)

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Siswa menentukan ide & tema game: **Snake** (dikembangkan dalam 1 file `index.html`).
- [x] Variasi unik dipertimbangkan: Neon Color Snake, Portal Snake, Shrink & Grow Snake, Gravity Snake, Snake Bomber.
- [x] Variasi final dipilih: **Gravity Snake** — ular terus-menerus ditarik gravitasi ke bawah; pemain harus naik/berarahan untuk tidak jatuh.
- [x] Kontrol permainan: Keyboard Arrow/WASD + Spasi (naik), sentuh layar untuk mobile (tombol naik).
- [x] Aturan menang/kalah: Makanan menambah panjang & skor; kalah jika menabir dinding, badan sendiri, atau jatuh di bawah layar karena gravitasi.
- [x] Gaya visual: Neon Glow (Canvas gradient + glow effects).

### Phase 1: Setup Single-File `index.html`
- [x] Buat kerangka HTML5 dengan meta tag **Zero-Cache**.
- [x] Siapkan kanvas responsif dengan rasio layar tetap (400x500).
- [x] Susun struktur kode modular 8 blok di JavaScript.
- [x] Siapkan game loop utama (`requestAnimationFrame`).

### Phase 2: Username & Leaderboard LocalStorage
- [x] Buat modal input username dengan validasi nama (1–15 karakter, anti-XSS).
- [x] Simpan dan baca username terakhir dari `arcade_last_username`.
- [x] Buat fungsi penyimpanan dan penyortiran Top 10 skor di `arcade_leaderboard`.
- [x] Buat tampilan antarmuka (UI) tabel peringkat skor di menu game.

### Phase 3: Mekanik Inti Permainan (Core Gameplay)
- [x] Sistem status game (`MENU`, `PLAYING`, `PAUSED`, `GAMEOVER`).
- [x] Karakter pemain (pergerakan dengan gravitasi dan batas layar).
- [x] Makanan (spawn acak, pertambahan panjang & skor).
- [x] Deteksi tabrakan (dinding, badan sendiri, jatuh karena gravitasi) dan perhitungan skor.

### Phase 4: Efek Suara & Visual Juice
- [x] Efek suara arcade sintetis dengan Web Audio API (Start, Makan, Naik, Game Over, Menu).
- [ ] Efek ledakan partikel sederhana saat tabrakan/poin didapat.
- [ ] Efek getar layar (screen shake) saat game over.

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`.
- [x] Buat repository GitHub publik via GitHub CLI (`gh repo create gravity-snake --public --source=. --remote=origin --push`).
- [x] Aktifkan GitHub Pages via CLI `gh api` (branch `main`, path `/`).
- [x] Live demo: https://fakhri24.github.io/gravity-snake/
- [ ] Pantau status workflow build di tab Actions (`gh run list`).
- [ ] Tes live demo dan verifikasi zero-cache setelah build selesai.

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Pembuatan template `AGENTS.md` & `PLAN.md` untuk Siswa | Fondasi | `DONE` | AI | Template standar single model siap |
| **T-01** | Brainstorming Ide & Konsep Game Spesifik | Phase 0 | `DONE` | Siswa | Tema: Gravity Snake (Neon Glow) |
| **T-02** | Pembuatan Skeleton `index.html` & Meta Zero-Cache | Phase 1 | `DONE` | AI | 8 blok modular, Gravity Snake implementasi lengkap |
| **T-03** | Modul Input Username & Leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage CRUD, anti-XSS, tabel peringkat |
| **T-04** | Logika Pergerakan, Rintangan & Tabrakan | Phase 3 | `DONE` | AI | Gravitasi, wrap horizontal, collision dinding/badan |
| **T-05** | Efek Suara Synth Web Audio API & Partikel | Phase 4 | `DONE` | AI | Audio sintetis (6 efek); partikel & screen shake belum |
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Repo: fakhri24/gravity-snake, URL: https://fakhri24.github.io/gravity-snake/ |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.3.0** | 2026-10-24 | AI | Implementasi Gravity Snake lengkap di index.html (8 blok AGENTS.md), LocalStorage leaderboard, audio Web Audio API, UI neon glow, deployment GitHub Pages | `-` |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |
