# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (DSR). Penting untuk membedakan keduanya:

| Paradigma | Cara Kerja | Contoh di TI |
|-----------|-----------|---------------|
| **Positivis** | Uji hipotesis dengan eksperimen terkontrol | Apakah CNN lebih akurat dari RF pada dataset X? |
| **Design Science Research** | Bangun artefak (sistem/model/framework) untuk menguji proposisi | Dapatkah arsitektur hybrid CNN+LSTM membuktikan peningkatan recall ≥5%? |
| **Interpretivis** | Pahami makna melalui konteks & kualitatif | Bagaimana peneliti manafsirkan anomali data sensor IoT? |

Dalam DSR, artefak **bukan tujuan akhir** — ia adalah instrumen untuk menghasilkan pengetahuan. Pertanyaan riset tetap harus difalsifikasi.

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Syukron Nur Fadillah
Tanggal          : 23 April 2026

1. Ketika membaca klaim "EfficientNet-B6 meningkatkan akurasi terbaik hingga 77.05%":
   - Pertanyaan pertama saya: Apakah performa 77.05% ini konsisten di setiap fold pengujian, atau hanya lonjakan acak (cherry-picked) akibat bias pembagian dataset yang tidak seimbang?
   - Data yang dibutuhkan untuk verifikasi: Laporan performa rata-rata dari seluruh 5-Fold Cross Validation, nilai standar deviasi akurasi, serta confusion matrix untuk melihat sebaran salah klasifikasi.

2. Posisi paradigma:
   - Pendekatan: [✓] Positivis  [ ] Interpretivis  [✓] Design Science  [ ] Mixed
   - Alasan: Penelitian ini membangun artefak teknologi berupa model klasifikasi deep learning (Design Science) dan menguji kinerjanya secara objektif melalui metrik matematis kuantitatif (Positivis).

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Dataset sekunder (Kaggle) dengan latar belakang seragam dianggap mewakili variasi visual riil daun padi di area persawahan terbuka.
   - Sumber bias potensial: Ketidakseimbangan data (imbalanced class) di mana jumlah citra daun sehat jauh mendominasi dibanding citra daun sakit.
   - Langkah mitigasi: Melakukan evaluasi menggunakan Accuracy, Precision, Recall, F1-Score, dan AUC sehingga performa model pada setiap kelas dapat dianalisis         secara lebih menyeluruh dibanding hanya menggunakan nilai akurasi.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Hasil akurasi dari setiap fold pengujian, termasuk fold dengan performa rendah (seperti fold 2 yang hanya berkisar ~71%).
   - Batasan yang diakui sejak awal: Ketergantungan penuh pada dataset sekunder terkurasi dan keterbatasan fungsional model yang hanya mendeteksi 3 jenis penyakit spesifik.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: Klasifikasi Penyakit Daun Padi Menggunakan Model Deep Learning EfficientNet-B6
> Penulis (Tahun): Amanda Caecilia Milano, Achmad Yasid, Rima Tri Wahyuningrum (2024)
> Sumber/Link DOI: JITET (Jurnal Informatika dan Teknik Elektro Terapan) / http://dx.doi.org/10.23960/jitet.v12i1.3855

