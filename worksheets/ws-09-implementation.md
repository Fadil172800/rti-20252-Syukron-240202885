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

| Library        | Version | Sumber | Hash/Checksum |
|----------------|---------|--------|---------------|
| Python         | 3.11    | Google Colab | Akan dibuat pada requirements.txt |
| TensorFlow     | 2.x     | pip | Akan dibuat pada requirements.txt |
| NumPy          | 1.x     | pip | Akan dibuat pada requirements.txt |
| Pandas         | 2.x     | pip | Akan dibuat pada requirements.txt |
| Scikit-learn   | 1.x     | pip | Akan dibuat pada requirements.txt |
| Matplotlib     | 3.x     | pip | Akan dibuat pada requirements.txt |
| OpenCV         | 4.x     | pip | Akan dibuat pada requirements.txt |

Konfigurasi:

Config file     : Google Colab Notebook (.ipynb)

Random seed     : 42

Hyperparameters :

- Model            : EfficientNet-B6
- Input Size       : 224 × 224
- Epoch            : 25
- Optimizer        : Adam
- Batch Size       : 2
- Validation       : Single Split (80% Training, 20% Validation)

Reproducibility Check

[x] Dependency akan didokumentasikan dalam requirements.txt

[x] Random seed ditetapkan pada Python, NumPy, dan TensorFlow

[x] Config eksperimen disimpan pada repository GitHub

[x] README disediakan sebagai panduan reproduksi penelitian
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment yang direncanakan untuk eksperimen.

| Komponen    | Spesifikasi                           |
| ----------- | ------------------------------------- |
| CPU         | Intel Xeon (Google Colab Runtime)     |
| RAM         | ±12 GB RAM                            |
| GPU         | NVIDIA Tesla T4 atau GPU Google Colab |
| OS          | Linux (Ubuntu - Google Colab)         |
| Runtime     | Python 3.11                           |
| Framework   | TensorFlow 2.x dan Keras              |
| Random Seed | 42                                    |


### Dependencies

| Library      | Version | Alasan Dibutuhkan                                                   |
| ------------ | ------- | ------------------------------------------------------------------- |
| Python       | 3.11    | Bahasa pemrograman utama                                            |
| TensorFlow   | 2.x     | Implementasi model EfficientNet-B6                                  |
| NumPy        | 1.x     | Operasi numerik                                                     |
| Pandas       | 2.x     | Pengolahan dataset                                                  |
| Scikit-learn | 1.x     | Perhitungan Accuracy, Precision, Recall, F1-Score, Confusion Matrix |
| Matplotlib   | 3.x     | Visualisasi hasil pelatihan                                         |
| OpenCV       | 4.x     | Membaca dan memproses citra                                         |


---

## Latihan 2 — Repeatability Test Plan

Rencana pengujian repeatability akan dilakukan menggunakan konfigurasi yang sama sebanyak tiga kali.

| Run | Seed | Metrik Utama | Hasil Sama?  |
| --- | ---- | ------------ | ------------ |
| 1   | 42   | Accuracy     | Direncanakan |
| 2   | 42   | Accuracy     | Direncanakan |
| 3   | 42   | Accuracy     | Direncanakan |

**Jika hasil berbeda, kemungkinan penyebab:**

* GPU Google Colab yang digunakan berbeda.
* Operasi paralel TensorFlow tidak sepenuhnya deterministik.
* Dataset diproses dalam urutan berbeda akibat proses shuffle.
* Perbedaan versi library.
* Perubahan konfigurasi eksperimen.

### Checklist kontrol yang direncanakan

* ☑ Random seed ditetapkan pada Python, NumPy, dan TensorFlow.
* ☑ Cache dibersihkan sebelum proses pelatihan.
* ☑ Konfigurasi eksperimen yang sama digunakan pada setiap pengujian.
* ☑ Dataset menggunakan pembagian data (train-validation split) yang sama.

---

## Latihan 3 — README Eksperimen

```
# Judul Eksperimen

Klasifikasi Penyakit Daun Padi Menggunakan EfficientNet-B6 dengan Pendekatan Transfer Learning

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
pip install opencv-python-headless

## 3. Data

Dataset Rice Leafs

Jumlah data : 3.355 citra

Jumlah kelas : 4

- Brown Spot
- Healthy
- Hispa
- Leaf Blast

## 4. Execution

Eksperimen dijalankan menggunakan Google Colab mulai dari proses import library, preprocessing dataset, data augmentation, pembangunan model EfficientNet-B6, proses pelatihan menggunakan transfer learning, hingga evaluasi model.

## 5. Configuration

Model :
EfficientNet-B6

Transfer Learning :
Feature Extraction

Input Size :
224 × 224

Epoch :
25

Batch Size :
2

Validation :
Single Split (80% Training, 20% Validation)

Optimizer :
Adam

Random Seed :
42

## 6. Output

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- Classification Report
- Grafik Accuracy
- Grafik Loss
- Model (.keras)
- Model (.h5)
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:**

* [☑] Repeatability
* [ ] Reproducibility
* [ ] Belum keduanya

**Komponen yang belum terdokumentasi:**

Eksperimen telah memiliki notebook Google Colab, konfigurasi model, dataset, serta parameter pelatihan yang terdokumentasi. Namun, penelitian masih perlu dilengkapi dengan file requirements.txt yang memuat versi seluruh library, dokumentasi versi TensorFlow dan Python yang digunakan saat pelatihan, serta README yang lebih rinci mengenai langkah reproduksi eksperimen. Dengan melengkapi komponen tersebut, penelitian akan lebih mudah direproduksi oleh peneliti lain pada lingkungan yang serupa.
roducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> ___________________________________________________
