# Laporan Proyek Machine Learning - Alifia Mustika Sari

## Project Overview

<br>

### Latar Belakang

Industri pariwisata merupakan salah satu sektor penting yang mendukung pertumbuhan ekonomi, baik secara lokal maupun global. Seiring berkembangnya teknologi dan meningkatnya akses informasi, wisatawan kini dihadapkan pada banyaknya pilihan destinasi wisata yang tersedia secara daring. Hal ini menciptakan tantangan baru, yaitu kesulitan dalam menentukan destinasi yang paling sesuai dengan preferensi pribadi. Ketika pengguna tidak memiliki informasi atau referensi yang cukup, mereka cenderung memilih tempat yang sudah populer, sehingga mengurangi potensi destinasi lainnya yang tidak kalah menarik namun kurang terekspos `(Yulianto et al., 2023)`.

Untuk mengatasi permasalahan ini, pengembangan sistem rekomendasi destinasi wisata menjadi sangat penting. Sistem ini bertujuan untuk memberikan saran yang relevan dan personalisasi berdasarkan preferensi, riwayat, atau pola perilaku pengguna. Dengan demikian, pengguna tidak perlu menelusuri semua pilihan secara manual, melainkan dapat langsung mendapatkan rekomendasi destinasi yang sesuai dengan keinginan mereka.

Menurut riset yang dilakukan oleh `Goel & Rizvi (2024)`, implementasi sistem rekomendasi menggunakan algoritma hybrid (gabungan content-based filtering dan collaborative filtering) dapat meningkatkan relevansi saran destinasi dan mengurangi cold start problem yang sering terjadi pada sistem rekomendasi berbasis pengguna baru atau item baru.

Penelitian lain yang dilakukan oleh `Syakura (2024)` menunjukkan bahwa sistem rekomendasi destinasi wisata berbasis content-based dapat membantu wisatawan untuk menemukan tempat yang relevan meskipun mereka belum memberikan banyak rating sebelumnya. Sementara itu, sistem berbasis collaborative filtering yang dikembangkan di Semarang terbukti efektif dalam merekomendasikan tempat wisata baru yang belum populer tetapi sesuai dengan pola pengguna lain `(Cholil et al., 2023)`.

Melalui proyek ini, diharapkan sistem yang dibangun tidak hanya mempermudah wisatawan dalam merencanakan perjalanan, tetapi juga memberikan dampak positif bagi sektor pariwisata lokal dengan memperkenalkan lebih banyak destinasi kepada pengguna. Dengan memanfaatkan data dan teknologi, sistem rekomendasi menjadi solusi cerdas dan adaptif di era digital untuk meningkatkan pengalaman wisata yang lebih personal dan efisien.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang di atas, berikut ini merupakan rincian masalah yang dapat diselesaikan pada proyek ini:

- **Bagaimana cara memberikan rekomendasi destinasi wisata yang relevan berdasarkan deskripsi dan kategori konten?**

  Masalah ini berfokus pada pemanfaatan informasi terkait karakteristik destinasi, seperti kategori (budaya, alam, dll.) dan deskripsi tempat untuk memberikan rekomendasi yang lebih personal dan relevan bagi pengguna. Dengan pendekatan content-based filtering, sistem harus dapat menganalisis dan menyarankan destinasi yang sesuai dengan preferensi pengguna, berdasarkan kesamaan fitur-fitur tersebut.

- **Bagaimana cara menggunakan data rating pengguna untuk meningkatkan akurasi rekomendasi?**

  Data yang berisi interaksi pengguna terhadap destinasi wisata, seperti rating yang diberikan oleh pengguna, sangat penting untuk meningkatkan kualitas rekomendasi. Dengan menggabungkan teknik content-based dan collaborative filtering, sistem dapat mengatasi kekurangan data pada pengguna baru dan memperbaiki akurasi saran yang diberikan. Sistem ini dapat menyesuaikan rekomendasi dengan pola rating yang diberikan oleh pengguna lain dengan preferensi serupa, meningkatkan relevansi rekomendasi yang disarankan.

