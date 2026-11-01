# Anime Recommendation System — Content-Based & Collaborative Filtering

## Overview
Project ini membangun sistem rekomendasi anime menggunakan dua pendekatan machine learning yang berbeda: **Content-Based Filtering** (merekomendasikan anime berdasarkan kemiripan genre) dan **Collaborative Filtering** (merekomendasikan anime berdasarkan pola rating pengguna lain). Kedua model dibangun, dievaluasi, dan dibandingkan kelebihan-kekurangannya menggunakan dataset publik dari MyAnimeList.

## Background / Problem
Dengan puluhan ribu judul anime yang tersedia, pengguna sering kesulitan menemukan tontonan yang sesuai preferensi mereka (information overload). Project ini mencoba menjawab masalah tersebut dengan membangun dua jenis sistem rekomendasi:
- Merekomendasikan anime yang mirip secara konten (genre, tipe, jumlah episode) dengan anime yang disukai pengguna.
- Merekomendasikan anime yang mungkin disukai pengguna berdasarkan pola rating dari pengguna lain yang memiliki selera serupa.

## Objectives
- Membangun model Content-Based Filtering menggunakan representasi TF-IDF dari genre anime.
- Membangun model Collaborative Filtering berbasis neural network embedding untuk memprediksi rating pengguna terhadap anime.
- Mengevaluasi kedua model menggunakan metrik yang sesuai (Precision@k, Recall@k untuk CBF; RMSE untuk CF).
- Membandingkan kelebihan dan kekurangan masing-masing pendekatan.

## Features
- **Content-Based Filtering** — merekomendasikan Top-N anime paling mirip dengan anime referensi, berdasarkan genre (TF-IDF), tipe (one-hot encoding), dan fitur numerik (rating, members, episodes) yang dinormalisasi.
- **Collaborative Filtering** — model neural network kustom (`RecommenderNet`) yang mempelajari embedding pengguna dan anime untuk memprediksi rating, lalu menghasilkan Top-N rekomendasi personal per pengguna.
- **Evaluasi kuantitatif** — Precision@10 dan Recall@10 untuk CBF, serta RMSE untuk CF, lengkap dengan interpretasi hasil.
- **Exploratory Data Analysis (EDA)** — analisis univariat dan multivariat terhadap genre, tipe, rating, popularitas, dan segmentasi pengguna.

## Tech Stack
- **Bahasa:** Python
- **Data processing:** pandas, NumPy
- **Content-Based Filtering:** scikit-learn (`TfidfVectorizer`, `MinMaxScaler`, `cosine_similarity`)
- **Collaborative Filtering:** TensorFlow / Keras (custom `Embedding` layer, `tf.keras.Model`)
- **Visualisasi:** *(sesuai laporan menggunakan bar chart, histogram, pie chart, boxplot. library spesifik: matplotlib/seaborn/plotly)*

## How It Works / Methodology

**Dataset:** [Anime Recommendation Database 2020](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database) dari Kaggle — terdiri dari `anime.csv` (12.294 anime, metadata seperti genre/tipe/rating/members) dan `rating.csv` (7.813.737 rating dari 73.515 pengguna untuk 11.200 anime).

**1. Content-Based Filtering**
- Fitur `genre` diubah menjadi vektor TF-IDF, `type` di-one-hot-encode, dan fitur numerik (`episodes`, `members`, `rating`) dinormalisasi dengan Min-Max Scaling.
- Seluruh fitur digabung menjadi satu matriks fitur konten per anime.
- Kemiripan antar anime dihitung dengan Cosine Similarity, lalu fungsi `anime_recommendations()` mengembalikan Top-N anime paling mirip dengan anime input.

**2. Collaborative Filtering**
- Data rating dibersihkan (hapus duplikat, hapus rating tidak valid `-1`, filter pengguna & anime dengan minimal 10 interaksi) untuk mengurangi sparsity.
- User ID dan anime ID dipetakan ke indeks numerik, lalu dilatih pada model `RecommenderNet`: embedding pengguna & anime (dimensi 50) + bias, dikombinasikan lewat dot product dan diaktivasi sigmoid.
- Model dilatih dengan `BinaryCrossentropy` loss, optimizer Adam (`lr=0.0001`), `batch_size=512`, dilengkapi EarlyStopping (patience 7) dan ModelCheckpoint.
- Rekomendasi dihasilkan dengan memprediksi skor untuk seluruh anime yang belum ditonton pengguna, lalu mengambil skor tertinggi.

