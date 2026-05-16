# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Akurasi klasifikasi penyakit daun padi masih belum optimal dan sebagian besar penelitian masih menggunakan metode CNN standar sehingga performa klasifikasi pada beberapa kelas penyakit masih rendah.

Research Question:
  Tipe         : [x] Comparison  [ ] Improvement  [ ] Exploratory
  
  Formulasi    :
  Apakah metode EfficientNet-B6 menghasilkan nilai accuracy dan F1-Score yang lebih tinggi dibandingkan CNN standar pada klasifikasi penyakit daun padi?

  - Variabel IV  : Jenis metode deep learning (EfficientNet-B6 vs CNN standar)
  
  - Variabel DV  : Nilai accuracy dan F1-Score klasifikasi penyakit daun padi
  
  - Metrik       : Accuracy, Precision, Recall, dan F1-Score
  
  - Dataset      : 3355 citra daun padi dengan 4 kelas penyakit (Healthy, LeafBlast, Hispa, BrownSpot)
  
  - Baseline     : CNN standar

Quality Check RQ:
  [x] Variabel spesifik
  [x] Metrik jelas
  [x] Baseline ada
  [x] Konteks disebutkan
  [x] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:

  Apa yang baru diketahui :
  Perbandingan performa EfficientNet-B6 dan CNN standar pada klasifikasi penyakit daun padi berdasarkan accuracy dan F1-Score.

  Jenis kontribusi :
  [ ] Improvement  [x] Comparison  [ ] Novel approach

  Gap yang diisi :
  Memberikan bukti empiris mengenai efektivitas EfficientNet-B6 dalam meningkatkan performa klasifikasi penyakit daun padi dibanding CNN standar.

Hypothesis Pair:

  H₀ :
  Tidak ada perbedaan signifikan accuracy dan F1-Score antara EfficientNet-B6 dan CNN standar pada klasifikasi penyakit daun padi.

  H₁ :
  EfficientNet-B6 menghasilkan accuracy dan F1-Score lebih tinggi dibanding CNN standar pada klasifikasi penyakit daun padi.

  Threshold              :
  Accuracy > 77% dan p-value < 0.05

  Justifikasi threshold  :
  Nilai accuracy 77% diambil dari hasil penelitian sebelumnya sebagai baseline performa terbaik, sedangkan p-value < 0.05 digunakan sebagai standar signifikansi statistik.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Akurasi klasifikasi penyakit daun padi masih rendah dan metode modern belum banyak diterapkan pada klasifikasi daun padi.

**RQ versi pertama (tulis bebas):**
> Apakah EfficientNet-B6 lebih baik dibanding CNN standar untuk klasifikasi penyakit daun padi?

**Evaluasi RQ:**

| Komponen        | Ada? | Isi                            |
| --------------- | ---- | ------------------------------ |
| Metode spesifik | ya   | EfficientNet-B6 vs CNN standar |
| Metrik terukur  | ya   | Accuracy dan F1-Score          |
| Baseline        | ya   | CNN standar                    |
| Dataset/konteks | ya   | Dataset citra daun padi        |

**Tipe RQ:** [X] Comparison / [ ] Improvement / [ ] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Apakah metode EfficientNet-B6 menghasilkan accuracy dan F1-Score yang lebih tinggi dibanding CNN standar pada klasifikasi penyakit daun padi menggunakan dataset 3355 citra daun padi?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen              | Isi                                                                                                  |
| --------------------- | ---------------------------------------------------------------------------------------------------- |
| H₀                    | Tidak ada perbedaan signifikan accuracy dan F1-Score antara EfficientNet-B6 dan CNN standar          |
| H₁                    | EfficientNet-B6 menghasilkan accuracy dan F1-Score lebih tinggi dibanding CNN standar                |
| Metrik                | Accuracy dan F1-Score                                                                                |
| Threshold             | Accuracy > 77% dan p-value < 0.05                                                                    |
| Justifikasi threshold | Accuracy 77% berasal dari penelitian sebelumnya dan p-value 0.05 adalah standar statistik penelitian |


**Apakah hipotesis ini falsifiable?** [X] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah?
Melakukan eksperimen klasifikasi menggunakan kedua metode. Jika hasil EfficientNet-B6 tidak lebih tinggi dibanding CNN standar atau p-value > 0.05, maka H₁ ditolak.
---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap           | Isi                                                                              |
| --------------- | -------------------------------------------------------------------------------- |
| RQ              | Apakah EfficientNet-B6 menghasilkan accuracy lebih tinggi dibanding CNN standar? |
| Variable (IV)   | Jenis algoritma deep learning                                                    |
| Variable (DV)   | Nilai accuracy dan F1-Score                                                      |
| Metric          | Accuracy, Precision, Recall, F1-Score                                            |
| Data source     | Dataset citra daun padi sebanyak 3355 gambar                                     |
| Analysis method | Perbandingan hasil evaluasi model dan pengujian statistik                        |


**Apakah rantai lengkap?** [X] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? ______________

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** "Klasifikasi Penyakit Daun Padi Menggunakan Model Deep Learning EfficientNet-B6"
**RQ yang diekstrak:** Apakah EfficientNet-B6 mampu meningkatkan performa klasifikasi penyakit daun padi?
**Komponen yang hilang:** Paper tersebut belum menjelaskan baseline pembanding secara rinci sehingga perbandingan performa dengan metode lain belum terlalu jelas.
