# Laporan Proyek Machine Learning - Moch Dani Kurniawan Sugiarto
**Proyek-Akhir-Membuat-Model-Sistem-Rekomendasi**
## Project Overview

Di era digital saat ini, jumlah konten film yang tersedia secara daring semakin melimpah. Platform streaming seperti Netflix, Disney+, dan layanan lokal menghadirkan ribuan judul film dari berbagai genre dan negara. Situasi ini membuat pengguna sering merasa kebingungan dalam memilih film yang sesuai dengan minat dan preferensi mereka. Di sinilah sistem rekomendasi memiliki peran penting — membantu pengguna menemukan film yang relevan dan menarik tanpa harus mencarinya secara manual.

Proyek ini bertujuan untuk membangun sistem rekomendasi film dengan dua pendekatan utama: Content-Based Filtering dan Collaborative Filtering. Content-Based Filtering menggunakan informasi dari konten film seperti genre dan sinopsis, sedangkan Collaborative Filtering memanfaatkan data interaksi pengguna seperti rating dan pola preferensi untuk mempelajari kesamaan antar pengguna atau antar item.

Pengembangan sistem ini tidak hanya memberikan pengalaman personalisasi yang lebih baik bagi pengguna, tetapi juga dapat meningkatkan durasi keterlibatan pengguna (user engagement) dan kepuasan pelanggan di platform layanan streaming. Selain itu, sistem rekomendasi memiliki nilai komersial yang tinggi karena dapat digunakan oleh industri hiburan untuk menyajikan konten yang lebih tepat sasaran.

Dengan memanfaatkan Movie Recommender Dataset, proyek ini juga menjadi media pembelajaran untuk mengimplementasikan teknik pemrosesan data, machine learning, dan evaluasi model secara praktis dalam konteks dunia nyata.

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

### Solution statements
Untuk mencapai tujuan tersebut, digunakan dua pendekatan utama:

- Content-Based Filtering : Menggunakan metadata film (judul, genre) untuk menghitung kesamaan antar film dengan TF-IDF dan cosine similarity.
- Collaborative Filtering : Menggunakan model Neural Network berbasis TensorFlow/Keras untuk mempelajari pola rating pengguna dan memberikan prediksi rating film.

### Data Understanding
**Dataset**
Dataset yang digunakan berasal dari MovieLens (ml-latest-small) , tersedia melalui Kaggle: https://www.kaggle.com/rohan4050/movie-recommendation-data

**Struktur Dataset**
Dataset terdiri dari 4 file CSV utama:

movies.csv: Informasi film (movieId, title, genres)
ratings.csv: Rating pengguna (userId, movieId, rating, timestamp)
tags.csv: Tags tambahan untuk film (userId, movieId, tag, timestamp)
links.csv: Tautan eksternal ke IMDb dan TMDB (movieId, imdbId, tmdbId)

**Analisis Dimensi Dataset**
- File movies.csv:

Jumlah baris: 9,742 film
Jumlah kolom: 3 kolom
Ukuran: ~500KB

- File ratings.csv:

Jumlah baris: 100,836 rating
Jumlah kolom: 4 kolom
Ukuran: ~2.5MB

- File tags.csv:

Jumlah baris: 3,683 tag
Jumlah kolom: 4 kolom
Ukuran: ~288KB

- File links.csv:

Jumlah baris: 9,742 link
Jumlah kolom: 3 kolom
Ukuran: ~191KB

**Deskripsi Fitur**
- movies.csv

movieId: ID unik untuk setiap film (integer)
title: Judul film beserta tahun rilis dalam format "Title (Year)" (string)
genres: Genre film dipisahkan dengan "|" (string)

- ratings.csv

userId: ID unik untuk setiap pengguna (integer)
movieId: ID film yang sama dengan movies.csv (integer)
rating: Rating yang diberikan pengguna, skala 0.5-5.0 dengan increment 0.5 (float)
timestamp: Waktu pemberian rating dalam format Unix timestamp (integer)

- tags.csv

userId: ID pengguna yang memberikan tag (integer)
movieId: ID film yang diberi tag (integer)
tag: Tag/label yang diberikan pengguna (string)
timestamp: Waktu pemberian tag dalam format Unix timestamp (integer)