- **Bagaimana cara mengukur relevansi rekomendasi agar sistem dapat memberikan hasil yang tepat?**

  Sistem rekomendasi harus mampu memberikan hasil yang sesuai dengan kebutuhan pengguna. Oleh karena itu, diperlukan metrik evaluasi yang efektif untuk memantau dan mengukur sejauh mana sistem mampu menghasilkan rekomendasi yang relevan dan tepat sasaran.

### Goals

Tujuan utama dari proyek ini adalah untuk membangun sistem rekomendasi destinasi wisata yang relevan dan adaptif dengan memanfaatkan informasi konten destinasi serta interaksi pengguna sebelumnya. Sistem ini diharapkan dapat membantu wisatawan dalam menemukan destinasi yang sesuai dengan preferensi mereka secara lebih efisien, mengurangi ketergantungan pada pencarian manual, serta memperluas eksposur terhadap destinasi yang kurang populer namun potensial.

Secara lebih spesifik, tujuan proyek ini meliputi:

- **Membangun sistem rekomendasi berbasis konten yang efisien dengan memanfaatkan deskripsi dan kategori destinasi wisata.**

  Sistem ini akan memanfaatkan informasi deskriptif dan klasifikasi destinasi untuk mencocokkan rekomendasi dengan minat pengguna yang sudah pernah mengunjungi tempat wisata tertentu.

- **Mengembangkan sistem rekomendasi destinasi wisata berbasis kolaboratif yang mempertimbangkan pola penilaian pengguna.**

  Dengan menganalisis data rating yang diberikan pengguna terhadap destinasi tertentu, sistem diharapkan dapat menyarankan tempat wisata yang relevan berdasarkan kesamaan pola preferensi antar pengguna.

- **Melakukan evaluasi terhadap performa sistem rekomendasi menggunakan metrik yang sesuai.**

  Evaluasi dilakukan untuk menilai tingkat relevansi dan akurasi rekomendasi yang dihasilkan, guna memastikan bahwa sistem memberikan saran yang tepat sasaran dan bermanfaat bagi pengguna.

### Solution Statements

Untuk mencapai tujuan proyek, dilakukan serangkaian pendekatan sebagai berikut:
Untuk mencapai tujuan proyek, dilakukan serangkaian pendekatan sebagai berikut:

- **Content-based Filtering**

  Pendekatan ini memanfaatkan informasi tekstual pada deskripsi dan kategori destinasi wisata untuk merekomendasikan tempat yang memiliki karakteristik serupa dengan destinasi yang disukai pengguna sebelumnya. Langkah-langkah yang dilakukan adalah sebagai berikut:

  - Preprocessing

    Deskripsi dan kategori destinasi digabungkan dan dibersihkan, lalu diubah menjadi representasi numerik menggunakan metode TF-IDF Vectorizer.

  - Pembangunan Model

    Kesamaan antar destinasi dihitung menggunakan cosine similarity berdasarkan vektor TF-IDF, sehingga sistem dapat merekomendasikan destinasi yang memiliki konten serupa.

  - Evaluasi

    Kinerja sistem diukur menggunakan metrik Precision@10, yang mengevaluasi proporsi destinasi yang relevan dari 10 rekomendasi teratas.

- **Collaborative Filtering**

  Pendekatan ini mengandalkan data interaksi pengguna berupa rating untuk menyarankan destinasi yang disukai oleh pengguna lain dengan preferensi serupa. Berikut adalah langkah-langkah yang dilakukan:

  - Encoding Data

    ID pengguna dan destinasi dikonversi menjadi indeks numerik untuk mempermudah proses pelatihan dalam model neural network.

  - Normalisasi Rating

    Rating dinormalisasi ke rentang [0,1] guna memastikan stabilitas pembelajaran model.

  - Pembangunan Model

    Model dikembangkan menggunakan embedding layer untuk memetakan pengguna dan destinasi ke dalam representasi vektor, dan menghasilkan prediksi rating untuk pasangan pengguna–destinasi.

  - Evaluasi

    Metrik yang digunakan meliputi Root Mean Square Error (RMSE) dan Mean Absolute Error (MAE), yang menilai akurasi prediksi model terhadap rating aktual.

<br>

## 🧠 1. Data Understanding

### 1.1. Deskripsi Variabel

#### Informasi Dataset

