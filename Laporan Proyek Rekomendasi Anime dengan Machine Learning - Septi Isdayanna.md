# Laporan Proyek Rekomendasi Anime - Septi Isdayanna
## Bab 1: Project Overview

### 1.1 Latar Belakang

Fenomena *booming* media digital dan platform hiburan telah mengubah cara individu mengonsumsi konten, termasuk film, musik, dan tentunya, anime. Dengan jutaan judul yang tersedia di berbagai platform *streaming* dan database seperti MyAnimeList, pengguna seringkali menghadapi masalah "kelebihan pilihan" (information overload), di mana menemukan konten yang relevan dan sesuai preferensi menjadi tantangan [1]. Ketersediaan anime yang masif, dengan beragam genre, gaya animasi, dan format (TV, Movie, OVA, dll.), membuat proses penemuan menjadi semakin kompleks bagi penggemar baru maupun veteran.

Fenomena "binge-watching" dan popularitas anime di seluruh dunia semakin mempertejelas kebutuhan akan sistem yang dapat memandu pengguna melalui lautan konten. MyAnimeList, sebagai salah satu database anime terbesar, telah menjadi hub utama bagi komunitas penggemar untuk melacak, menilai, dan mendiskusikan berbagai judul anime. Data interaksi pengguna dan metadata anime yang terkumpul di platform semacam ini menjadi sumber daya berharga untuk mengembangkan solusi penemuan konten yang lebih cerdas.

### 1.2 Urgensi Proyek

Pengembangan sistem rekomendasi anime adalah upaya krusial yang membawa manfaat signifikan bagi pengguna dan platform itu sendiri:

1.  **Peningkatan Kepuasan Pengguna:** Dengan merekomendasikan anime yang relevan dan sesuai preferensi, sistem dapat secara signifikan meningkatkan pengalaman pengguna, mengurangi waktu pencarian, dan memperkenalkan mereka pada judul-judul baru yang mungkin belum pernah mereka temukan [2]. Bagi penggemar, menemukan "permata tersembunyi" yang selaras dengan selera pribadi adalah nilai tambah yang besar.
2.  **Mendorong Konsumsi Konten:** Rekomendasi yang akurat mendorong pengguna untuk menonton lebih banyak anime, sehingga meningkatkan waktu keterlibatan (engagement time) di platform. Ini secara langsung berkorelasi dengan pertumbuhan platform dan potensi monetisasi.
3.  **Mitigasi Masalah *Cold Start* dan *Sparsity*:** Dataset rating, seperti yang disediakan oleh MyAnimeList, seringkali sangat jarang (sparse), artinya sebagian besar pengguna hanya memberikan rating untuk sebagian kecil dari keseluruhan item. Sistem rekomendasi perlu dirancang untuk mengatasi tantangan ini, termasuk *cold start problem* bagi pengguna atau item baru yang belum memiliki riwayat interaksi yang cukup [3]. Proyek ini bertujuan untuk mengeksplorasi metode yang efektif dalam mengatasi tantangan ini.
4.  **Optimalisasi Bisnis Platform:** Bagi platform *streaming* anime, rekomendasi yang personalisasi adalah kunci untuk mempertahankan pengguna, mengurangi *churn rate*, dan meningkatkan loyalitas. Sebuah sistem rekomendasi yang kuat dapat menjadi diferensiator kompetitif.

Proyek ini bertujuan untuk membangun sistem rekomendasi anime yang efektif, memanfaatkan data rating dan metadata anime dari MyAnimeList. Dengan mengimplementasikan teknik *machine learning* seperti *Collaborative Filtering* dan *Content-Based Filtering*, sistem ini diharapkan mampu memberikan rekomendasi yang personalisasi dan meningkatkan pengalaman penemuan anime bagi penggunanya.

### 1.3 Riset dan Referensi Terkait

Riset dalam bidang sistem rekomendasi telah berkembang pesat sejak munculnya konsep dasar pada tahun 1990-an. Dua pendekatan utama yang menjadi fokus proyek ini adalah:

* **Collaborative Filtering (CF):** Pendekatan ini merekomendasikan item kepada pengguna berdasarkan preferensi pengguna lain yang memiliki selera serupa (User-Based CF) atau berdasarkan item yang seringkali disukai oleh pengguna yang sama (Item-Based CF) [4]. Penelitian oleh Sarwar et al. (2001) yang memperkenalkan Item-Based Collaborative Filtering di Amazon, menunjukkan efektivitas pendekatan ini dalam skala besar [5]. Tantangan utama dalam CF adalah *data sparsity* dan *scalability* [6].

* **Content-Based Filtering (CBF):** Pendekatan ini merekomendasikan item yang serupa dengan item yang disukai pengguna di masa lalu, berdasarkan atribut-atribut item tersebut (misalnya, genre, sutradara, aktor, plot) [7]. Dalam konteks anime, fitur-fitur seperti genre, tipe (TV, Movie, OVA), dan jumlah episode menjadi sangat relevan. Vektorisasi teks seperti TF-IDF (Term Frequency-Inverse Document Frequency) sering digunakan untuk merepresentasikan fitur tekstual seperti genre, sementara *One-Hot Encoding* cocok untuk fitur kategorikal [8].

Banyak penelitian telah mencoba menggabungkan kedua pendekatan ini menjadi **Hybrid Recommender Systems** untuk mengatasi kelemahan masing-masing metode tunggal dan memberikan rekomendasi yang lebih kuat dan akurat, terutama dalam menghadapi *cold start problem* [9]. Proyek ini akan menjadi landasan untuk eksplorasi lebih lanjut menuju sistem hibrida di masa depan.

**Referensi:**

[1] P. Resnick and H. R. Varian, "Recommender Systems," *Communications of the ACM*, vol. 40, no. 3, pp. 56-59, Mar. 1997.
[2] A. K. R. Khan and L. Zhang, "A survey of recommender systems and their applications," *International Journal of Computer Science and Network Security*, vol. 9, no. 1, pp. 268-275, Jan. 2009.
[3] G. Linden, B. Smith, and J. York, "Amazon.com Recommendations: Item-to-Item Collaborative Filtering," *IEEE Internet Computing*, vol. 7, no. 1, pp. 76-80, Jan. 2003.
[4] J. B. Schafer, J. Konstan, and J. Riedl, "Recommender Systems in E-Commerce," in *Proceedings of the 1st ACM conference on Electronic commerce*, Denver, CO, USA, 1999, pp. 158-166.
[5] B. Sarwar, G. Karypis, J. Konstan, and J. Riedl, "Item-based collaborative filtering recommendation algorithms," in *Proceedings of the 10th international conference on World Wide Web*, Hong Kong, China, 2001, pp. 285-295.
[6] X. Su and T. M. Khoshgoftaar, "A Survey of Collaborative Filtering Techniques," *Advances in Artificial Intelligence*, vol. 2009, 2009.
[7] P. Lops, M. de Gemmis, and G. Semeraro, "Content-based Recommender Systems: State of the Art and Trends," in *Recommender Systems Handbook*, F. Ricci, L. Rokach, B. Shapira, and P. B. Kantor, Eds. Boston, MA: Springer US, 2011, pp. 73-105.
[8] C. D. Manning, P. Raghavan, and H. Schütze, *Introduction to Information Retrieval*. Cambridge University Press, 2008.
[9] A. Burke, "Hybrid Recommender Systems: Survey and Experiments," *User Modeling and User-Adapted Interaction*, vol. 12, no. 4, pp. 331-370, Dec. 2002.

---

## Bab 2: Business Understanding

Pada bagian ini, kita akan mengklarifikasi masalah yang ingin dipecahkan oleh proyek sistem rekomendasi anime ini, menetapkan tujuan yang jelas, dan menguraikan pendekatan solusi yang akan digunakan.

### 2.1 Problem Statements

Dalam ekosistem konsumsi anime modern, terdapat beberapa masalah fundamental yang menghambat pengalaman pengguna dan efisiensi platform:

* **Pernyataan Masalah 1: Kesulitan Penemuan Konten Relevan (Information Overload).**
    Dengan puluhan ribu judul anime yang tersedia dan terus bertambah setiap musimnya, pengguna seringkali kewalahan dalam menemukan anime baru yang benar-benar sesuai dengan preferensi pribadi mereka. Mekanisme pencarian tradisional berdasarkan kata kunci atau kategori umum seringkali tidak cukup personalisasi, menyebabkan pengguna menghabiskan banyak waktu untuk mencari dan kadang-kadang melewatkan judul-judul potensial yang sangat relevan.

* **Pernyataan Masalah 2: Tingkat Keterlibatan (Engagement) Pengguna yang Tidak Optimal.**
    Kurangnya sistem yang efektif untuk memandu pengguna menuju konten yang disukai dapat mengakibatkan tingkat *churn* (berhenti menggunakan platform) yang lebih tinggi atau penurunan durasi sesi penggunaan. Pengguna mungkin merasa frustrasi dan beralih ke platform lain atau meninggalkan kebiasaan menonton anime jika mereka kesulitan menemukan konten menarik secara konsisten.

