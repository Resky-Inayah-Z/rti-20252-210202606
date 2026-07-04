# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Apakah penggunaan website profil sekolah berbasis WordPress dapat meningkatkan kepuasan pengguna dibandingkan media sosialdan papan pengumuman sebagai media informasi sebelumnya?
Hypothesis        : Penggunaan website profil sekolah berbasis WordPress dapat meningkatkan kepuasan pengguna dibandingkan media sosial dan papan pengumuman sebagai media informasi sebelumnya. 
Tipe Eksperimen   : [✅] Comparison  [ ] Ablation  [ ] Parameter


Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Pengguna memperoleh informasi melalui media sosial dan papan pengumuman sekolah | Media informasi lama | Responden sama, informasi yang dicari sama, perangkat pengujian sama |
| Treatment | Pengguna memperoleh informasi melalui website profil sekolah berbasis WordPress | Website WordPress | Responden sama, informasi yang dicari sama, perangkat pengujian sama |

Fairness Checklist:

  [✅] Dataset identik untuk semua kondisi
  [✅] Preprocessing setara
  [✅] Tuning effort setara
  [✅] Environment identik
  [✅] Metrik evaluasi sama


Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|

| Internal    | Responden lebih terbiasa menggunakan media sosial dibanding website | Responden diminta mencoba kedua media sebelum mengisi kuesioner |
| External    | Pengujian hanya dilakukan pada pengguna di SMP Negeri 1 Alian | Menambah jumlah responden yang lebih beragam pada penelitian selanjutnya |
| Construct   | Kepuasan pengguna bersifat subjektif | Menggunakan indikator pertanyaan yang jelas pada kuesioner |
| Conclusion  | Jumlah responden yang terlalu sedikit dapat memengaruhi hasil penelitian | Mengumpulkan responden dalam jumlah yang cukup |

Statistical Plan:
  Uji statistik   : Analisis deskriptif kuantitatif menggunakan rata-rata skor kepuasan.
  Justifikasi      : Digunakan untuk mengetahui tingkat kepuasan pengguna berdasarkan hasil kuesioner yang telah diisi oleh responden.
  Alpha            : 0,05
  Effect size min  : Belum ditentukan secara spesifik dan akan disesuaikan dengan hasil pengujian.
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Apakah penggunaan website profil sekolah berbasis WordPress dapat meningkatkan kepuasan pengguna dibandingkan media sosial dan papan pengumuman sebagai media informasi sebelumnya?

**Tipe eksperimen:** [✅] Comparison / [ ] Ablation / [ ] Parameter


| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Pengguna mencari informasi sekolah melalui media sosial dan papan pengumuman | Media informasi lama | Responden sama, informasi yang dicari sama, perangkat sama |
| Treatment | Pengguna mencari informasi sekolah melalui website profil sekolah berbasis WordPress | Website WordPress | Responden sama, informasi yang dicari sama, perangkat sama |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✅ | Informasi yang dicari responden sama pada kedua kondisi |
| Preprocessing setara | ✅ | 	Data dan informasi sekolah yang ditampilkan sama |
| Tuning effort setara | ✅ | Informasi yang tersedia pada kedua media dibuat setara sehingga tidak ada kondisi yang lebih diuntungkan |
| Environment identik | ✅ | Pengujian dilakukan menggunakan perangkat dan jaringan yang sama |
| Metrik evaluasi sama | ✅ | Sama-sama dinilai menggunakan kuesioner kepuasan pengguna |

**Ada yang tidak fair?** [ ] Ya / [✅] Tidak

> Jika ya, bagaimana cara memperbaikinya? ________________

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Responden sudah memiliki pengalaman menggunakan media sosial sehingga penilaian bisa menjadi bias | Responden diminta mencoba kedua media sebelum memberikan penilaian |
| External | Penelitian hanya dilakukan pada lingkungan SMP Negeri 1 Alian | Menambah jumlah dan variasi responden pada penelitian berikutnya |
| Construct | 	Kepuasan pengguna dapat berbeda-beda karena penilaian bersifat subjektif | Menggunakan indikator kuesioner yang jelas dan mudah dipahami |
| Conclusion | Jumlah responden yang sedikit dapat memengaruhi keakuratan hasil | Menambah jumlah responden agar data lebih representatif |

**Ancaman mana yang paling sulit dimitigasi?** External validity.
**Mengapa?**
> Karena penelitian hanya dilakukan pada satu sekolah sehingga hasil yang diperoleh belum tentu sama jika diterapkan pada sekolah lain yang memiliki kondisi dan kebutuhan yang berbeda.


---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua metode diuji menggunakan dataset, kondisi pengujian, dan metrik evaluasi yang sama?
2. Apakah baseline yang digunakan sudah sesuai dan sering digunakan dalam penelitian sebelumnya?
3. Apakah perbedaan hasil yang diperoleh benar-benar signifikan secara statistik?