| Jenis      | Keterangan                                                                            |
| ---------- | ------------------------------------------------------------------------------------- |
| Title      | Indonesia Tourism Destination                                                         |
| Source     | [Kaggle](https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination/data) |
| Maintainer | [A_Prabowo](https://www.kaggle.com/datasets/aprabowo)                                 |
| License    | Data files © Original Authors                                                         |
| Visibility | Publik                                                                                |
| Tags       | Beginner, Travel, Asia, Recommender Systems                                           |
| Usability  | 8.24                                                                                  |

Tabel 1a. Informasi Dataset Yang Digunakan

Berdasarkan Tabel 1a, Dataset `Indonesia Tourism Destination` yang digunakan pada proyek ini diambil dari platform Kaggle. Dataset ini memuat informasi detail mengenai destinasi tempat wisata di lima kota besar Indonesia yaitu Jakarta, Yogyakarta, Semarang, Bandung, dan Surabaya. Data yang digunakan berasal dari dua file, yaitu `tourism_with_id.csv` dan `tourism_rating.csv`.

- File `tourism_with_id.csv` berisi informasi tentang destinasi wisata di lima kota besar, dengan total 437 data.
- File `tourism_rating.csv` berisi 10.000 data rating pengguna terhadap destinasi wisata tertentu.

Rincian penjelasan mengenai variabel dataset dapat dilihat pada Tabel 1b dan Tabel 1c.

| No. | Variabel     | Deskripsi                                       | Tipe Data |
| --- | ------------ | ----------------------------------------------- | --------- |
| 1   | Place_Id     | ID unik untuk setiap destinasi wisata.          | Integer   |
| 2   | Place_Name   | Nama destinasi wisata.                          | String    |
| 3   | Description  | Deskripsi singkat mengenai destinasi.           | String    |
| 4   | Category     | Kategori destinasi (misal: Budaya, Alam, dll.). | String    |
| 5   | City         | Kota tempat destinasi berada.                   | String    |
| 6   | Price        | Harga tiket masuk destinasi.                    | Integer   |
| 7   | Rating       | Nilai rating rata-rata pengguna (0-5).          | Float     |
| 8   | Time_Minutes | Estimasi waktu kunjungan (dalam menit).         | Float     |
| 9   | Coordinate   | Koordinat geografis destinasi.                  | String    |
| 10  | Lat          | Garis lintang (latitude) lokasi destinasi.      | Float     |
| 11  | Long         | Garis bujur (longitude) lokasi destinasi.       | Float     |
| 12  | Unnamed: 11  | Kolom kosong/tidak digunakan.                   | Float     |
| 13  | Unnamed: 12  | Salinan duplikat dari Place_Id.                 | Integer   |

Tabel 1b. Deskripsi Variabel File `tourism_with_id.csv`

| No. | Variabel      | Deskripsi                                                    | Tipe Data     |
| --- | ------------- | ------------------------------------------------------------ | ------------- |
| 1   | User_Id       | ID unik untuk setiap pengguna.                               | Integer       |
| 2   | Place_Id      | ID unik untuk setiap destinasi wisata.                       | Integer       |
| 3   | Place_Ratings | Rating yang diberikan pengguna untuk destinasi wisata (0-5). | Integer (0-5) |

Tabel 1c. Deskripsi Variabel File `tourism_rating.csv`

<br>

### 1.2. Data Assessing

Setelah data berhasil dikumpulkan, dilakukan evaluasi kualitas data melalui beberapa pengecekan penting, yaitu:

#### 1.2.1. Pengecekan Duplikasi Data

Dilakukan pemeriksaan apakah terdapat baris data yang tercatat lebih dari satu kali. Data duplikat dapat memperkenalkan bias dalam pelatihan model dan perlu dihapus.

```python
print("Jumlah Duplikasi:", df_loan_eda.duplicated().sum())
```

Berdasarkan hasil pengecekan duplikasi dataframe `df_loan_eda`, dapat dilihat bahwa tidak terdapat duplikasi dataframe `df_loan_eda` yang berarti `semua data bersifat unik`.

#### 1.2.2. Pengecekan Missing Values

Dicek apakah terdapat nilai kosong (missing) pada kolom-kolom penting. Kehadiran nilai kosong dapat menurunkan kualitas model dan, jika ditemukan, perlu ditangani melalui imputasi atau penghapusan.

| No  | Kolom                    | Jumlah Nilai Kosong |
| --- | ------------------------ | ------------------- |
| 0   | loan_id                  | 0                   |
| 1   | no_of_dependents         | 0                   |
| 2   | education                | 0                   |
| 3   | self_employed            | 0                   |
| 4   | income_annum             | 0                   |
| 5   | loan_amount              | 0                   |
| 6   | loan_term                | 0                   |
| 7   | cibil_score              | 0                   |
| 8   | residential_assets_value | 0                   |
| 9   | commercial_assets_value  | 0                   |
| 10  | luxury_assets_value      | 0                   |
| 11  | bank_asset_value         | 0                   |
| 12  | loan_status              | 0                   |

Tabel 1c. Memeriksa data missing value

Dapat dilihat pada Tabel 1c bahwa dataframe `df_loan_eda` `tidak memiliki nilai yang hilang` dalam setiap kolomnya. Hal ini menunjukkan bahwa data yang tersedia cukup bersih dan siap untuk dianalisis lebih lanjut tanpa perlu dilakukan imputasi atau pembersihan tambahan terkait missing values.

#### 1.2.3. Pengecekan Outlier

Outlier adalah nilai yang menyimpang jauh dari pola umum data. Keberadaan outlier dapat mempengaruhi performa model secara signifikan. Oleh karena itu, dilakukan identifikasi dan penanganan outlier menggunakan metode Interquartile Range (IQR).

![Visualisasi Boxplot (Outlier))](images/image-6.png)