* **Pernyataan Masalah 3: Tantangan *Cold Start* untuk Anime Baru dan Pengguna Baru.**
    Sistem rekomendasi tradisional yang hanya mengandalkan riwayat interaksi seringkali gagal memberikan rekomendasi yang memadai untuk anime baru yang belum memiliki banyak rating, atau untuk pengguna baru yang belum memiliki riwayat tontonan yang cukup. Hal ini menghambat visibilitas konten baru dan personalisasi pengalaman bagi pengguna baru.

### 2.2 Goals

Berdasarkan pernyataan masalah di atas, tujuan utama dari proyek pengembangan sistem rekomendasi anime ini adalah sebagai berikut:

* **Tujuan 1: Membangun Sistem yang Mampu Memberikan Rekomendasi Anime Personal.**
    Mengembangkan algoritma rekomendasi yang dapat secara akurat mengidentifikasi dan menyarankan anime yang sangat relevan dengan selera unik masing-masing pengguna, sehingga mengurangi masalah *information overload* dan meningkatkan efisiensi penemuan konten.

* **Tujuan 2: Meningkatkan Kepuasan dan Retensi Pengguna.**
    Dengan menyediakan rekomendasi yang presisi dan tepat waktu, sistem ini bertujuan untuk meningkatkan kepuasan pengguna terhadap platform, mendorong durasi tontonan yang lebih lama, dan pada akhirnya meningkatkan retensi pengguna.

* **Tujuan 3: Mengatasi Masalah *Cold Start* dan Keterbatasan Data Sparsity.**
    Mengeksplorasi dan mengimplementasikan pendekatan yang efektif untuk memberikan rekomendasi yang masuk akal bahkan ketika riwayat interaksi pengguna atau data tentang anime baru terbatas, serta mengelola sifat data rating yang cenderung sangat jarang.

### 2.3 Solution Approach

Untuk mencapai tujuan-tujuan yang telah ditetapkan, proyek ini akan mengadopsi dua pendekatan *machine learning* utama dalam membangun sistem rekomendasi:

#### 2.3.1 Content-Based Filtering (CBF)

Pendekatan *Content-Based Filtering* berfokus pada atribut intrinsik dari item (anime) untuk menentukan kemiripan dan merekomendasikannya.

* **Cara Kerja:** Sistem ini akan menganalisis fitur-fitur dari anime yang disukai pengguna di masa lalu (misalnya, genre, tipe, jumlah episode, rata-rata rating, popularitas). Kemudian, ia akan merekomendasikan anime lain yang memiliki fitur serupa.
* **Implementasi:**
    * **Ekstraksi Fitur:** Fitur-fitur seperti `genre`, `type`, `episodes`, `members`, dan `rating` akan diekstraksi dari dataset `anime.csv`.
    * **Vektorisasi/Normalisasi:** Kolom `genre` akan diolah menggunakan **TF-IDF Vectorization** untuk menangkap bobot relatif genre yang unik. Kolom `type` akan diubah menjadi representasi numerik menggunakan **One-Hot Encoding**. Kolom `episodes`, `members`, dan `rating` (yang numerik) akan dinormalisasi menggunakan **Min-Max Scaling** untuk memastikan skala yang konsisten antar fitur.
    * **Pembentukan Matriks Fitur:** Semua fitur yang telah diproses ini akan digabungkan menjadi satu matriks fitur konten tunggal, di mana setiap baris merepresentasikan satu anime dan kolom merepresentasikan fiturnya.
    * **Perhitungan Kemiripan:** **Cosine Similarity** akan digunakan untuk menghitung tingkat kemiripan antara setiap pasangan anime berdasarkan vektor fitur konten mereka.
* **Kelebihan:** Mampu mengatasi *cold start problem* untuk pengguna baru (dapat merekomendasikan berdasarkan profil awal pengguna) dan untuk item baru (dapat merekomendasikan berdasarkan atributnya). Rekomendasi yang dihasilkan mudah dijelaskan (misalnya, "Anda suka anime ini karena genre-nya sama").
* **Kekurangan:** Mungkin terbatas pada penemuan item yang "mirip" dan kurang mampu merekomendasikan item di luar preferensi historis pengguna (kurang variasi).

#### 2.3.2 Collaborative Filtering (CF)

Pendekatan *Collaborative Filtering* berfokus pada pola interaksi pengguna (rating) terhadap anime untuk mengidentifikasi preferensi tersembunyi (latent preference). Dalam proyek ini, pendekatan yang digunakan adalah **Model-Based Collaborative Filtering** menggunakan **Neural Matrix Factorization**.

* **Cara Kerja:** Setiap pengguna dan anime direpresentasikan dalam bentuk **vektor embedding berdimensi tetap**, yang dilatih untuk memprediksi rating secara akurat berdasarkan pola historis. Semakin mirip vektor laten antara pengguna dan item, semakin tinggi prediksi ratingnya.
* **Implementasi:**
  * Dataset rating diubah menjadi pasangan `(user_id, anime_id)` sebagai input, dan `rating` sebagai target.
  * Masing-masing ID diubah menjadi indeks numerik dan dipetakan ke layer **embedding**.
  * Model neural network mempelajari **interaksi antar embedding** melalui operasi dot product, ditambah bias pengguna, dan item(anime) untuk menghasilkan prediksi.
  * Rating diprediksi, dinormalisasi ke \[0,1] selama training, dan kemudian dinormalisasi ulang ke skala asli (1–10) untuk interpretasi hasil.
  * Model dievaluasi menggunakan **Root Mean Squared Error (RMSE)**
* **Kelebihan:** Dapat menangkap preferensi kompleks pengguna secara laten, lebih fleksibel dan akurat dibanding pendekatan memory-based. Dan juga mampu menangani skenario data sparsity dengan performa stabil.
* **Kekurangan:** Membutuhkan proses training yang lebih kompleks dan sumber daya komputasi lebih besar dan masih mengalami kesulitan dalam menghadapi cold start (khususnya untuk pengguna atau item baru yang belum ada data).

---

## Bab 3: Data Understanding

Bagian ini menyajikan pemahaman mendalam mengenai data yang digunakan dalam proyek sistem rekomendasi anime ini, meliputi sumber, struktur, variabel, dan analisis eksplorasi awal untuk mendapatkan *insight*.

Dataset yang digunakan dalam proyek ini adalah **Anime Recommendation Database 2020**, yang tersedia dan dapat diunduh dari Kaggle melalui tautan berikut: [https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database). Dataset ini merupakan kumpulan data interaksi pengguna dan metadata anime yang berasal dari MyAnimeList.net, salah satu basis data anime terbesar di dunia.

Secara keseluruhan, dataset ini menyediakan kombinasi data konten (metadata anime) dan data interaksi (rating pengguna), yang esensial untuk membangun sistem rekomendasi menggunakan pendekatan Content-Based Filtering dan Collaborative Filtering.

### 3.1 Jumlah dan Kondisi Data Awal

##### Dataset `anime.csv` (kondisi awal):
* **Jumlah Entri:** 12.294 baris  
* **Jumlah Kolom:** 7 kolom  
* **Duplikasi:** Tidak ada duplikasi  
* **Data Hilang:**  
  - genre: 62 nilai hilang  
  - type: 25 nilai hilang  
  - rating: 230 nilai hilang  
  - episodes: Perlu penanganan nilai "Unknown" sebagai non-numerik

##### Dataset `rating.csv` (kondisi awal):
* **Jumlah Entri:** 7.813.737 entri  
* **Jumlah Pengguna Unik:** 73.515  
* **Jumlah Anime Unik:** 11.200  
* **Data Hilang:** Tidak ada  
* **Duplikasi:** Terdapat 1 baris duplikat  
* **Rating Tidak Standar:** Nilai -1 terdeteksi (di luar skala 1–10; kemungkinan menunjukkan status tontonan tanpa rating eksplisit)  
* **Integritas Data:** Terdapat 3 anime_id yang ada di rating.csv namun tidak ditemukan di anime.csv, sehingga total entri setelah penggabungan menjadi 12.297

### 3.2 Deskripsi Fitur

Berikut adalah uraian variabel atau fitur yang terdapat pada kedua dataset:

#### Dataset `anime.csv`

| Nama Fitur | Deskripsi | Tipe |
|------------|-----------|------|
| `anime_id` | ID unik untuk setiap anime. Berfungsi sebagai kunci utama. | Integer |
| `name`     | Judul lengkap anime. | String |
| `genre`    | Daftar genre yang terkait dengan anime, dipisahkan oleh koma (misalnya, "Action, Comedy, Fantasy"). | String/Kategorikal Multi-label |
| `type`     | Jenis format anime (misalnya, "TV", "Movie", "OVA", "Special", "ONA", "Music"). | Kategorikal String |
| `episodes` | Jumlah episode dari seri anime. Dapat berupa angka atau "Unknown". | String |
| `rating`   | Rata-rata skor rating global anime dari MyAnimeList (skala 1.0-10.0). | Float |
| `members`  | Jumlah anggota komunitas MyAnimeList yang telah menambahkan anime ke daftar mereka. | Integer |