- links.csv

movieId: ID film (integer)
imdbId: ID film di IMDb (integer)
tmdbId: ID film di The Movie Database (integer)

Kondisi Data Awal (Sebelum Preprocessing) Berdasarkan analisis pada code, berikut kondisi data mentah sebelum dilakukan preprocessing:
**Missing Values Analysis**
- Dataset movies.csv:

movieId: 0 missing values (100% complete)
title: 0 missing values (100% complete)
genres: 0 missing values (100% complete)

- Dataset ratings.csv:

userId: 0 missing values (100% complete)
movieId: 0 missing values (100% complete)
rating: 0 missing values (100% complete)
timestamp: 0 missing values (100% complete)

- Dataset tags.csv:

userId: 0 missing values (100% complete)
movieId: 0 missing values (100% complete)
tag: 0 missing values (100% complete)
timestamp: 0 missing values (100% complete)

- Dataset links.csv:

movieId: 0 missing values (100% complete)
imdbId: 0 missing values (100% complete)
tmdbId: Terdapat beberapa missing values untuk film yang tidak ada di TMDB

**Data Duplikat Analysis**
- Dataset movies.csv:

Total duplikat berdasarkan movieId: 0 baris
Dataset sudah bersih dari duplikasi film

- Dataset ratings.csv:

Total duplikat berdasarkan kombinasi (userId, movieId): 0 baris
Setiap pengguna hanya memberikan satu rating per film

- Dataset tags.csv:

Terdapat kemungkinan duplikat tag untuk film yang sama oleh pengguna yang sama
Tag duplikat tidak menjadi masalah karena menunjukkan konsistensi labeling

**Statistical Summary**
- Distribusi Rating (ratings.csv)

Total pengguna unik: 610 pengguna
Total film unik: 9,724 film (dari 9,742 film tersedia)
Total rating: 100,836 rating
Rata-rata rating per pengguna: ~165 rating
Range rating: 0.5 - 5.0
Rata-rata rating keseluruhan: ~3.5
Distribusi rating: Mayoritas pengguna memberikan rating 3-5, dengan rating 4.0 paling populer

- Distribusi Genre

Total genre unik: 20 genre utama
Genre terpopuler: Drama (4,361 film), Comedy (3,756 film), Thriller (1,894 film)
Kombinasi genre: Sebagian besar film memiliki 2-3 genre
Film tanpa genre: Beberapa film memiliki label "(no genres listed)"

- Distribusi Temporal

Range tahun film: 1902 - 2018
Periode paling produktif: 1990-2010 (ledakan industri Hollywood)
Film terbaru: Hingga tahun 2018
Rating timestamp: Data rating dikumpulkan antara 1996-2018

**Data Quality Assessment**
- Kualitas Data Tinggi:

Tidak ada missing values pada kolom kritis (movieId, userId, rating)
Konsistensi format data across files
ID linking antar tabel berfungsi dengan baik
Range nilai rating valid (0.5-5.0)

- Potensi Masalah:

Sparsity: Hanya ~1.7% dari kemungkinan kombinasi user-movie memiliki rating
Cold start: Beberapa film memiliki rating sangat sedikit
Data imbalance: Distribusi rating condong ke nilai tinggi (3-5)
Genre encoding: Beberapa film memiliki banyak genre yang dapat mempersulit modeling

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
- Final Training MAE: ~0.0457
- Final Validation MAE: ~0.1611
- Final Training MSE: ~0.0042
- Final Validation MSE: ~0.0443

Grafik evaluasi selama epoch menunjukkan bahwa model tidak overfitting dan memiliki performa yang stabil.

## Perbandingan Pendekatan Content-Based dan Collaborative Filtering

| Aspek               | Content-Based Filtering | Collaborative Filtering |
|---------------------|--------------------------|--------------------------|
| **Data Requirement**| Movie metadata| User ratings |
| **Cold Start**      |No problem                  | Problematic           |
| **Scalability**     | High                   | Medium                 |
| **Diversity**       | Low                   | High                   |
| **Interpretability**       | High                   | Low                   |
