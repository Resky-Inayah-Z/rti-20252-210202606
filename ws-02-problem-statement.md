# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Sistem Informasi
  Konteks  : Pengelolaan dana Karang Taruna di lingkungan desa yang masih belum transparan kepada warga.

System Context
  Input       : Data pemasukan (iuran warga, donatur) dan pengeluaran (biaya acara, perlengkapan, hadiah).
  Process     : Pengurus karang taruna mengelola dan mencatat dana kegiatan. 
  Output      : Laporan penggunaan dana kegiatan.
  Outcome     : Tingkat pemahaman dan kepercayaan warga terhadap penggunaan dana.
  Constraints : Tidak adanya sistem transparansi, keterbatasan penggunaan teknologi, serta laporan tidak disampaikan secara rutin.
  Stakeholders: Warga, anggota Karang Taruna, serta pengurus lingkungan (RT/RW).

Fenomena → Problem
  Fenomena yang diamati             : Dalam kegiatan Karang Taruna, sering dilakukan pengumpulan dana dari warga untuk berbagai acara seperti lomba Agustusan, kegiatan Ramadhan seperti berbagi takjil, oncor keliling, dan acara jalan sehat.
  Gejala (symptom) yang terukur     : Warga sering mempertanyakan penggunaan dana karena tidak mengetahui secara jelas total pemasukan, pengeluaran, dan sisa dana.
  Masalah yang didiagnosis          : Informasi penggunaan dana hanya diketahui oleh anggota Karang Taruna serta pengurus lingkungan (RT/RW).
  Masalah riset (researchable)      : Belum adanya mekanisme yang efektif untuk menyampaikan informasi penggunaan dana Karang Taruna secara transparan dan mudah diakses oleh warga.
  Variabel yang terukur             : Tingkat transparansi informasi (%), jumlah laporan yang tersedia, dan tingkat kepuasan warga (%).

Problem Quality Check
  [√] Clarity — Apakah satu orang membaca akan paham? Masalah sudah jelas dan mudah dipahami.
  [√] Measurability — Apakah ada metrik kuantitatif? Memiliki indikator yang dapat diukur.
  [√] Relevance — Apakah penting untuk domain? Relevan dengan kondisi di masyarakat.
  [√] Testability — Apakah bisa gagal? Dapat diuji melalui penerapan sistem.
  [√] Impact — Apakah ada kontribusi jika terjawab? Memberikan dampak terhadap kepercayaan warga.

Problem Statement (1 paragraf):
  Dalam kegiatan Karang Taruna, seperti acara lomba Agustusan dan kegiatan Ramadhan, sering dilakukan pengumpulan dana dari warga untuk mendukung pelaksanaan acara. Namun, tidak semua warga mengetahui secara jelas bagaimana dana tersebut digunakan, termasuk total pemasukan, pengeluaran, dan sisa dana. Hal ini menyebabkan munculnya pertanyaan serta kurangnya transparansi dalam pengelolaan dana. Permasalahan ini terjadi karena informasi keuangan hanya diketahui oleh anggota Karang Taruna serta pengurus lingkungan (RT/RW) dan tidak disampaikan secara terbuka kepada seluruh warga. Oleh karena itu, diperlukan penelitian untuk menganalisis bagaimana penerapan sistem informasi dapat menyajikan laporan penggunaan dana Karang Taruna secara transparan dan mudah diakses oleh warga, dengan variabel pengukuran berupa tingkat transparansi informasi, jumlah laporan yang tersedia, serta tingkat kepuasan warga.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Sistem Informasi Transparansi Dana Karang Taruna Berbasis Web

| Tahap | Hasil |
|-------|-------|
| Reality | Dalam kegiatan Karang Taruna seperti lomba Agustusan atau acara Ramadhan, sering dilakukan pengumpulan dana dari warga. |
| Observed Issue (Symptom) | Warga sering mempertanyakan penggunaan dana karena tidak mengetahui secara jelas total pemasukan, pengeluaran, dan sisa dana. |
| Diagnosed Problem (Root Cause) | Informasi penggunaan dana hanya diketahui oleh anggota Karang Taruna serta pengurus lingkungan (RT/RW) dan tidak disampaikan secara terbuka kepada seluruh warga. |
| Researchable Problem | Belum adanya mekanisme yang efektif untuk menyampaikan informasi penggunaan dana Karang Taruna secara transparan dan mudah diakses oleh warga. |
| Measurable Variable | Tingkat transparansi (%), jumlah laporan yang tersedia, tingkat kepuasan warga (%). |

**Apakah terjebak solution-first thinking?** [ ] Ya / [√] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data pemasukan (iuran warga, donatur) dan pengeluaran (biaya acara, perlengkapan, hadiah). |
| Process | Sistem mengelola dan menyusun data keuangan menjadi laporan yang jelas dan terstruktur. |
| Output | Informasi laporan dana yang dapat diakses oleh warga. |
| Outcome | Warga lebih memahami penggunaan dana dan meningkatnya kepercayaan terhadap Karang Taruna. |
| Constraints | Tidak semua warga terbiasa menggunakan teknologi, serta keterbatasan akses internet. |
| Stakeholders | Warga, anggota Karang Taruna, serta pengurus lingkungan (RT/RW). |

**Komponen mana yang paling relevan dengan masalah riset?** Process

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Sudah jelas karena berdasarkan kondisi nyata di lingkungan masyarakat. |
| Measurability | 4 | Dapat diukur melalui jumlah laporan dan tingkat kepuasan warga. |
| Relevance | 5 | Sangat relevan dengan kebutuhan transparansi di masyarakat. |
| Testability | 4 | Dapat diuji melalui penerapan sistem informasi. |
| Impact | 5 | Memberikan dampak pada peningkatan kepercayaan dan partisipasi warga. |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
> Pengelolaan dana Karang Taruna yang berasal dari iuran warga seringkali tidak disertai dengan laporan yang transparan, sehingga menimbulkan pertanyaan dan keraguan dari masyarakat terkait penggunaan dana. Hal ini terjadi karena informasi keuangan hanya diketahui oleh anggota Karang Taruna serta pengurus lingkungan (RT/RW) dan tidak disampaikan secara terbuka kepada seluruh warga. Oleh karena itu, penelitian ini bertujuan untuk menganalisis bagaimana penerapan sistem informasi dapat meningkatkan transparansi pengelolaan dana serta kepercayaan warga, yang diukur melalui tingkat transparansi informasi, jumlah laporan yang tersedia, dan tingkat kepuasan warga.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Menurut saya, masalah dalam coding dan masalah dalam riset itu berbeda. Pada coding, masalah biasanya terlihat langsung seperti error atau bug sehingga fokusnya adalah memperbaiki. Sedangkan dalam riset, masalah tidak selalu terlihat secara langsung dan perlu dianalisis terlebih dahulu untuk menemukan akar permasalahan. Selain itu, masalah dalam riset juga harus dapat diukur dan dibuktikan menggunakan data, sehingga pendekatannya lebih sistematis dibandingkan dengan penyelesaian masalah pada coding.