#### Dataset `rating.csv`

| Nama Fitur | Deskripsi | Tipe |
|------------|-----------|------|
| `user_id`  | ID unik untuk setiap pengguna. | Integer |
| `anime_id` | ID unik anime yang dirating oleh pengguna. Kunci asing ke dataset `anime.csv`. | Integer |
| `rating`   | Rating yang diberikan oleh pengguna (skala 1-10). Nilai -1 menunjukkan bahwa pengguna telah menonton anime tanpa memberikan rating eksplisit. | Integer |

### 3.3 EDA Kritis

Eksplorasi Data Analisis (EDA) kritis dilakukan untuk mendapatkan pemahaman mendalam tentang distribusi, pola, dan karakteristik data yang relevan untuk pembangunan sistem rekomendasi. Visualisasi yang digunakan mencakup bar chart, histogram, pie chart, boxplot (untuk analisis univariat), serta berbagai kombinasi visualisasi untuk analisis multivariat.

**Temuan Utama hasil `Univariate Analisis`:**

| **Fitur**                   | **Insight**                                                                                                                                                                             |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Genre Anime**             | "Comedy" adalah genre yang paling banyak muncul (~4.500 kemunculan). Secara total terdapat 43 genre dengan distribusi yang sangat tidak merata, sehingga diperlukan pembobotan fitur (misalnya TF-IDF). |
| **Tipe Anime**              | Tipe "TV" mendominasi (~3.700 entri), diikuti oleh "OVA" (~3.300) dan "Movie" (~2.300). Format lain seperti "ONA", "Special", dan "Music" memiliki jumlah entri yang jauh lebih rendah. |
| **Kategori Episode**        | Mayoritas anime dikategorikan sebagai "Short" (>8.000 entri). Dimana anime tersebut memiliki kurang dari 10 episode. Adanya kategori "Unknown" menandakan perlunya penanganan khusus pada data episode.                                      |
| **Skor Rating Anime**       | Distribusi skor rating relatif normal dengan puncak sekitar 7.0, mayoritas berada di kisaran 6.0–7.5, yang mengindikasikan bahwa komunitas menilai kebanyakan anime dengan baik.      |
| **Popularitas (Members)**   | Kebanyakan anime memiliki jumlah anggota berada di kategori "Very Small" atau "Small", menunjukkan distribusi popularitas yang sangat miring ke kanan.                              |
| **Rating Pengguna**         | Pada dataset rating, terdapat dominasi rating -1 (~1.4 juta entri) yang menandakan "ditonton tanpa skor". Untuk skor 1–10, pengguna cenderung memberikan nilai tinggi.            |
| **Segmentasi Pengguna**     | Mayoritas pengguna adalah Light User (52.6%), dengan Medium User (35.0%) dan Power User (12.4%) sebagai minoritas, menyoroti sifat data rating yang sparse.                      |
| **Partisipasi Rating**      | Sekitar 94.7% pengguna memberikan setidaknya satu rating numerik, menandakan partisipasi yang aktif dalam sistem penilaian.                                                         

**Temuan Utama hasil `Multivariate Analisis`:**

| **Analisis**                       | **Insight**                                                                                                                                                   |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Top 10 Anime**               | "Death Note" memimpin mendekati 35k rating, diikuti oleh judul populer seperti "Sword Art Online" dan "Shingeki no Kyojin".                                      |
| **Popularitas vs Rating**       | Anime dengan banyak ulasan cenderung memiliki rating rata-rata tinggi; entri dengan sedikit ulasan menunjukkan variasi yang lebih lebar.                       |
| **Rating Berdasarkan Tipe**     | Tipe "Movie" dan "TV" memiliki median tinggi (8–9); tipe "OVA" dan "ONA" lebih rendah; "Music" paling rendah.                                                   |
| **Rating Berdasarkan Genre**    | Genre mainstream (Drama, Romance, School, Supernatural) menunjukkan rating median stabil (7.5–8.5); genre polarisasi memperlihatkan variasi ekstrim.         |
| **10 User Paling Aktif**        | Sebagian besar pengguna aktif memberikan rating di atas rata-rata (6–8), meski terdapat beberapa pola ekstrem.                                                 |
| **Rating Berdasarkan Members**  | Median rating meningkat seiring dengan jumlah anggota; anime dengan anggota kecil menunjukkan variasi yang lebih besar.                                         |
| **Rating Berdasarkan Episode**  | Anime berjenis "Long" dan "Standard" memiliki median lebih tinggi, sedangkan kategori "Short" lebih rendah; rating untuk "Unknown" sangat bervariasi.       |

---

## 4. Data Preparation

Tahap ini bertujuan untuk membersihkan, memformat, dan mengoptimalkan data agar sistem rekomendasi dapat bekerja dengan akurasi tinggi. Proses ini melibatkan penanganan data yang hilang, transformasi fitur, serta normalisasi informasi sehingga model dapat memahami pola dan preferensi pengguna secara efektif. Mengingat perbedaan pendekatan antara **Content-Based Filtering (CBF)** dan **Collaborative Filtering (CF)**, setiap metode memiliki teknik persiapan data yang berbeda untuk memastikan performa terbaik dalam menghasilkan rekomendasi yang relevan.

### 4.1 Dataset `anime` (untuk Content-Based Filtering)

| No | Tahapan                           | Teknik/Metode                                      | Tools/Library                                 | Parameter/Keterangan                                                       | Alasan                                                                |
| -- | --------------------------------- | -------------------------------------------------- | --------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| 1  | **Handling Missing Values**       | Hapus baris dengan nilai `NaN`                     | `pandas.dropna()`                             | Kolom penting seperti `genre`, `type`, `rating`                            | Menjaga integritas fitur konten dan mencegah bias akibat data hilang. |
| 2  | **Handling Invalid Values**       | Ubah `"Unknown"` ke `NaN`, konversi numerik, hapus | `pandas.replace()`, `astype(int)`, `dropna()` | Kolom `episodes` dibersihkan dan dikonversi ke integer                     | Konsistensi tipe data numerik untuk analisis dan model.               |
| 3  | **Normalisasi Fitur Numerik**     | Min-Max Scaling                                    | `MinMaxScaler` dari `sklearn.preprocessing`   | Kolom `episodes`, `members`, dan `rating` dinormalisasi ke rentang \[0, 1] | Menyamakan skala fitur agar tidak mendominasi satu sama lain.         |
| 4  | **Vektorisasi Fitur Kategorikal** | One-Hot Encoding & TF-IDF                          | `get_dummies()`, `TfidfVectorizer`            | `type`: One-hot; `genre`: TF-IDF setelah tokenisasi                        | Mengubah data kategorikal dan teks menjadi representasi numerik.      |
| 5  | **Penggabungan Fitur**            | Gabungkan semua fitur menjadi satu vektor          | `scipy.sparse.hstack()`                       | Digabung: TF-IDF `genre` + One-hot `type` + fitur numerik                  | Membangun vektor fitur komprehensif untuk setiap item anime.          |

### 4.2 Dataset `rating` (untuk Collaborative Filtering)

| No | Tahapan                                 | Teknik/Metode                                                              | Tools/Library                     | Parameter/Keterangan                                                                                                          | Alasan                                                                                                      |
| -- | --------------------------------------- | -------------------------------------------------------------------------- | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| 1  | **Handling Duplikat Data**              | Hapus baris duplikat                                                       | `pandas.drop_duplicates()`        | Menghapus semua baris identik                                                                                                 | Mencegah bias karena pengulangan interaksi.                                                                 |
| 2  | **Handling Invalid Rating (-1)**        | Hapus rating = -1                                                          | Boolean filtering (`pandas`)      | Rating -1 dianggap tidak valid ("ditonton tapi tidak diberi skor")                                                            | Model CF memerlukan rating eksplisit untuk pembelajaran yang akurat.                                        |
| 3  | **Filtering User & Anime**              | Hanya pertahankan user dan anime dengan jumlah interaksi cukup             | `value_counts()`, `isin()`        | User dengan ≥10 rating, dan Anime dengan ≥10 rating (pasca-filter user)                                                     | Mengurangi sparsity dan meningkatkan keandalan data.                                                        |
| 4  | **Pemetaan ID & Persiapan Dasar**       | Mapping ID ke indeks integer, penghitungan jumlah unik, konversi tipe data | `unique()`, `map()`, `astype()`   | Pemetaan ID ke indeks 0-N, `rating` dikonversi ke `float32`, hitung `min_rating`, `max_rating`, dan `rating_range`            | Membuat input numerik yang efisien untuk embedding, serta mempersiapkan parameter untuk normalisasi target. |
| 5  | **Data Splitting & Normalisasi Target** | Pengacakan, pemisahan fitur-target, normalisasi rating, dan pembagian data | `sample()`, slicing NumPy, lambda | Data diacak (`random_state=42`), `X = [user, anime]` `y = rating`, Split: 80% train, 20% validation | Standar preprocessing sebelum training model dan penting untuk generalisasi serta evaluasi performa model.  |

