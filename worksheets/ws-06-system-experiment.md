# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Bagaimana perancangan website profile sekolah yang responsif dapat membantu pengguna dalam memperoleh informasi di SMP Negeri 1 Alian?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
| Desain website responsif | IV | Tampilan desktop dan mobile website | Mengubah layout dan tampilan website |
| Kemudahan memperoleh informasi | DV | Aktivitas pengguna saat menggunakan website | Diukur dari feedback pengguna setelah mencoba website |
| Konten informasi sekolah | CV | Isi website profile sekolah | Informasi dibuat tetap selama pengujian |

4 Prinsip Desain:
  [✅] Traceability — Setiap komponen sistem berhubungan dengan variabel penelitian
  [✅] Variable Isolation — Tampilan website dapat diubah tanpa mengubah isi informasi sekolah
  [✅] Measurement Integration — Sistem menyediakan proses pengambilan feedback pengguna
  [✅] Reproducibility — Pengujian dapat dilakukan kembali dengan kondisi yang sama

Experimental Setup:
  Input data     : Data profil SMP Negeri 1 Alian
  Parameter      : Tampilan desktop, mobile, dan navigasi website
  Output format  : Feedback pengguna mengenai kemudahan penggunaan website
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Bagaimana perancangan website profile sekolah yang responsif dapat membantu pengguna dalam memperoleh informasi di SMP Negeri 1 Alian?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| Desain website responsif | IV | Tampilan website desktop dan mobile | Mengubah desain layout website |
| Kemudahan memperoleh informasi | DV | Aktivitas pengguna pada website | Diukur dari feedback pengguna setelah mencoba website |
| Informasi sekolah | CV | Konten website | Data informasi dibuat tetap selama pengujian |

**Apakah semua variabel bisa di-map?** [✅] Ya / [ ] Tidak
> Semua variabel penelitian sudah memiliki komponen sistem masing-masing.

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | ✅ | Setiap variabel memiliki hubungan dengan komponen website |
| Modularity | ✅ | Tampilan website dapat diubah tanpa mengubah isi informasi sekolah |
| Controllability | ✅ | Informasi sekolah dibuat tetap selama pengujian |
| Measurability | ✅ | Pengukuran dilakukan melalui feedback pengguna setelah mencoba website |

**Prinsip mana yang paling sulit dipenuhi?** Measurability
**Strategi untuk mengatasinya:**
> Menggunakan feedback pengguna secara langsung setelah mencoba website agar hasil pengukuran lebih jelas dan sesuai pengalaman pengguna.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅ Tampilan responsif | ✅ Navigasi jelas | ✅ Informasi lengkap | Pengguna lebih mudah memperoleh informasi |
| – A | ❌ Tampilan tidak responsif | ✅ | ✅ | Pengguna mobile lebih sulit mengakses website |
| – B | ✅ | ❌ Navigasi kurang jelas | ✅ | Pengguna kesulitan mencari menu tertentu |
| – C | ✅ | ✅ | ❌ Informasi kurang lengkap | Pengguna kurang memperoleh informasi yang dibutuhkan |

**Komponen mana yang diprediksi paling berkontribusi?** Navigasi website
**Mengapa?**
> Karena navigasi membantu pengguna menemukan informasi dengan lebih cepat dan mempermudah penggunaan website.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Jika sistem langsung dibuat seperti produk lengkap dengan banyak fitur, penelitian bisa menjadi kurang fokus karena terlalu banyak fitur dan komponen yang memengaruhi hasil eksperimen. Akibatnya, peneliti sulit mengetahui bagian mana yang benar-benar berpengaruh terhadap hasil penelitian.
> Arsitektur modular penting dalam riset karena setiap komponen website dapat diuji secara terpisah, seperti tampilan responsif, navigasi, dan informasi sekolah. Dengan begitu proses penelitian menjadi lebih mudah dikontrol dan hasil pengujian lebih jelas.
