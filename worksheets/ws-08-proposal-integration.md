# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):
```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```
Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [ ] Problem → Gap: masalah terdokumentasi di literatur
  [ ] Gap → RQ: pertanyaan menjawab gap spesifik
  [ ] RQ → Hypothesis: hipotesis memprediksi jawaban
  [ ] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [ ] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [ ] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [ ] Istilah sama di semua bagian
  [ ] Variabel di RQ = variabel di hipotesis = metrik di desain
  [ ] Scope tidak berubah dari masalah ke eksperimen

Cognitive Trap Checklist:
  [ ] Tidak ada paragraf "promosi" di pendahuluan (hanya data & gap)
  [ ] Metodologi disesuaikan ke RQ, bukan copy-paste textbook
  [ ] Timeline sudah ditambah buffer 30-50% dari estimasi awal
  [ ] Proposal mengakui kemungkinan H0 tidak ditolak (honest uncertainty)
  [ ] Tidak ada klaim "pasti berhasil" atau "meningkatkan signifikan"

Rubrik Self-Assessment:
| Kriteria     | 1 (Lemah)                                        | 2 (Cukup)                                     | 3 (Baik)                                           | Skor |
|------------- |--------------------------------------------------|-----------------------------------------------|----------------------------------------------------|------|
| Koherensi    | >2 koneksi vertikal terputus                     | 1-2 koneksi lemah, argumen masih bisa diikuti | Semua 6 koneksi terhubung, red thread jelas        |      |
| Specificity  | Variabel/metrik masih abstrak, tidak ada angka   | Sebagian metrik terdefinisi numerik           | Semua metrik + threshold + unit pengukuran jelas   |      |
| Feasibility  | Timeline >6 bulan tanpa memperhitungkan sumber   | Timeline 3-6 bulan dengan asumsi tertentu     | Timeline 1-3 bulan realistis dengan rencana detail |      |
| Rigor        | Baseline tidak jelas atau straw man              | 1-2 baseline dengan justifikasi partial       | 2+ baseline SOTA + justifikasi pemilihan lengkap   |      |
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| **Problem Statement** | WS-02 | Identifikasi penyakit daun padi secara manual masih membutuhkan waktu yang relatif lama dan berpotensi menimbulkan kesalahan diagnosis sehingga diperlukan sistem klasifikasi otomatis berbasis Deep Learning. |
| **Gap** | WS-03 | Penelitian sebelumnya menunjukkan bahwa EfficientNet-B6 memiliki performa yang baik, namun evaluasi terhadap pengaruh variasi ukuran input citra (224×224 dan 528×528) serta jumlah epoch (25 dan 50) terhadap performa model masih terbatas. |
| **Research Question** | WS-04 | Bagaimana pengaruh variasi ukuran input citra (224×224 dan 528×528) serta jumlah epoch (25 dan 50) terhadap performa model EfficientNet-B6 dalam mengklasifikasikan penyakit daun padi? |
| **Hipotesis** | WS-04 | Variasi ukuran input citra dan jumlah epoch diduga mempengaruhi performa model EfficientNet-B6 berdasarkan nilai Accuracy, Precision, Recall, F1-Score, dan AUC. |
| **Variabel & Metrik** | WS-05 | Variabel bebas berupa ukuran input citra dan jumlah epoch, sedangkan variabel terikat berupa Accuracy, Precision, Recall, F1-Score, dan AUC sebagai metrik evaluasi model. |
| **Sistem** | WS-06 | Sistem klasifikasi dibangun menggunakan arsitektur EfficientNet-B6 yang dijalankan pada Google Colab dengan dataset Rice Leafs dan metode validasi 5-Fold Cross Validation. |
| **Desain Eksperimen** | WS-07 | Penelitian akan menggunakan empat skenario eksperimen berdasarkan kombinasi ukuran input (224×224 dan 528×528) serta jumlah epoch (25 dan 50) untuk menentukan konfigurasi terbaik model EfficientNet-B6. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis berdasarkan proposal penelitian.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ | Research gap diperoleh dari hasil analisis penelitian sebelumnya yang menunjukkan masih terbatasnya evaluasi variasi ukuran input dan jumlah epoch pada EfficientNet-B6. |
| Gap → RQ | ✅ | Research Question disusun secara langsung untuk menjawab research gap mengenai pengaruh variasi parameter terhadap performa model. |
| RQ → Hypothesis | ✅ | Hipotesis memprediksi bahwa variasi ukuran input citra dan jumlah epoch akan memberikan perbedaan performa pada model EfficientNet-B6. |
| Hypothesis → Metric | ✅ | Hipotesis diuji menggunakan Accuracy, Precision, Recall, F1-Score, dan AUC sebagai metrik evaluasi. |
| Metric → System | ✅ | Sistem menghasilkan seluruh metrik evaluasi secara otomatis setelah proses pelatihan dan pengujian model selesai. |
| System → Experiment | ✅ | Sistem digunakan sebagai instrumen utama dalam empat skenario eksperimen dengan metode 5-Fold Cross Validation. |