---

## Bab 5: Modeling and Result

Bab ini berfokus pada pengembangan dan evaluasi sistem rekomendasi anime. Dua pendekatan utama akan diimplementasikan dan dianalisis: **Collaborative Filtering (CF)** dan **Content-Based Filtering (CBF)**. Setiap pendekatan akan dijelaskan mulai dari arsitektur model, penggunaan fitur, cara kerja algoritma, hingga parameter yang digunakan. Hasil dari kedua model akan disajikan dalam bentuk top-N rekomendasi, diikuti dengan analisis kelebihan dan kekurangan masing-masing pendekatan.

### 5.1 Gambaran Umum Sistem Rekomendasi
Sebelum masuk ke detail masing-masing model, bagian ini memberikan gambaran umum tentang alur kerja sistem rekomendasi yang dibangun. Ini mencakup bagaimana data yang telah diproses pada tahap 'Data Preparation' (termasuk fitur hasil TF-IDF untuk CBF dan data rating pengguna yang telah di-encode untuk CF) akan dimanfaatkan oleh model-model yang akan dijelaskan.

### 5.2 Pendekatan 1: Content-Based Filtering (CBF)

Pendekatan Content-Based Filtering (CBF) merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu atau item referensi tertentu. Kemiripan diukur berdasarkan fitur-fitur konten dari item tersebut.

#### 5.2.1 Arsitektur Model dan Cara Kerja Algoritma

Model CBF yang dibangun bekerja dengan merepresentasikan setiap anime sebagai sebuah vektor fitur berdasarkan kontennya. Dalam implementasi ini, fitur konten utama yang dipertimbangkan adalah informasi tekstual seperti genre atau deskripsi anime, yang telah diolah menjadi representasi numerik menggunakan TF-IDF pada tahap 'Data Preparation'.

Cara kerja algoritma ini adalah dengan menghitung kemiripan antar anime menggunakan metrik **Cosine Similarity**. 

**Formula:**
$$\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \times \|B\|}$$
Di mana $A$ dan $B$ adalah vektor fitur dari dua anime.

Matriks kemiripan kosinus ($$\text{cosine\_sim}$$)  dihasilkan, di mana setiap elemen ($$C_{ij}$$) dalam matriks ini merepresentasikan skor kemiripan antara anime $$i$$ dan anime $$j$$. Semakin tinggi skornya (mendekati 1), semakin mirip kedua anime tersebut berdasarkan kontennya. Ketika pengguna memberikan input berupa nama anime, sistem akan mencari anime tersebut dalam matriks kemiripan, kemudian mengambil daftar anime lain yang memiliki skor kemiripan tertinggi dengan anime input.

#### 5.2.2 Penggunaan Fitur (Hasil TF-IDF)

Fitur utama yang digunakan oleh model CBF ini adalah vektor TF-IDF yang telah dihasilkan pada tahap 'Data Preparation'. Variabel `all_content_features` yang digunakan dalam perhitungan kemiripan merupakan matriks hasil transformasi TF-IDF dari data tekstual anime (misalnya, kolom 'genre' atau gabungan beberapa kolom teks). Setiap baris dalam `all_content_features` merepresentasikan satu anime, dan setiap kolom merepresentasikan bobot TF-IDF dari sebuah term (kata) dalam keseluruhan korpus data teks. Vektor-vektor inilah yang menjadi dasar bagi algoritma **Cosine Similarity** untuk mengukur seberapa mirip konten satu anime dengan anime lainnya.

#### 5.2.3 Implementasi dan Parameter Model

Implementasi model CBF melibatkan dua langkah utama: perhitungan matriks kemiripan dan fungsi untuk menghasilkan rekomendasi.

* **Perhitungan Matriks Kemiripan**:
    Matriks kemiripan kosinus dihitung menggunakan fungsi `cosine_similarity` dari library `sklearn.metrics.pairwise`. Hasilnya kemudian diubah menjadi DataFrame Pandas (`cosine_sim_df`) untuk kemudahan akses, dengan nama anime sebagai indeks dan kolom.
    ```python
    from sklearn.metrics.pairwise import cosine_similarity
    import pandas as pd

    # all_content_features diasumsikan adalah matriks TF-IDF dari tahap Data Preparation
    # cosine_sim = cosine_similarity(all_content_features)
    
    # anime_cleaned adalah DataFrame yang berisi nama anime dan data lainnya
    # cosine_sim_df = pd.DataFrame(cosine_sim, index=anime_cleaned.name, columns=anime_cleaned.name)
    ```
    Parameter utama di sini adalah `all_content_features` itu sendiri, yang kualitasnya bergantung pada proses TF-IDF di tahap pra-pemrosesan.

* **Fungsi Rekomendasi**:
    Fungsi `anime_recommendations` dirancang untuk mengambil nama anime sebagai input dan menghasilkan daftar anime yang paling mirip.
    ```python
    def anime_recommendations(anime_name, similarity_data, anime_data, k=10):
        # ... (isi fungsi seperti yang Anda berikan) ...
        # Ambil skor kemiripan untuk anime yang diberikan
        similarity_scores_series = similarity_data.loc[anime_name]

        # Urutkan anime berdasarkan skor kemiripan (descending)
        sorted_series = similarity_scores_series.sort_values(ascending=False)
        
        # Ambil k+1 teratas dan buang yang pertama (anime itu sendiri)
        if len(sorted_series) > 1:
            top_k_others_indices = sorted_series.index[1:k+1]
            # top_k_others_scores = sorted_series.values[1:k+1] # Not strictly needed if only indices are used for lookup
        # ... (sisa fungsi) ...
        # return recommended_anime_final.head(k) 
    ```
    Parameter-parameter utama dalam fungsi ini adalah:
    * `anime_name` (str): Nama anime referensi.
    * `similarity_data` (pd.DataFrame): `cosine_sim_df` yang telah dihitung sebelumnya.
    * `anime_data` (pd.DataFrame): DataFrame `anime_cleaned` yang berisi detail anime.
    * `k` (int): Jumlah rekomendasi yang diinginkan, defaultnya adalah 10.

#### 5.2.4 Hasil Rekomendasi Top-N

Model CBF diuji dengan mencari rekomendasi untuk anime 'Kimi no Na wa.' dengan parameter `k=10` (meminta 10 rekomendasi teratas). Hasilnya adalah sebagai berikut:

--- Rekomendasi Langsung untuk 'Kimi no Na wa.' ---
| name                                                    | Genre                                           | Type  | Rating (Source) | Members | Episodes | Similarity Score |
| :------------------------------------------------------ | :---------------------------------------------- | :---- | :-------------- | :------ | :------- | :--------------- |
| Aura: Maryuuin Kouga Saigo no Tatakai                   | Comedy, Drama, Romance, School, Supernatural    | Movie | 7.67            | 22599   | 1        | 0.972428         |
| Harmonie                                                | Drama, School, Supernatural                   | Movie | 7.52            | 29029   | 1        | 0.940894         |
| Kokoro ga Sakebitagatterunda.                           | Drama, Romance, School                          | Movie | 8.32            | 59652   | 1        | 0.935994         |
| Air Movie                                               | Drama, Romance, Supernatural                    | Movie | 7.39            | 44179   | 1        | 0.933315         |
| Clannad Movie                                           | Drama, Fantasy, Romance, School               | Movie | 7.35            | 99506   | 1        | 0.896420         |
| Hotarubi no Mori e                                     | Drama, Romance, Shoujo, Supernatural          | Movie | 8.61            | 197439  | 1        | 0.887718         |
| Zutto Mae kara Suki deshita.: Kokuhaku Jikkou Iinkai    | Romance, School                                 | Movie | 7.47            | 35058   | 1        | 0.881569         |
| Momo e no Tegami                                        | Drama, Supernatural                           | Movie | 7.78            | 30519   | 1        | 0.879606         |
| Takanashi Rikka Kai: Chuunibyou demo Koi ga Shitai! Movie | Comedy, Drama, Romance, School, Slice of Life | Movie | 7.37            | 34272   | 1        | 0.867437         |
| Suzumiya Haruhi no Shoushitsu                           | Comedy, Mystery, Romance, School, Sci-Fi, Supe... | Movie | 8.81            | 240297  | 1        | 0.864291         |

#### 5.2.5 Penjelasan Kode

Berikut adalah penjelasan untuk beberapa bagian penting dari kode yang digunakan:

