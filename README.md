# Laporan Proyek Machine Learning - Alifia Mustika Sari

## Project Overview

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

### Goals/ Tujuan

Tujuan utama dari proyek ini adalah untuk membangun sistem rekomendasi destinasi wisata yang relevan dan adaptif dengan memanfaatkan informasi konten destinasi serta interaksi pengguna sebelumnya. Sistem ini diharapkan dapat membantu wisatawan dalam menemukan destinasi yang sesuai dengan preferensi mereka secara lebih efisien, mengurangi ketergantungan pada pencarian manual, serta memperluas eksposur terhadap destinasi yang kurang populer namun potensial.

Secara lebih spesifik, tujuan proyek ini meliputi:

- **Membangun sistem rekomendasi berbasis konten yang efisien dengan memanfaatkan deskripsi dan kategori destinasi wisata.**

  Sistem ini akan memanfaatkan informasi deskriptif dan klasifikasi destinasi untuk mencocokkan rekomendasi dengan minat pengguna yang sudah pernah mengunjungi tempat wisata tertentu.

- **Mengembangkan sistem rekomendasi destinasi wisata berbasis kolaboratif yang mempertimbangkan pola penilaian pengguna.**

  Dengan menganalisis data rating yang diberikan pengguna terhadap destinasi tertentu, sistem diharapkan dapat menyarankan tempat wisata yang relevan berdasarkan kesamaan pola preferensi antar pengguna.

- **Melakukan evaluasi terhadap performa sistem rekomendasi menggunakan metrik yang sesuai.**

  Evaluasi dilakukan untuk menilai tingkat relevansi dan akurasi rekomendasi yang dihasilkan, guna memastikan bahwa sistem memberikan saran yang tepat sasaran dan bermanfaat bagi pengguna.

### Solution Statements

Untuk mencapai tujuan dari proyek ini, diterapkan dua pendekatan utama dalam sistem rekomendasi, yaitu Content-based Filtering dan Collaborative Filtering, dengan tahapan sebagai berikut:

- **Content-based Filtering**

  Metode ini memanfaatkan informasi deskriptif dan kategori dari destinasi wisata untuk merekomendasikan tempat-tempat yang memiliki kesamaan karakteristik dengan destinasi yang pernah disukai pengguna. Proses pengembangannya mencakup:

  - **Preprocessing Text**

    Data teks berupa deskripsi dan kategori destinasi digabungkan dan dibersihkan, kemudian diubah menjadi representasi numerik menggunakan teknik TF-IDF Vectorizer.

  - **Model Development**

    Kesamaan antar destinasi dihitung menggunakan cosine similarity pada hasil vektorisasi TF-IDF, sehingga memungkinkan sistem untuk mengidentifikasi dan merekomendasikan destinasi dengan konten yang mirip.

  - **Evaluation**

    Performa model diuji menggunakan metrik Precision@10, yang mengukur seberapa banyak rekomendasi dari 10 teratas yang relevan bagi pengguna.

- **Collaborative Filtering**

  Pendekatan ini didasarkan pada perilaku pengguna, khususnya data rating, untuk memberikan rekomendasi berdasarkan kesamaan preferensi antar pengguna. Langkah-langkah pengembangannya meliputi:

  - **Encoding Data**

    ID pengguna dan destinasi dikonversi menjadi indeks numerik untuk mempermudah proses pelatihan dalam model neural network.

  - **Normalisasi Rating**

    Nilai rating dinormalisasi ke dalam rentang [0,1] guna meningkatkan kestabilan pelatihan model.

  - **Model Development**

    Model dibangun menggunakan lapisan embedding untuk merepresentasikan pengguna dan destinasi dalam bentuk vektor, kemudian digunakan untuk memprediksi rating yang mungkin diberikan pengguna terhadap destinasi tertentu.

  - **Evaluation**

    Akurasi prediksi model dinilai menggunakan metrik Root Mean Square Error (RMSE) dan Mean Absolute Error (MAE), yang membandingkan hasil prediksi dengan data rating aktual.

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

### 1.2. Data Assessing

Setelah data berhasil dikumpulkan, dilakukan evaluasi kualitas data melalui beberapa pengecekan penting, yaitu:

#### 1.2.1. Pengecekan Duplikasi Data

Dilakukan pemeriksaan apakah terdapat baris data yang tercatat lebih dari satu kali. Data duplikat dapat memperkenalkan bias dalam pelatihan model dan perlu dihapus.

```
df_tourism[df_tourism.duplicated('Place_Id', keep=False)]
```

| Place_Id | Place_Name | Description | Category | City | Price | Rating | Time_Minutes | Coordinate | Lat | Long | Unnamed: 11 | Unnamed: 12 |
| -------- | ---------- | ----------- | -------- | ---- | ----- | ------ | ------------ | ---------- | --- | ---- | ----------- | ----------- |

Tabel 1d. Memeriksa data duplikasi pada `df_tourism`

