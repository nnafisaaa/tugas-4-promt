# High-Level Design (HLD)

## Penerapan Algoritma XGBoost dengan Optimasi Grid Search untuk Prediksi Jumlah Pengunjung Berdasarkan Hari Kunjungan pada Wisata Religi Makam Gus Dur


# 1. Deskripsi Sistem

Sistem ini merupakan aplikasi berbasis website yang dirancang untuk melakukan prediksi jumlah pengunjung pada Wisata Religi Makam Gus Dur berdasarkan hari kunjungan.

Sistem menggunakan algoritma **XGBoost (Extreme Gradient Boosting)** sebagai model machine learning untuk menghasilkan estimasi jumlah pengunjung. Optimasi model dilakukan menggunakan metode **Grid Search** untuk menentukan kombinasi parameter model yang sesuai berdasarkan konfigurasi yang digunakan.

Pengguna utama sistem adalah pengelola wisata. Pengguna dapat memasukkan hari kunjungan yang ingin diprediksi, kemudian sistem melakukan validasi data, menjalankan proses prediksi menggunakan model XGBoost, dan menampilkan hasil estimasi jumlah pengunjung.


# 2. Tujuan Arsitektur Sistem

Perancangan arsitektur sistem bertujuan untuk:

1. Memisahkan komponen antarmuka pengguna, proses bisnis, layanan prediksi, dan penyimpanan data.
2. Mempermudah pengembangan serta pemeliharaan sistem.
3. Menyediakan alur komunikasi yang jelas antara pengguna, aplikasi, dan model machine learning.
4. Mendukung integrasi model XGBoost ke dalam aplikasi berbasis website.


# 3. Arsitektur Sistem

Sistem menggunakan pendekatan **client-server architecture** yang terdiri dari beberapa komponen utama.


## 3.1 Frontend Website

Frontend merupakan bagian sistem yang berinteraksi langsung dengan pengguna.

Tanggung jawab:

- Menyediakan halaman input hari kunjungan.
- Mengirimkan permintaan prediksi.
- Menampilkan status proses.
- Menampilkan hasil prediksi jumlah pengunjung.


## 3.2 Backend API

Backend API berfungsi sebagai penghubung antara frontend dengan layanan prediksi.

Tanggung jawab:

- Menerima request dari pengguna.
- Melakukan validasi data masukan.
- Mengatur komunikasi antar komponen sistem.
- Mengirimkan hasil prediksi kepada frontend.


## 3.3 Prediction Service

Prediction Service bertanggung jawab dalam mengatur proses prediksi.

Tanggung jawab:

- Menerima data yang telah divalidasi.
- Melakukan preprocessing data.
- Memanggil model machine learning.
- Mengembalikan hasil prediksi.


## 3.4 Machine Learning Model

Komponen utama AI menggunakan algoritma XGBoost.

Tanggung jawab:

- Melakukan prediksi jumlah pengunjung.
- Menggunakan model dengan parameter yang telah dioptimasi menggunakan Grid Search.


## 3.5 Database

Database digunakan untuk menyimpan data yang diperlukan dalam sistem.

Tanggung jawab:

- Menyimpan data historis.
- Menyimpan informasi pendukung proses prediksi.


# 4. Diagram Arsitektur Sistem

```mermaid
flowchart LR

A[Pengguna]
B[Frontend Website]
C[Backend API]
D[Prediction Service]
E[XGBoost Model]
F[Database]

A --> B
B --> C
C --> D
D --> E
E --> F

E --> D
D --> C
C --> B
B --> A
```


# 5. Diagram Alur Data

Alur data sistem dimulai ketika pengguna memasukkan hari kunjungan sampai sistem menghasilkan prediksi jumlah pengunjung.

```text
Input Hari Kunjungan
        |
        v
Validasi Input
        |
        v
Preprocessing Data
        |
        v
Prediction Service
        |
        v
XGBoost Model
        |
        v
Hasil Prediksi
        |
        v
Tampilan Website
```


# 6. Alur Data Fitur AI

Proses fitur AI terdiri dari beberapa tahap:

1. Pengguna memasukkan hari kunjungan.
2. Sistem melakukan validasi terhadap data masukan.
3. Data dipersiapkan sesuai format model.
4. Data dikirim ke Prediction Service.
5. Model XGBoost melakukan proses prediksi.
6. Hasil prediksi dikembalikan ke sistem.
7. Sistem menampilkan hasil prediksi kepada pengguna.


Apabila proses prediksi mengalami kegagalan, sistem memberikan informasi kegagalan dan menyediakan mekanisme percobaan ulang.


# 7. Komponen Sistem

| Komponen | Fungsi |
|---|---|
| Frontend Website | Menyediakan tampilan input dan hasil prediksi |
| Backend API | Mengatur komunikasi antar komponen sistem |
| Prediction Service | Menjalankan proses prediksi |
| XGBoost Model | Menghasilkan prediksi jumlah pengunjung |
| Grid Search | Melakukan optimasi parameter model |
| Database | Menyimpan data yang diperlukan sistem |


# 8. Keputusan Teknologi

| Komponen | Teknologi | Alasan |
|---|---|---|
| Platform | Website | Mudah digunakan oleh pengelola wisata |
| Model AI | XGBoost | Sesuai untuk proses prediksi berbasis data |
| Optimasi Model | Grid Search | Membantu menentukan kombinasi parameter terbaik |
| Komunikasi Sistem | REST API | Mendukung komunikasi frontend dan backend |


# 9. Security dan Privacy

Aspek keamanan sistem yang diterapkan:

- Validasi input pengguna sebelum diproses.
- Pembatasan akses terhadap layanan sistem.
- Pengelolaan data secara aman.
- Menghindari penyimpanan data pengguna yang tidak diperlukan.


# 10. Deployment Environment

## Development Environment

Digunakan untuk:

- Pengembangan aplikasi.
- Pengujian fitur sistem.
- Pengujian model machine learning.


## Production Environment

Digunakan oleh pengelola wisata untuk menjalankan sistem prediksi jumlah pengunjung.


# 11. Asumsi dan Batasan

Beberapa detail teknis belum ditentukan pada tahap awal desain, antara lain:

- Konfigurasi server.
- Detail struktur database.
- Parameter Grid Search.
- Infrastruktur deployment akhir.

Detail tersebut akan disesuaikan pada tahap implementasi berikutnya.


# 12. Hubungan dengan Dokumen Requirement

Dokumen High-Level Design ini dibuat berdasarkan dokumen kebutuhan sebelumnya:

- Product Requirement Document (PRD).
- Software Requirement Specification (SRS).
- User Story.
- Use Case.
- Acceptance Criteria.

Dokumen HLD ini menjadi dasar penyusunan **Low-Level Design (LLD) awal** sebelum tahap implementasi sistem.