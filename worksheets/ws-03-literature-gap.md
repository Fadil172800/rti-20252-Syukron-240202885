# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
**LITERATURE MAPPING**

**Topik** : Klasifikasi Penyakit Daun Padi Menggunakan Deep Learning EfficientNet-B6.
**Database** : Google Scholar, IEEE Xplore, ResearchGate.
**Query** : `("rice leaf disease" OR "plant disease classification") AND ("CNN" OR "EfficientNet" OR "deep learning")`
**Tahun** : 2020 - 2024
**Hasil awal** : 12 paper → Screening → 5 paper final

**Literature Matrix (concept-centric):**

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Amanda Caecilia Milano et al. | 2024 | EfficientNet-B6 | 3355 citra daun padi | Akurasi terbaik 77.05% | Klasifikasi kelas Hispa dan LeafBlast masih sering salah |
| Singh et al. | 2023 | EfficientNet-B6 | Dataset daun buncis | EfficientNet-B6 unggul dibanding MobileNet dan NasNet | Fokus hanya pada daun buncis |
| Yuliany et al. | 2022 | CNN | Dataset hama padi | CNN mampu mengenali hama dengan baik | Belum menggunakan arsitektur modern |
| Agustiani et al. | 2022 | Random Forest + Color Histogram | Dataset daun padi | Dapat melakukan klasifikasi penyakit daun padi | Akurasi lebih rendah dibanding deep learning |
| Atila et al. | 2021 | EfficientNet | Dataset penyakit daun tanaman | EfficientNet memiliki performa tinggi dan efisien | Belum fokus pada tanaman padi Indonesia |

**Pola yang ditemukan:**
* **Metode dominan:** CNN dan EfficientNet menjadi metode yang paling sering digunakan untuk klasifikasi citra daun tanaman.
* **Dataset umum:** Dataset citra daun tanaman dengan beberapa kelas penyakit.
* **Limitasi berulang:** Akurasi model masih belum optimal dan sering terjadi kesalahan klasifikasi pada kelas tertentu.

---

**GAP IDENTIFICATION**

**Gap 1: [Performance Gap]**
* **Deskripsi** : Akurasi klasifikasi penyakit daun padi masih berada di sekitar 77% sehingga performa model belum optimal.
* **Bukti** : Penelitian Amanda Caecilia Milano et al. (2024) menghasilkan akurasi tertinggi sebesar 77.05%.
* **Signifikansi** : Akurasi yang lebih tinggi sangat penting agar diagnosis penyakit tanaman lebih tepat dan membantu petani mencegah gagal panen.

**Gap 2: [Method Gap]**
* **Deskripsi** : Sebagian besar penelitian masih menggunakan CNN biasa dan EfficientNet, sedangkan metode transformer masih jarang digunakan.
* **Bukti** : Dari beberapa paper yang dianalisis, metode dominan masih berbasis CNN.
* **Signifikansi** : Penggunaan metode yang lebih modern dapat meningkatkan performa klasifikasi citra daun padi.

**Baseline Selection:**

| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
| CNN Standar | Digunakan untuk klasifikasi citra daun padi | Banyak dipakai pada penelitian sebelumnya | Yuliany et al. (2022) |
| EfficientNet-B6 | Digunakan pada klasifikasi penyakit daun padi | Termasuk metode modern dengan performa tinggi | Amanda et al. (2024) |
```

---

---

## Latihan 1 — Concept-Centric Literature Table

Topik riset: Klasifikasi Penyakit Daun Padi Menggunakan Deep Learning EfficientNet-B6.
Query pencarian: ("rice leaf disease" OR "plant disease classification") AND ("CNN" OR "EfficientNet")
Database: Google Scholar, IEEE Xplore.

| # | Study                         | Tahun | Method          | Dataset                   | Result                                   | Limitasi                           |
| - | ----------------------------- | ----- | --------------- | ------------------------- | ---------------------------------------- | ---------------------------------- |
| 1 | Amanda Caecilia Milano et al. | 2024  | EfficientNet-B6 | 3355 citra daun padi      | Akurasi 77.05%                           | Kesalahan klasifikasi masih tinggi |
| 2 | Singh et al.                  | 2023  | EfficientNet-B6 | Dataset daun buncis       | EfficientNet unggul dibanding model lain | Fokus bukan pada daun padi         |
| 3 | Yuliany et al.                | 2022  | CNN             | Dataset hama tanaman padi | CNN cukup efektif                        | Belum memakai arsitektur modern    |
| 4 | Agustiani et al.              | 2022  | Random Forest   | Dataset daun padi         | Mampu mengklasifikasi penyakit           | Akurasi lebih rendah               |
| 5 | Atila et al.                  | 2021  | EfficientNet    | Dataset daun tanaman      | Performa model tinggi                    | Belum diuji pada konteks Indonesia |


Pola yang terlihat — Metode dominan:
CNN dan EfficientNet mendominasi penelitian klasifikasi citra daun tanaman.

Limitasi yang berulang:
Akurasi model masih belum stabil dan dataset yang digunakan masih terbatas.

---

## Latihan 2 — Gap Identification

| Jenis Gap       | Ditemukan?         | Gap Statement                                                                |
| --------------- | ------------------ | ---------------------------------------------------------------------------- |
| Performance Gap | [X] Ya / [ ] Tidak | Akurasi klasifikasi masih sekitar 77% sehingga model belum optimal.          |
| Method Gap      | [X] Ya / [ ] Tidak | Belum banyak penelitian menggunakan transformer untuk klasifikasi daun padi. |
| Data Gap        | [X] Ya / [ ] Tidak | Dataset masih terbatas dan jumlah kelas penyakit sedikit.                    |
| Context Gap     | [X] Ya / [ ] Tidak | Belum banyak penelitian pada kondisi pertanian Indonesia secara luas.        |

Gap utama yang dipilih: Performance Gap dan Method Gap.

Mengapa gap ini penting?

Karena hasil klasifikasi yang kurang akurat dapat menyebabkan kesalahan diagnosis penyakit tanaman padi. Jika metode yang lebih baik digunakan, maka petani dapat melakukan penanganan lebih cepat dan tepat.

---

## Latihan 3 — Baseline Selection

| # | Baseline        | Mengapa Relevan                                       | Mengapa Representatif                         | Apakah SOTA? | Sumber               |
| - | --------------- | ----------------------------------------------------- | --------------------------------------------- | ------------ | -------------------- |
| 1 | CNN Standar     | Sama-sama digunakan untuk klasifikasi citra daun padi | Metode umum pada penelitian sebelumnya        | Tidak        | Yuliany et al., 2022 |
| 2 | EfficientNet-B6 | Digunakan pada klasifikasi penyakit daun tanaman      | Memiliki performa tinggi dibanding model lain | Ya           | Amanda et al., 2024  |

---


## Refleksi

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [X] Tidak
>Justifikasi: Baseline dipilih secara adil karena menggunakan metode yang benar-benar relevan dan umum digunakan dalam penelitian klasifikasi citra daun tanaman.


**Jawaban:**
> Klaim “belum ada yang meneliti ini” tanpa bukti hanyalah asumsi biasa. Sedangkan research gap yang valid harus dibuktikan dengan membaca dan membandingkan beberapa penelitian sebelumnya. Gap dapat ditemukan jika terdapat kekurangan yang terus muncul, seperti akurasi rendah, metode yang belum digunakan, atau dataset yang terbatas.
