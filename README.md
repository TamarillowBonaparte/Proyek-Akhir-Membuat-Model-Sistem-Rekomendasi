# Laporan Proyek Machine Learning - Moch Dani Kurniawan Sugiarto
**Proyek-Akhir-Membuat-Model-Sistem-Rekomendasi**
## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

## Business Understanding

Sistem rekomendasi merupakan salah satu aplikasi machine learning yang paling umum digunakan dalam industri digital, terutama di platform streaming film seperti Netflix, IMDb, dan lainnya. Tujuan dari sistem ini adalah memberikan saran konten (film) kepada pengguna berdasarkan preferensi mereka, baik berdasarkan riwayat tontonan maupun perilaku pengguna lain.

Dalam proyek ini, dibangun dua jenis pendekatan sistem rekomendasi:

- Content-Based Filtering , yang merekomendasikan film berdasarkan kesamaan genre dan deskripsi.
- Collaborative Filtering , yang menggunakan data rating pengguna secara kolektif untuk menemukan pola kesukaan.

Masalah ini penting diselesaikan karena sistem rekomendasi meningkatkan keterlibatan pengguna, membantu menemukan konten baru yang relevan, dan pada akhirnya meningkatkan kepuasan dan retensi pengguna

### Problem Statements

Bagaimana cara merekomendasikan film kepada pengguna berdasarkan film yang sebelumnya telah ditonton atau disukai oleh pengguna lain, khususnya yang memiliki genre serupa dan kemungkinan besar juga akan disukai?

### Goals

Membangun sebuah sistem rekomendasi yang mampu memberikan saran film secara akurat berdasarkan rating dan riwayat tontonan pengguna di masa lalu.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
**Dataset**
Dataset yang digunakan berasal dari MovieLens (ml-latest-small) , tersedia melalui Kaggle: https://www.kaggle.com/rohan4050/movie-recommendation-data

Dataset terdiri dari 4 file CSV:

- movies.csv: Informasi film (movieId, title, genres)
- ratings.csv: Rating pengguna (userId, movieId, rating)
- tags.csv: Tags tambahan untuk film
- links.csv: Tautan eksternal ke IMDb dan TMDB

**EDA**

Total film: ±9.000+

Total pengguna: ±600+

Total rating: ±100.000+

Distribusi rating dominan pada skala 3–5

Genre populer: Drama, Comedy, Thriller

Jumlah film per tahun meningkat pesat setelah 1990-an

## Visualisasi

Visualisasi distribusi rating, jumlah film per genre, jumlah rating per user, dan tren film per tahun dilakukan untuk mendapatkan insight awal tentang dataset.

## Data Preparation
**Tahapan Preprocessing**
1. Penggabungan Dataset

Gabung tabel ratings dengan movies untuk mendapatkan informasi judul dan genre.

2. Penanganan Missing Value

Hapus baris duplikat dan nilai kosong pada kolom movieId.

3. Encoding ID Pengguna dan Film

Mapping userId dan movieId menjadi indeks numerik untuk model Collaborative Filtering.

4. Normalisasi Rating

Normalisasi nilai rating dari 0 hingga 1 untuk pelatihan model neural network.

Alasan : Preprocessing diperlukan agar data siap digunakan dalam model machine learning, termasuk encoding ID, normalisasi fitur, dan penyesuaian format input.

## Modeling
1. Content-Based Filtering
Model ini menggunakan TF-IDF Vectorizer untuk mengubah genre film menjadi vektor numerik, lalu menghitung cosine similarity untuk menemukan film dengan genre mirip.

🎯 Recommendations for 'Toy Story (1995)':
   • Toy Story 2 (1999) - Animation|Children|Comedy
     Similarity: 0.333
   • Finding Nemo (2003) - Animation|Children|Comedy|Adventure
     Similarity: 0.298

2. Collaborative Filtering (Neural Network)
Model ini menggunakan arsitektur Neural Collaborative Filtering (NCF), dengan embedding layer untuk user dan film, serta dot product untuk menghitung interaksi. Model dilatih dengan optimisasi Adam dan loss binary crossentropy.

Arsitektur:
Input: userId, movieId
Embedding: 50 dimensi
Output: Prediksi rating (0–5)

🎯 Top 5 Recommendations for User 143:
   • The Godfather (1972) - Drama
     Predicted Rating: 4.92
   • Pulp Fiction (1994) - Crime|Drama
     Predicted Rating: 4.87

## Evaluation
Model Collaborative Filtering dievaluasi menggunakan:

MAE (Mean Absolute Error) : Rata-rata kesalahan absolut antara prediksi dan nilai sebenarnya.

MSE (Mean Squared Error) : Rata-rata kuadrat kesalahan, lebih sensitif terhadap error besar.

Hasil Evaluasi
- Final Training MAE: ~0.12
- Final Validation MAE: ~0.15
- Final Training MSE: ~0.027
- Final Validation MSE: ~0.036

Grafik evaluasi selama epoch menunjukkan bahwa model tidak overfitting dan memiliki performa yang stabil.

## Perbandingan Pendekatan Content-Based dan Collaborative Filtering

| Aspek               | Content-Based Filtering | Collaborative Filtering |
|---------------------|--------------------------|--------------------------|
| **Data Requirement**| Metadata film            | Riwayat rating pengguna  |
| **Cold Start**      | Baik                     | Buruk                    |
| **Scalability**     | Tinggi                   | Menengah                 |
| **Diversity**       | Rendah                   | Tinggi                   |