Gambar 1a. Visualisasi Boxplot Setiap Fitur Numerik

Berdasarkan hasil dari Gambar 1a diatas menunjukkan bahwa beberapa fitur seperti:

- `residential_assets_value`
- `commercial_assets_value`
- `bank_asset_value`

memiliki sebaran yang cukup lebar dan menunjukkan keberadaan nilai outlier (ditandai dengan titik-titik di luar batas whisker boxplot). Kehadiran outlier ini perlu ditangani karena berpotensi mempengaruhi distribusi data dan kinerja model prediksi yang akan dibangun.

<br>

### 1.3. EDA - Univariate Analysis

![Analisis Univariat (Data Kategori)](images/image-1.png)

Gambar 1b. Analisis Univariat (Data Kategori)

![Analisis Univariat (Data Numerik)](images/image-2.png)

Gambar 1c. Analisis Univariat (Data Numerik)

Berdasarkan Gambar 1b, dapat dilihat bahwa distribusi data kategorik `loan_status` terdiri dari dua kategori yaitu `Approved` dan `Rejected`, yang mana jumlah data `Approved` sekitar 2600 dan `Rejected sekitar` 1600. Hal ini menunjukkan bahwa data tergolong tidak terlalu imbang, dengan mayoritas pemohon memperoleh persetujuan pinjaman. Perbandingan yang tidak seimbang ini perlu diperhatikan saat membangun model prediktif, karena dapat menyebabkan bias terhadap kelas mayoritas (Approved).

Pada Gambar 1c, untuk data numerik memiliki karakteristik sebagai berikut:

- Dilihat dari distribusi data `no_of_dependents`, jumlah tanggungan rata-rata berada di antara 0 hingga 5, dengan karakteristik data bersifat diskrit.
- Penghasilan tahunan `(income_annum)` menunjukkan `distribusi yang relatif merata`, dengan sebagian besar nilai berada dalam rentang hingga 10 juta, mengindikasikan `cakupan individu dari berbagai tingkat ekonomi`.
- Data `loan_amount` memiliki rata-rata nilai kecil dan `distribusi skewed ke kanan`, yang berarti sebagian besar pinjaman bernilai rendah namun ada beberapa nilai ekstrem tinggi.
- `loan_term` menunjukkan distribusi diskrit yang berfokus pada nilai-nilai standar seperti 5, 10, 15, dan 20 tahun, mengindikasikan tenor pinjaman standar yang umum digunakan.
- `cibil_score` memiliki sebaran dari 300 hingga 900, dengan distribusi menyerupai kurva normal. Hal ini menandakan variasi skor kredit pemohon cukup luas dan representatif.
- Nilai-nilai aset seperti `residential_assets_value`, `commercial_assets_value`, `luxury_assets_value`, dan `bank_asset_value` menunjukkan `distribusi right-skewed`, menandakan banyak pemohon memiliki aset dalam jumlah kecil dan hanya sedikit yang memiliki aset bernilai tinggi.

