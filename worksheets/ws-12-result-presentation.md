# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : Bagaimana tingkat kepuasan pengguna terhadap website profil SMP Negeri 1 Alian berbasis WordPress?
Metrik Utama      : Nilai rata-rata kepuasan pengguna

Tabel Hasil:
| Skenario | Skor Kepuasan (mean ± std) | Kemudahan Penggunaan (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Responden siswa | 4,52 ± 0,31 | 4,61 ± 0,28 | 30 |
| Responden guru | 4,68 ± 0,25 | 4,70 ± 0,22 | 15 |
| Responden masyarakat | 4,44 ± 0,37 | 4,48 ± 0,35 | 20 |

Visualisasi yang Direncanakan:
| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
| 1 | Bar chart | Perbandingan rata-rata kepuasan setiap kelompok responden | Mean skor kepuasan |
| 2 | Bar chart | Perbandingan kemudahan penggunaan website | Mean kemudahan penggunaan |

Bias Check:
  [✅] Y-axis mulai dari 0 (atau dijustifikasi)
  [✅] Error bar ditampilkan
  [✅] Semua data disertakan (tidak cherry-picked)
  [✅] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Skenario | Skor Kepuasan (mean ± std) | Kemudahan Penggunaan (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Responden guru | 4,68 ± 0,25 | 4,70 ± 0,22 | 15 |
| Responden siswa | 4,52 ± 0,31 | 4,61 ± 0,28 | 30 |
| Responden masyarakat | 4,44 ± 0,37 | 4,48 ± 0,35 | 20 |

**Checklist tabel:**
- [✅] Self-contained (judul jelas, satuan ada, N tercantum)
- [✅] Mean ± std (bukan single number)
- [✅] Diurutkan berdasarkan metrik utama
- [✅] Format konsisten di semua baris

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Bar chart + error bar | Membandingkan tingkat kepuasan pengguna | Mean skor kepuasan ± std |
| 2 | Bar chart + error bar | Membandingkan kemudahan penggunaan website | Mean kemudahan penggunaan ± std |
| 3 | Box plot | Menunjukkan sebaran skor kepuasan dari setiap kelompok responden | Seluruh skor kuesioner |

---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Ya. Karena sumbu Y dimulai dari angka 90, selisih nilai terlihat jauh lebih besar daripada kondisi sebenarnya. |
| Apakah error bar ditampilkan? | Tidak. |
| Apakah semua kondisi ditampilkan? | Ya. |
| Apa solusinya? | Menggunakan sumbu Y yang dimulai dari 0 dan menambahkan error bar agar perbedaan data dapat ditampilkan dengan lebih objektif. |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [✅] Semua bias check lulus
- [ ] Ada yang perlu diperbaiki: -

---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Menurut saya, tabel dan grafik memiliki fungsi yang berbeda sehingga keduanya tetap diperlukan. Tabel digunakan untuk menampilkan data secara rinci dan memudahkan pembaca melihat nilai setiap hasil pengujian. Sementara itu, grafik membantu memperlihatkan pola atau perbandingan data sehingga lebih mudah dipahami secara visual.
> Saya belum pernah membuat grafik yang menyesatkan secara sengaja. Namun, setelah mempelajari materi ini saya mengetahui bahwa pemilihan skala, jenis grafik, dan cara penyajian data dapat memengaruhi cara pembaca memahami hasil penelitian. Oleh karena itu, saya akan lebih memperhatikan penyajian grafik agar informasi yang ditampilkan tetap sesuai dengan data yang diperoleh.
