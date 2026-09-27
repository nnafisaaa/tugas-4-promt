# Prompt Log Pertemuan 04

## Dokumentasi Penggunaan AI dalam Proses Perancangan HLD dan LLD Awal

Dokumen ini berisi catatan penggunaan AI sebagai alat bantu dalam proses penyusunan dokumen desain sistem, khususnya pada tahap pembuatan High-Level Design (HLD) dan Low-Level Design (LLD) awal.

Penggunaan AI dilakukan untuk membantu menghasilkan rancangan awal yang kemudian dilakukan pemeriksaan dan penyesuaian agar tetap sesuai dengan requirement sistem.


# 1. Prompt Penyusunan High-Level Design (HLD)

## Tujuan

Membantu menyusun rancangan arsitektur tingkat tinggi berdasarkan dokumen kebutuhan sistem yang telah dibuat sebelumnya.


## Prompt

```
Bertindak sebagai Software Architect.

Buat rancangan High-Level Design (HLD) untuk aplikasi berbasis website dengan topik prediksi jumlah pengunjung menggunakan algoritma XGBoost dengan optimasi Grid Search.

Rancangan harus mencakup:
- deskripsi sistem;
- arsitektur sistem;
- diagram komponen;
- diagram alur data;
- komponen utama sistem;
- keputusan teknologi;
- security dan privacy;
- deployment environment.

Pastikan rancangan mengikuti requirement pada SRS dan user story yang tersedia.
Jangan menambahkan fitur baru di luar kebutuhan sistem.
```


## Output AI

AI menghasilkan rancangan awal berupa:

- struktur arsitektur client-server;
- pembagian komponen frontend, backend, prediction service, model AI, dan database;
- alur data dari input pengguna hingga hasil prediksi;
- rekomendasi struktur dokumentasi HLD.


## Evaluasi Manual

Hasil AI diperiksa kembali dengan memastikan:

- komponen sistem sesuai dengan kebutuhan aplikasi;
- tidak terdapat fitur tambahan di luar requirement;
- penggunaan XGBoost dan Grid Search tetap menjadi fokus utama sistem.


# 2. Prompt Penyusunan Low-Level Design (LLD) Awal

## Tujuan

Membantu menurunkan rancangan HLD menjadi desain implementasi awal yang lebih detail.


## Prompt

```
Bertindak sebagai Software Engineer.

Buat rancangan Low-Level Design (LLD) awal berdasarkan dokumen High-Level Design.

Rancangan harus mencakup:
- desain modul;
- tanggung jawab setiap modul;
- method utama;
- struktur data;
- spesifikasi API;
- request dan response JSON;
- error handling;
- traceability antara requirement dan modul.

Gunakan rancangan sistem prediksi jumlah pengunjung berbasis XGBoost dan Grid Search.
Jangan membuat implementasi kode secara detail, cukup desain awal.
```


## Output AI

AI menghasilkan rancangan awal berupa:

- modul validation;
- modul prediction;
- model service;
- grid search module;
- result module;
- error handling module;
- rancangan endpoint API;
- struktur data awal.


## Evaluasi Manual

Hasil AI diperiksa dengan memastikan:

- modul sesuai dengan arsitektur HLD;
- API hanya mencakup kebutuhan sistem;
- struktur data tidak menambahkan atribut yang tidak diperlukan;
- detail implementasi masih berada pada tingkat desain awal.


# 3. Prompt Review dan Penyempurnaan Dokumen

## Tujuan

Melakukan pengecekan konsistensi antara requirement, HLD, dan LLD.


## Prompt

```
Lakukan review terhadap dokumen HLD dan LLD awal.

Periksa:
- kesesuaian dengan SRS;
- kesesuaian dengan user story;
- kelengkapan komponen desain;
- konsistensi antara HLD dan LLD;
- kemungkinan requirement yang belum terakomodasi.

Berikan perbaikan tanpa mengubah tujuan utama sistem.
```


## Hasil Review

Perbaikan yang dilakukan:

- Menambahkan penjelasan fungsi setiap komponen sistem.
- Memperjelas alur data prediksi.
- Menambahkan spesifikasi API.
- Menambahkan traceability requirement terhadap modul.
- Menambahkan asumsi untuk detail yang belum tersedia.


# 4. Koreksi Manual Akhir

Setelah menggunakan AI, dilakukan penyesuaian manual dengan ketentuan:

- Tidak menambahkan fitur baru di luar requirement.
- Rancangan tetap mengikuti PRD, SRS, dan user story.
- Detail yang belum tersedia ditulis sebagai asumsi.
- Hasil akhir disesuaikan dengan kebutuhan tugas HLD dan LLD awal.


# 5. Kesimpulan Penggunaan AI

AI digunakan sebagai alat bantu dalam menghasilkan rancangan awal sistem, mempercepat penyusunan struktur dokumen, dan membantu pemeriksaan konsistensi desain.

Seluruh hasil dari AI tetap melalui proses evaluasi manual agar sesuai dengan kebutuhan sistem dan batasan proyek.