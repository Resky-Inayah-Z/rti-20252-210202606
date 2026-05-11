# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Penyampaian informasi sekolah masih dilakukan secara konvensional sehingga informasi kurang efektif dan sulit diakses oleh siswa maupun masyarakat.

Research Question:
  Tipe         : [ ] Comparison  [√] Improvement  [ ] Exploratory
  Formulasi    : Apakah website profile sekolah berbasis WordPress mampu meningkatkan efektivitas penyampaian informasi dibandingkan media informasi konvensional pada SD Negeri 12 Badau?
  Variabel IV  : Media informasi yang digunakan
  Variabel DV  : Efektivitas penyampaian informasi
  Metrik       : Tingkat akses informasi dan kepuasan pengguna
  Dataset      : Data pengguna website SD Negeri 12 Badau
  Baseline     : Media informasi konvensional seperti papan pengumuman

Quality Check RQ:
  [√] Variabel spesifik
  [√] Metrik jelas
  [√] Baseline ada
  [√] Konteks disebutkan
  [√] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Website profile sekolah berbasis WordPress lebih efektif dalam penyampaian informasi dibandingkan media konvensional.
  Jenis kontribusi        : [√] Improvement  [ ] Comparison  [ ] Novel approach
  Gap yang diisi          : Kurangnya media informasi sekolah yang efektif dan mudah diakses.

Hypothesis Pair:
  H₀ : Tidak ada perbedaan signifikan antara website profile sekolah berbasis WordPress dan media informasi konvensional dalam efektivitas penyampaian informasi.
  H₁ : Website profile sekolah berbasis WordPress memiliki efektivitas penyampaian informasi yang lebih baik dibandingkan media informasi konvensional.
  Threshold              : ≥ 70% tingkat kepuasan pengguna
  Justifikasi threshold  : Nilai 70% termasuk kategori baik dalam pengukuran keberhasilan sistem informasi.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Penyampaian informasi sekolah masih dilakukan secara manual sehingga informasi kurang efektif dan sulit diakses.

**RQ versi pertama (tulis bebas):**
> Apakah website profile sekolah dapat meningkatkan akses informasi pendidikan?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya | Website profile sekolah berbasis WordPress |
| Metrik terukur | Belum jelas | Belum ada ukuran yang digunakan |
| Baseline | Belum jelas | Belum ada pembanding |
| Dataset/konteks | Ya | SD Negeri 12 Badau |

**Tipe RQ:** [ ] Comparison / [√] Improvement / [ ] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Apakah website profile sekolah berbasis WordPress mampu meningkatkan efektivitas penyampaian informasi dibandingkan media informasi konvensional pada SD Negeri 12 Badau berdasarkan tingkat akses dan kepuasan pengguna?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak ada perbedaan signifikan antara website profile sekolah berbasis WordPress dan media informasi konvensional dalam efektivitas penyampaian informasi di SD Negeri 12 Badau |
| H₁ | Website profile sekolah berbasis WordPress memiliki efektivitas penyampaian informasi yang lebih baik dibandingkan media informasi konvensional di SD Negeri 12 Badau |
| Metrik | Tingkat akses informasi dan kepuasan pengguna |
| Threshold | ≥ 70% tingkat kepuasan pengguna|
| Justifikasi threshold | Nilai 70% sudah termasuk kategori baik dalam pengukuran keberhasilan sistem informasi|

**Apakah hipotesis ini falsifiable?** [√] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Dengan melakukan pengujian kepada pengguna. Jika hasil kepuasan pengguna tidak meningkat atau kurang dari threshold yang ditentukan, maka H₀ diterima.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Apakah website profile sekolah berbasis WordPress mampu meningkatkan efektivitas penyampaian informasi dibandingkan media informasi konvensional pada SD Negeri 12 Badau? |
| Variable (IV) | Jenis media informasi yang digunakan |
| Variable (DV) | Efektivitas penyampaian informasi |
| Metric | Tingkat akses informasi dan kepuasan pengguna |
| Data source | Data kuesioner pengguna dan data akses website |
| Analysis method | Analisis deskriptif dan perbandingan hasil kuesioner |

**Apakah rantai lengkap?** [√] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? Tidak ada, karena seluruh tahapan sudah lengkap.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Pembuatan Website Profile Sekolah untuk Meningkatkan Akses Informasi Pendidikan SD Negeri 12 Badau
**RQ yang diekstrak:** Apakah website profile sekolah dapat membantu meningkatkan akses informasi pendidikan di SD Negeri 12 Badau?
**Komponen yang hilang:** RQ tersebut belum memiliki metrik yang jelas dan belum menyebutkan baseline atau pembanding secara spesifik sehingga pengukurannya masih kurang detail.