```python
df_ratings[df_ratings.duplicated(['User_Id', 'Place_Id'], keep=False)]
```

| No   | User_Id | Place_Id | Place_Ratings |
| ---- | ------- | -------- | ------------- |
| 25   | 1       | 328      | 2             |
| 29   | 1       | 328      | 2             |
| 42   | 2       | 437      | 5             |
| 46   | 2       | 208      | 5             |
| 47   | 2       | 437      | 4             |
| ...  | ...     | ...      | ...           |
| 9952 | 299     | 290      | 5             |
| 9972 | 299     | 407      | 5             |
| 9976 | 300     | 69       | 4             |
| 9978 | 300     | 69       | 3             |
| 9983 | 300     | 69       | 1             |

\*798 rows × 3 columns

Tabel 1e. Memeriksa data duplikasi pada `df_ratings`

Hasil dari pengecekan duplikasi menunjukkan bahwa pada dataset `df_tourism` (Tabel 1d), tidak ditemukan duplikasi baik pada kolom `Place_Id` maupun `Place_Name`, sehingga dapat disimpulkan bahwa setiap destinasi wisata memiliki ID dan nama yang tercatat secara unik. Hal ini menunjukkan bahwa data destinasi sudah tersusun dengan baik dan tidak memerlukan tindakan pembersihan terkait duplikasi.

Sementara itu, pada dataset `df_ratings` (Tabel 1e), ditemukan sebanyak `798 baris duplikasi` pada kombinasi kolom `User_Id` dan `Place_Id`. Artinya, terdapat **sejumlah pengguna yang memberikan lebih dari satu rating untuk destinasi wisata yang sama**. Kondisi ini perlu menjadi perhatian pada tahap preprocessing, karena duplikasi semacam ini dapat memengaruhi akurasi sistem rekomendasi yang dibangun.

#### 1.2.2. Pengecekan Missing Values

Dicek apakah terdapat nilai kosong (missing) pada kolom-kolom penting. Kehadiran nilai kosong dapat menurunkan kualitas model dan, jika ditemukan, perlu ditangani melalui imputasi atau penghapusan.

| No  | Kolom        | Jumlah Nilai Kosong |
| --- | ------------ | ------------------- |
| 0   | Place_Id     | 0                   |
| 1   | Place_Name   | 0                   |
| 2   | Description  | 0                   |
| 3   | Category     | 0                   |
| 4   | City         | 0                   |
| 5   | Price        | 0                   |
| 6   | Rating       | 0                   |
| 7   | Time_Minutes | 232                 |
| 8   | Coordinate   | 0                   |
| 9   | Lat          | 0                   |
| 10  | Long         | 0                   |
| 11  | Unnamed: 11  | 437                 |
| 12  | Unnamed: 12  | 0                   |

Tabel 1f. Memeriksa data missing value pada `df_tourism`

| No  | Kolom         | Jumlah Nilai Kosong |
| --- | ------------- | ------------------- |
| 0   | User_Id       | 0                   |
| 1   | Place_Id      | 0                   |
| 2   | Place_Ratings | 0                   |

Tabel 1g. Memeriksa data missing value pada `df_ratings`

Dapat dilihat pada Tabel 1f bahwa pada dataset `df_tourism` terdapat missing values pada kolom `Time_Minutes` sebanyak `232 baris`, serta seluruh baris pada kolom `Unnamed: 11` kosong. Hal ini menunjukkan bahwa kolom `Time_Minutes` memerlukan penanganan lebih lanjut seperti imputasi, sedangkan kolom `Unnamed: 11` kemungkinan dapat dihapus karena tidak mengandung informasi.

Sementara itu, berdasarkan Tabel 1g, dataset `df_ratings` tidak memiliki missing values pada seluruh kolomnya. Artinya, data pada `df_ratings` sudah bersih dan siap digunakan dalam proses analisis atau pemodelan tanpa perlu penanganan terhadap nilai yang hilang.

#### 1.2.3. Pengecekan Kolom Yang Tidak Relevan

Kolom yang tidak memuat informasi berguna atau hanya merupakan salinan dari kolom lain dapat menyebabkan redundansi dan memperbesar ukuran dataset secara tidak perlu. Oleh karena itu, perlu dilakukan pemeriksaan lebih lanjut sebelum memutuskan untuk menghapusnya.

Saat meninjau struktur dataset, saya menyadari ada sebuah kolom tambahan bernama `Unnamed: 12` yang tampaknya tidak familiar dan sekilas terlihat mirip dengan `Place_Id`. Hal ini membuat saya penasaran, **apakah kolom ini benar-benar memuat informasi baru atau hanya sekadar salinan dari kolom yang sudah ada**.

Dilakukan pengecekan lebih lanjut dengan membandingkan seluruh isi kedua kolom dengan menggunakan kode berikut:

```python
(df_tourism['Place_Id'] == df_tourism['Unnamed: 12']).all()
```

