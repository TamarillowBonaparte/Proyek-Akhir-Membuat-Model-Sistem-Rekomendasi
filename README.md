# Proyek-Akhir-Membuat-Model-Sistem-Rekomendasi
# Laporan Proyek Machine Learning - Moch Dani Kurniawan Sugiarto

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
🔍 Dataset
Dataset yang digunakan berasal dari MovieLens (ml-latest-small) , tersedia melalui Kaggle:
https://www.kaggle.com/rohan4050/movie-recommendation-data

Dataset terdiri dari 4 file CSV:

movies.csv: Informasi film (movieId, title, genres)

ratings.csv: Rating pengguna (userId, movieId, rating)

tags.csv: Tags tambahan untuk film

links.csv: Tautan eksternal ke IMDb dan TMDB

📊 EDA Singkat

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
Penggabungan Dataset
Gabung tabel ratings dengan movies untuk mendapatkan informasi judul dan genre.
Penanganan Missing Value
Hapus baris duplikat dan nilai kosong pada kolom movieId.
Encoding ID Pengguna dan Film
Mapping userId dan movieId menjadi indeks numerik untuk model Collaborative Filtering.
Normalisasi Rating
Normalisasi nilai rating dari 0 hingga 1 untuk pelatihan model neural network.
🤔 Alasan
Preprocessing diperlukan agar data siap digunakan dalam model machine learning, termasuk encoding ID, normalisasi fitur, dan penyesuaian format input.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.