* `cosine_sim = cosine_similarity(all_content_features)`: Baris ini adalah inti dari perhitungan kemiripan. Fungsi `cosine_similarity` menerima matriks fitur TF-IDF (`all_content_features`) dan menghitung kemiripan kosinus antara setiap pasang anime (baris) dalam matriks tersebut. Hasilnya adalah sebuah matriks NumPy di mana nilai pada posisi `(i, j)` adalah skor kemiripan antara anime `i` dan anime `j`.
* `cosine_sim_df = pd.DataFrame(cosine_sim, index=anime_cleaned.name, columns=anime_cleaned.name)`: Matriks NumPy hasil `cosine_similarity` diubah menjadi DataFrame Pandas. Penggunaan `index=anime_cleaned.name` dan `columns=anime_cleaned.name` memungkinkan kita untuk dengan mudah mencari skor kemiripan menggunakan nama anime, misalnya `cosine_sim_df.loc['Kimi no Na wa.']`.
* Dalam fungsi `anime_recommendations`:
    * `similarity_scores_series = similarity_data.loc[anime_name]`: Mengambil satu baris dari `cosine_sim_df` yang sesuai dengan `anime_name`. Baris ini berisi skor kemiripan `anime_name` dengan semua anime lainnya.
    * `sorted_series = similarity_scores_series.sort_values(ascending=False)`: Mengurutkan skor kemiripan dari yang tertinggi ke terendah.
    * `top_k_others_indices = sorted_series.index[1:k+1]`: Mengambil `k` nama anime teratas setelah pengurutan. Indeks `[1:k+1]` digunakan karena `sorted_series.index[0]` adalah anime input itu sendiri (yang memiliki kemiripan 1.0 dengan dirinya sendiri), sehingga kita mengabaikannya dan mengambil `k` anime berikutnya.
    * Bagian selanjutnya dari fungsi bertanggung jawab untuk mengambil detail anime yang direkomendasikan dari `anime_data` (yaitu `anime_cleaned`), menambahkan skor kemiripan, memilih kolom yang relevan, dan memformat output.

### 5.3 Pendekatan 2: Collaborative Filtering (CF) dengan Neural Network

Pendekatan Collaborative Filtering (CF) yang digunakan adalah model berbasis Neural Network menggunakan TensorFlow/Keras. Model ini mempelajari representasi laten (embedding) dari pengguna dan anime untuk memprediksi rating yang mungkin diberikan pengguna terhadap anime. Ini termasuk dalam kategori model-based CF, yang seringkali memiliki kemiripan konseptual dengan teknik faktorisasi matriks.

#### 5.3.1 Arsitektur Model dan Cara Kerja Algoritma

Arsitektur model didefinisikan dalam kelas `RecommenderNet` yang mewarisi dari `tf.keras.Model`.

* **Inisialisasi (`__init__`)**:
    Model menerima jumlah pengguna unik (`num_users`), jumlah anime unik (`num_anime`), dan ukuran embedding (`embedding_size`) sebagai parameter.
    Di dalamnya, terdapat beberapa layer Embedding dari Keras:
    1.  `self.user_embedding`: Layer untuk menghasilkan vektor embedding bagi setiap pengguna.
    2.  `self.user_bias`: Layer untuk mempelajari bias spesifik per pengguna (seberapa cenderung seorang pengguna memberi rating tinggi/rendah secara umum).
    3.  `self.anime_embedding`: Layer untuk menghasilkan vektor embedding bagi setiap anime.
    4.  `self.anime_bias`: Layer untuk mempelajari bias spesifik per anime (seberapa cenderung sebuah anime mendapatkan rating tinggi/rendah secara umum).
    Inisialisasi bobot embedding menggunakan `'he_normal'` dan regularisasi L2 diterapkan untuk mencegah overfitting.

* **Proses Prediksi (`call`)**:
    Ketika model dipanggil dengan input berupa pasangan indeks pengguna dan indeks anime:
    1.  Vektor embedding untuk pengguna dan anime diambil dari layer masing-masing.
    2.  Bias untuk pengguna dan anime juga diambil.
    3.  Interaksi antara pengguna dan anime dihitung menggunakan *dot product* antara vektor embedding pengguna dan vektor embedding anime ($$\text{dot\_user\_anime} = \text{user\_vector} \cdot \text{anime\_vector}$$).    
    4.  Prediksi awal ($$x$$) dihitung sebagai jumlah dari hasil dot product, bias pengguna, dan bias anime: $$x = \text\{dot\_user_anime\} + \text{user\_bias} + \text{anime\_bias}$$.
    5.  Hasil prediksi akhir diperoleh dengan melewatkan $$x$$ melalui fungsi aktivasi sigmoid ($$\sigma(x)$$). Ini menghasilkan output antara 0 dan 1, yang dapat diinterpretasikan sebagai probabilitas kesukaan atau rating yang telah dinormalisasi.

#### 5.3.2 Penggunaan Fitur

Fitur utama yang digunakan oleh model CF ini adalah:

* **User ID**: Identifikasi unik untuk setiap pengguna.
* **Anime ID**: Identifikasi unik untuk setiap anime.

Sebelum dimasukkan ke model, User ID dan Anime ID dipetakan ke dalam bentuk indeks numerik integer (melalui `user_to_index` dan `anime_to_index` yang dibuat pada tahap persiapan data). Indeks inilah yang digunakan untuk mengambil vektor embedding yang sesuai dari layer embedding model.
Data pelatihan (`x_train`) terdiri dari pasangan `(user_index, anime_index)`, dan target variabel (`y_train`) adalah rating yang diberikan oleh pengguna tersebut ke anime tersebut. Mengingat penggunaan `BinaryCrossentropy` sebagai fungsi loss dan aktivasi sigmoid, nilai rating pada `y_train` diasumsikan telah dinormalisasi ke rentang [0,1] atau dikonversi menjadi representasi biner (misalnya, disukai/tidak disukai).

#### 5.3.3 Implementasi dan Parameter Model

Berikut adalah detail implementasi dan parameter kunci yang digunakan:

* **Definisi Model**:
    ```python
    import tensorflow as tf
    from tensorflow import keras
    from tensorflow.keras import layers

    class RecommenderNet(tf.keras.Model):
        def __init__(self, num_users, num_anime, embedding_size, **kwargs):
            super(RecommenderNet, self).__init__(**kwargs)
            self.num_users = num_users
            self.num_anime = num_anime
            self.embedding_size = embedding_size
            self.user_embedding = layers.Embedding(
                num_users,
                embedding_size,
                embeddings_initializer = 'he_normal',
                embeddings_regularizer = keras.regularizers.l2(1e-6)
            )
            self.user_bias = layers.Embedding(num_users, 1)
            self.anime_embedding = layers.Embedding(
                num_anime,
                embedding_size,
                embeddings_initializer = 'he_normal',
                embeddings_regularizer = keras.regularizers.l2(1e-6)
            )
            self.anime_bias = layers.Embedding(num_anime, 1)

        def call(self, inputs):
            user_vector = self.user_embedding(inputs[:,0])
            user_bias = self.user_bias(inputs[:, 0])
            anime_vector = self.anime_embedding(inputs[:, 1])
            anime_bias = self.anime_bias(inputs[:, 1])

            dot_user_anime = tf.tensordot(user_vector, anime_vector, 2)
            x = dot_user_anime + user_bias + anime_bias
            return tf.nn.sigmoid(x)

    # Inisialisasi model dengan num_users, num_anime dari data, dan embedding_size=50
    # model = RecommenderNet(num_users, num_anime, 50)
    ```
    Parameter `embedding_size` diatur ke **50**, yang menentukan dimensi dari ruang laten tempat pengguna dan anime direpresentasikan.

* **Kompilasi Model**:
    ```python
    # model.compile(
    #     loss = tf.keras.losses.BinaryCrossentropy(),
    #     optimizer = keras.optimizers.Adam(learning_rate=0.0001),
    #     metrics=[tf.keras.metrics.RootMeanSquaredError()]
    # )
    ```
    * **Loss Function**: `tf.keras.losses.BinaryCrossentropy()` dipilih, yang mengindikasikan bahwa target rating (variabel `y`) telah dinormalisasi ke rentang [0,1] atau merupakan target biner.
    * **Optimizer**: `keras.optimizers.Adam` dengan `learning_rate=0.0001`.
    * **Metrics**: `tf.keras.metrics.RootMeanSquaredError()` digunakan untuk memantau performa model. Penggunaan RMSE bersama dengan BinaryCrossentropy menyarankan bahwa meskipun model dilatih untuk output [0,1], evaluasi masih ingin melihat seberapa dekat prediksi (setelah mungkin di-denormalisasi atau jika metrik diterapkan pada output sebelum sigmoid) dengan skala rating asli.