Hasil dari pengecekan ini menghasilkan `True`, yang berarti seluruh nilai di `Unnamed: 12` memang 100% identik dengan `Place_Id`. Dengan demikian, dapat disimpulkan bahwa kolom `Unnamed: 12` tidak memuat informasi baru dan dapat dihapus untuk menjaga kebersihan serta efisiensi data.

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

## 🔗 2. Data Preparation

Pada tahap data preparation, dilakukan serangkaian langkah untuk memastikan bahwa data yang digunakan dalam proses pemodelan bersih, terstruktur, dan siap untuk dianalisis. Tahapan ini mencakup pembersihan data, penggabungan dataset, pengolahan teks, encoding variabel kategorikal, normalisasi rating, dan pembagian data menjadi set pelatihan dan pengujian. Berikut adalah uraian mendetail mengenai setiap langkah yang dilakukan:

### 2.1. Menghapus Kolom Yang Tidak Diperlukan

Untuk menyederhanakan struktur data serta memastikan hanya informasi yang relevan digunakan dalam proses analisis dan pengembangan sistem rekomendasi, dilakukan penghapusan terhadap beberapa kolom yang dinilai tidak memiliki kontribusi signifikan. Proses ini menggunakan perintah:

```python
df_tourism_cleaned = df_tourism.drop(['City', 'Price', 'Time_Minutes', 'Coordinate', 'Lat', 'Long', 'Unnamed: 11', 'Unnamed: 12'], axis=1)
```

Pertimbangan penghapusan kolom adalah sebagai berikut:

- Kolom `Time_Minutes` memiliki jumlah nilai yang hilang cukup besar, yakni sebanyak 232 baris, sehingga dianggap kurang representatif untuk dianalisis lebih lanjut.
- `Unnamed: 11` merupakan kolom kosong tanpa informasi yang berguna, sehingga dikeluarkan dari dataset.
- Kolom seperti `City`, `Price`, `Coordinate`, `Lat`, dan `Long` juga dihapus karena dianggap tidak memberikan kontribusi signifikan terhadap proses analisis atau model rekomendasi yang dikembangkan.

Hasil dari proses ini disimpan dalam variabel baru bernama `df_tourism_cleaned`, yang berisi versi dataset yang telah disederhanakan dan dibersihkan. Untuk memverifikasi hasil penghapusan, kolom-kolom dalam dataset tersebut ditampilkan melalui `df_tourism_cleaned.head()`.

| No  | Place_Id | Place_Name                        | Description                                       | Category      | Rating |
| --- | -------- | --------------------------------- | ------------------------------------------------- | ------------- | ------ |
| 0   | 1        | Monumen Nasional                  | Monumen Nasional atau yang populer disingkat d... | Budaya        | 4.6    |
| 1   | 2        | Kota Tua                          | Kota tua di Jakarta, yang juga bernama Kota Tu... | Budaya        | 4.6    |
| 2   | 3        | Dunia Fantasi                     | Dunia Fantasi atau disebut juga Dufan adalah t... | Taman Hiburan | 4.6    |
| 3   | 4        | Taman Mini Indonesia Indah (TMII) | Taman Mini Indonesia Indah merupakan suatu kaw... | Taman Hiburan | 4.5    |
| 4   | 5        | Atlantis Water Adventure          | Atlantis Water Adventure atau dikenal dengan A... | Taman Hiburan | 4.5    |

Tabel 2a. Cuplikan dataset `df_tourism_cleaned` setelah penghapusan kolom yang tidak relevan

### 2.2. Menghapus Data Yang Duplikat

Untuk menjaga integritas serta konsistensi data selama proses analisis dan pemodelan, seluruh baris yang teridentifikasi sebagai duplikat dihapus dari dataset menggunakan fungsi `drop_duplicates()`. Langkah ini penting dilakukan guna menghindari bias dan distorsi hasil analisis yang dapat muncul akibat data ganda.

Setelah proses penghapusan, dilakukan verifikasi ulang untuk memastikan bahwa tidak ada lagi baris duplikat yang tersisa dalam dataset. Hasil perbandingan jumlah data duplikat sebelum dan sesudah penghapusan disajikan pada `Tabel 2b` berikut:

| Dataset            | Duplikasi Sebelum Dihapus | Duplikasi Setelah Dihapus |
| ------------------ | ------------------------- | ------------------------- |
| df_ratings         | 79                        | 0                         |
| df_tourism_cleaned | 0                         | 0                         |

Tabel 2b. Perbandingan Jumlah Duplikasi Sebelum dan Sesudah Penghapusan

Dengan tidak adanya duplikasi yang tersisa, dataset kini berada dalam kondisi yang lebih bersih dan siap untuk digunakan dalam tahap analisis lebih lanjut maupun pembangunan sistem rekomendasi.

### 2.3. Menggabungkan Dataset

