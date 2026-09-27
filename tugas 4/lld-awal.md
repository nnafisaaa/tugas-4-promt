# Low-Level Design (LLD) Awal

## Penerapan Algoritma XGBoost dengan Optimasi Grid Search untuk Prediksi Jumlah Pengunjung Berdasarkan Hari Kunjungan pada Wisata Religi Makam Gus Dur


# 1. Desain Modul Sistem

Low-Level Design menjelaskan rancangan detail awal dari komponen sistem berdasarkan arsitektur High-Level Design.

Modul utama yang dirancang meliputi:

1. Validation Module
2. Prediction Module
3. Model Service
4. Grid Search Module
5. Result Module
6. Error Handling Module


# 1.1 Validation Module

## Deskripsi

Validation Module bertanggung jawab untuk melakukan pemeriksaan terhadap data masukan sebelum proses prediksi dijalankan.

## Tanggung Jawab

- Memeriksa kelengkapan input pengguna.
- Memastikan format data sesuai kebutuhan sistem.
- Memberikan response apabila data tidak valid.


## Method

### validateInput()

Input:

```text
visit_day
```

Output:

```text
valid / invalid
```


# 1.2 Prediction Module

## Deskripsi

Prediction Module merupakan modul utama yang mengatur proses prediksi jumlah pengunjung.

## Tanggung Jawab

- Menerima data hari kunjungan.
- Mengirim data ke model machine learning.
- Menghasilkan hasil prediksi jumlah pengunjung.


## Method

### predictVisitor()

Input:

```text
visit_day
```

Output:

```text
prediction_result
```


# 1.3 Model Service

## Deskripsi

Model Service bertanggung jawab untuk mengelola model machine learning XGBoost.

## Tanggung Jawab

- Memuat model XGBoost.
- Menjalankan proses prediksi.
- Mengembalikan hasil prediksi.


## Method

### loadModel()

Fungsi:

Memuat model XGBoost yang telah tersedia.


### predict()

Fungsi:

Melakukan prediksi berdasarkan data masukan.


Input:

```text
preprocessed_data
```

Output:

```text
predicted_value
```


# 1.4 Grid Search Module

## Deskripsi

Grid Search Module digunakan untuk melakukan optimasi parameter model XGBoost.

## Tanggung Jawab

- Menentukan kombinasi parameter model.
- Melakukan pengujian konfigurasi parameter.
- Menghasilkan parameter model terbaik.


## Method

### optimizeModel()

Input:

```text
parameter_grid
```

Output:

```text
best_parameter
```


# 1.5 Result Module

## Deskripsi

Result Module bertanggung jawab untuk mengelola hasil prediksi sebelum ditampilkan kepada pengguna.

## Tanggung Jawab

- Menerima hasil prediksi.
- Menyusun response.
- Menampilkan informasi kepada pengguna.


## Method

### displayResult()

Input:

```text
prediction_result
```

Output:

```text
prediction_response
```


# 1.6 Error Handling Module

## Deskripsi

Error Handling Module menangani kondisi kegagalan selama proses sistem berjalan.

## Tanggung Jawab

- Menangkap kesalahan proses.
- Memberikan informasi error.
- Mendukung proses ulang.


# 2. Struktur Data

Struktur data awal yang digunakan sistem:

| Field | Type | Description |
|---|---|---|
| id | integer | Identitas data |
| visit_day | string | Hari kunjungan yang diprediksi |
| prediction_result | integer | Hasil prediksi jumlah pengunjung |
| created_at | datetime | Waktu proses prediksi |


# 3. Spesifikasi API

## 3.1 Predict Visitor API


### Endpoint

```text
POST /api/predict
```


### Deskripsi

API digunakan untuk menerima input hari kunjungan dan menghasilkan prediksi jumlah pengunjung.


### Request

Header:

```text
Content-Type: application/json
```


Body:

```json
{
    "visit_day": "Sunday"
}
```


### Response Berhasil

Status Code:

```text
200 OK
```


Response:

```json
{
    "status": "success",
    "prediction": 1500
}
```


### Response Gagal

Status Code:

```text
400 Bad Request
```


Response:

```json
{
    "status": "error",
    "message": "Input tidak valid"
}
```


# 4. Sequence Flow Prediksi

Alur proses prediksi:

```text
User
 |
 | Input Hari Kunjungan
 v
Frontend
 |
 | Request Prediction
 v
Backend API
 |
 | Validasi Data
 v
Validation Module
 |
 | Data Valid
 v
Prediction Module
 |
 v
Model Service
 |
 v
XGBoost Model
 |
 v
Prediction Result
 |
 v
Frontend
 |
 v
User
```


# 5. Error Handling

Sistem memiliki beberapa penanganan kesalahan:

| Error Code | Kondisi | Response |
|---|---|---|
| 400 | Input tidak valid | Data masukan tidak sesuai |
| 408 | Proses timeout | Proses prediksi terlalu lama |
| 500 | Model error | Model gagal melakukan prediksi |


# 6. Traceability Requirement terhadap Modul

| Requirement | Modul |
|---|---|
| FR-01 Input hari kunjungan | Validation Module |
| FR-02 Validasi input | Validation Module |
| FR-03 Prediksi menggunakan XGBoost | Prediction Module |
| FR-04 Optimasi Grid Search | Grid Search Module |
| FR-05 Menampilkan hasil prediksi | Result Module |
| FR-06 Informasi kegagalan | Error Handling Module |
| FR-07 Status proses | Result Module |
| FR-08 Proses ulang ketika gagal | Error Handling Module |


# 7. Asumsi Implementasi

Beberapa detail implementasi belum ditentukan pada tahap awal:

- Framework frontend.
- Framework backend.
- Database yang digunakan.
- Infrastruktur deployment.
- Detail parameter model XGBoost.

Detail tersebut dapat disesuaikan pada tahap implementasi berikutnya.