* **Callbacks**:
    ```python
    # callbacks = [
    #     keras.callbacks.EarlyStopping(
    #         monitor='val_root_mean_squared_error',
    #         patience=7,
    #         restore_best_weights=True,
    #         verbose=1,
    #         mode='min'
    #     ),
    #     keras.callbacks.ModelCheckpoint(
    #         'best_model_fix.weights.h5',
    #         monitor='val_root_mean_squared_error',
    #         save_best_only=True,
    #         save_weights_only=True,
    #         verbose=1,
    #         mode='min'
    #     )
    # ]
    ```
    * `EarlyStopping`: Menghentikan training jika `val_root_mean_squared_error` tidak membaik selama 7 epoch, dan mengembalikan bobot terbaik.
    * `ModelCheckpoint`: Menyimpan bobot model terbaik (`best_model_fix.weights.h5`) berdasarkan `val_root_mean_squared_error` terendah pada data validasi.

* **Pelatihan Model**:
    ```python
    # history = model.fit(
    #     x = x_train,
    #     y = y_train,
    #     batch_size = 512,
    #     epochs = 100,
    #     callbacks = callbacks,
    #     validation_data = (x_val, y_val)
    # )
    ```
    Model dilatih dengan `batch_size` 512 selama maksimal 100 `epochs`, menggunakan data `x_train` dan `y_train`, serta divalidasi dengan `x_val` dan `y_val`.

#### 5.3.4 Hasil Rekomendasi Top-N

Untuk menghasilkan rekomendasi bagi pengguna tertentu (dalam contoh ini, User ID 39397), langkah-langkah berikut dilakukan:
1.  Identifikasi semua anime yang telah ditonton oleh pengguna tersebut.
2.  Buat daftar anime yang belum ditonton oleh pengguna tersebut dari himpunan anime yang ada dalam data.
3.  Siapkan array input untuk model prediksi, yang terdiri dari ID pengguna (yang di-encode) dan daftar ID anime yang belum ditonton (juga di-encode).
4.  Gunakan `model.predict()` untuk mendapatkan skor prediksi (antara 0 dan 1) untuk setiap anime yang belum ditonton.
5.  Urutkan anime berdasarkan skor prediksi tertinggi dan ambil 10 teratas.

Berikut adalah hasil rekomendasi untuk **User 39397**:
```
Daftar rekomendasi untuk: User 39397
=============================================

anime dengan rating paling tinggi dari user
------------------------------------------------------------
Death Note : Mystery, Police, Psychological, Supernatural, Thriller
Durarara!! : Action, Mystery, Supernatural
Break Blade 2: Ketsubetsu no Michi : Action, Fantasy, Mecha, Military, Shounen
Black Cat : Adventure, Comedy, Sci-Fi, Shounen, Super Power
Uragiri wa Boku no Namae wo Shitteiru : Adventure, Drama, Fantasy, Shoujo, Shounen Ai

------------------------------------------------------------
Top 10 Rekomendasi anime untuk Anda
------------------------------------------------------------
1. Ashita no Nadja
    genre        : Adventure, Drama, Historical, Romance, Shoujo
    type         : TV
    rating       : 7.68
    members      : 13742
    episodes     : 50
2. Konjiki no Gash Bell!!
    genre        : Adventure, Comedy, Magic, Shounen, Supernatural
    type         : TV
    rating       : 7.66
    members      : 51403
    episodes     : 150
3. Bokura ga Ita
    genre        : Drama, Romance, Shoujo, Slice of Life
    type         : TV
    rating       : 7.54
    members      : 125051
    episodes     : 26
4. Kyougoku Natsuhiko: Kousetsu Hyaku Monogatari
    genre        : Fantasy, Historical, Horror, Mystery, Psychological, Supernatural
    type         : TV
    rating       : 7.27
    members      : 20859
    episodes     : 13
5. Doubutsu no Mori
    genre        : Kids, Slice of Life
    type         : Movie
    rating       : 7.15
    members      : 12051
    episodes     : 1
6. Magical Canan
    genre        : Drama, Fantasy, Magic, Supernatural
    type         : TV
    rating       : 6.42
    members      : 2942
    episodes     : 13
7. Himiko-den
    genre        : Adventure, Drama, Fantasy, Supernatural
    type         : TV
    rating       : 6.4
    members      : 3731
    episodes     : 12
8. Kikou Sennyo Rouran
    genre        : Action, Fantasy, Mecha
    type         : TV
    rating       : 6.08
    members      : 1049
    episodes     : 28
9. Dimension Loop
    genre        : Sci-Fi
    type         : OVA
    rating       : 5.79
    members      : 1805
    episodes     : 1
10. Flashback Game
    genre        : Hentai
    type         : OVA
    rating       : 5.53
    members      : 1195
    episodes     : 3
=============================================
```
Perlu dicatat bahwa kolom 'rating' yang ditampilkan pada hasil rekomendasi di atas adalah rata-rata rating asli dari dataset anime, bukan skor rating yang diprediksi oleh model untuk pengguna tersebut. Model menghasilkan skor prediksi antara 0 dan 1 yang digunakan untuk *ranking*, tetapi output akhir menampilkan rating global anime.

#### 5.3.5 Penjelasan Kode

* **Kelas `RecommenderNet`**:
    * `layers.Embedding(...)`: Membuat tabel lookup di mana setiap baris adalah vektor representasi (embedding) untuk satu pengguna atau satu anime. Ukuran `embedding_size=50` berarti setiap pengguna dan anime direpresentasikan oleh vektor 50-dimensi.
    * `embeddings_initializer='he_normal'`: Metode inisialisasi bobot yang cocok untuk layer-layer dengan aktivasi ReLU atau variasinya, meskipun di sini output akhirnya sigmoid.
    * `keras.regularizers.l2(1e-6)`: Menambahkan penalti L2 pada bobot embedding untuk mengurangi overfitting.
    * `tf.tensordot(user_vector, anime_vector, 2)`: Menghitung dot product antara vektor pengguna dan vektor anime. Ini adalah inti dari interaksi model.
    * `tf.nn.sigmoid(x)`: Menerapkan fungsi aktivasi sigmoid untuk memetakan output ke rentang [0,1].

* **Kompilasi Model**:
    * `loss = tf.keras.losses.BinaryCrossentropy()`: Fungsi loss ini mengukur perbedaan antara probabilitas prediksi (output sigmoid) dan nilai target aktual (yang diasumsikan biner atau [0,1]).
    * `optimizer = keras.optimizers.Adam(learning_rate=0.0001)`: Algoritma optimasi Adam digunakan untuk memperbarui bobot model berdasarkan loss.
    * `metrics=[tf.keras.metrics.RootMeanSquaredError()]`: Meskipun loss adalah Binary Crossentropy, RMSE tetap dihitung sebagai metrik tambahan, yang mungkin memberikan insight tentang error dalam skala rating yang lebih mudah diinterpretasikan jika targetnya adalah rating yang dinormalisasi.

* **Logika Pembuatan Rekomendasi**:
    * `anime_not_watched = anime_df[~anime_df['id'].isin(anime_watched_by_user.anime_id.values)]['id']`: Menyaring anime untuk mendapatkan daftar yang belum ditonton oleh pengguna.
    * `user_anime_array = np.hstack(([[user_encoder]] * len(anime_not_watched), anime_not_watched))`: Membangun array input untuk `model.predict()`. Setiap baris adalah `[user_index, anime_index]`.
    * `ratings = model.predict(user_anime_array).flatten()`: Mendapatkan prediksi skor untuk semua anime yang belum ditonton.
    * `top_ratings_indices = ratings.argsort()[-10:][::-1]`: Mengambil indeks dari 10 anime dengan skor prediksi tertinggi. `argsort()` mengurutkan dari kecil ke besar, sehingga `[-10:]` mengambil 10 terakhir (tertinggi) dan `[::-1]` membalik urutannya menjadi dari tertinggi ke terendah.

### 5.4 Analisis Pendekatan yang Dipilih
Bagian ini akan membahas kelebihan dan kekurangan dari masing-masing pendekatan (CF dan CBF) yang telah diimplementasikan dalam konteks sistem rekomendasi anime ini.

#### 5.4.1 Kelebihan dan Kekurangan Content-Based Filtering
**Kelebihan CBF**
* **Transparansi Rekomendasi**: CBF dapat memberikan penjelasan mengapa suatu item direkomendasikan (misalnya, "direkomendasikan karena memiliki genre yang sama dengan anime yang Anda sukai").
* **Tidak Ada Masalah Cold Start untuk Item Baru**: Selama item baru memiliki deskripsi konten (genre, sinopsis, dll.), item tersebut dapat langsung direkomendasikan tanpa memerlukan data interaksi pengguna.
* **Personalisasi Spesifik**: Mampu merekomendasikan item yang sangat spesifik dan sesuai dengan minat pengguna berdasarkan konten yang disukai sebelumnya, bahkan jika item tersebut tidak populer.
* **Tidak Memerlukan Data Pengguna Lain**: Rekomendasi untuk satu pengguna tidak bergantung pada data pengguna lain, hanya pada profil pengguna itu sendiri (jika dibangun) atau item referensi dan konten item.