Setelah proses pembersihan dilakukan pada kedua dataset, langkah selanjutnya adalah menggabungkan informasi dari data rating pengguna `(df_ratings)` dengan data destinasi wisata yang telah dibersihkan `(df_tourism_cleaned)`. Tujuan dari penggabungan ini adalah untuk membentuk dataset rekomendasi yang menyajikan informasi rata-rata rating dari setiap destinasi wisata berdasarkan data yang diberikan oleh pengguna.

Penggabungan dilakukan melalui langkah-langkah berikut:

- **Menghitung Rata-rata Rating**

  Dataset `df_ratings` dikelompokkan berdasarkan kolom `Place_Id`, kemudian dihitung rata-rata dari kolom `Place_Ratings` untuk setiap destinasi. Proses ini menghasilkan dataframe baru yang berisi dua kolom: `Place_Id` dan `Place_Ratings`.

- **Penggabungan Dataset**

  Rata-rata rating yang telah dihitung kemudian digabungkan dengan dataset `df_tourism_cleaned` menggunakan fungsi `pd.merge()` dengan parameter `on='Place_Id'`. Penggabungan dilakukan berdasarkan kolom `Place_Id` yang merupakan kunci unik bagi setiap destinasi wisata.

Kode yang digunakan:

```python
df_recommendation = pd.merge(
    df_ratings.groupby('Place_Id')['Place_Ratings'].mean().reset_index(),
    df_tourism_cleaned,
    on='Place_Id'
)
```

Hasil akhir dari proses ini adalah dataframe `df_recommendation` yang menyatukan informasi deskriptif destinasi wisata dengan nilai rata-rata rating dari pengguna, dan siap digunakan sebagai basis sistem rekomendasi.

| Place_Id | Place_Ratings | Place_Name                        | Description                                       | Category      | Rating |
| -------- | ------------- | --------------------------------- | ------------------------------------------------- | ------------- | ------ |
| 1        | 3.722222      | Monumen Nasional                  | Monumen Nasional atau yang populer disingkat d... | Budaya        | 4.6    |
| 2        | 2.840000      | Kota Tua                          | Kota tua di Jakarta, yang juga bernama Kota Tu... | Budaya        | 4.6    |
| 3        | 2.526316      | Dunia Fantasi                     | Dunia Fantasi atau disebut juga Dufan adalah t... | Taman Hiburan | 4.6    |
| 4        | 2.857143      | Taman Mini Indonesia Indah (TMII) | Taman Mini Indonesia Indah merupakan suatu kaw... | Taman Hiburan | 4.5    |
| 5        | 3.520000      | Atlantis Water Adventure          | Atlantis Water Adventure atau dikenal dengan A... | Taman Hiburan | 4.5    |

Tabel 2c. Dataset hasil penggabungan `df_ratings` dan `df_tourism_cleaned` berdasarkan `Place_Id`

### 2.4. Preprocessing Text

Pada tahap ini, dilakukan proses pra-pemrosesan terhadap data teks yang terdapat pada dataset destinasi wisata. Langkah ini sangat penting dalam sistem rekomendasi berbasis konten (content-based recommendation system), karena kualitas representasi teks secara langsung mempengaruhi hasil rekomendasi yang diberikan. Tujuan dari preprocessing ini adalah untuk mengurangi kebisingan (noise), menyederhanakan bentuk kata, dan memperkaya konteks antar fitur sehingga informasi yang diperoleh oleh model menjadi lebih relevan dan bermakna.

Langkah-Langkah Preprocessing:

- **Penggabungan Informasi Deskripsi dan Kategori**

  Langkah pertama yang dilakukan adalah menggabungkan informasi dari kolom `Description` dan `Category` ke dalam satu kolom baru bernama `Tags`. Hal ini dilakukan untuk memperkaya konteks dari tiap destinasi wisata. Kolom `Description` memberikan gambaran tentang tempat tersebut, sedangkan kolom `Category` memberi tahu klasifikasinya, seperti budaya, taman hiburan, sejarah, dan sebagainya.

- **Normalisasi Teks**

  Setelah digabungkan, seluruh teks pada kolom Tags diubah menjadi huruf kecil (lowercase) agar formatnya seragam dan tidak ada perbedaan yang disebabkan oleh kapitalisasi huruf.

- **Stemming dan Stopword Removal Menggunakan Sastrawi**

  Untuk menangani kata-kata dalam Bahasa Indonesia, digunakan pustaka Sastrawi yang menyediakan dua fungsi utama:

  - `Stemming`: Mengubah kata menjadi bentuk dasarnya. Contohnya, kata “berkunjung”, “mengunjungi”, dan “kunjungan” akan diubah menjadi “kunjung”.
  - `Stopword Removal`: Menghapus kata-kata umum yang tidak memberikan makna signifikan terhadap konteks, seperti “yang”, “di”, dan “dan”.