| Tahap                 | Apa yang Dilakukan                                                       | Potensi Distorsi                                                                            |
| --------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| Reality → Data        | Mengambil dataset sekunder "Rice Leafs" dari Kaggle dengan total 3.355 citra (1.488 Healthy, 779 LeafBlast, 565 Hispa, dan 523 BrownSpot) | Distorsi Seleksi & Representasi: Dataset tidak seimbang secara alami (imbalanced). Distribusi kelas sehat terlalu mendominasi. Foto di Kaggle cenderung bersih dengan background seragam, sehingga kurang merepresentasikan realitas di sawah terbuka (masalah pencahayaan, debu, bayangan) |
| Data → Processing     | Melakukan penyamaan ukuran (resize) citra input menjadi 224 X 224 piksel dan 528 X 528 piksel, serta memisahkan data dengan stratified 5-Fold Cross Validation           | Distorsi Resolusi Informasi: Proses resizing ekstrem dari gambar asli beresolusi tinggi ke ukuran sekecil 224 X 224 berpotensi menghilangkan detail bercak penyakit yang sangat halus (misalnya titik-titik kecil Brown Spot)                      |
| Processing → Analysis | Melatih model EfficientNet-B6 menggunakan variasi parameter size input (224 vs 528) dan jumlah epoch (25 vs 50).              | Distorsi Komparasi/Parameter Bias: Paper ini langsung menggunakan EfficientNet-B6 tanpa melakukan komparasi langsung secara eksperimental dengan arsitektur lain (seperti ResNet atau MobileNet) pada dataset yang sama untuk membuktikan klaim "keunggulan efisiensinya" di kasus ini.                         |
| Analysis → Inference  | Menyajikan hasil uji coba di mana skenario ukuran input 224 dengan 50 epoch pada fold ke-5 memberikan akurasi tertinggi sebesar 77.05%                  | Distorsi Cherry-Picking: Menyoroti performa fold terbaik (77.05%) sebagai hasil utama, alih-alih berfokus pada performa rata-rata keseluruhan fold yang mencerminkan stabilitas model yang sebenarnya di lingkungan acak                    |
| Inference → Knowledge | Menyimpulkan bahwa metode Deep Learning dengan arsitektur EfficientNet-B6 sangat optimal untuk klasifikasi penyakit tanaman padi   | Over-generalization: Klaim performa optimal ditarik hanya berdasarkan pengujian pada satu sumber dataset laboratorium (Kaggle). Model belum diuji pada dataset eksternal independen untuk membuktikan generalisasinya                              |


Distorsi paling besar terjadi di tahap: Reality → Data (External Validity)

Justifikasi: Dataset yang digunakan berasal dari Kaggle yang dikondisikan (controlled environment). Di dunia nyata, daun padi bergoyang karena angin, memiliki bayangan dari daun lain, terkena pantulan sinar matahari terik, atau tertutup lumpur kering. Model yang mencapai akurasi ~77% pada data Kaggle ini kemungkinan besar akan mengalami penurunan performa drastis jika digunakan oleh petani di sawah secara langsung menggunakan kamera smartphone kelas menengah.

Dua distorsi spesifik yang teridentifikasi:

1.Class Imbalance Bias: Kelas daun sehat (Healthy) jauh lebih banyak daripada kelas berpenyakit. Metrik akurasi tinggi bisa terdistorsi akibat model sangat mahir menebak daun sehat, namun buruk dalam mendeteksi bercak penyakit yang krusial.

2.Resolution Downscaling Distortion: Pengurangan ukuran resolusi gambar secara drastis demi menghemat komputasi berisiko melenyapkan tekstur tepi bercak Leaf Blast atau pola garis halus Hispa yang merupakan fitur pembeda utama.


## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.


| Perspektif       | Analisis                                                                                                 |
| ---------------- | -------------------------------------------------------------------------------------------------------- |
| Kejujuran ilmiah | Peneliti wajib melaporkan seluruh metrik kinerja apa adanya. Misalnya, dalam paper ini, meskipun akurasi tertingginya 77.05% pada fold ke-5, peneliti secara jujur menyajikan tabel fold lain yang memiliki performa lebih rendah (misalnya fold ke-2 yang hanya mendapat akurasi 71.39%). Peneliti tidak menyembunyikan variabilitas performa model tersebut             |
| Transparansi     | Peneliti harus membeberkan batasan sistem, seperti kenyataan bahwa model ini dilatih menggunakan skenario parameter tertentu, dan mengakui keterbatasan fungsionalitas model yang kinerjanya sangat bergantung pada variasi ukuran input dan epoch                              |
| Peer review      | Penilai (reviewer) akan mengevaluasi kejujuran metodologi. Jika peneliti menghapus citra daun tertentu hanya karena model salah mengklasifikasikannya (agar akurasi terlihat naik dari 77% ke 85%), tindakan manipulasi ini akan merusak reproduksibilitas riset dan menyesatkan komunitas ilmiah pertanian |


