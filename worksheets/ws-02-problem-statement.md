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
  Konteks  : Identifikasi otomatis spesies bunga lokal Indonesia menggunakan citra digital

System Context
  Input       : Citra/gambar bunga (RGB) dari 11 spesies berbeda (total 2137 citra)
  Process     : Pre-processing (augmentasi), ekstraksi fitur menggunakan MobileNetV2, dan fine-tuning melalui Transfer Learning
  Output      : Label prediksi kelas/spesies bunga
  Outcome     : Kemudahan identifikasi flora lokal secara cepat dan akurat melalui perangkat mobile
  Constraints : Dataset lokal yang relatif kecil dan kemiripan visual (warna/struktur) antar spesies
  Stakeholders: Peneliti botani, penggiat pelestarian hayati, dan masyarakat umum pengguna smartphone

Fenomena → Problem
  Fenomena yang diamati             : Tingginya keanekaragaman flora Indonesia namun identifikasi masih manual
  Gejala (symptom) yang terukur     : Akurasi model CNN standar tanpa optimasi hanya mencapai 42% pada data uji
  Masalah yang didiagnosis          : Model CNN "from scratch" gagal menggeneralisasi pola pada dataset kecil
  Masalah riset (researchable)      : Sejauh mana teknik Transfer Learning dengan arsitektur MobileNetV2 dapat meningkatkan akurasi klasifikasi pada dataset bunga lokal yang terbatas?
  Variabel yang terukur             : Nilai Akurasi (%) dan nilai Loss

Problem Quality Check
  [x] Clarity — Masalah perbedaan performa antara model dasar dan transfer learning jelas
  [x] Measurability — Menggunakan metrik akurasi yang dapat diuji secara kuantitatif
  [x] Relevance — Relevan dengan kebutuhan digitalisasi identifikasi flora Indonesia
  [x] Testability — Dapat diuji melalui perbandingan model dengan dan tanpa transfer learning
  [x] Impact — Memberikan efisiensi tinggi (peningkatan akurasi hingga 52%)

Problem Statement (1 paragraf):
  Identifikasi spesies bunga di Indonesia secara manual memerlukan waktu lama dan keahlian khusus, sementara model Deep Learning standar seringkali gagal mencapai akurasi optimal ketika dilatih pada dataset lokal yang terbatas. Penelitian ini mengusulkan penerapan teknik Transfer Learning menggunakan arsitektur MobileNetV2 untuk mengatasi kendala tersebut. Hasil penelitian menunjukkan bahwa pendekatan ini mampu meningkatkan akurasi klasifikasi secara signifikan dari 42% menjadi 73%, memberikan solusi identifikasi flora yang efisien dan andal untuk diimplementasikan pada perangkat smartphone.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Klasifikasi Spesies Bunga Indonesia

| Tahap | Hasil |
|-------|-------|
| Reality | Indonesia memiliki lebih dari 30.000 spesies bunga yang perlu diidentifikasi |
| Observed Issue (Symptom) | Model klasifikasi dasar memiliki akurasi rendah (42%) dan sering salah prediksi |
| Diagnosed Problem (Root Cause) | Model CNN standar membutuhkan data besar untuk konvergensi; dataset lokal terbatas |
| Researchable Problem | Pemanfaatan Transfer Learning ImageNet pada MobileNetV2 untuk klasifikasi bunga[cite: 1] |
| Measurable Variable | Akurasi (%) pada data training, validasi, dan testing[cite: 1] |

Apakah terjebak solution-first thinking? [ ] Ya / [x] Tidak

Justifikasi: Penelitian berangkat dari masalah rendahnya akurasi identifikasi pada dataset bunga lokal sebelum mengajukan transfer learning sebagai solusinya[cite: 1].
---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Citra digital spesies bunga dari mesin pencari Bing (11 kelas)[cite: 1] |
| Process | Transfer parameter dari pre-trained model ImageNet ke MobileNetV2[cite: 1] |
| Output | Prediksi label spesies (misal: "Anggrek Phalaenopsis", "Mawar")[cite: 1] |
| Outcome | Sistem identifikasi yang dapat digunakan masyarakat melalui smartphone[cite: 1] |
| Constraints | Kemiripan warna antar spesies yang menyulitkan pemisahan fitur[cite: 1] |
| Stakeholders | Badan Penelitian Pertanian, Peneliti AI, dan Masyarakat[cite: 1] |

**Komponen mana yang paling relevan dengan masalah riset?** Process (karena fokus riset adalah pada efektivitas teknik Transfer Learning dibandingkan pelatihan dari awal)[cite: 1].

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Perbedaan tujuan antara model dasar dan transfer learning sangat gamblang[cite: 1] |
| Measurability | 5 | Menggunakan rumus akurasi standar yang jelas perhitungannya[cite: 1] |
| Relevance | 4 | Sangat berguna untuk bidang botani dan teknologi informasi di Indonesia[cite: 1] |
| Testability | 5 | Prosedur eksperimen (100 epoch, Adam optimizer) sangat mungkin direplikasi[cite: 1] |
| Impact | 4 | Peningkatan performa sebesar 52% memberikan dampak praktis yang besar[cite: 1] |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
Penelitian ini mengatasi permasalahan rendahnya akurasi identifikasi otomatis pada spesies bunga lokal Indonesia akibat keterbatasan dataset pelatihan. Dengan mengintegrasikan teknik Transfer Learning pada arsitektur CNN MobileNetV2, riset ini berhasil memanfaatkan pengetahuan dari model pre-trained ImageNet untuk meningkatkan kemampuan generalisasi model[cite: 1]. Hasil pengujian membuktikan bahwa metode ini mampu menekan nilai loss secara signifikan dan meningkatkan akurasi rata-rata hingga 73% pada perangkat mobile, sehingga menjadi solusi yang efisien dalam mendukung pelestarian keanekaragaman hayati melalui teknologi digital[cite: 1].

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
Perbedaan fundamentalnya terletak pada cakupan dan sifat solusinya. Masalah coding (bug/error) bersifat deterministik dan teknis; tujuannya adalah fungsionalitas (correctness) agar kode berjalan sesuai spesifikasi yang sudah ada. Pendekatannya adalah debugging. Sementara itu, masalah riset bersifat eksploratif dan bertujuan menghasilkan pengetahuan baru atau membuktikan keunggulan sebuah metode (efficacy)[cite: 1]. Riset tidak mencari "mana baris kode yang salah", melainkan "mengapa metode A lebih baik dari metode B" dan membuktikannya melalui eksperimen yang terukur dan sistematis[cite: 1].
