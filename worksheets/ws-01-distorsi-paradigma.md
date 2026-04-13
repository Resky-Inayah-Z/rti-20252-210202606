# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Resky Inayah Z
Tanggal          : Sabtu, 4-4-2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Bagaimana cara mengukur akurasi tersebut dan data yang digunakan didapat dari mana, karena angka akurasi bisa  berbeda tergantung data dan cara pengujiannya. Tapi itu semua tergantung dari pemahaman saya. Kalau masih masuk di logika dan saya paham konteksnya, saya akan langsung mempertanyakan. Kalau belum terlalu paham, saya tidak langsung mempertanyakan, tapi saya akan mencari pemahaman dulu melalui internet, seperti membaca artikel atau jurnal ilmiah, serta sedikit bantuan AI. Setelah mulai paham, biasanya baru muncul pertanyaan-pertanyaan yang lebih kritis terhadap klaim tersebut.
   - Data yang dibutuhkan untuk verifikasi: Dataset yang digunakan, jumlah dan jenis data, cara pembagian data, serta metode evaluasi yang dipakai untuk mengukur akurasi. Selain itu, perlu juga melihat apakah pengujian dilakukan pada data lain untuk memastikan hasilnya tidak hanya bagus di satu dataset saja. Hal ini penting karena hasil akurasi bisa terlihat tinggi, tetapi belum tentu mencerminkan performa sebenarnya jika data dan metode pengujiannya tidak tepat.

2. Posisi paradigma:
   - Pendekatan: [✓] Positivis  [ ] Interpretivis  [ ] Design Science  [ ] Mixed
   - Alasan: Karena dalam bidang TI biasanya hasilnya bisa dilihat dari data atau angka, jadi lebih jelas dan bisa dibuktikan.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Data yang digunakan sudah mewakili kondisi sebenarnya, padahal belum tentu.
   - Sumber bias potensial: Data yang dipakai bisa saja terlalu sedikit atau hanya dari satu sumber, jadi hasilnya belum tentu akurat.
   - Langkah mitigasi: Menggunakan data yang lebih banyak dan beragam, serta mencoba melakukan pengujian ulang supaya hasilnya lebih meyakinkan.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Data hasil pengujian tidak akan diubah-ubah walaupun hasilnya tidak sesuai yang diharapkan.
   - Batasan yang diakui sejak awal: Data yang digunakan mungkin masih terbatas dan belum tentu mewakili semua kondisi.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: Penerapan Metode Naive Bayes Dalam Memprediksi Kepuasan Mahasiswa Terhadap Cara Pengajaran Dosen
> Penulis (Tahun): Putri Ramadani, Gunadi Widi Nurcahyo, Billy Hendrik (2024)

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Mengumpulkan data kepuasan mahasiswa terhadap dosen (biasanya dari kuesioner) | Data hanya dari mahasiswa tertentu, bisa jadi tidak mewakili semua mahasiswa |
| Data → Processing | Data dibersihkan dan dikategorikan (puas/tidak puas, dll) | Proses pengolahan bisa menghilangkan data penting atau menyederhanakan opini mahasiswa |
| Processing → Analysis | Menggunakan metode Naive Bayes untuk klasifikasi | Pemilihan metode tidak dibandingkan dengan metode lain secara mendalam |
| Analysis → Inference | Menyimpulkan bahwa metode memiliki akurasi tinggi (misal 98%) | Akurasi tinggi belum tentu valid kalau datanya terbatas atau tidak beragam |
| Inference → Knowledge | Mengklaim metode cocok untuk memprediksi kepuasan mahasiswa secara umum | Generalisasi terlalu luas, padahal belum diuji di kampus lain atau kondisi berbeda |

**Distorsi paling besar di tahap:** Analysis → Inference

**Dua distorsi spesifik yang teridentifikasi:**
1. Sampling bias → data kemungkinan hanya dari satu kampus atau jumlah responden terbatas.
2. Overclaim → langsung menyimpulkan metode sangat akurat tanpa pengujian lebih luas

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Menurut saya, data outlier itu tetap bagian dari data asli, jadi seharusnya tidak langsung dihapus hanya karena bikin hasil jadi jelek. Kalau dihapus, harus ada alasan yang jelas dan masuk akal secara ilmiah. |
| Transparansi | Peneliti harus menjelaskan secara terbuka apakah data outlier dihapus atau tidak. Lebih baik ditampilkan dua hasil sekaligus (dengan dan tanpa outlier), jadi pembaca bisa menilai sendiri. |
| Peer review | Reviewer kemungkinan akan mempertanyakan keputusan penghapusan outlier, apalagi kalau tidak dijelaskan. Bisa dianggap manipulasi data kalau tujuannya hanya untuk bikin hasil terlihat signifikan. |

**Keputusan akhir dan justifikasi:**
> Menurut saya, sebaiknya peneliti tetap melaporkan kedua hasil, yaitu dengan outlier dan tanpa outlier, lalu dijelaskan alasan kenapa outlier tersebut dipertimbangkan untuk dihapus. Hal ini penting supaya penelitian tetap jujur dan transparan. Kalau langsung dihapus tanpa penjelasan, bisa merusak kepercayaan terhadap hasil penelitian, karena terlihat seperti memaksakan hasil agar sesuai dengan harapan.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Analisis Penggunaan Metode Naive Bayes Untuk Memprediksi Kepuasan Mahasiswa Terhadap Cara Pengajaran Dosen

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 | 2 | 3 |
| Jenis data yang dikumpulkan | Data numerik dari hasil kuesioner (misalnya puas/tidak puas) | Pendapat atau pengalaman mahasiswa secara mendalam | Sistem atau model yang dibuat |
| Limitasi paradigma | Tidak terlalu menggali alasan di balik kepuasan mahasiswa | Sulit diukur secara angka | Lebih fokus ke pembuatan sistem, bukan analisis data |

**Paradigma yang dipilih:** Positivis
**Alasan:** Karena penelitian ini menggunakan data berupa angka dari hasil kuesioner, lalu dianalisis menggunakan metode Naive Bayes untuk menghasilkan akurasi. Jadi lebih fokus ke pengukuran dan pembuktian secara objektif. Maka dari itu, pendekatan positivis lebih cocok digunakan.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelum membaca materi ini, saya belum pernah benar-benar mempertanyakan klaim seperti "95% akurat". Biasanya saya langsung percaya saja selama terlihat meyakinkan. Namun setelah membaca materi ini, saya mulai sedikit paham bahwa angka tersebut tidak bisa langsung dipercaya begitu saja.
> Sekarang saya jadi lebih kepikiran, misalnya data yang digunakan itu didapat dari mana, jumlah datanya berapa, dan apakah data tersebut benar-benar mewakili kondisi sebenarnya. Selain itu, saya juga mulai memahami bahwa proses pengolahan dan pengujian data sangat berpengaruh terhadap hasil akhir.
> Jadi, setelah memahami konsep distorasi dalam penelitian, saya jadi lebih hati-hati dan tidak langsung percaya pada hasil, tetapi mencoba melihat proses di baliknya terlebih dahulu.