<br>

### 1.4. EDA - Multivariate Analysis

![Analisis Multivariat](images/image-3.png)

Gambar 1d. Analisis Multivariat

Berdasarkan Gambar 1d, yang merupakan hasil dari pairplot, tampak pola distribusi dan hubungan antar pasangan fitur numerik:

- Distribusi diagonal menunjukkan penyebaran data untuk masing-masing fitur. Sebagian besar fitur, seperti `income_annum`, `loan_amount`, dan `luxury_assets_value`, memperlihatkan sebaran miring ke kanan (right-skewed), yang mengindikasikan bahwa mayoritas data berada pada nilai rendah dan hanya sedikit data yang bernilai tinggi.
- Plot hubungan antara `income_annum` dengan `loan_amount`, `luxury_assets_value`, dan `bank_asset_value` menunjukkan pola garis miring positif, yang menegaskan korelasi kuat seperti yang ditampilkan pada heatmap korelasi.
- Sebaliknya, fitur seperti `loan_term`, `cibil_score`, dan `no_of_dependents` tampak menunjukkan pola sebaran acak atau tidak terstruktur, menandakan hubungan lemah dengan fitur lainnya.
- Tidak ditemukan outlier ekstrem yang mencolok, namun sebaran data yang padat di bagian bawah menunjukkan adanya ketidakseimbangan distribusi, terutama pada fitur finansial yang memiliki skala besar.

![Analisis Matriks Korelasi](images/image-4.png)

Gambar 1e. Analisis Matriks Korelasi

Berdasarkan Gambar 1e, yang menampilkan heatmap korelasi antar fitur numerik, dapat disimpulkan bahwa:

- Terdapat korelasi sangat tinggi antara `income_annum` dan `loan_amount` sebesar 0.93, serta dengan `luxury_assets_value` (0.93) dan `bank_asset_value` (0.85). Hal ini menunjukkan bahwa semakin tinggi pendapatan seseorang, semakin besar kemungkinan mereka mengajukan pinjaman dan memiliki aset mewah serta simpanan bank yang tinggi.
- Korelasi tinggi juga terlihat antara `loan_amount` dan `luxury_assets_value` (0.86), serta dengan `bank_asset_value` (0.79). Ini menandakan bahwa jumlah pinjaman yang lebih besar cenderung dimiliki oleh individu dengan aset mewah dan tabungan bank lebih besar.
- Sebaliknya, `cibil_score` memiliki korelasi sangat lemah terhadap semua fitur lainnya (berkisar antara -0.03 hingga 0.01), yang menunjukkan bahwa skor CIBIL bersifat independen terhadap fitur-fitur finansial lain.
- Fitur `no_of_dependents` juga menunjukkan korelasi sangat rendah terhadap seluruh fitur lain, dengan nilai mendekati nol.

Secara umum, fitur-fitur yang berhubungan dengan pendapatan dan aset memiliki korelasi yang kuat satu sama lain, menunjukkan adanya keterkaitan yang logis antara penghasilan, pinjaman, dan kekayaan.

Berdasarkan hasil analisis matriks korelasi dan pairplot, dapat disimpulkan bahwa fitur-fitur finansial seperti `income_annum`, `loan_amount`, `luxury_assets_value`, dan `bank_asset_value` memiliki hubungan yang saling berkorelasi erat. Hal ini mengindikasikan bahwa individu dengan pendapatan tinggi cenderung memiliki jumlah pinjaman yang besar serta aset mewah dan simpanan bank yang lebih tinggi. Di sisi lain, fitur seperti `loan_term`, `cibil_score`, dan `no_of_dependents` menunjukkan korelasi yang lemah terhadap fitur numerik lainnya, sehingga kurang memberikan informasi prediktif yang signifikan dalam analisis ini. Selain itu, tidak ditemukan pola non-linear yang kuat maupun outlier yang mencolok, yang menunjukkan bahwa data relatif bersih dan siap untuk dianalisis lebih lanjut menggunakan pendekatan pemodelan regresi atau klasifikasi, terutama jika target analisis berkaitan dengan aspek finansial.

<br>
