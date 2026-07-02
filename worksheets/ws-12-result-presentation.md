# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question :
Bagaimana performa model EfficientNet-B6 menggunakan pendekatan transfer learning dalam mengklasifikasikan penyakit daun padi?

Metrik Utama :
Accuracy, Precision, Recall, F1-Score

Tabel Hasil:

| Skenario | Accuracy | Precision | Recall | F1-Score | n |
|----------|----------|-----------|--------|----------|---|
| EfficientNet-B6 Transfer Learning | 63,04% | 58,76% | 63,04% | 58,45% | 671 |

Visualisasi yang Direncanakan:

| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
| 1 | Line Chart | Perkembangan accuracy dan validation accuracy selama pelatihan | Accuracy |
| 2 | Line Chart | Perkembangan training loss dan validation loss | Loss |
| 3 | Confusion Matrix Heatmap | Distribusi hasil klasifikasi setiap kelas | Confusion Matrix |

Bias Check:

[x] Y-axis menggunakan skala yang sesuai

[x] Tidak ada manipulasi skala grafik

[x] Seluruh data hasil eksperimen ditampilkan

[x] Tidak menggunakan efek 3D
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Model                             |   Accuracy |  Precision |     Recall |   F1-Score | Jumlah Data Uji (n) |
| --------------------------------- | ---------: | ---------: | ---------: | ---------: | ------------------: |
| EfficientNet-B6 Transfer Learning | **63,04%** | **58,76%** | **63,04%** | **58,45%** |             **671** |


**Checklist tabel:**
 [v] Self-contained (judul tabel jelas)
 [v] Satuan (%)
 [v] Jumlah data uji (n) dicantumkan
 [ ] Mean ± Std (tidak digunakan karena penelitian hanya memiliki satu eksperimen utama)
 [v] Format konsisten

Catatan: Karena penelitian ini hanya menggunakan satu konfigurasi model dan satu hasil evaluasi utama, nilai disajikan sebagai hasil akhir tanpa mean ± standar deviasi.

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| No | Jenis Grafik             | Pesan                                                                                | Data yang Digunakan |
| -- | ------------------------ | ------------------------------------------------------------------------------------ | ------------------- |
| 1  | Line Chart               | Menunjukkan perkembangan accuracy dan validation accuracy selama proses pelatihan    | History Accuracy    |
| 2  | Line Chart               | Menunjukkan perubahan training loss dan validation loss selama pelatihan             | History Loss        |
| 3  | Heatmap Confusion Matrix | Menunjukkan distribusi prediksi benar dan salah pada setiap kelas penyakit daun padi | Confusion Matrix    |


---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan                        | Jawaban                                                                                                                                      |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Apakah Y-axis menyesatkan?        | Ya. Grafik dengan sumbu Y dimulai dari 90% dapat memperbesar perbedaan yang sebenarnya kecil.                                                |
| Apakah error bar ditampilkan?     | Tidak.                                                                                                                                       |
| Apakah semua kondisi ditampilkan? | Ya.                                                                                                                                          |
| Apa solusinya?                    | Menggunakan sumbu Y yang proporsional atau memberikan justifikasi jika tidak dimulai dari nol, serta menambahkan error bar apabila tersedia. |


**Evaluasi grafik Anda sendiri dari Latihan 2:**
 [v] Semua grafik menggunakan skala yang proporsional.
 [v] Seluruh hasil eksperimen ditampilkan.
 [v] Tidak menggunakan efek visual yang dapat menyesatkan.
 [v] Confusion matrix ditampilkan secara lengkap.
 [ ] Error bar tidak ditampilkan karena penelitian hanya memiliki satu hasil eksperimen sehingga tidak tersedia nilai standar deviasi.
---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

>Tabel dan grafik memiliki fungsi yang saling melengkapi dalam penyajian hasil penelitian. Tabel memberikan informasi numerik secara rinci dan presisi sehingga memudahkan pembaca melihat nilai setiap metrik. Sebaliknya, grafik membantu memperlihatkan pola, tren, dan hubungan antarvariabel secara visual sehingga hasil penelitian lebih mudah dipahami. Oleh karena itu, penggunaan keduanya secara bersamaan memberikan penyajian hasil yang lebih informatif dan objektif.

Dalam penelitian ini, penyajian grafik dilakukan dengan memperhatikan prinsip visualisasi ilmiah, seperti penggunaan skala sumbu yang proporsional, penyajian seluruh data hasil eksperimen, serta menghindari manipulasi tampilan yang dapat menimbulkan interpretasi yang menyesatkan.

##catatan
"Mean ± standar deviasi tidak disajikan karena penelitian ini hanya menggunakan satu eksperimen utama (single run)."



