# Proyek-Akhir-Membuat-Model-Sistem-Rekomendasi
# Laporan Proyek Machine Learning - Moch Dani Kurniawan Sugiarto

## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
- Format Referensi dapat mengacu pada penulisan sitasi [IEEE](https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf), [APA](https://www.mendeley.com/guides/apa-citation-guide/) atau secara umum seperti [di sini](https://penerbitdeepublish.com/menulis-buku-membuat-sitasi-dengan-mudah/)
- Sumber yang bisa digunakan [Scholar](https://scholar.google.com/)

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

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

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
