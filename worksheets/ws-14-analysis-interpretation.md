# WS-14: Analysis, Interpretation & Failure Analysis

> **Bab 14 — Analisis Data, Interpretasi & Failure Analysis**

---

## Ringkasan Materi

### Data → Knowledge Model

```
Data → Analysis → Interpretation → Explanation → Knowledge
```

Tiga level yang berbeda:
- **Analysis** — "Apa yang terjadi?" (deskriptif + inferensial)
- **Interpretation** — "Apa artinya?" (konteks RQ + literatur)
- **Failure Analysis** — "Mengapa tidak berhasil?" (boundary conditions)

### Beyond p-value

**Statistical significance ≠ practical significance.** Selalu laporkan:
1. p-value (signifikansi statistik)
2. Effect size (besarnya efek)
3. Confidence interval (rentang ketidakpastian)

| Effect Size (Cohen's d) | Interpretasi |
|-------------------------|-------------|
| < 0.2 | Small |
| 0.2 – 0.8 | Medium |
| > 0.8 | Large |

### Pemilihan Uji Statistik

| Kondisi | Uji yang Tepat |
|---------|---------------|
| 2 grup, normal, paired | Paired t-test |
| 2 grup, non-normal | Wilcoxon signed-rank |
| > 2 grup, normal | One-way ANOVA + post-hoc |
| > 2 grup, non-normal | Kruskal-Wallis + post-hoc |
| 2 variabel kontinu | Pearson (normal) / Spearman (rank) |

### Failure Analysis as Contribution

Hipotesis yang ditolak adalah **temuan yang berharga**:

| Dataset | New (F1) | Baseline (F1) | p-value | Cohen's d |
|---------|---------|--------------|---------|-----------|
| DS-1 (small, clean) | 94.2±1.1 | 89.3±1.5 | <0.001 | **3.7** |
| DS-4 (medium, noisy) | 78.3±3.2 | 82.1±2.8 | 0.008 | **-1.3** |
| DS-5 (large, noisy) | 71.6±4.1 | 80.5±3.0 | <0.001 | **-2.5** |

**Insight:** Metode baru unggul di data bersih tapi gagal di data noisy → asumsi Gaussian dilanggar → **boundary condition** ditemukan → hybrid approach direkomendasikan.

**Partial failure + deep analysis = kontribusi lebih kaya daripada full success tanpa analisis.**

### Limitation Types

| Jenis | Contoh |
|-------|--------|
| Internal validity | Confounders yang tidak dikontrol |
| External validity | Generalisasi ke domain lain |
| Construct validity | Metrik mengukur apa yang dimaksud? |
| Statistical limitation | Sample size, asumsi distribusi |

### Jebakan Kognitif

1. "Signifikan statistik = penting secara praktis" → cek effect size
2. "Hipotesis tidak didukung → cari sudut baru" → p-hacking
3. "Kegagalan tidak perlu dilaporkan detail" → missed insight
4. "Limitasi cukup disebutkan, tidak perlu dianalisis" → kedalaman hilang

---

## Template A.14 — Analysis & Interpretation Report

```
ANALYSIS & INTERPRETATION

1. Statistik Deskriptif

| Model | Accuracy | Precision | Recall | F1-Score | n |
|--------|----------|-----------|--------|----------|---|
| EfficientNet-B6 Transfer Learning | 63,04% | 58,76% | 63,04% | 58,45% | 671 |

2. Uji Hipotesis

Uji yang digunakan :
Analisis deskriptif

Justifikasi :
Penelitian ini hanya menggunakan satu konfigurasi model sehingga tidak terdapat kelompok pembanding yang memungkinkan dilakukan uji hipotesis inferensial.

Hasil :
Accuracy = 63,04%
Precision = 58,76%
Recall = 63,04%
F1-Score = 58,45%

Confidence Interval :
Tidak dihitung.

3. Keputusan

[x] Hipotesis dievaluasi secara deskriptif

[ ] H₀ ditolak

[ ] H₀ tidak ditolak

4. Interpretasi

Hubungan ke Research Question :
Model EfficientNet-B6 mampu melakukan klasifikasi penyakit daun padi menggunakan pendekatan transfer learning dan menghasilkan nilai accuracy sebesar 63,04%.

Practical significance :
Model dapat digunakan sebagai dasar sistem klasifikasi otomatis, namun performanya masih memiliki ruang untuk ditingkatkan terutama pada kelas minoritas.

Perbandingan dengan literatur :
Hasil penelitian lebih rendah dibandingkan penelitian Milano dkk. (2024) yang memperoleh akurasi sekitar 77%, kemungkinan dipengaruhi oleh penggunaan skema single split dan keterbatasan sumber daya Google Colab Free.

5. Limitation

| Jenis | Ancaman | Dampak | Mitigasi |
|-------|----------|--------|----------|
| Internal | Satu konfigurasi model | Tidak dapat membandingkan performa metode lain | Penelitian berikutnya dapat menggunakan beberapa konfigurasi model |
| External | Dataset hanya Rice Leafs | Generalisasi terbatas | Menggunakan dataset lain pada penelitian lanjutan |
| Statistical | Tidak ada multiple run | Tidak dapat menghitung variabilitas hasil | Melakukan repeatability test pada penelitian berikutnya |

6. Failure Analysis

Penyebab potensial :

Performa model belum optimal pada kelas Hispa dan Leaf Blast karena jumlah data kedua kelas lebih sedikit dibandingkan kelas Healthy.

Boundary condition :

Pendekatan transfer learning dengan feature extraction pada lingkungan Google Colab Free masih memiliki keterbatasan dalam mencapai performa yang setara dengan penelitian yang menggunakan konfigurasi eksperimen lebih kompleks.

Insight :

Transfer learning menggunakan EfficientNet-B6 tetap mampu melakukan klasifikasi penyakit daun padi, namun peningkatan performa kemungkinan memerlukan fine-tuning, penanganan ketidakseimbangan data, atau sumber daya komputasi yang lebih tinggi.
```

---

## Latihan 1 — Pemilihan Uji Statistik

Tentukan uji statistik yang tepat untuk eksperimen Anda.

| Pertanyaan                        | Jawaban                                                                                                                                                                                                                            |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Berapa grup yang dibandingkan?    | **1 (EfficientNet-B6 Transfer Learning)**                                                                                                                                                                                          |
| Apakah data berpasangan (paired)? | Tidak                                                                                                                                                                                                                              |
| Apakah distribusi normal?         | Tidak diuji karena hanya terdapat satu kelompok eksperimen                                                                                                                                                                         |
| **Uji yang dipilih**              | Analisis deskriptif                                                                                                                                                                                                                |
| **Justifikasi**                   | Penelitian hanya mengevaluasi satu konfigurasi model sehingga uji statistik inferensial seperti t-test atau ANOVA tidak relevan. Analisis dilakukan berdasarkan nilai Accuracy, Precision, Recall, F1-Score, dan Confusion Matrix. |

**Effect size yang akan dilaporkan:** [ ] Cohen's d / [ ] Eta-squared / [V] Tidak dihitung (tidak terdapat kelompok pembanding)

---

## Latihan 2 — Interpretasi Hasil

Gunakan data berikut (atau data riil Anda) untuk berlatih interpretasi.

**Data:**
| Model                             |   Accuracy |       n |
| --------------------------------- | ---------: | ------: |
| EfficientNet-B6 Transfer Learning | **63,04%** | **671** |



| Aspek                         | Interpretasi                                                                                                                                                                                                                                                        |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Signifikansi statistik        | Tidak dilakukan uji signifikansi statistik karena penelitian hanya menggunakan satu konfigurasi model.                                                                                                                                                              |
| Effect size                   | Tidak dihitung karena tidak terdapat kelompok pembanding.                                                                                                                                                                                                           |
| Practical significance        | Model berhasil mengklasifikasikan empat kelas penyakit daun padi dengan accuracy 63,04%, sehingga menunjukkan bahwa EfficientNet-B6 dapat diterapkan untuk tugas klasifikasi, meskipun performa pada beberapa kelas masih perlu ditingkatkan.                       |
| Hubungan ke Research Question | Hasil penelitian menjawab research question dengan menunjukkan performa model berdasarkan accuracy, precision, recall, F1-score, dan confusion matrix.                                                                                                              |
| Perbandingan literatur        | Akurasi yang diperoleh lebih rendah dibandingkan penelitian Milano dkk. (2024). Perbedaan tersebut dapat dipengaruhi oleh penggunaan skema single split, konfigurasi pelatihan yang lebih sederhana, dan keterbatasan sumber daya komputasi pada Google Colab Free. |

---

## Latihan 3 — Failure Analysis

Latih kemampuan failure analysis: hipotesis TIDAK didukung. Apa yang bisa dipelajari?

**Skenario:** Metode baru Anda mendapat F1 = 83.2%, baseline = 84.7%. p = 0.12 (tidak signifikan).

| Pertanyaan                        | Jawaban                                                                                                                                                                                                                                             |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Apakah ini "gagal"?               | Tidak. Penelitian berhasil menghasilkan model klasifikasi dan memberikan evaluasi performa. Perbedaan hasil dengan penelitian acuan menjadi temuan yang dapat dianalisis lebih lanjut.                                                              |
| Kemungkinan penyebab?             | Penggunaan feature extraction tanpa fine-tuning, keterbatasan komputasi Google Colab Free, serta distribusi data yang tidak seimbang antar kelas.                                                                                                   |
| Boundary condition?               | Pendekatan ini sesuai untuk lingkungan komputasi terbatas, tetapi performanya dapat menurun dibandingkan konfigurasi yang menggunakan fine-tuning, validasi silang, atau sumber daya komputasi yang lebih besar.                                    |
| Insight yang bisa diambil?        | EfficientNet-B6 tetap efektif sebagai model dasar klasifikasi penyakit daun padi, namun peningkatan performa dapat dicapai melalui fine-tuning, optimasi hiperparameter, atau strategi penanganan ketidakseimbangan kelas pada penelitian lanjutan. |
| Apakah layak dilaporkan? Mengapa? | Ya. Hasil penelitian, termasuk keterbatasannya, merupakan bagian penting dari kontribusi ilmiah karena memberikan informasi mengenai performa model pada kondisi komputasi yang lebih sederhana dan realistis.                                      |


**Limitation terkait:**
| Jenis       | Ancaman                       | Dampak                                                              |
| ----------- | ----------------------------- | ------------------------------------------------------------------- |
| Statistical | Hanya satu eksperimen utama   | Tidak dapat menghitung variasi hasil atau melakukan uji inferensial |
| Internal    | Tidak menggunakan fine-tuning | Performa model belum optimal                                        |
| External    | Dataset hanya Rice Leafs      | Generalisasi hasil masih terbatas                                   |


---

## Refleksi

> Apakah "failure" dalam riset benar-benar gagal, atau justru kontribusi? Bagaimana failure analysis mengubah cara Anda melihat hasil negatif?

> Dalam penelitian, hasil yang tidak mencapai performa tertinggi bukan berarti penelitian gagal. Failure analysis membantu peneliti memahami faktor-faktor yang memengaruhi hasil eksperimen, seperti keterbatasan metode, konfigurasi model, maupun sumber daya komputasi. Dengan melakukan analisis terhadap keterbatasan tersebut, penelitian tetap memberikan kontribusi ilmiah karena dapat menjadi dasar perbaikan dan pengembangan pada penelitian selanjutnya.
