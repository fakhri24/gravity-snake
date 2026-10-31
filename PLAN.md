# PLAN.md — Universal 2D Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade 2D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: **Gravity Snake** — ular neon yang menyelam tanpa henti
- **Genre**: 2D Arcade Endless Descent (dunia bergulir, grid 20×25)
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
- [x] Pergerakan terpadu: horizontal, gravitasi, dan manuver naik/turun lewat satu fungsi `stepSnake()` (tidak ada mutasi ganda).
- [x] Thrust naik/turun dengan cooldown; menekan atas benar-benar mengangkat ular, bukan sekadar membatalkan gravitasi.
- [x] Anti belokan 180° beruntun dan tabrakan ekor yang adil (sel ekor yang akan ditinggalkan tidak dihitung).
- [x] Game loop berbasis delta time (`dt`) dengan satu loop permanen (tidak ada loop ganda saat resume/restart).

### Phase 4: Efek Suara & Visual Juice
- [x] Efek suara arcade sintetis dengan Web Audio API (Start, Makan, Naik, Game Over, Menu).
- [x] Efek ledakan partikel sederhana saat makan dan game over.
- [x] Efek getar layar (screen shake) saat makan bonus dan game over.

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`.
- [x] Buat repository GitHub publik via GitHub CLI (`gh repo create gravity-snake --public --source=. --remote=origin --push`).
- [x] Aktifkan GitHub Pages via CLI `gh api` (branch `main`, path `/`).
- [x] Live demo: https://fakhri24.github.io/gravity-snake/
- [x] Pantau status workflow build di tab Actions (`gh run list`).
- [x] Tes live demo dan verifikasi zero-cache setelah build selesai.

### Phase 6: Poles Kontrol & Ketahanan Data
- [x] Pause: tombol HUD, tombol `Esc`/`P`, dan auto-pause saat tab tidak aktif (`visibilitychange`).
- [x] Kontrol sentuh lengkap dan simetris (▲ / ◀ ▼ ▶) plus tombol pause untuk mobile.
- [x] Feedback peringkat di layar Game Over ("REKOR BARU!" / "Masuk peringkat #n" / "Belum masuk Top 10").
- [x] Skor terbaik dimuat dari leaderboard saat game dibuka.
- [x] `JSON.parse` dibungkus `try/catch` + normalisasi entri leaderboard yang rusak.
- [x] Makanan tidak pernah muncul di badan ular atau di sel yang akan dilewati kepala.

### Phase 7: Redesign — Endless Descent (v0.5.0)
- [x] Keputusan desain: kontrol naik/turun dihapus; ular selalu turun, pemain hanya menggeser kiri/kanan.
- [x] Kamera dunia mengikuti kepala (kepala tetap di baris layar ke-8) sehingga permainan tidak pernah berhenti di dasar.
- [x] Glide: laju turun menjadi 0,55× selama menggeser, menciptakan trade-off kecepatan vs keamanan.
- [x] Generator band rintangan dengan jaminan celah minimal 3 kolom dan kepadatan yang naik seiring kedalaman.
- [x] Makanan selalu lahir di bawah kepala, diganti otomatis jika terlewat.
- [x] Skor = 10 per makanan + 1 per meter kedalaman; kecepatan naik tiap 40 meter.
- [x] Game over hanya karena menabrak rintangan atau badan sendiri; belokan 180° ke leher ditolak tanpa mematikan.
- [x] Background bintang parallax sebagai penanda laju penyelaman; HUD menampilkan Skor, Kedalaman, Terbaik.
- [x] Kontrol sentuh disederhanakan menjadi ◀ ▶ + tombol pause.

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Pembuatan template `AGENTS.md` & `PLAN.md` untuk Siswa | Fondasi | `DONE` | AI | Template standar single model siap |
| **T-01** | Brainstorming Ide & Konsep Game Spesifik | Phase 0 | `DONE` | Siswa | Tema: Gravity Snake (Neon Glow) |
| **T-02** | Pembuatan Skeleton `index.html` & Meta Zero-Cache | Phase 1 | `DONE` | AI | 8 blok modular, Gravity Snake implementasi lengkap |
| **T-03** | Modul Input Username & Leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage CRUD, anti-XSS, tabel peringkat |
| **T-04** | Logika Pergerakan, Rintangan & Tabrakan | Phase 3 | `DONE` | AI | Gravitasi, wrap horizontal, collision dinding/badan |
| **T-05** | Efek Suara Synth Web Audio API & Partikel | Phase 4 | `DONE` | AI | Audio sintetis (6 efek), partikel makan/game over, screen shake |
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Repo: fakhri24/gravity-snake, URL: https://fakhri24.github.io/gravity-snake/ |
| **T-07** | Perbaikan mekanik inti (step terpadu, thrust, anti-180°, ekor adil) | Phase 3 | `DONE` | AI | Satu `stepSnake()` untuk horizontal, gravitasi, dan manuver |
| **T-08** | Game loop delta time + satu loop permanen | Phase 3 | `DONE` | AI | Kecepatan konsisten di 60/120 Hz, tidak ada loop ganda |
| **T-09** | Pause lengkap (HUD/Esc/P, auto-pause tab hidden) & kontrol sentuh | Phase 6 | `DONE` | AI | Grid sentuh ▲ / ◀ ▼ ▶ + tombol pause |
| **T-10** | Feedback peringkat Game Over & skor terbaik dari leaderboard | Phase 6 | `DONE` | AI | "REKOR BARU!", "Masuk peringkat #n", "Belum masuk Top 10" |
| **T-11** | Ketahanan data LocalStorage & spawn makanan | Phase 6 | `DONE` | AI | `try/catch`, normalisasi entri, anti-spawn di badan/arah kepala |
| **T-12** | Redesign mekanik menjadi Endless Descent | Phase 7 | `DONE` | AI | Hapus thrust, tambah kamera dunia + glide |
| **T-13** | Generator dunia: band rintangan + makanan + pruning | Phase 7 | `DONE` | AI | Celah minimal 3 kolom, kepadatan naik tiap 120 m |
| **T-14** | Progresi skor kedalaman & kecepatan | Phase 7 | `DONE` | AI | +1 per meter, +10 makanan, percept tiap 40 m |
| **T-15** | Penyesuaian UI/HUD & kontrol sentuh 2 tombol | Phase 7 | `DONE` | AI | HUD Skor/Dalam/Terbaik, ◀ ▶ + pause |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.5.0** | 2026-10-31 | AI | Redesign ke Endless Descent: kamera dunia, glide kiri/kanan, generator band rintangan + makanan, skor kedalaman, HUD baru, kontrol 2 tombol, game over hanya rintangan/badan | `d71bf02` |
| **v0.4.0** | 2026-10-31 | AI | Poles mekanik & UX: step terpadu (horizontal/gravitasi/thrust), loop delta time tunggal, pause lengkap + auto-pause, kontrol sentuh lengkap, feedback peringkat Game Over, skor terbaik dari leaderboard, partikel + screen shake, hardening LocalStorage | `2beb8e8` |
| **v0.3.0** | 2026-10-24 | AI | Implementasi Gravity Snake lengkap di index.html (8 blok AGENTS.md), LocalStorage leaderboard, audio Web Audio API, UI neon glow, deployment GitHub Pages | `-` |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |

---

## 5. Aturan Main (v0.5.0)

| Aspek | Aturan |
| :--- | :--- |
| Kontrol | ←/→ atau A/D (tahan) untuk menggeser; Esc/P atau tombol HUD untuk pause |
| Gerak | Ular selalu turun 1 sel per 300 ms; tidak ada kontrol naik |
| Glide | Selama menggeser, laju turun menjadi 0,55× (turun lebih lambat) |
| Makanan | +10 skor, +1 panjang, selalu lahir di bawah kepala |
| Kedalaman | +1 skor per meter (1 sel); kecepatan naik tiap 40 m (maks. 150 ms/sel) |
| Rintangan | Band blok merah dengan celah minimal 3 kolom; makin dalam makin rapat |
| Game over | Kepala menabrak rintangan atau badan sendiri |
| Horizontal | Wrap: keluar kanan muncul di kiri, dan sebaliknya |
| Peringkat | Top 10 berdasarkan skor, tersimpan di `arcade_leaderboard` |
