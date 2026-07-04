# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel(R) Core(TM) i5-6200 CPU @ 2.30GHz 2.40 GHz
  RAM     : 8,00 GB
  GPU     : Intel(R) HD Graphics 520 (128 MB)
  Storage : 238 GB

Software:
  OS        : Windows 10 Pro
  Runtime   : Web Browser (Google Chrome)
  Framework : WordPress

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
| WordPress | Versi terbaru | WordPress.com | - |
| Google Chrome | Versi terbaru | Google Chrome | - |

Konfigurasi:
  Config file     : Pengaturan bawaan WordPress
  Random seed     : Tidak digunakan
  Hyperparameters : Tidak digunakan

Reproducibility Check:
  [✅] Dependency terdokumentasi (requirements.txt / lock file)
  [ ] Seed ditetapkan di semua level (Python, NumPy, framework)
  [ ] Config di version control
  [✅] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU |Intel(R) Core(TM) i5-6200 CPU @ 2.30 GHz 2.40 GHz |
| RAM | 8,00 GB DDR3 |
| GPU | Intel(R) HD Graphics 520 (128 MB) |
| OS | Windows 10 Pro |
| Runtime | Web Browser (Google Chrome) |
| Framework | WordPress |
| Random Seed | Tidak digunakan karena penelitian tidak melibatkan proses acak. |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| WordPress | Versi terbaru | Digunakan untuk membangun website profil sekolah. |
| Google Chrome | Versi terbaru | Digunakan untuk mengakses, mengelola, dan menguji website. |
| Google Forms | Versi web | Digunakan untuk mengumpulkan data kuesioner dari responden. |
| Microsoft Excel | Microsoft 365 | Digunakan untuk mengolah hasil kuesioner. |
| Koneksi Internet | Stabil | Dibutuhkan agar website dapat diakses oleh responden selama pengujian. |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | - | Website dapat diakses dan seluruh menu berfungsi dengan baik | — |
| 2 | - | Website dapat diakses dan seluruh menu berfungsi dengan baik | [✅] Ya / [ ] Tidak |
| 3 | - | Website dapat diakses dan seluruh menu berfungsi dengan baik | [✅] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**
> Perbedaan hasil dapat disebabkan oleh koneksi internet yang tidak stabil, perubahan konfigurasi website, atau adanya pembaruan pada platform WordPress selama proses pengujian.

**Checklist kontrol yang sudah diterapkan:**
- [ ] Random seed di-set di semua level (tidak digunakan pada penelitian ini)
- [✅] Tidak ada background process yang mengganggu
- [✅] Cache dibersihkan antar-run
- [✅] Menggunakan konfigurasi website yang sama untuk semua run

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Pengujian Website Profil Sekolah Berbasis WordPress

## 1. Environment
| Komponen | Spesifikasi |
|----------|------------|
| CPU |Intel(R) Core(TM) i5-6200 CPU @ 2.30 GHz 2.40 GHz |
| RAM | 8,00 GB DDR3 |
| GPU | Intel(R) HD Graphics 520 (128 MB) |
| OS | Windows 10 Pro |
| Runtime | Web Browser (Google Chrome) |
| Framework | WordPress |
| Random Seed | Tidak digunakan karena penelitian tidak melibatkan proses acak. |

## 2. Installation
> 1. Membuat website menggunakan WordPress.
> 2. Memastikan website dapat diakses melalui browser.
> 3. Membagikan tautan website kepada responden untuk dilakukan pengujian.

## 3. Data
> Data yang digunakan berupa informasi profil sekolah, seperti profil sekolah, fasilitas, berita, dan informasi lainnya yang ditampilkan pada website. Data penelitian diperoleh dari hasil pengisian kuesioner oleh responden setelah mengakses website.

## 4. Execution
> Responden mengakses website melalui tautan yang diberikan, mencoba fitur dan menu yang tersedia, kemudian mengisi kuesioner untuk menilai efektivitas penyampaian informasi.

## 5. Configuration
> Website menggunakan konfigurasi bawaan WordPress. Selama proses pengujian tidak dilakukan perubahan konfigurasi agar seluruh responden mengakses sistem yang sama.

## 6. Expected Output
> Website dapat diakses dengan baik oleh responden, seluruh informasi dapat ditampilkan dengan benar, dan diperoleh data kuesioner yang dapat digunakan untuk mengukur efektivitas website sebagai media penyampaian informasi.
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [✅] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> Dokumentasi penelitian masih perlu dilengkapi, terutama terkait langkah-langkah pengujian yang lebih rinci, versi WordPress yang digunakan, serta dokumentasi konfigurasi website. Dengan dokumentasi yang lebih lengkap, penelitian akan lebih mudah direproduksi oleh peneliti lain.
