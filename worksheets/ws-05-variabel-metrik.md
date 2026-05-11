# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Apakah website profile sekolah berbasis WordPress mampu meningkatkan efektivitas penyampaian informasi dibandingkan media informasi konvensional pada SD Negeri 12 Badau?
| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| Media Informasi | IV | Penggunaan media informasi sekolah | Website WordPress dan media konvensional | Nominal | - | Membandingkan media yang digunakan | Karena penelitian fokus membandingkan website dengan cara lama |
| Efektivitas penyampaian informasi | DV | Keberhasilan penyampaian informasi | Kepuasan pengguna dan akses informasi | Ordinal | Skor 1-5 | Kuesioner dan data akses website | Karena efektivitas bisa dilihat dari kepuasan pengguna |
| Responden pengguna | CV | Jenis pengguna sistem | Siswa dan masyarakat sekolah | Nominal | - | Menentukan responden yang sama | Agar hasil penelitian tidak bias |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [√] Setiap langkah terdokumentasi
  [√] Tidak ada "lompatan logis"
  [√] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Apakah website profile sekolah berbasis WordPress mampu meningkatkan efektivitas penyampaian informasi dibandingkan media informasi konvensional pada SD Negeri 12 Badau?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Media informasi | IV | Metode penyampaian informasi | Website WordPress dan media konvensional | Nominal | — |
| Efektivitas informasi | DV | Tingkat keberhasilan penyampaian informasi | Kepuasan pengguna dan jumlah akses informasi | Ordinal | Skor 1-5 |
| Responden | CV | Konsistensi pengguna | Siswa dan masyarakat sekolah | Nominal | — |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [√] Tidak
> Jika ya, di mana? Tidak ada, karena semua variabel dan metrik masih saling berhubungan.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 4 | Kepuasan pengguna cukup mewakili efektivitas informasi |
| Sensitive | 4 | Perubahan kecil masih bisa terlihat dari hasil kuesioner |
| Feasible | 5 | Data mudah dikumpulkan melalui Google Form atau kuesioner |

**Apakah perlu secondary metric?** [√] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Jumlah kunjungan website, karena dapat mendukung hasil kepuasan pengguna dan menunjukkan apakah website benar-benar digunakan.

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika hampir semua pengguna memberikan nilai 5 pada kuesioner, maka perbedaan kualitas website akan sulit terlihat.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | *Apakah semua data point terkumpul?* | Bisa saja ada responden yang tidak mengisi lengkap | Membuat semua pertanyaan wajib diisi |
| Consistency | *Apakah ada kontradiksi internal?* | Ada kemungkinan jawaban tidak konsisten | Mengecek ulang data sebelum analisis |
| Validity | *Apakah benar-benar mengukur yang dimaksud?* | Data sudah sesuai dengan tujuan penelitian | Menggunakan pertanyaan yang relevan |
| Representativeness | *Apakah sampel mewakili populasi target?* | Sampel berasal dari siswa dan masyarakat sekolah | Mengambil responden dari beberapa kelompok |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik setelah melihat data dianggap p-hacking karena peneliti bisa memilih hasil yang paling bagus dan mengabaikan hasil lainnya. Sedangkan eksplorasi data yang sah tetap menggunakan metrik awal dan hanya mencari pola tambahan tanpa mengubah metrik utama penelitian.
> 