**Kekurangan CBF**
* **Keterbatasan Analisis Konten**: Kualitas rekomendasi sangat bergantung pada ketersediaan dan kualitas data konten serta kemampuan untuk merepresentasikan fitur konten secara efektif (misalnya, melalui TF-IDF). Fitur yang sulit diekstrak atau subjektif bisa menjadi masalah.
* **Over-Specialization (Filter Bubble)**: Cenderung merekomendasikan item yang sangat mirip dengan apa yang sudah disukai pengguna atau item referensi, sehingga mengurangi kemungkinan pengguna menemukan item di luar preferensi biasanya (kurang *serendipity*).
* **Masalah Cold Start untuk Pengguna Baru (jika membangun profil pengguna)**: Jika CBF bergantung pada pembangunan profil pengguna berdasarkan item yang disukai, maka pengguna baru tanpa histori akan sulit mendapatkan rekomendasi yang relevan. Namun, jika CBF berbasis item-ke-item (seperti yang diimplementasikan di sini dengan input nama anime), masalah ini kurang signifikan.
* **Membutuhkan Rekayasa Fitur**: Ekstraksi dan pemilihan fitur konten yang baik seringkali memerlukan domain expertise dan upaya rekayasa fitur yang signifikan agar representasi TF-IDF menjadi bermakna.

#### 5.4.2 Kelebihan dan Kekurangan Collaborative Filtering (dengan Neural Network)
**Kelebihan CF (Neural Network)**
* **Kemampuan Menangkap Pola Kompleks**: Model Neural Network, dengan penggunaan embedding dan layer non-linear (meskipun di sini interaksi utamanya dot product + bias, namun arsitektur dasarnya mampu dikembangkan lebih lanjut), dapat menangkap pola interaksi pengguna-item yang lebih kompleks dibandingkan metode CF tradisional seperti k-NN.
* **Serendipity**: Dapat merekomendasikan item yang tidak terduga namun relevan bagi pengguna, karena model belajar dari perilaku kolektif pengguna. Jika pengguna A mirip dengan pengguna B, dan B menyukai item X yang belum diketahui A, X bisa direkomendasikan ke A.
* **Tidak Memerlukan Fitur Konten Eksplisit**: Model ini tidak memerlukan analisis manual terhadap konten item (seperti genre atau deskripsi). Model belajar preferensi secara implisit dari data interaksi.
* **Personalisasi**: Rekomendasi disesuaikan untuk setiap pengguna berdasarkan histori interaksinya dan kemiripannya dengan pengguna lain.
* **Scalability dengan Teknik Tertentu**: Meskipun training bisa mahal, model embedding dapat diskalakan dengan baik untuk prediksi setelah dilatih.

**Kekurangan CF (Neural Network)**
* **Masalah Cold Start**:
    - **Pengguna Baru (New User Problem)**: Model kesulitan memberikan rekomendasi yang akurat untuk pengguna baru karena tidak ada data histori interaksi pengguna tersebut untuk membuat embedding yang representatif.
    - **Item Baru (New Item Problem)**: Item baru yang belum pernah mendapatkan rating atau interaksi tidak akan direkomendasikan karena belum memiliki representasi embedding yang terlatih.
* **Sparsity Data**: Jika matriks interaksi pengguna-item sangat renggang (banyak pengguna hanya memberi rating pada sedikit item, atau banyak item hanya dirating oleh sedikit pengguna), model mungkin kesulitan mempelajari embedding yang baik, yang dapat mempengaruhi kualitas rekomendasi.
* **Popularity Bias**: Model CF, termasuk yang berbasis neural network, cenderung merekomendasikan item yang populer karena item tersebut memiliki lebih banyak data interaksi, sehingga embedding-nya lebih terlatih dan lebih mungkin muncul sebagai rekomendasi.
* **Membutuhkan Data Interaksi yang Cukup**: Kinerja model sangat bergantung pada kuantitas dan kualitas data interaksi pengguna-item.
* **Kompleksitas Model dan Training**: Model Neural Network bisa lebih kompleks untuk diimplementasikan dan di-debug dibandingkan metode CF yang lebih sederhana. Proses training juga bisa memakan waktu dan sumber daya komputasi yang signifikan, terutama dengan dataset besar.

### 5.5 Ringkasan Hasil Modeling
Dalam penelitian ini, dua pendekatan sistem rekomendasi anime telah berhasil diimplementasikan dan diuji: Collaborative Filtering (CF) menggunakan arsitektur Neural Network dan Content-Based Filtering (CBF) menggunakan TF-IDF dan Cosine Similarity.

* **Collaborative Filtering (CF)** menunjukkan kemampuannya untuk mempelajari preferensi pengguna dari data interaksi historis (rating) dan menghasilkan rekomendasi yang dipersonalisasi. Model Neural Network yang digunakan dapat menangkap pola interaksi yang kompleks antara pengguna dan anime. Meskipun demikian, model ini menghadapi tantangan klasik CF seperti masalah *cold start* untuk pengguna dan item baru, serta potensi *popularity bias*. Output rekomendasi untuk pengguna contoh (User 39397) menampilkan daftar anime yang belum ditonton pengguna tersebut, diurutkan berdasarkan prediksi skor kesukaan dari model.

* **Content-Based Filtering (CBF)** memberikan rekomendasi berdasarkan kemiripan konten antar anime, khususnya menggunakan fitur genre yang direpresentasikan dengan TF-IDF. Pendekatan ini efektif dalam menemukan anime yang secara tematik serupa dengan anime input (misalnya, 'Kimi no Na wa.'), dan tidak bergantung pada data interaksi pengguna lain. Keunggulannya adalah transparansi dan kemampuan menangani item baru (selama ada deskripsi konten). Namun, CBF cenderung menghasilkan rekomendasi yang kurang beragam (*over-specialization*) dan kualitasnya sangat bergantung pada kualitas fitur konten yang diekstrak.

---

## Bab 6: Evaluasi

Bab ini bertujuan untuk melakukan evaluasi terhadap kinerja dua model sistem rekomendasi anime yang telah dikembangkan pada Bab 5, yaitu model Collaborative Filtering (CF) dan Content-Based Filtering (CBF). Evaluasi dilakukan dengan menggunakan metrik yang relevan untuk setiap jenis model dan tujuan yang ingin dicapai. Untuk model CF, evaluasi difokuskan pada akurasi prediksi rating, sedangkan untuk model CBF, evaluasi difokuskan pada kualitas daftar rekomendasi top-N yang dihasilkan. Bab ini akan menjelaskan metrik evaluasi yang digunakan, menyajikan hasil evaluasi, dan membahas implikasi dari hasil tersebut terhadap performa model.

### 6.1 Metrik Evaluasi
Pemilihan metrik evaluasi yang tepat sangat penting untuk mengukur sejauh mana model rekomendasi berhasil mencapai tujuannya. Dalam proyek ini, metrik yang berbeda digunakan untuk mengevaluasi model CF dan CBF, sesuai dengan karakteristik dan output masing-masing model.

#### 6.1.1 Root Mean Squared Error (RMSE)
Root Mean Squared Error (RMSE) adalah metrik standar yang digunakan untuk mengukur rata-rata besarnya kesalahan antara nilai yang diprediksi oleh model dan nilai aktual. Dalam konteks sistem rekomendasi Collaborative Filtering yang memprediksi rating, RMSE mengukur seberapa jauh prediksi rating model dari rating yang sebenarnya diberikan oleh pengguna.
    
Formula RMSE adalah sebagai berikut:
$$RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2}$$ 
Di mana:
* $$N$$ adalah jumlah total data poin (rating).
* $$y_i$$ adalah nilai rating aktual ke-$$i$$.
* $$\hat{y}_i$$ adalah nilai rating yang diprediksi oleh model untuk data poin ke-$$i$$.
    
Cara kerja RMSE adalah dengan mengkuadratkan selisih antara nilai aktual dan prediksi (error), merata-ratakannya, kemudian mengakarkannya. Pengkuadratan error memberikan bobot lebih pada kesalahan yang besar. Nilai RMSE yang lebih rendah menunjukkan performa model yang lebih baik, artinya prediksi model lebih dekat dengan nilai aktual. Metrik ini sangat relevan untuk model CF yang dilatih untuk meminimalkan error prediksi rating.

#### 6.1.2 Precision@k
Precision@k adalah metrik evaluasi yang digunakan untuk mengukur proporsi item yang relevan dari sejumlah $$k$$ item teratas yang direkomendasikan oleh sistem. Metrik ini berfokus pada akurasi dan relevansi dari daftar rekomendasi yang disajikan kepada pengguna.

Formula Precision@k adalah:
    $$Precision@k = \frac{\text{Jumlah item relevan dalam } k \text{ rekomendasi teratas}}{\text{Jumlah item yang direkomendasikan } (k)}$$