- **Penerapan Fungsi Preprocessing**

  Seluruh proses tersebut dikemas dalam sebuah fungsi preprocessing(text) yang akan mengubah teks menjadi huruf kecil, melakukan stemming, dan menghapus stopword. Fungsi ini diterapkan pada kolom `Tags` serta pada kolom Description secara terpisah.

  Penerapan pada kolom `Tags` digunakan untuk membentuk representasi teks gabungan yang akan digunakan sebagai input utama dalam model rekomendasi. Sementara itu, preprocessing pada kolom Description saja dilakukan untuk keperluan eksperimen pembandingan performa antara representasi gabungan (deskripsi + kategori) dan deskripsi saja.

- **Menyimpan Dataset Hasil Preprocessing**

  Karena proses preprocessing ini cukup memakan waktu, dataset hasil akhir disimpan dalam sebuah file CSV bernama `data_recommendation_preprocessed.csv`. Dengan cara ini, proses eksperimen selanjutnya dapat dilakukan tanpa perlu mengulangi tahap preprocessing dari awal.

<br>

## 🤖 3. Modeling and Result

Pada tahap ini, dua pendekatan sistem rekomendasi yang berbeda dikembangkan, yaitu Content-Based Filtering dan Collaborative Filtering. Masing-masing pendekatan memiliki metode tersendiri dalam menganalisis data dan memberikan rekomendasi destinasi wisata yang sesuai dengan preferensi pengguna.

### 3.1. Model Development - Content Based Filtering

Dalam pendekatan Content-Based Filtering, model dikembangkan berdasarkan informasi yang melekat pada setiap destinasi, seperti deskripsi dan kategori. Proses pembangunan model dilakukan melalui beberapa tahapan utama berikut:

#### **a. Ekstraksi Fitur Teks dengan TF-IDF**

Dalam membangun sistem rekomendasi berbasis Content-Based Filtering, representasi numerik dari data teks menjadi kunci dalam mengidentifikasi kemiripan antar destinasi wisata. Salah satu teknik yang digunakan adalah `TF-IDF (Term Frequency–Inverse Document Frequency)`, yang memungkinkan pemetaan teks ke dalam bentuk vektor numerik berdasarkan pentingnya suatu kata dalam dokumen relatif terhadap seluruh korpus.

Deskripsi dan kategori destinasi digabungkan dan kemudian direpresentasikan dalam bentuk vektor numerik menggunakan TF-IDF, yang menekankan pentingnya kata-kata unik di setiap destinasi. Teknik ini diterapkan pada dua kolom berbeda:

- `Tags`: Gabungan antara deskripsi dan kategori.
- `Description_Preprocessed`: Deskripsi destinasi setelah melalui tahap praproses.

Untuk masing-masing kolom, dilakukan proses sebagai berikut:

- Inisialisasi `TfidfVectorizer` dengan parameter seperti `max_features=5000`, `ngram_range=(1,2)`, dan `min_df=2`.
- Fit dan transformasi teks menjadi matriks numerik.
- Visualisasi sebagian matriks TF-IDF untuk menganalisis kata-kata penting per destinasi.

Matriks TF-IDF yang dihasilkan kemudian digunakan sebagai dasar untuk mengukur kesamaan antar destinasi dan mendukung sistem rekomendasi berbasis konten.

#### **b. Perhitungan Kemiripan dengan Cosine Similarity**

Setelah data vektor diperoleh, tingkat kemiripan antar destinasi dihitung menggunakan `cosine similarity`. Nilai ini menunjukkan seberapa mirip suatu destinasi dengan destinasi lainnya berdasarkan konten teksnya.

- Kolom `Tags`

  Representasi teks dari kombinasi deskripsi dan kategori dihitung menggunakan `cosine_similarity` dari pustaka `sklearn.metrics.pairwise`. Hasilnya berupa matriks kesamaan yang menunjukkan nilai kemiripan antar setiap pasangan destinasi. Nilai yang semakin mendekati 1 menandakan bahwa dua destinasi memiliki konten yang sangat mirip.

  ```python
  similarity_tags = cosine_similarity(vectors_tags, dense_output=True)
  ```

  Sebagian hasil dari matriks kesamaan ditampilkan secara acak untuk keperluan eksplorasi dan validasi awal.

- Kolom `Description_Preprocessed`

  Proses yang sama diterapkan pada kolom yang hanya memuat deskripsi destinasi tanpa informasi kategori. Tujuannya adalah untuk mengevaluasi seberapa besar pengaruh deskripsi murni terhadap kemiripan antar destinasi.

  ```python
  similarity_desc = cosine_similarity(vectors_desc, dense_output=True)
  ```

#### **c. Mendapatkan Rekomendasi**

Setelah mendapatkan matriks kesamaan antar destinasi wisata, langkah selanjutnya adalah membangun `sistem rekomendasi berbasis konten (content-based recommendation system)`. Penulis mengembangkan sebuah fungsi bernama `get_content_based_recommendations` yang bertujuan untuk menghasilkan daftar destinasi wisata yang paling relevan atau mirip dengan destinasi yang dipilih pengguna.

