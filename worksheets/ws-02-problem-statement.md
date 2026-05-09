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
  Domain   : Visi Komputer (Computer Vision) / Deep Learning
  Konteks  : Klasifikasi dan identifikasi otomatis penyakit pada daun tanaman padi menggunakan citra digital

System Context
  Input       : Citra digital daun tanaman padi (RGB) berukuran 224x224 atau 528x528 piksel, terbagi menjadi 4 kelas: Healthy (1488 citra), LeafBlast (779 citra), Hispa (565 citra), dan BrownSpot (523 citra) dengan total 3.355 citra
  Process     : Preprocessing (Resize ukuran citra input), pembagian dataset menggunakan metode 5-Fold Cross Validation dengan split dataset 80:20, dilanjutkan pemodelan/pelatihan menggunakan arsitektur CNN EfficientNet-B6 dengan variasi parameter size input dan jumlah epoch
  Output      : Label prediksi kelas kondisi kesehatan daun padi (Healthy, Leaf Blast, Hispa, atau Brown Spot)
  Outcome     : Kemudahan bagi penyuluh pertanian dan petani dalam mendeteksi serta mengidentifikasi jenis penyakit daun padi secara cepat dan akurat demi mencegah gagal panen
  Constraints : Kompleksitas ekstraksi fitur visual akibat kemiripan karakteristik bercak pada daun dan keterbatasan jumlah data latih pada kelas penyakit tertentu (imbalance class)
  Stakeholders: Petani padi, penyuluh pertanian, peneliti bidang agrikultur/botani, dan akademisi AI/Deep Learning

Fenomena → Problem
  Fenomena yang diamati           : Sektor pertanian padi sering mengalami penurunan kualitas hingga gagal panen akibat keterlambatan diagnosis manual penyakit daun oleh petani dan penyuluh
  Gejala (symptom) yang terukur   : Rendahnya akurasi dan tingginya subjektivitas identifikasi manual yang berdampak pada salah penanganan obat/metode pencegahan
  Masalah yang didiagnosis        : Kurangnya alat bantu otomatis berbasis kecerdasan buatan yang mampu mengenali pola visual penyakit daun padi secara presisi dan efisien dalam volume besar
  Masalah riset (researchable)    : Bagaimana pengaruh variasi parameter size input (224 vs 528) dan jumlah epoch (25 vs 50) terhadap performa arsitektur CNN EfficientNet-B6 dalam mengklasifikasikan penyakit daun padi?
  Variabel yang terukur           : Akurasi (%), Presisi (%), Recall (%), F1-Score (%), dan Area Under the Curve (AUC)

Problem Quality Check
  [x] Clarity — Masalah deteksi penyakit daun padi dan pengujian arsitektur spesifik sangat jelas digambarkan
  [x] Measurability — Menggunakan metrik evaluasi kuantitatif yang standar (akurasi, presisi, recall, F1-score, AUC)
  [x] Relevance — Relevan dengan isu ketahanan pangan nasional dan penerapan AI di bidang agrikultur
  [x] Testability — Dapat diuji dan dibuktikan secara empiris melalui 4 skenario eksperimen dengan 5-Fold Cross Validation
  [x] Impact — Memberikan model klasifikasi dengan performa optimal (akurasi mencapai 77.05% dan AUC 0.90 - 0.93) sebagai acuan sistem deteksi dini

Problem Statement (1 paragraf):
  Keterlambatan dan ketidakakuratan dalam mendiagnosis penyakit pada daun padi sering kali memicu kegagalan panen akibat minimnya alat bantu identifikasi otomatis yang presisi bagi petani dan penyuluh lapangan. Penelitian ini mengusulkan penerapan model Deep Learning menggunakan arsitektur CNN EfficientNet-B6 untuk melakukan klasifikasi otomatis pada empat kondisi daun padi (Healthy, Leaf Blast, Hispa, dan Brown Spot). Melalui pengujian 4 skenario eksperimen dengan metode 5-Fold Cross Validation, penelitian ini membuktikan bahwa kombinasi parameter size input 224 dan 50 epoch mampu menghasilkan performa klasifikasi paling optimal dengan akurasi tertinggi sebesar 77.05% serta nilai AUC berkisar antara 0.90 hingga 0.93, sehingga layak dijadikan solusi teknologi pendeteksian dini penyakit tanaman pangan.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Klasifikasi Penyakit Daun Padi Menggunakan Deep Learning


| Tahap | Hasil |
|-------|-------|
| Reality | Tanaman padi merupakan komoditas pangan utama di Indonesia yang sangat rentan terhadap penyakit daun, namun proses diagnosis oleh petani saat ini masih dilakukan secara manual |
| Observed Issue (Symptom) | Proses diagnosis manual sering terlambat, subjektif, dan tidak akurat, sehingga petani kesulitan menentukan solusi penanganan yang tepat dan berujung pada penurunan hasil panen |
| Diagnosed Problem (Root Cause) | Kurangnya pemanfaatan sistem visi komputer (computer vision) berbasis deep learning yang dievaluasi secara sistematis untuk mengenali karakteristik visual penyakit daun secara cepat dan akurat |
| Researchable Problem | Sejauh mana efektivitas arsitektur Convolutional Neural Network (CNN) EfficientNet-B6 dengan variasi ukuran citra input (size input) dan jumlah epoch dalam mengklasifikasikan 4 jenis kondisi daun padi?|
| Measurable Variable | Nilai Akurasi, Presisi, Recall, F1-Score, dan nilai AUC (Area Under the Curve) dari model yang dievaluasi menggunakan 5-Fold Cross Validation |