*Keputusan akhir dan justifikasi:*
> Outlier atau data "sulit" (seperti citra daun padi dengan bercak ganda atau pencahayaan buruk) tidak boleh dihapus tanpa landasan ilmiah yang valid dan terdokumentasi (misalnya gambar tersebut memang rusak secara fisik/korup). Justifikasi penghapusan harus tertulis secara transparan di bagian metodologi. Jika tidak, hasil riset tersebut menjadi semu dan gagal ketika diimplementasikan pada aplikasi nyata petani di lapangan.

---

## Latihan 3 — Posisi Paradigma

*Topik riset:* Topik riset: Klasifikasi penyakit daun padi menggunakan model deep learning EfficientNet-B6.

> *Skala 1–5:* 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria                      | Positivis                                   | Interpretivis                            | Design Science                          |
| ----------------------------- | ------------------------------------------- | ---------------------------------------- | --------------------------------------- |
| Kesesuaian dengan topik (1–5) | 5 (Sangat Sesuai)     | 1 (Tidak Sesuai) | 5 (Sangat Sesuai) |
| Jenis data yang dikumpulkan   | Data numerik kuantitatif berupa akurasi (%), presisi, recall, F1-score, dan luas kurva AUC | Tidak digunakan                          | Artefak berupa arsitektur model klasifikasi dan parameter konfigurasi pelatihan       |
| Limitasi paradigma            | Sangat bergantung pada data historis numerik; gagal menangani faktor kualitatif di lapangan          | TTidak menghasilkan solusi teknis operasional yang presisi untuk klasifikasi citra       | Terlalu fokus pada optimasi fungsional artefak (kecepatan/akurasi), kadang mengabaikan kepraktisan penggunaannya oleh pengguna akhir                |


Paradigma yang dipilih: Positivis + Design Science Research (DSR)

Alasan: Penelitian ini mengikuti kerangka kerja DSR dengan menciptakan solusi berupa artefak teknologi (model klasifikasi penyakit tanaman berbasis EfficientNet-B6) untuk memecahkan masalah praktis pertanian. Kinerja dari artefak tersebut kemudian diuji dan divalidasi secara ketat menggunakan paradigma Positivis melalui metode eksperimen kuantitatif (K-Fold Cross Validation dan matriks evaluasi statistik) untuk mendapatkan kebenaran objektif yang terukur.https://journal.eng.unila.ac.id/index.php/jitet/article/view/3855

---

## Refleksi

> Pertanyaan Refleksi: Sebelum membaca materi ini, apakah Anda pernah mempertanyakan klaim "akurasi tinggi"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan Anda ajukan saat membaca paper klasifikasi citra berbasis deep learning?

**Jawaban:**
Sebelum memahami metodologi penelitian IT secara mendalam, saya sering kali terpukau dengan klaim akurasi tinggi tanpa melihat proses di baliknya. Kini, setelah memahami Research Trust Model dan rantai distorsinya, saya menyadari bahwa angka akurasi (bahkan yang setinggi 77% atau lebih) dapat dengan mudah bias.

Saat membaca paper bertopik sejenis di masa depan, pertanyaan kritis pertama saya adalah: "Apakah pembagian data pelatihan dan pengujian benar-benar bersih?" (mencegah data leakage akibat augmentasi sebelum pemisahan data). Pertanyaan kedua adalah: "Bagaimana performa model pada kelas minoritas?" (memastikan model tidak mengalami bias akibat kelas mayoritas). Dan yang terpenting: "Apakah model ini pernah diuji pada dataset yang sepenuhnya berbeda dari dataset pelatihannya untuk membuktikan validitas eksternalnya?"
