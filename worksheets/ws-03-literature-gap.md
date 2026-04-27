# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Perancangan Website Profil Sekolah sebagai Media Informasi Berbasis WordPress
Database   : Google Scholar / Jurnal Nasional
Query      : Website sekolah, profil sekolah, sistem informasi sekolah, wordpress
Tahun      : 2022-2025
Hasil awal : 8 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Andika Saputra et al. | 2025 | WordPress + Partisipatif | Profil Sekolah | Website berhasil mempermudah penyampaian informasi sekolah | Keterampilan digital pengguna masih terbatas |
| Firman et al. | 2023 | Prototype + WordPress | Data Sekolah | Website layak digunakan sebagai media informasi sekolah | Fitur masih terbatas |
| Bagus Ageng Alfahri et al. | 2025 | SDLC Prototyping | Profil Sekolah | Informasi lebih cepat dan mudah diakses | Fitur belum lengkap |
| Muhammad Prayoga Indra Surya et al. | 2024 | Agile | Data Sekolah | Sistem berjalan sesuai kebutuhan sekolah | Perlu pengembangan lanjutan |
| Ragil Widodo Saputro et al. | 2022 | Waterfall | Profil TK | Sistem berjalan baik dan membantu penyampaian informasi | Loading masih lambat |

Pola yang ditemukan:
  Metode dominan     : Prototype, SDLC, Agile, dan Waterfall
  Dataset umum       : Data profil sekolah, data guru, data siswa, dan informasi sekolah
  Limitasi berulang  : Fitur masih terbatas, performa sistem belum optimal, dan perlu pengembangan lebih lanjut.

GAP IDENTIFICATION

Gap 1: [Jenis: Method Gap]
  Deskripsi    : Belum banyak penelitian yang menggunakan WordPress sebagai CMS utama untuk pengelolaan website sekolah.
  Bukti        : Dari beberapa penelitian,sebagaian besar masih menggunakan PHP native dan MySQL.
  Signifikansi : WordPress lebih mudah digunakan, terutama untuk sekolah yang tidak memiliki tenaga IT khusus.

Gap 2: [Jenis: Context Gap]
  Deskripsi    : Belum ada implementasi website profil sekolah berbasis WordPress pada SMP Negeri 1 Alian
  Bukti        : Objek penelitian sebelumnya masih pada sekolah lain seperti TK dan SD.
  Signifikansi : Penelitian ini dapat menjadi solusi baru sesuai kebutuhan sekolah yang menjadi objek penelitian.

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
| Website sekolah SD Negeri 42 Kota Sorong | Sama-sama website sekolah berbasis WordPress | Mewakili implementasi WordPress di sekolah | Firman et al., 2023 |
| Website profile SD Negeri 12 Badau | Fokus pada profil sekolah | Relevan sebagai pembanding sistem informasi sekolah | Andika Saputra et al., 2025 |
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Perancangan Website Profil Sekolah sebagai Media Informasi Berbasis WordPress
**Query pencarian:** Website sekolah, profil sekolah, sistem informasi sekolah, wordpress
**Database:** Google Scholar / Jurnal Nasional

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Andika Saputra et al. | 2025 | WordPress + Partisipatif | Data profil sekolah | Website berhasil dibangun dan mempermudah akses informasi sekolah | Keterampilan digital guru masih terbatas |
| 2 | Firman et al. | 2023 | Prototype + WordPress | Data Sekolah | Website layak digunakan sebagai media informasi sekolah | Fitur masih fokus pada informasi dasar |
| 3 | Bagus Ageng Alfahri et al. | 2025 | SDLC | Profil Sekolah | Sistem membantu penyampaian informasi menjadi lebih cepat dan interaktif | Fitur masih sederhana |
| 4 | Muhammad Prayoga Indra Surya et al. | 2024 | Agile | Data Sekolah | Sistem informasi sekolah berbasis web berhasil memenuhi kebutuhan sekolah | Perlu pengembangan lebih lanjut |
| 5 | Ragil Widodo Saputro et al. | 2022 | Waterfall | Profil TK | Sistem informasi berbasis website berjalan dengan baik | Loading masih lambat |

**Pola yang terlihat — Metode dominan:** Metode yang paling sering digunakan adalah Prototype, SDLC, Agile, dan Waterfall
**Limitasi yang berulang:** Fitur masih terbatas, performa sistem belum optimal, dan pengembangan sistem masih perlu ditingkatkan.

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ √ ] Ya / [ ] Tidak | Beberapa website sekolah masih memiliki kendala performa seperti loading lambat dan belum optimal |
| Method Gap | [ √ ] Ya / [ ] Tidak | Belum banyak penelitian yang memanfaatkan WordPress sebagai CMS utama dalam pengembangan website sekolah |
| Data Gap | [ ] Ya / [ √ ] Tidak | Data yang digunakan sudah cukup sesuai dengan kebutuhan penelitian |
| Context Gap | [ √ ] Ya / [ ] Tidak | Belum ada implementasi website sekolah berbasis WordPress pada SMP Negeri 1 Alian |

**Gap utama yang dipilih:** Method Gap dan Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Karena sekolah membutuhkan sistem yang mudah dikelola dan dikembangkan tanpa harus memiliki kemampuan coding yang tinggi. WordPress menjadi solusi yang lebih praktis dan efisien.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | Website sekolah SD Negeri 42 Kota Sorong | Sama-sama menggunakan WordPress dan fokus pada media informasi sekolah | Mewakili implementasi WordPress untuk sekolah | Tidak, karena hanya menerapkan WordPress sebagai media informasi sekolah dan masih menggunakan pendekatan yang umum digunakan | Firman et al., 2023 |
| 2 | Website profile SD Negeri 12 Badau | Sama-sama fokus pada profil sekolah | Implementasi terbaru berbasis WordPress | Tidak, karena penelitian berfokus pada implementasi website profil sekolah, bukan pengembangan metode atau teknologi terbaru | Andika Saputra et al., 2025 |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [√] Tidak
> Justifikasi: Karena kedua baseline dipilih dari penelitian yang memiliki tujuan dan fitur yang hampir sama, sehingga layak dijadikan pembanding.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Perbedaan antara klaim "belum ada yang meneliti" dengan research gap yang valid terletak pada bukti yang digunakan. Jika hanya mengatakan belum ada penelitian tanpa dasar yang jelas, maka itu hanya asumsi. Sedangkan research gap yang valid harus didasarkan pada hasil analisis beberapa penelitian sebelumnya yang menunjukkan adanya kekurangan atau keterbatasan.
> Cara membuktikan bahwa gap tersebut benar-benar ada yaitu dengan mencari dan membandingkan beberapa penelitian yang relevan, lalu melihat pola kelemahan atau kekurangan yang masih bisa dikembangkan pada penelitian berikutnya.
