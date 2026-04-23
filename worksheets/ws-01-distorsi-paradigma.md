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

1. Ketika membaca klaim "model CNN + transfer learning meningkatkan akurasi menjadi 73%":
   - Pertanyaan pertama saya: Apakah peningkatan akurasi tersebut benar-benar berasal dari metode transfer learning, atau dipengaruhi oleh faktor lain seperti kualitas dataset, preprocessing, atau pembagian data?
   - Data yang dibutuhkan untuk verifikasi: Detail dataset (jumlah, distribusi kelas), confusion matrix, metode split data (train/validation/test), arsitektur model, serta perbandingan eksperimen yang adil.


2. Posisi paradigma:
   - Pendekatan: [✓ ] Positivis  [ ] Interpretivis  [✓ ] Design Science  [ ] Mixed
   - Alasan: Penelitian menguji performa model CNN secara kuantitatif (positivis) serta membangun artefak berupa model klasifikasi berbasis MobileNetV2 (design science).

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Dataset bunga hasil crawling dianggap merepresentasikan kondisi nyata di lapangan.
   - Sumber bias potensial: Dataset kecil (2137 citra), kemungkinan ketidakseimbangan kelas, serta data hasil crawling yang tidak terstandarisasi.
   - Langkah mitigasi: Menggunakan dataset tambahan, validasi silang, serta evaluasi pada data real-world (bukan hanya dataset uji internal).

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Seluruh hasil akurasi, termasuk jika model tanpa transfer learning memiliki performa rendah.
   - Batasan yang diakui sejak awal: Dataset terbatas dan mungkin tidak mewakili seluruh variasi bunga di Indonesia.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: Klasifikasi Citra Spesies Bunga di Indonesia Berbasis CNN dengan Transfer Learning
> Penulis (Tahun): Arif Rahman, Mansyur Salim, Imam Riadi (2023)
> Sumber/Link DOI: Jurnal Software Engineering and Computational Intelligence/ https://ejournal.uigm.ac.id/index.php/JSECI/article/view/4942

| Tahap                 | Apa yang Dilakukan                                                       | Potensi Distorsi                                                                            |
| --------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| Reality → Data        | Mengambil citra bunga dari internet (crawling Bing) sebanyak 2137 gambar | Data tidak terkontrol → berpotensi noisy dan tidak representatif (external validity rendah) |
| Data → Processing     | Preprocessing: normalisasi dan augmentasi (flip, resize)                 | Augmentasi dapat membuat data terlalu “ideal” dibanding kondisi nyata                       |
| Processing → Analysis | Training CNN MobileNetV2 dengan dan tanpa transfer learning              | Risiko overfitting karena dataset relatif kecil dan kurang variasi                          |
| Analysis → Inference  | Membandingkan performa berdasarkan akurasi (73% vs 42%)                  | Hanya menggunakan akurasi → tidak cukup merepresentasikan performa model                    |
| Inference → Knowledge | Menyimpulkan transfer learning meningkatkan performa secara signifikan   | Over-generalization karena hanya diuji pada satu dataset kecil                              |


*Distorsi paling besar di tahap:* Reality → Data (External Validity) Karena dataset berasal dari crawling internet dan jumlahnya terbatas, kemungkinan besar tidak merepresentasikan kondisi nyata (misalnya pencahayaan, sudut kamera, kualitas gambar).https://ejournal.uigm.ac.id/index.php/JSECI/article/view/4942

*Dua distorsi spesifik yang teridentifikasi:*
1. Dataset hasil crawling tidak terstandarisasi dan bisa mengandung noise
2. Dataset relatif kecil → model berpotensi overfitting


## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif       | Analisis                                                                                                 |
| ---------------- | -------------------------------------------------------------------------------------------------------- |
| Kejujuran ilmiah | Hasil tanpa transfer learning (akurasi lebih rendah) tetap harus dilaporkan secara lengkap               |
| Transparansi     | Peneliti harus menjelaskan keterbatasan dataset yang berasal dari crawling                               |
| Peer review      | Reviewer kemungkinan mempertanyakan validitas dan generalisasi jika hanya menggunakan satu dataset kecil |


*Keputusan akhir dan justifikasi:*
> Data tidak boleh dimanipulasi untuk meningkatkan hasil. Dalam konteks jurnal ini, perbandingan antara model dengan dan tanpa transfer learning sudah benar dilakukan. Namun, peneliti tetap harus transparan bahwa peningkatan akurasi bisa dipengaruhi oleh keterbatasan dataset, bukan hanya keunggulan metode.

---

## Latihan 3 — Posisi Paradigma

*Topik riset:* Topik riset: Klasifikasi citra bunga menggunakan CNN + Transfer Learning

> *Skala 1–5:* 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria                      | Positivis                                   | Interpretivis                            | Design Science                          |
| ----------------------------- | ------------------------------------------- | ---------------------------------------- | --------------------------------------- |
| Kesesuaian dengan topik (1–5) | 5 — fokus pada pengujian performa model     | 1 — tidak melibatkan analisis kualitatif | 5 — membangun model CNN sebagai artefak |
| Jenis data yang dikumpulkan   | Data numerik (akurasi, loss, dataset citra) | Tidak digunakan                          | Output model dan performa sistem        |
| Limitasi paradigma            | Bergantung pada kualitas dataset            | Tidak relevan untuk masalah teknis       | Model berpotensi overfit                |


*Paradigma yang dipilih:* Positivis + Design Science
*Alasan:* Penelitian ini menguji performa model secara kuantitatif (positivis) sekaligus membangun artefak berupa model CNN berbasis MobileNetV2 dengan transfer learning (design science).https://ejournal.uigm.ac.id/index.php/JSECI/article/view/4942

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelumnya, saya cenderung menerima klaim akurasi tinggi seperti 73% pada model CNN dengan transfer learning tanpa mempertanyakan konteksnya. Setelah memahami konsep distorsi dalam Research Trust Model, saya menyadari bahwa angka tersebut bisa dipengaruhi oleh banyak faktor seperti pemilihan dataset, preprocessing, dan metode evaluasi.
> Sekarang, saya akan mempertanyakan apakah dataset yang digunakan representatif terhadap kondisi nyata, apakah terdapat bias dalam preprocessing seperti augmentasi atau penghapusan data tertentu, serta apakah hasil tersebut dapat digeneralisasi ke data lain. Saya juga lebih kritis terhadap klaim performa tinggi dan tidak langsung menganggapnya sebagai bukti keunggulan metode.