**Koneksi mana yang paling lemah?**

Belum terdapat koneksi yang benar-benar lemah, namun hubungan antara research gap dan research question masih dapat diperkuat dengan menambahkan referensi penelitian terbaru mengenai pengaruh variasi parameter pelatihan pada EfficientNet.

**Bagaimana cara memperkuatnya?**

> Menambahkan beberapa referensi ilmiah terbaru (2023–2025) yang membahas pengaruh ukuran input citra dan jumlah epoch terhadap performa model EfficientNet sehingga research gap menjadi lebih kuat.

**Konsistensi horizontal — apakah istilah dan scope konsisten?**

**[X] Ya**

Seluruh istilah yang digunakan pada proposal telah konsisten mulai dari rumusan masalah, research question, hipotesis, variabel penelitian, sistem, hingga desain eksperimen.

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal menggunakan rubrik berikut.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| **Koherensi** | **3** | Alur proposal telah tersusun secara logis mulai dari identifikasi masalah, research gap, research question, hipotesis, metodologi, hingga desain eksperimen. |
| **Specificity** | **3** | Variabel penelitian, dataset, metode, metrik evaluasi, dan skenario eksperimen telah dijelaskan secara spesifik. |
| **Feasibility** | **3** | Penelitian dapat dilaksanakan menggunakan Google Colab dan dataset Rice Leafs dengan sumber daya yang tersedia. |
| **Rigor** | **3** | Penelitian menggunakan metode Deep Learning EfficientNet-B6, validasi 5-Fold Cross Validation, serta metrik evaluasi Accuracy, Precision, Recall, F1-Score, dan AUC. |

**Skor total:** **12 / 12**

**Apakah proposal siap untuk fase eksekusi?**

**[X] Ya**

Proposal telah memiliki keterkaitan yang konsisten antara permasalahan, research gap, research question, metodologi, dan desain eksperimen sehingga siap dilanjutkan ke tahap implementasi.

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:**

Menganalisis isi jurnal dan menyusun ringkasan setiap bagian karena penelitian acuan telah memiliki struktur yang jelas sehingga memudahkan proses identifikasi masalah dan metode penelitian.

**Bagian tersulit:**

Menentukan research gap dan menjaga konsistensi antara research question, hipotesis, variabel penelitian, serta metodologi karena seluruh komponen harus saling berkaitan dan tidak boleh bertentangan.

**Yang akan dilakukan berbeda:**

> Jika mengulang dari awal, saya akan melakukan telaah literatur yang lebih luas sebelum menentukan research gap sehingga proposal memiliki dasar teori yang lebih kuat. Selain itu, saya akan menyusun rancangan eksperimen sejak awal agar proses implementasi penelitian dapat berjalan lebih terarah dan efisien.
