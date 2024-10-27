# Retail Sales Forecasting
By Alfa Isa Dewa


Notebook ini berfokus pada prediksi penjualan ritel untuk mendukung manajemen persediaan yang lebih efisien dan meningkatkan tingkat layanan pelanggan.

## Deskripsi Proyek

Proyek ini ditujukan untuk perusahaan ritel yang ingin **memperkirakan penjualan selama 30 hari ke depan** dan **mengoptimalkan safety stock** untuk menjaga tingkat layanan pelanggan. Dalam industri ritel, persediaan yang tidak tepat bisa mengakibatkan kekurangan atau kelebihan stok, yang dapat mempengaruhi biaya penyimpanan dan potensi pendapatan. Oleh karena itu, notebook ini mengimplementasikan model prediksi yang akurat untuk membantu dalam pengambilan keputusan persediaan.

### Stakeholders

1. **Tim Manajemen dan Eksekutif**: Memanfaatkan prediksi penjualan untuk perencanaan strategis.
2. **Tim Pemasaran**: Menggunakan hasil prediksi untuk menyesuaikan kampanye pemasaran dengan tren penjualan.

## Tujuan Proyek

1. **Memprediksi penjualan (sales) 30 hari ke depan** untuk perencanaan persediaan.
2. **Menentukan safety stock** yang optimal untuk lead time 30 hari, guna mempertahankan tingkat layanan 95%.

### Metode Prediksi

Pendekatan yang digunakan meliputi:
- Model **ARIMA**, **SARIMA**, dan **FB Prophet** untuk menangkap tren musiman dan dampak hari libur.
- Evaluasi akurasi menggunakan metrik **Mean Absolute Error (MAE)** dan **Root Mean Squared Error (RMSE)**.

### Hasil Evaluasi Model

| Model                                                     | MAE       | RMSE      |
|-----------------------------------------------------------|-----------|-----------|
| FB Prophet (portugal_holidays, changepoint_prior)         | 32.39     | 41.98     |
| ARIMA (1,1,1)                                             | 83.02     | 103.21    |
| SARIMA (1,1,3) Seasonal (1,0,1,7)                         | 83.29     | 102.84    |


### Perhitungan Safety Stock

- **Standard Deviation of Forecast Error (σ)**: 82.23
- **Z-score untuk Service Level 95%**: 1.64485
- **Calculated Safety Stock**: 740.85

## Struktur Notebook

### 1. Business Understanding

   - **Context**: Penjelasan tentang sektor ritel, tantangan inventori, dan pentingnya prediksi penjualan.
   - **Problem Statement**: Perusahaan menghadapi fluktuasi permintaan yang sering mengakibatkan ketidakseimbangan persediaan.
   - **Goals**: Menyediakan prediksi penjualan dan mengoptimalkan safety stock untuk tingkat layanan yang lebih tinggi.

### 2. Data Understanding

   - Menyediakan analisis data awal, seperti rangkuman statistik dan pola musiman, yang relevan untuk pelatihan model prediksi.

### 3. Data Preprocessing

   - Proses penanganan data, termasuk pembersihan data, transformasi waktu, dan pemilihan fitur relevan yang sesuai untuk model prediksi.

### 4. Model Building

   - **ARIMA, SARIMA, dan FB Prophet**: Model dibangun untuk menangkap tren dan pola musiman.
   - **Evaluasi Model**: Menggunakan MAE dan RMSE untuk mengevaluasi akurasi masing-masing model.

### 5. Forecasting and Safety Stock Calculation

   - **Forecasting**: Membuat prediksi 30 hari ke depan untuk penjualan.
   - **Safety Stock Calculation**: Menghitung safety stock dengan mempertimbangkan standar deviasi error dan Z-score untuk mencapai tingkat layanan 95%.

### 6. Cross-Validation and Optimization

   - Melakukan cross-validation pada model untuk menilai performanya pada berbagai horizon prediksi.
   - Optimasi safety stock untuk menyeimbangkan antara biaya penyimpanan dan tingkat layanan.

## Rekomendasi Singkat

### **Untuk Perusahaan**

1. **Pertahankan Safety Stock untuk Lead Time 30 Hari**:  
   Pertahankan safety stock sebesar 741 unit untuk menghindari kekurangan stok selama lead time, menjaga tingkat layanan 95%.

2. **Tinjau Safety Stock Berkala**:  
   Lakukan peninjauan safety stock setiap beberapa bulan untuk mengantisipasi perubahan pola permintaan.

3. **Perhatikan Musim dan Hari Libur**:  
   Tingkatkan safety stock saat permintaan tinggi (seperti musim liburan) untuk mengurangi risiko kehabisan stok.

### **Untuk Model Prediksi**

1. **Gunakan FB Prophet sebagai Model Utama**:  
   Prophet terbukti unggul dalam menangkap tren dan pola musiman, sehingga cocok digunakan sebagai model utama.

2. **Eksplorasi Model Hybrid untuk Akurasi Lebih Tinggi**:  
   Pertimbangkan model hybrid seperti Prophet + XGBoost atau LSTM untuk pola permintaan yang kompleks.

3. **Uji Model Machine Learning**:  
   Pertimbangkan model seperti Random Forest atau Neural Networks jika data menjadi lebih dinamis.

4. **Monitoring dan Evaluasi Berkala**:  
   Evaluasi model setiap beberapa bulan untuk memastikan akurasi prediksi tetap optimal, dengan metrik MAE dan RMSE.

5. **Siapkan Data Berkualitas untuk Model AI**:  
   Kumpulkan data historis yang konsisten untuk mendukung model prediksi berbasis AI di masa depan.

### **Rekomendasi Akhir**

Gunakan **FB Prophet sebagai model utama** saat ini, mengingat kemampuannya menangani tren dan musiman dengan baik. Seiring bertambahnya data dan perubahan pola, pertimbangkan model hybrid atau ensemble untuk meningkatkan akurasi dan adaptabilitas prediksi. Monitoring berkala akan memastikan model tetap optimal sesuai kebutuhan bisnis.

## Cara Menggunakan Notebook
- **Instalasi Dependensi**

   Instal semua pustaka yang diperlukan:

   ```bash
   pip install pandas numpy matplotlib joblib prophet statsmodels
