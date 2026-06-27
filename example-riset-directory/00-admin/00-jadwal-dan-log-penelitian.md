# Jadwal & Log Pelaksanaan Penelitian

Catatan kronologis pelaksanaan tiap tahap penelitian (sumber: riwayat commit GitHub & dokumen `09-docs/tahap-N-*.md`). Tanggal mengikuti `git log`.

## Log Pelaksanaan

| Tanggal                    | Tahap   | Aktivitas                                                                                                                                                                        | Referensi                                                                                                                               |
| -------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 2026-06-27                 | Tahap 1 | Finalisasi judul penelitian, penyusunan proposal penelitian, penyempurnaan Research Question (RQ), hipotesis, variabel penelitian, serta pembuatan repository GitHub penelitian. | [01-proposal/Proposal_Penelitian_EfficientNet_B6_Revisi.docx](../01-proposal/)                                                          |
| 2026-06-28                 | Tahap 2 | Studi literatur mengenai Artificial Intelligence, Deep Learning, CNN, EfficientNet-B6, serta klasifikasi penyakit daun padi. Pengumpulan referensi jurnal pendukung penelitian.  | [02-literatur/](../02-literatur/), [09-docs/tahap-2-studi-literatur.md](../09-docs/tahap-2-studi-literatur.md)                          |
| 2026-06-29                 | Tahap 2 | Penyusunan landasan teori mengenai Deep Learning, CNN, EfficientNet-B6, TensorFlow, Google Colab, dan dataset Rice Leafs.                                                        | [03-teori/](../03-teori/), [09-docs/tahap-2-landasan-teori.md](../09-docs/tahap-2-landasan-teori.md)                                    |
| 2026-06-30                 | Tahap 3 | Persiapan lingkungan penelitian menggunakan Google Colab, Google Drive, GitHub, instalasi library Python, serta identifikasi dataset Rice Leafs dari Kaggle.                     | [04-data/](../04-data/), [05-kode/](../05-kode/), [09-docs/tahap-3-persiapan-lingkungan.md](../09-docs/tahap-3-persiapan-lingkungan.md) |
| 2026-07-01                 | Tahap 3 | Persiapan dataset penelitian, dokumentasi sumber dataset, serta penyusunan struktur folder penelitian.                                                                           | [04-data/README.md](../04-data/README.md), [09-docs/tahap-3-persiapan-dataset.md](../09-docs/tahap-3-persiapan-dataset.md)              |
| 2026-07-02                 | Tahap 3 | Implementasi preprocessing dataset meliputi resize citra, normalisasi, pembagian data training-testing (80:20), dan konfigurasi 5-Fold Cross Validation.                         | [05-kode/preprocessing.ipynb](../05-kode/preprocessing.ipynb), [09-docs/tahap-3-preprocessing.md](../09-docs/tahap-3-preprocessing.md)  |
| 2026-07-03                 | Tahap 4 | Implementasi model EfficientNet-B6 serta konfigurasi empat skenario eksperimen berdasarkan variasi ukuran input citra dan jumlah epoch.                                          | [05-kode/training.ipynb](../05-kode/training.ipynb), [09-docs/tahap-4-training-model.md](../09-docs/tahap-4-training-model.md)          |
| 2026-07-04 s.d. 2026-07-07 | Tahap 4 | Pelaksanaan eksperimen empat skenario menggunakan EfficientNet-B6 pada Google Colab serta penyimpanan model hasil pelatihan.                                                     | [05-kode/](../05-kode/), [06-output/](../06-output/), [09-docs/tahap-4-eksperimen.md](../09-docs/tahap-4-eksperimen.md)                 |
| 2026-07-08                 | Tahap 5 | Evaluasi model menggunakan Accuracy, Precision, Recall, F1-Score, AUC, Confusion Matrix, dan ROC Curve.                                                                          | [06-output/](../06-output/), [09-docs/tahap-5-evaluasi.md](../09-docs/tahap-5-evaluasi.md)                                              |
| 2026-07-09                 | Tahap 5 | Analisis hasil eksperimen, pembahasan pengaruh ukuran input citra dan jumlah epoch, serta pengujian hipotesis penelitian.                                                        | [07-manuskrip/](../07-manuskrip/), [08-laporan/](../08-laporan/), [09-docs/tahap-5-analisis.md](../09-docs/tahap-5-analisis.md)         |
| 2026-07-10                 | Tahap 5 | Finalisasi laporan penelitian, pemeriksaan akhir dokumen, dan persiapan submit repository GitHub penelitian.                                                                     | [08-laporan/](../08-laporan/), [09-docs/](../09-docs/)                                                                                  |

## Status Ringkas

* **Tahap 1**: Selesai (Proposal penelitian dan repository GitHub selesai disiapkan).
* **Tahap 2**: Terjadwal (Studi literatur dan penyusunan landasan teori).
* **Tahap 3**: Terjadwal (Persiapan lingkungan penelitian, dataset, dan preprocessing).
* **Tahap 4**: Terjadwal (Implementasi dan eksperimen EfficientNet-B6).
* **Tahap 5**: Terjadwal (Evaluasi model, analisis hasil, dan penyusunan laporan).

## Item Tindak Lanjut (Checklist Sebelum Submission)

* [x] Menentukan judul penelitian
* [x] Menyusun proposal penelitian
* [x] Membuat repository GitHub penelitian
* [ ] Melengkapi studi literatur
* [ ] Menyusun landasan teori
* [ ] Menyiapkan Google Colab
* [ ] Menentukan dataset Rice Leafs dari Kaggle
* [ ] Melakukan preprocessing dataset
* [ ] Implementasi model EfficientNet-B6
* [ ] Menjalankan empat skenario eksperimen
* [ ] Melakukan evaluasi model
* [ ] Analisis hasil penelitian
* [ ] Penyusunan naskah penelitian
* [ ] Finalisasi laporan penelitian
* [ ] Review akhir seluruh dokumen sebelum submission

## Korespondensi

*(Belum ada. Tambahkan catatan bimbingan dengan dosen pembimbing atau korespondensi lain apabila sudah tersedia.)*