Fungsi ini memiliki beberapa parameter penting, yaitu:

- `place_name`: Nama destinasi wisata yang dijadikan acuan pencarian rekomendasi.
- `data`: Dataset yang berisi informasi lengkap tentang destinasi wisata.
- `similarity_matrix`: Matriks kemiripan antar destinasi yang telah dihitung sebelumnya, menggunakan pendekatan seperti TF-IDF dan cosine similarity.
- `top_n`: Jumlah destinasi wisata yang ingin direkomendasikan, dengan nilai default sebanyak 10.

Rekomendasi diperoleh dengan cara mengurutkan skor kemiripan dari yang tertinggi dan mengabaikan destinasi itu sendiri dalam daftar hasil. Fungsi ini akan mengembalikan daftar `Place_Id` dari destinasi yang dianggap paling mirip dan layak direkomendasikan.

##### Implementasi Fungsi

Berikut implementasi fungsi `get_content_based_recommendations`:

```python
def get_content_based_recommendations(place_name, data, similarity_matrix, top_n=10):
    # Memastikan destinasi yang diminta ada dalam dataset
    if place_name not in data['Place_Name'].values:
        print(f"'{place_name}' tidak ditemukan dalam dataset.")
        return []

    # Mendapatkan indeks destinasi
    place_idx = data[data['Place_Name'] == place_name].index[0]

    # Mendapatkan skor similarity
    place_similarity = similarity_matrix[place_idx].flatten()

    # Mengurutkan skor secara menurun dan menghapus indeks dirinya sendiri
    similar_indices = place_similarity.argsort()[::-1]
    similar_indices = similar_indices[similar_indices != place_idx]

    # Mengambil top-n destinasi
    top_indices = similar_indices[:top_n]
    recommended_place_ids = data.iloc[top_indices]['Place_Id'].tolist()

    return recommended_place_ids
```

Fungsi tambahan `show_recommendations` digunakan untuk menampilkan hasil rekomendasi dalam bentuk tabel agar lebih informatif bagi pengguna:

```python
def show_recommendations(place_name, similarity_matrix, df_recommendation, df_tourism_cleaned, source_label=""):
    recommended_place_ids = get_content_based_recommendations(
        place_name=place_name,
        data=df_recommendation,
        similarity_matrix=similarity_matrix,
        top_n=10
    )

    # Menyaring dan menampilkan hasil
    recommended_destinations = df_tourism_cleaned[
        df_tourism_cleaned['Place_Id'].isin(recommended_place_ids)
    ][['Place_Name', 'Category', 'Rating', 'Description']].copy()

    recommended_destinations.reset_index(drop=True, inplace=True)
    recommended_destinations.index += 1
    recommended_destinations.index.name = 'No.'

    print(f"\nRekomendasi destinasi wisata untuk '{place_name}' berdasarkan {source_label}:\n")
    display(recommended_destinations)
```

##### Hasil Rekomendasi

Sebagai studi kasus, destinasi **Wisata Alam Kalibiru** digunakan sebagai acuan untuk pencarian destinasi lain yang mirip. Hasil rekomendasi disajikan berdasarkan dua pendekatan:

- Berdasarkan kolom `Tags`: Menggabungkan informasi deskripsi dan kategori.
- Berdasarkan kolom `Description_Preprocessed`: Hanya menggunakan teks deskripsi yang telah diproses.

Berikut hasil rekomendasi:

- Rekomendasi Berdasarkan `Tags`

  | No. | Place_Name                        | Category      | Rating | Description                                       |
  | --- | --------------------------------- | ------------- | ------ | ------------------------------------------------- |
  | 1   | Watu Lumbung                      | Cagar Alam    | 4.3    | Letak Kampung Edukasi Watu Lumbung yang berada... |
  | 2   | Wisata Kaliurang                  | Cagar Alam    | 4.4    | Jogja selalu menarik untuk dikulik, terlebih t... |
  | 3   | Ciwangun Indah Camp Official      | Cagar Alam    | 4.3    | Ciwangun Indah Camp atau CIC adalah sebuah tem... |
  | 4   | Curug Cilengkrang                 | Cagar Alam    | 4.0    | Curug Cilengkrang bisa menjadi pilihan tujuan ... |
  | 5   | Happyfarm Ciwidey                 | Cagar Alam    | 4.2    | Objek wisata alam dan edukasi tengah banyak me... |
  | 6   | Hutan Wisata Tinjomoyo Semarang   | Cagar Alam    | 4.3    | Awalnya taman wisata hutan Tinjomoyo Semarang ... |
  | 7   | Umbul Sidomukti                   | Cagar Alam    | 4.6    | Kawasan wisata umbul Sidomukti merupakan salah... |
  | 8   | Wisata Alam Wana Wisata Penggaron | Cagar Alam    | 4.1    | Berada sekitar 2 KM dari Kota Ungaran atau sek... |
  | 9   | Kampoeng Kopi Banaran             | Taman Hiburan | 4.3    | Kampoeng Kopi Banaran, sebuah agro wisata perk... |
  | 10  | Air Terjun Semirang               | Cagar Alam    | 4.4    | Terletak di lereng Gunung Ungaran bagian utara... |

  Tabel 3a. Hasil Rekomendasi Berdasarkan `Tags`