## Dataset
- **Sumber:** [Kaggle – Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)
- **anime.csv:** 12.294 baris, 7 kolom (`anime_id`, `name`, `genre`, `type`, `episodes`, `rating`, `members`)
- **rating.csv:** 7.813.737 baris (`user_id`, `anime_id`, `rating`), 73.515 pengguna unik, 11.200 anime unik

## Results / Output

**Content-Based Filtering** — dievaluasi dengan Precision@10 dan Recall@10 terhadap 55.115 pengguna (threshold rating ≥ 7):
- Mean Precision@10: **0.1033**
- Mean Recall@10: **0.0202**

Artinya, dari 10 rekomendasi yang diberikan, rata-rata sekitar 1 anime benar-benar relevan bagi pengguna. Angka recall yang rendah adalah hal yang wajar untuk sistem rekomendasi top-N ketika jumlah item relevan seorang pengguna jauh lebih banyak dari k=10.

**Collaborative Filtering** — dievaluasi dengan RMSE pada data validasi:
- Best validation RMSE: **0.13256** (training berhenti otomatis di epoch ke-86 via early stopping, bobot terbaik dikembalikan dari epoch ke-79)

Contoh output: model berhasil menghasilkan Top-10 rekomendasi personal untuk pengguna contoh (User 39397) berdasarkan pola rating anime yang pernah ia sukai.

## Installation
```bash
git clone https://github.com/septiisdayanna/proyek_rekomendasi_septi_isdayanna.git
cd proyek_rekomendasi_septi_isdayanna
pip install pandas numpy scikit-learn tensorflow
```

## Usage
Jalankan notebook utama untuk melihat keseluruhan alur — dari data loading, EDA, preprocessing, training kedua model, hingga evaluasi:
```bash
jupyter notebook "Proyek Rekomendasi Anime dengan Machine Learning - Septi Isdayanna.md.ipynb"
```
Atau jalankan versi script Python-nya secara langsung.

## Project Structure
```
proyek_rekomendasi_septi_isdayanna/
├── Laporan Proyek Rekomendasi Anime dengan Machine Learning - Septi Isdayanna.md   # Laporan lengkap (project overview → evaluasi)
├── Proyek Rekomendasi Anime dengan Machine Learning - Septi Isdayanna.md.ipynb     # Notebook end-to-end
└── Proyek Rekomendasi Anime dengan Machine Learning - Septi Isdayanna.md.py        # Versi script Python
```
> Untuk laporan analisis yang lebih mendalam (termasuk seluruh referensi akademik, tabel EDA lengkap, dan penjelasan kode baris per baris), baca [laporan lengkap di sini](<link ke file .md>).

## Limitations
- Content-Based Filtering hanya mengandalkan genre sebagai fitur teks utama — belum menggunakan sinopsis/deskripsi anime yang berpotensi memberi representasi konten lebih kaya.
- Precision@10 dan Recall@10 pada model CBF masih relatif rendah, menandakan ruang perbaikan pada representasi fitur atau strategi rekomendasi.
- Kedua model belum digabung menjadi pendekatan hybrid, sehingga kelemahan masing-masing (cold start pada CF, over-specialization pada CBF) belum saling menutupi.
- Model CF dan artefak hasil training (bobot terbaik `best_model_fix.weights.h5`) tidak disertakan di repo — hanya notebook yang menjalankan trainingnya.

## Future Improvements
- Menambahkan sinopsis/deskripsi anime ke pipeline CBF untuk representasi konten yang lebih kaya (bukan hanya genre).
- Menggabungkan CBF dan CF menjadi sistem rekomendasi hybrid.
- Menyimpan dan menyertakan artefak model terlatih agar reproducible tanpa perlu training ulang dari awal.
- Melakukan hyperparameter tuning pada embedding size dan learning rate model CF.

## Author
**Septi Isdayanna**
