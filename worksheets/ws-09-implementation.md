# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Template A.9 — Dokumentasi Setup Eksperimen

```text
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel Xeon (Google Colab Runtime)
  RAM     : ±12 GB RAM
  GPU     : NVIDIA Tesla T4 atau GPU yang tersedia pada Google Colab
  Storage : Google Drive dan Google Colab Storage

Software:
  OS        : Linux (Ubuntu - Google Colab)
  Runtime   : Python 3.11
  Framework : TensorFlow 2.x, Keras

Dependencies:

| Library        | Version | Sumber         | Hash/Checksum |
|----------------|---------|----------------|---------------|
| Python         | 3.11    | Google Colab   | Akan dibuat pada requirements.txt |
| TensorFlow     | 2.x     | pip            | Akan dibuat pada requirements.txt |
| NumPy          | 1.x     | pip            | Akan dibuat pada requirements.txt |
| Pandas         | 2.x     | pip            | Akan dibuat pada requirements.txt |
| Scikit-learn   | 1.x     | pip            | Akan dibuat pada requirements.txt |
| Matplotlib     | 3.x     | pip            | Akan dibuat pada requirements.txt |

Konfigurasi:

  Config file     : config.ipynb (Google Colab Notebook)
  Random seed     : 42
  Hyperparameters :
    - Model            : EfficientNet-B6
    - Input Size       : 224×224 dan 528×528
    - Epoch            : 25 dan 50
    - Optimizer        : Adam
    - Batch Size       : 32
    - Validation       : 5-Fold Cross Validation

Reproducibility Check:

  [x] Dependency akan didokumentasikan dalam requirements.txt / lock file
  [x] Random seed direncanakan ditetapkan pada Python, NumPy, dan TensorFlow
  [x] Config eksperimen akan disimpan pada repository GitHub
  [x] README akan dilengkapi sebagai panduan reproduksi penelitian
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment yang direncanakan untuk eksperimen.

| Komponen    | Spesifikasi                                              |
| ----------- | -------------------------------------------------------- |
| CPU         | Intel Xeon (Google Colab Runtime)                        |
| RAM         | ±12 GB RAM                                               |
| GPU         | NVIDIA Tesla T4 atau GPU yang tersedia pada Google Colab |
| OS          | Linux (Ubuntu - Google Colab)                            |
| Runtime     | Python 3.11                                              |
| Framework   | TensorFlow 2.x dan Keras                                 |
| Random Seed | 42                                                       |

### Dependencies

| Library      | Version | Alasan Dibutuhkan                                          |
| ------------ | ------- | ---------------------------------------------------------- |
| Python       | 3.11    | Bahasa pemrograman utama                                   |
| TensorFlow   | 2.x     | Implementasi model EfficientNet-B6                         |
| NumPy        | 1.x     | Operasi numerik                                            |
| Pandas       | 2.x     | Pengolahan dataset                                         |
| Scikit-learn | 1.x     | Perhitungan Accuracy, Precision, Recall, F1-Score, dan AUC |
| Matplotlib   | 3.x     | Visualisasi grafik hasil pelatihan                         |

---

## Latihan 2 — Repeatability Test Plan

Rencana pengujian repeatability akan dilakukan menggunakan konfigurasi yang sama sebanyak tiga kali.

| Run | Seed | Metrik Utama | Hasil Sama?  |
| --- | ---- | ------------ | ------------ |
| 1   | 42   | Accuracy     | Direncanakan |
| 2   | 42   | Accuracy     | Direncanakan |
| 3   | 42   | Accuracy     | Direncanakan |

**Jika hasil berbeda, kemungkinan penyebab:**

* Random seed belum diterapkan pada seluruh proses pelatihan.
* GPU Google Colab yang digunakan berbeda.
* Dataset diproses dengan urutan yang berbeda.
* Perbedaan versi library yang digunakan.
* Konfigurasi eksperimen berubah.

### Checklist kontrol yang direncanakan

* [x] Random seed akan ditetapkan pada seluruh proses.
* [x] Tidak akan menjalankan proses lain yang mengganggu eksperimen.
* [x] Cache akan dibersihkan sebelum setiap pengujian.
* [x] Config file yang sama akan digunakan pada setiap run.

---

## Latihan 3 — README Eksperimen

```
# Judul Eksperimen

Pengaruh Variasi Ukuran Input Citra dan Jumlah Epoch terhadap Performa Model EfficientNet-B6 untuk Klasifikasi Penyakit Daun Padi

## 1. Environment

Google Colab
Python 3.11
TensorFlow 2.x
GPU NVIDIA Tesla T4 (atau GPU yang tersedia)

## 2. Installation

pip install tensorflow
pip install numpy
pip install pandas
pip install matplotlib
pip install scikit-learn

## 3. Data

Dataset Rice Leafs
Jumlah data : 3.355 citra
Jumlah kelas : 4

- Healthy
- Leaf Blast
- Hispa
- Brown Spot

## 4. Execution

Eksperimen direncanakan dijalankan menggunakan Google Colab mulai dari proses import library, preprocessing dataset, pelatihan model EfficientNet-B6, hingga evaluasi model.

## 5. Configuration

Model : EfficientNet-B6

Input Size :
- 224 × 224
- 528 × 528

Epoch :
- 25
- 50

Validation :
5-Fold Cross Validation

Optimizer :
Adam

Batch Size :
32

Random Seed :
42

## 6. Expected Output

- Accuracy
- Precision
- Recall
- F1-Score
- AUC
- Confusion Matrix
- ROC Curve
- Grafik Accuracy
- Grafik Loss
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:**

* [ ] Repeatability
* [ ] Reproducibility
* [x] Belum keduanya

**Komponen yang belum terdokumentasi:**

Penelitian masih berada pada tahap persiapan implementasi. Dokumentasi environment, konfigurasi eksperimen, serta README telah direncanakan. Setelah eksperimen selesai dilakukan, dokumentasi akan diperbarui dengan versi library yang digunakan, notebook Google Colab, file requirements.txt, hasil pengujian repeatability, dan output eksperimen sehingga penelitian dapat direproduksi oleh peneliti lain.
roducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> ___________________________________________________