- Rekomendasi Berdasarkan `Description`

  | No. | Place_Name                        | Category      | Rating | Description                                       |
  | --- | --------------------------------- | ------------- | ------ | ------------------------------------------------- |
  | 1   | Watu Lumbung                      | Cagar Alam    | 4.3    | Letak Kampung Edukasi Watu Lumbung yang berada... |
  | 2   | Wisata Kaliurang                  | Cagar Alam    | 4.4    | Jogja selalu menarik untuk dikulik, terlebih t... |
  | 3   | Ciwangun Indah Camp Official      | Cagar Alam    | 4.3    | Ciwangun Indah Camp atau CIC adalah sebuah tem... |
  | 4   | Curug Cilengkrang                 | Cagar Alam    | 4.0    | Curug Cilengkrang bisa menjadi pilihan tujuan ... |
  | 5   | Happyfarm Ciwidey                 | Cagar Alam    | 4.2    | Objek wisata alam dan edukasi tengah banyak me... |
  | 6   | Desa Wisata Lembah Kalipancur     | Taman Hiburan | 3.9    | Wisata alam tengah menjadi sorotan bagi dunia ... |
  | 7   | Hutan Wisata Tinjomoyo Semarang   | Cagar Alam    | 4.3    | Awalnya taman wisata hutan Tinjomoyo Semarang ... |
  | 8   | Wisata Alam Wana Wisata Penggaron | Cagar Alam    | 4.1    | Berada sekitar 2 KM dari Kota Ungaran atau sek... |
  | 9   | Kampoeng Kopi Banaran             | Taman Hiburan | 4.3    | Kampoeng Kopi Banaran, sebuah agro wisata perk... |
  | 10  | Air Terjun Semirang               | Cagar Alam    | 4.4    | Terletak di lereng Gunung Ungaran bagian utara... |

  Tabel 3b. Hasil Rekomendasi Berdasarkan `Description_Preprocessed`

Hasil tersebut menunjukkan bahwa sistem berhasil mengidentifikasi destinasi yang memiliki karakteristik serupa, baik dari sisi deskripsi maupun kategori, sehingga dapat membantu pengguna menemukan tempat wisata alternatif yang relevan dengan preferensinya.

### 3.2. Model Development - Content Based Filtering

Pada tahap ini, dilakukan beberapa proses awal untuk menyiapkan data sebelum dimodelkan menggunakan metode Collaborative Filtering. Data yang digunakan adalah data rating pengguna terhadap tempat wisata, yang terdiri atas tiga kolom utama: `User_Id`, `Place_Id`, dan `Rating`. Berikut adalah tahapan persiapan data yang dilakukan:

a. Mengambil Daftar User dan Place Unik

    Langkah pertama adalah memperoleh daftar unik dari pengguna (user) dan tempat (place) yang terdapat dalam data rating. Hal ini penting karena dalam Collaborative Filtering, kita perlu merepresentasikan pengguna dan tempat sebagai indeks integer untuk keperluan pelatihan model.

    ```python
    user_ids = df_ratings['User_Id'].unique().tolist()
    place_ids = df_ratings['Place_Id'].unique().tolist()

    print('list User_Id: ', user_ids)
    print('list Place_Id: ', place_ids)
    ```

    Output dari perintah ini akan menghasilkan dua buah list yang berisi seluruh `User_Id` dan `Place_Id` unik dalam dataset. Hasil ini akan digunakan untuk melakukan encoding pada langkah berikutnya.

    b. Melakukan Encoding pada `User_Id` dan `Place_Id`

      Karena algoritma pembelajaran mesin tidak dapat langsung bekerja dengan data kategori dalam bentuk string atau integer tidak berurut, maka dilakukan proses encoding. Encoding ini bertujuan untuk mengubah `User_Id` dan `Place_Id` menjadi indeks integer yang berurutan dimulai dari 0. Proses ini menggunakan dictionary untuk memetakan nilai asli ke nilai yang sudah diencode, serta dictionary sebaliknya untuk keperluan decoding hasil prediksi nantinya.

      ```python
      # Melakukan encoding pada User_Id
      user_to_user_encoded = {user_id: idx for idx, user_id in enumerate(user_ids)}
      user_encoded_to_user = {idx: user_id for idx, user_id in enumerate(user_ids)}

      # Melakukan encoding pada Place_Id
      place_to_place_encoded = {place_id: idx for idx, place_id in enumerate(place_ids)}
      place_encoded_to_place = {idx: place_id for idx, place_id in enumerate(place_ids)}

      # Menampilkan hasil encoding
      print('encoded angka ke User_Id: ', user_encoded_to_user)
      print('encoded angka ke Place_Id: ', place_encoded_to_place)
      ```

      Dengan encoding ini, setiap `User_Id` dan `Place_Id` telah dikonversi ke format numerik. Sebagai contoh, `User_Id` bernilai 1 mungkin di-encode menjadi 0, `User_Id` bernilai 2 menjadi 1, dan seterusnya. Proses ini menjadikan data lebih siap untuk dimasukkan ke dalam model pembelajaran mesin, khususnya model berbasis embedding yang umum digunakan dalam sistem rekomendasi.

    c. Transformasi Data Rating

      Selanjutnya, data rating asli akan ditransformasikan menjadi bentuk baru yang menggunakan nilai hasil encoding. Langkah ini akan menghasilkan dataset baru dengan kolom `user`, `place`, dan `rating`, di mana `user` dan `place` sudah dalam bentuk integer hasil encoding.

      ```python
      # Transformasi nilai User_Id dan Place_Id ke bentuk encoded
      df_ratings['user'] = df_ratings['User_Id'].map(user_to_user_encoded)
      df_ratings['place'] = df_ratings['Place_Id'].map(place_to_place_encoded)

      # Menyusun dataframe baru dengan kolom yang sudah diencoding
      df_encoded = df_ratings[['user', 'place', 'Rating']]

      # Menampilkan data hasil encoding
      df_encoded.head()
      ```

      Dengan hasil ini, dataframe `df_encoded` siap digunakan sebagai input untuk membangun model Collaborative Filtering. Kolom `user` dan `place` akan digunakan sebagai input ke model, sedangkan `Rating` akan menjadi target yang diprediksi.