Cara kerja Precision@k adalah dengan memeriksa$$k$$ item pertama dalam daftar rekomendasi dan menghitung berapa banyak di antaranya yang benar-benar relevan bagi pengguna. Item "relevan" dalam konteks ini biasanya adalah item yang disukai atau diberi rating tinggi oleh pengguna di masa lalu (yang tidak digunakan untuk menghasilkan rekomendasi saat evaluasi). Nilai Precision@k yang lebih tinggi menunjukkan bahwa sebagian besar item yang direkomendasikan dalam top-k adalah relevan.

#### 6.1.3 Recall@k
Recall@k mengukur proporsi item relevan yang berhasil ditemukan dan direkomendasikan oleh sistem dalam daftar $$k$$ item teratas, dari keseluruhan item relevan yang ada untuk pengguna tersebut.

Formula Recall@k adalah:
$$Recall@k = \frac{\text{Jumlah item relevan dalam } k \text{ rekomendasi teratas}}{\text{Total jumlah item relevan untuk pengguna}}$$    

Cara kerja Recall@k adalah dengan menilai seberapa banyak dari semua item yang seharusnya direkomendasikan (item relevan) yang berhasil masuk ke dalam daftar$$k$$ rekomendasi teratas. Nilai Recall@k yang lebih tinggi menunjukkan kemampuan model yang lebih baik dalam menemukan kembali item-item yang relevan bagi pengguna. Seringkali ada trade-off antara Precision@k dan Recall@k; meningkatkan salah satu bisa jadi menurunkan yang lainnya.

## 6.2 Evaluasi Model Content-Based Filtering (CBF)

### 6.2.1 Metrik yang Digunakan
Untuk model Content-Based Filtering (CBF), yang merekomendasikan item berdasarkan kemiripan konten, metrik evaluasi yang digunakan adalah **Precision@k** dan **Recall@k**. Metrik ini dipilih karena CBF secara langsung menghasilkan daftar top-N rekomendasi, dan kita ingin mengukur seberapa relevan item-item dalam daftar tersebut.

Proses evaluasi CBF dilakukan dengan fungsi `content_based_evaluation` dengan skenario sebagai berikut:
    1.  Pengguna yang memiliki sejumlah rating positif (didefinisikan dengan `threshold` rating $\ge 7$) disertakan dalam evaluasi.
    2.  Untuk setiap pengguna, satu anime yang pernah diberi rating positif (`seed_anime_id`) digunakan sebagai input untuk menghasilkan $$k$$ rekomendasi.
    3.  Anime lain yang juga pernah diberi rating positif oleh pengguna tersebut (dan tidak termasuk `seed_anime_id`) dianggap sebagai "item relevan".
    4.  Daftar $$k$$ rekomendasi dibandingkan dengan himpunan "item relevan" untuk menghitung Precision@k dan Recall@k.
    5.  Nilai rata-rata Precision@k dan Recall@k dihitung dari seluruh pengguna yang diproses.
    Pada evaluasi ini, digunakan parameter `k=10` dan `threshold=7`.

### 6.2.2 Hasil dan Pembahasan**
Setelah menjalankan fungsi evaluasi `content_based_evaluation` terhadap 55.115 pengguna yang memenuhi kriteria, diperoleh hasil sebagai berikut:
```
    {'Mean Precision@10 (CBF)': 0.10327497051619343, 'Mean Recall@10 (CBF)': 0.020172935241919425}
```

Interpretasi hasil:
* **Mean Precision@10 (CBF) = 0.1033**: Rata-rata, sekitar 10.33% dari 10 anime yang direkomendasikan oleh model CBF benar-benar relevan bagi pengguna (yaitu, termasuk dalam item yang juga mereka sukai berdasarkan rating tinggi). Ini berarti, dari 10 rekomendasi yang diberikan, sekitar 1 anime adalah anime yang memang relevan bagi pengguna.
* **Mean Recall@10 (CBF) = 0.0202**: Model CBF mampu menemukan kembali sekitar 2.02% dari total keseluruhan item relevan pengguna dalam 10 rekomendasi teratasnya.

Nilai Precision@10 sebesar 0.1033 menunjukkan adanya kemampuan model untuk menyajikan item yang relevan, meskipun ruang untuk peningkatan masih signifikan. Nilai Recall@10 yang relatif rendah (0.0202) cukup umum terjadi dalam sistem rekomendasi top-N, terutama ketika nilai $$k$$ (dalam hal ini 10) jauh lebih kecil daripada jumlah total item yang mungkin relevan bagi seorang pengguna. Jika seorang pengguna menyukai banyak anime, sulit bagi sistem untuk mencakup semuanya hanya dalam 10 rekomendasi. Kualitas rekomendasi CBF sangat bergantung pada kualitas representasi konten (hasil TF-IDF dari genre) dan bagaimana kemiripan diukur.

### 6.3 Evaluasi Model Collaborative Filtering (CF)

#### 6.3.1 Metrik yang Digunakan
Untuk model Collaborative Filtering (CF) yang dibangun menggunakan arsitektur `RecommenderNet` dengan TensorFlow/Keras, metrik evaluasi utama yang digunakan selama proses training dan validasi adalah **Root Mean Squared Error (RMSE)**. Metrik ini dipilih karena model CF dilatih untuk memprediksi nilai rating yang kemudian digunakan untuk menghasilkan rekomendasi. RMSE secara langsung mengukur akurasi prediksi rating tersebut.

#### 6.3.2 Hasil dan Pembahasan
Proses pelatihan model CF dimonitor menggunakan RMSE pada data training dan data validasi. Gambar berikut menunjukkan kurva metrik RMSE selama epoch pelatihan:

Berdasarkan Kurva Metrik RMSE Model CF Selama Pelatihan dan log pelatihan yang dihasilkan:
* Terlihat bahwa nilai RMSE baik pada data training (`train`) maupun data validasi (`test`/`val_root_mean_squared_error`) menurun seiring bertambahnya epoch, yang mengindikasikan bahwa model belajar dengan baik.
* Kurva `train` RMSE terus menurun, sementara kurva `test` RMSE mulai stagnan atau mendatar setelah sekitar epoch ke-20 hingga ke-30, dan mencapai nilai terendahnya di sekitar epoch ke-79.
* Model menggunakan mekanisme *early stopping* yang memantau `val_root_mean_squared_error`. Pelatihan berhenti pada epoch ke-86 karena tidak ada peningkatan performa pada data validasi selama beberapa epoch berturut-turut (`patience=7`), dan bobot model dikembalikan ke kondisi pada epoch ke-79, di mana `val_root_mean_squared_error` mencapai nilai terbaiknya.

Log pelatihan menunjukkan bahwa nilai `val_root_mean_squared_error` terbaik yang dicapai adalah sekitar **0.13256**.
```
    Epoch 86: early stopping
    Restoring model weights from the end of the best epoch: 79.
```
Nilai `val_root_mean_squared_error` sebesar 0.13256 mengindikasikan bahwa, rata-rata, prediksi rating yang dihasilkan oleh model CF memiliki selisih sekitar 0.13256 poin dari rating aktual pada skala rating yang telah dinormalisasi (kemungkinan [0,1] atau skala serupa mengingat penggunaan `BinaryCrossentropy` sebagai loss). Semakin kecil nilai RMSE ini, semakin akurat model dalam memprediksi rating yang akan diberikan pengguna pada suatu anime. Akurasi prediksi rating ini penting karena menjadi dasar dalam menentukan anime mana yang akan direkomendasikan kepada pengguna.

## 6.4 Analisis Kesesuaian Metrik dan Kesimpulan Evaluasi
Metrik evaluasi yang dipilih untuk masing-masing model telah sesuai dengan konteks data, permasalahan yang ingin diselesaikan (memberikan rekomendasi anime), dan solusi yang diinginkan (prediksi rating yang akurat untuk CF, daftar rekomendasi yang relevan untuk CBF).

* **RMSE untuk CF**: Metrik ini tepat untuk mengevaluasi aspek prediksi rating dari model CF. Dengan mengetahui seberapa akurat model memprediksi preferensi rating pengguna, kita dapat memiliki keyakinan pada kualitas daftar rekomendasi yang dihasilkan berdasarkan urutan prediksi rating tersebut. Model CF menunjukkan performa yang cukup baik dengan `val_root_mean_squared_error` sebesar 0.13256, mengindikasikan error prediksi yang relatif kecil.
* **Precision@10 dan Recall@10 untuk CBF**: Metrik ini adalah standar industri untuk mengevaluasi kualitas daftar rekomendasi top-N. Keduanya memberikan gambaran tentang seberapa banyak rekomendasi yang relevan (Precision) dan seberapa banyak item relevan yang berhasil ditemukan (Recall). Model CBF memberikan hasil Precision@10 sebesar 0.1033 dan Recall@10 sebesar 0.0202. Meskipun angka ini mungkin tampak tidak terlalu tinggi, dalam sistem rekomendasi dengan jumlah item yang sangat besar, mencapai nilai presisi dan recall yang tinggi merupakan tantangan.
