Apakah terjebak solution-first thinking? [ ] Ya / [x] Tidak

Justifikasi: Penelitian ini didasarkan pada masalah nyata di lapangan, yaitu keterlambatan dan rendahnya akurasi diagnosis manual penyakit daun padi oleh petani yang sering memicu gagal panen, sebelum akhirnya mengajukan solusi pemodelan menggunakan arsitektur EfficientNet-B6 dengan parameterisasi yang optimal.
---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | 3.355 citra digital daun padi yang terdiri dari 4 kelas: Healthy (1488), Leaf Blast (779), Hispa (565), dan Brown Spot (523)|
| Process | Preprocessing berupa resize citra, pembagian dataset dengan rasio 80:20, penerapan teknik 5-Fold Cross Validation, dan pelatihan model klasifikasi menggunakan arsitektur EfficientNet-B6 dengan variasi ukuran input (224 / 528) dan epoch (25 / 50) |
| Output | Hasil prediksi kelas kondisi daun padi (Healthy, Leaf Blast, Hispa, atau Brown Spot) beserta probabilitas klasifikasinya |
| Outcome | Terwujudnya sistem diagnosis dini penyakit tanaman padi yang akurat untuk membantu meminimalkan risiko gagal panen dan mempermudah kerja penyuluh pertanian |
| Constraints | Ketidakseimbangan jumlah data antar kelas (imbalance class) dan kemiripan visual pola bercak antar penyakit yang dapat memengaruhi sensitivitas ekstraksi fitur model |
| Stakeholders |Petani padi, Penyuluh Pertanian, Peneliti AI di bidang Agrikultur, dan Dinas Pertanian |

**
Komponen mana yang paling relevan dengan masalah riset? Komponen Process. Hal ini dikarenakan fokus utama dari eksperimen riset ini adalah menguji dan membandingkan skenario parameterisasi (kombinasi size input dan jumlah epoch) pada arsitektur pemodelan EfficientNet-B6 guna menemukan konfigurasi terbaik yang menghasilkan akurasi klasifikasi tertinggi.


## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Masalah yang diangkat sangat jelas, yaitu bagaimana meminimalkan kesalahan identifikasi penyakit daun padi melalui optimasi arsitektur EfficientNet-B6 |
| Measurability | 5 | Kinerja model diukur menggunakan parameter evaluasi matematis yang baku seperti Akurasi, Presisi, Recall, F1-score, dan AUC |
| Relevance | 5 | Sangat relevan dengan kebutuhan sektor pertanian di Indonesia yang mengandalkan padi sebagai makanan pokok utama |
| Testability | 5 | Eksperimen dirancang dengan skenario kuantitatif yang jelas (4 skenario pengujian parameter) sehingga sangat mudah direplikasi oleh peneliti lain |
| Impact | 4 | Memberikan kontribusi nyata berupa model dengan tingkat akurasi mencapai 77.05% dan AUC hingga 0.93 untuk diintegrasikan ke sistem aplikasi pertanian |

**Skor total:** 24 / 25

**Problem statement versi final (1 paragraf):**
Identifikasi penyakit pada daun padi secara manual oleh petani sering kali mengalami keterlambatan dan ketidakakuratan karena keterbatasan pengetahuan taksonomi penyakit, yang pada akhirnya memicu risiko gagal panen dalam skala besar. Penelitian ini mengatasi permasalahan tersebut dengan merancang sistem klasifikasi otomatis menggunakan arsitektur Deep Learning EfficientNet-B6 yang diuji melalui 4 skenario kombinasi parameter size input (224 dan 528) serta jumlah epoch (25 dan 50) dengan validasi 5-Fold Cross Validation. Hasil eksperimen membuktikan bahwa konfigurasi size input 224 dan 50 epoch sukses memberikan kinerja terbaik dengan tingkat akurasi rata-rata tertinggi sebesar 77.05% dan nilai AUC 0.90 - 0.93. Hal ini membuktikan bahwa metode yang diusulkan sangat andal dan efisien untuk diimplementasikan sebagai sistem deteksi dini penyakit tanaman guna mendukung ketahanan pangan nasional.
---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
Perbedaan fundamentalnya adalah masalah coding bersifat taktis dan deterministik, di mana tujuannya adalah memperbaiki kegagalan teknis sistem (debugging) agar kembali berfungsi sesuai spesifikasi baku; sementara masalah riset bersifat strategis dan terbuka, yang bertujuan mengisi celah pengetahuan (knowledge gap) dengan menguji metode atau parameter baru secara empiris lewat metode ilmiah guna menghasilkan kontribusi ilmiah yang dapat dibuktikan serta direplikasi.