<br>

## 📊 4. Evaluation

<br>

## 📩 5. Kesimpulan

Luaran dari proyek ini adalah sebuah sistem rekomendasi destinasi wisata yang dikembangkan dengan dua pendekatan utama, yaitu Content-Based Filtering dan Collaborative Filtering.

Pada pendekatan Content-Based Filtering, sistem memberikan rekomendasi berdasarkan kemiripan konten seperti `tags` dan `description` dari destinasi wisata. Contohnya, untuk tempat wisata `"Wisata Alam Kalibiru"`, sistem berhasil merekomendasikan destinasi-destinasi lain yang memiliki karakteristik serupa baik dari sisi kategori maupun deskripsinya. Evaluasi menggunakan metrik Precision@10 menunjukkan hasil yang sangat baik, dengan `nilai 100% pada kasus uji "Museum Perangko"`, yang berarti `seluruh 10 rekomendasi yang diberikan relevan`.

Sementara itu, pendekatan Collaborative Filtering digunakan untuk `merekomendasikan wisata yang belum pernah dikunjungi oleh pengguna`, dengan memperhitungkan `pola rating dari pengguna lain yang memiliki preferensi serupa`. Evaluasi performa dilakukan menggunakan metrik Root Mean Squared Error (RMSE) dan Mean Absolute Error (MAE). Model Collaborative Filtering yang dibangun menghasilkan `RMSE sebesar 0.3642` dan `MAE sebesar 0.3145`, yang menunjukkan `tingkat kesalahan prediksi rating yang relatif rendah`, serta `potensi model dalam menghasilkan rekomendasi yang akurat` berdasarkan data perilaku pengguna.

Dengan demikian, kedua pendekatan yang diterapkan dalam proyek ini telah mampu membangun sistem rekomendasi yang efektif:

- Content-Based Filtering sangat akurat dalam menyarankan destinasi serupa berdasarkan konten,
- Collaborative Filtering memberikan rekomendasi personalisasi yang relevan dengan mempertimbangkan pola preferensi pengguna secara kolektif.

<br>

## 📚 6. Referensi

- Cholil, S. R., Rizki, N. A., & Hanifah, T. F. (2023). Sistem rekomendasi tempat wisata di Kota Semarang menggunakan metode collaborative filtering. JIKO (Jurnal Informatika dan Komputer), 7(1). [LINK](http://dx.doi.org/10.26798/jiko.v7i1.727)
- Goel, S., & Rizvi, S. W. A. (2024). Travel recommendation system using content and collaborative filtering. Journal of Mechanical and Construction Engineering (JMCE), 4(2), 1–8. [LINK](https://doi.org/10.54060/a2zjournals.jmce.63)
- Syakura, Z. I. (2024). Sistem rekomendasi destinasi wisata di Kota Surabaya menggunakan metode content based filtering dan neural collaborative filtering. Institut Teknologi Sepuluh Nopember Repository. [LINK](http://repository.its.ac.id/id/eprint/114885)
- Yulianto, A., Hadi, W., & Yulianto, Y. (2023). Analisis preferensi wisatawan terhadap pilihan berwisata di Sendang Sombomerti Depok Sleman Yogyakarta. Journal of Tourism and Economic, 6(2), 143-152. [LINK](https://doi.org/10.36594/jtec/tq2fkg11)
