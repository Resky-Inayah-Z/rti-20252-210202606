# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

## Ringkasan Materi

### Data Refinement Pipeline

```
Raw Data → Cleaning → Transformation → Normalization → Processed Data → Analysis Ready
```

Setiap tahap memiliki tujuan berbeda. **Preprocessing bukan langkah teknis biasa** — setiap keputusan preprocessing adalah keputusan riset yang bisa mengubah kesimpulan.

### Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|----------|
| **Consistency** | Metode sama untuk data yang sama |
| **Transparency** | Setiap langkah terdokumentasi |
| **Reproducibility** | Orang lain bisa mengulang dengan hasil sama |
| **Minimal Distortion** | Ubah sesedikit mungkin; jika normalisasi tidak perlu, jangan lakukan |

### Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|---------|--------|
| **Missing values** | | |
| — Listwise deletion | Missing < 5%, random | Data loss |
| — Mean/median imputation | Sedikit missing, dist. normal | Mengurangi variabilitas |
| — Model-based imputation | Banyak missing, pola sistematis | Introduces dependency |
| — Flag & separate | Missing karena alasan substantif | Kompleksitas analisis |
| **Duplikat** | Identifikasi → verifikasi → hapus | False positive (data mirip ≠ duplikat) |
| **Error format** | Standardisasi tipe, encoding | Kehilangan informasi saat konversi |

### Normalisasi — Kapan & Metode Mana

| Metode | Formula | Output | Sensitif Outlier? |
|--------|---------|--------|-------------------|
| Min-max | (x-min)/(max-min) | [0, 1] | Ya |
| Z-score | (x-mean)/std | Unbounded | Lebih robust |
| Robust scaling | (x-median)/IQR | Unbounded | Paling robust |

**Kunci:** Parameter normalisasi harus dihitung dari **training set saja** — bukan seluruh data. Pelanggaran = **data leakage**.

### Data Leakage Prevention

Data leakage terjadi ketika informasi dari test set "bocor" ke preprocessing:
- Normalisasi parameter dari seluruh dataset ← **SALAH**
- Cross-validation dilakukan sebelum split ← **SALAH**
- Feature selection menggunakan label test set ← **SALAH**

### Jebakan Kognitif

1. "Preprocessing cuma teknis — tidak perlu detail" → bisa ubah kesimpulan
2. "Lebih banyak preprocessing = lebih bersih = lebih baik" → over-processing distorsi data
3. "Normalisasi selalu diperlukan" → belum tentu, tergantung metode analisis
4. "Imputation sama untuk semua situasi" → strategi harus sesuai konteks

---

## Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : Data kuesioner kepuasan pengguna website profil SMP Negeri 1 Alian berbasis WordPress
Jumlah data awal  : Belum tersedia (pengumpulan data belum dilakukan)

Cleaning:
| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing | Belum diketahui | Akan diperiksa setelah data terkumpul | Pengumpulan data belum dilakukan |
| Duplikat| Belum diketahui | Akan dilakukan pengecekan data ganda | Menjaga kualitas data |
| Error   | Belum diketahui | Akan dilakukan standardisasi format data | Menjaga konsistensi data |

Transformation:
| Transformasi | Variabel | Detail | Alasan |
|-------------|----------|--------|--------|
| Belum dilakukan | - | - | Menunggu data hasil penelitian |

Normalization:
  Metode    : Belum ditentukan
  Alasan    : Menyesuaikan metode analisis yang digunakan
  Parameter : Akan dihitung dari training set apabila diperlukan

Leakage Check:
  [✅] Parameter normalisasi akan dihitung dari training set saja apabila diperlukan.
  [✅] Tidak ada informasi test set yang digunakan pada tahap preprocessing
  [✅] Cross-validation akan dilakukan setelah train-test split apabila diperlukan.

Jumlah data akhir : Belum dapat ditentukan
Script tersedia   : [ ] Ya → path: ____ | [✅] Belum
```

---

## Latihan 1 — Cleaning Plan

Periksa dataset Anda (atau dataset contoh) dan dokumentasikan masalah yang ditemukan.

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing data | Belum diketahui | Akan diperiksa setelah data terkumpul | Pengumpulan data belum dilakukan |
| Data duplikat | Belum diketahui | Akan dilakukan pengecekan data ganda | Menjamin setiap responden hanya tercatat satu kali |
| Error format | Belum diketahui | Standardisasi format data | Agar data memiliki format yang konsisten |

**Jumlah data sebelum cleaning:** Belum diketahui
**Jumlah data setelah cleaning:** Belum diketahui
**Persentase data yang hilang/berubah:** Belum dapat ditentukan.

---

## Latihan 2 — Normalisasi Decision

Tentukan apakah data Anda perlu normalisasi, dan jika ya, metode apa yang tepat.

| Variabel | Range Asli | Distribusi | Outlier? | Metode Normalisasi | Alasan |
|----------|-----------|-----------|----------|-------------------|--------|
| Skor kepuasan pengguna | 1-5 | Belum diketahui | Belum diketahui | Belum ditentukan | Keputusan normalisasi akan disesuaikan dengan metode analisis setelah data terkumpul. |

**Apakah normalisasi diperlukan?** [✅] Belum dapat ditentukan. 
**Justifikasi:**
> Penelitian masih berada pada tahap proposal sehingga belum terdapat data yang dapat dianalisis. Keputusan mengenai normalisasi akan ditentukan setelah data penelitian berhasil dikumpulkan dan disesuaikan dengan metode analisis yang digunakan.

**Leakage check:**
- [✅] Parameter normalisasi akan dihitung dari training set saja apabila diperlukan.
- [✅] Normalisasi akan diterapkan setelah pembagian data (train-test split) apabila penelitian memerlukan metode machine learning.

---

## Latihan 3 — Preprocessing Report

Buat ringkasan preprocessing lengkap — dokumentasi yang cukup bagi orang lain untuk mereplikasi.

```
PREPROCESSING SUMMARY

1. Dataset: Data kuesioner kepuasan pengguna website profil SMP Negeri 1 Alian berbasis WordPress
2. Data awal: Belum tersedia
3. Cleaning:
   - Missing values: Belum diketahui
   - Duplikat: Belum diketahui
   - Error: Belum diketahui
4. Transformation: Belum dilakukan
5. Normalisasi: Belum ditentukan
6. Data akhir: Belum dapat ditentukan
7. Leakage check: Akan diterapkan pada tahap analisis apabila diperlukan
```

---

## Refleksi

> Apakah Anda pernah melakukan normalisasi "karena biasa dilakukan" tanpa mempertimbangkan apakah benar-benar diperlukan? Apa risiko over-preprocessing?

> Karena penelitian saya masih berada pada tahap proposal, saya belum melakukan proses preprocessing maupun normalisasi data. Dari materi ini saya memahami bahwa normalisasi tidak selalu diperlukan, tetapi harus disesuaikan dengan karakteristik data dan metode analisis yang digunakan. Over-preprocessing dapat mengubah karakteristik asli data sehingga hasil analisis menjadi kurang akurat atau bahkan menghasilkan kesimpulan yang keliru.
> 
