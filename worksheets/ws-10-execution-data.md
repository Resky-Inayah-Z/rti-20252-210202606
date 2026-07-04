# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1     | Pengujian website oleh responden siswa | N/A | Website WordPress dan Google Form | Planned | - | hasil_siswa.csv |
| 2     | Pengujian website oleh responden guru | N/A | Website WordPress dan Google Form | Planned | - | hasil_guru.csv |
| 3     | Pengujian website oleh responden masyarakat | N/A | Website WordPress dan Google Form | Planned | - | hasil_masyarakat.csv |

Jumlah runs per skenario : 2 kali
Total runs               : 6 kali

DATA LOG (per run):
  Run ID    : RUN-001
  Timestamp : 04 Juli 2026
  Skenario  : Pengujian website oleh responden siswa.
  Input     : Website profil SMP Negeri 1 Alian berbasis WordPress. Responden diminta membuka halaman Home, Profil, Visi Misi, Berita, Galeri, dan Kontak.
  Output    : Hasil penelitian dari Google Form. Skor kepuasan pengguna. Masukan atau saran dari responden.
  Anomali   : Tidak ada.
  Catatan   : Pengujian berjalan dengan baik dan seluruh fitur website dapat diakses oleh responden.
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 | Pengujian website oleh responden siswa | N/A | Website WordPress dan Google Form | Planned |
| 2 | Pengujian website oleh responden guru | N/A | Website WordPress dan Google Form | Planned |
| 3 | Pengujian website oleh masyarakat | N/A | Website WordPress dan Google Form | Planned |
| 4 | Pengujian ulang responden siswa | N/A | Website WordPress dan Google Form | Planned |
| 5 | Pengujian ulang responden guru | N/A | Website WordPress dan Google Form | Planned |
| 6 | Pengujian ulang responden masyarakat | N/A | Website WordPress dan Google Form | Planned |

**Total skenario:** 3
**Run per skenario:** 2 kali
**Total run keseluruhan:** 6 kali

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | RUN-001 |
| Timestamp | 04 Juli 2026 |
| Skenario | Pengujian website oleh responden siswa |
| Status | Berhasil |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed | N/A |
| Platform | WordPress |
| Browser | Google Chrome |
| Perangkat | Laptop/Smartphone |
| Instrumen | Google Form |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Kemudahan penggunaan | Integer | 1-5 |
| Kecepatan memperoleh informasi | Integer | 1-5 |
| Tampilan website | Integer | 1-5 |
| Kelengkapan informasi | Integer | 1-5 |
| Kepuasan pengguna | Integer | 1-5 |

**Format output:** [✅] CSV / [ ] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash) | Website tidak dapat diakses saat pengujian | Mencatat penyebab gangguan, memperbaiki masalah, kemudian melakukan pengujian ulang. |
| Hasil ekstrem | Salah satu responden memberikan nilai sangat rendah pada seluruh aspek | Memastikan responden telah mencoba seluruh fitur website, kemudian mencatat hasil tersebut sebagai bagian dari data penelitian. |
| Waktu eksekusi anomali | Website lambat dimuat karena koneksi internet | Mencatat kondisi jaringan saat pengujian dan mengulang pengujian jika diperlukan. |
| Inkonsistensi dengan run lain | Jawaban responden berbeda jauh dibanding responden lainnya | Memeriksa kembali hasil kuesioner dan memastikan tidak terjadi kesalahan pengisian sebelum dilakukan analisis. |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Saya belum pernah melakukan pengujian penelitian seperti ini. Selama ini saya lebih sering membuat sistem atau menyelesaikan tugas tanpa menyusun execution plan maupun melakukan pengujian secara berulang. Saya juga belum terbiasa mencatat setiap hasil pengujian secara terstruktur, sehingga belum mengetahui apakah hasil yang diperoleh sudah benar-benar konsisten atau belum.
**Yang akan dilakukan berbeda:**
> Setelah mempelajari materi ini, saya memahami bahwa pelaksanaan eksperimen tidak cukup hanya dilakukan satu kali. Ke depannya saya akan menyusun rencana pengujian terlebih dahulu, melakukan beberapa kali pengujian pada setiap skenario, serta mencatat seluruh hasil pengujian, termasuk jika terjadi kendala atau anomali. Dengan cara tersebut, hasil penelitian menjadi lebih lengkap, lebih mudah dianalisis, dan kesimpulan yang diperoleh dapat lebih dipercaya.
