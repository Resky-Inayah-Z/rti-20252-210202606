# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [✅] Semua skenario tercakup
  [✅] Jumlah run sesuai rencana
  [✅] Tidak ada file output hilang
  Missing: 0 dari 6 data pengujian

Format Consistency:
  [✅] Semua file format sama (CSV)
  [✅] Header konsisten
  [✅] Tipe data konsisten (skor berupa numerik)

Range & Logic:
  [✅] Nilai dalam range masuk akal
  [✅] Tidak ada data yang kosong
  [✅] Skor kuesioner berada pada rentang 1-5
  Anomali ditemukan: Tidak ada

Cross-Validation:
  [✅] Hasil antar-run menunjukkan pola yang relatif konsisten
  [✅] Data sesuai dengan tujuan penelitian

Keputusan:
  [✅] Data siap analisis
  [ ] Perlu cleaning
  [ ] Perlu re-run (skenario: -)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| Pengujian oleh responden siswa | 2 | 2 | 0 | - |
| Pengujian oleh responden guru | 2 | 2 | 0 | - |
| Pengujian oleh responden masyarakat | 2 | 2 | 0 | - |

**Total expected:** 6 | **Total actual:** 6 | **Missing:** 0 

**Keputusan untuk data missing:**
> Seluruh data yang direncanakan telah terkumpul sehingga tidak diperlukan pengambilan data ulang.

---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset sampel (atau data Anda sendiri):**

| Run | Skor Kepuasan |
|-----|-------------|
| 1 | 5 |
| 2 | 4 |
| 3 | 5 |
| 4 | 4 |
| 5 | 5 |
| 6 | 4 |

**Deteksi outlier:**
- Q1 = 4 | Q3 = 5 | IQR = 1
- Batas bawah (Q1 - 1.5×IQR) = 2,5
- Batas atas (Q3 + 1.5×IQR) = 6,5
- Outlier terdeteksi: Tidak ada.

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Tidak ada | - | Seluruh data masih berada dalam batas normal berdasarkan perhitungan IQR. | Data dapat digunakan untuk tahap analisis. |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 100% data pengujian telah berhasil dikumpulkan sesuai dengan rencana.
**2. Format:** [✅] Konsisten / [ ] Ada inkonsistensi: ____
**3. Range check (anomali):** Tidak ditemukan data di luar rentang penilaian 1-5.
**4. Logic check:** [✅] Parameter sesuai plan / [ ] Ada ketidaksesuaian: ____

**Kesimpulan:** [✅] Data siap analisis / [ ] Perlu tindakan: ____

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Menurut saya, data yang benar belum tentu dapat langsung dipercaya karena masih perlu dipastikan apakah data tersebut lengkap, konsisten, dan sesuai dengan tujuan penelitian. Sementara itu, data yang dipercaya adalah data yang telah melalui proses validasi sehingga layak digunakan untuk analisis.
> Proses validasi tetap diperlukan meskipun data dikumpulkan secara otomatis, karena masih ada kemungkinan terjadi kesalahan, seperti data yang tidak lengkap, kesalahan pengisian, atau hasil yang tidak sesuai dengan rencana pengujian. Dengan adanya validasi, data yang digunakan dalam penelitian menjadi lebih akurat dan hasil analisis yang diperoleh juga lebih dapat dipertanggungjawabkan.
