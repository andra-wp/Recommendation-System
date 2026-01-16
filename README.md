# Laporan Proyek Machine Learning - Kadek Andra Wikanjaya Putra

## Project Overview

Perkembangan platform streaming musik digital seperti Spotify telah mengubah cara pengguna mengakses dan menikmati musik. Dengan jutaan lagu yang tersedia, pengguna dihadapkan pada kondisi information overload, di mana sulit untuk menemukan musik yang benar-benar sesuai dengan preferensi pribadi tanpa bantuan sistem cerdas. Oleh karena itu, sistem rekomendasi menjadi komponen krusial dalam meningkatkan pengalaman pengguna dengan menyajikan konten musik yang relevan, personal, dan kontekstual.

Spotify dikenal sebagai salah satu platform yang mengimplementasikan sistem rekomendasi berskala industri. Umumnya, sistem rekomendasi musik memanfaatkan pendekatan collaborative filtering, yang bekerja dengan menganalisis kesamaan perilaku antar pengguna. Meskipun metode ini efektif, collaborative filtering memiliki beberapa keterbatasan utama, seperti cold-start problem pada pengguna atau item baru serta ketergantungan tinggi pada data interaksi pengguna lain. Kondisi ini mendorong perlunya pendekatan alternatif yang lebih independen terhadap data pengguna lain.

Salah satu pendekatan yang banyak digunakan untuk mengatasi permasalahan tersebut adalah content-based filtering. Pendekatan ini merekomendasikan item berdasarkan kemiripan atribut konten dengan preferensi pengguna sebelumnya, tanpa bergantung pada data pengguna lain. Penelitian oleh Anthony et al. menunjukkan bahwa sistem rekomendasi musik berbasis content-based filtering dengan metode cosine similarity mampu menghasilkan tingkat kemiripan lagu hingga 80% dan kemiripan artis sebesar 50% dibandingkan rekomendasi Spotify, yang mengindikasikan bahwa pendekatan ini cukup efektif dalam menangkap karakteristik musik yang relevan dengan preferensi pengguna [1].

Dalam implementasinya, content-based filtering pada sistem rekomendasi musik memanfaatkan fitur-fitur audio dan metadata lagu, seperti energy, popularity, dan liveness, yang direpresentasikan dalam bentuk vektor numerik. Tingkat kemiripan antar lagu kemudian dihitung menggunakan cosine similarity, sehingga lagu-lagu dengan karakteristik serupa dapat direkomendasikan kepada pengguna. Pendekatan ini terbukti mampu menjaga konsistensi genre dan karakter musik yang disukai pengguna, sekaligus mengurangi ketergantungan terhadap data rating atau interaksi pengguna lain.

Pendekatan serupa juga banyak diterapkan pada domain lain, seperti sistem rekomendasi film. Penelitian oleh Shaikh dan Dani menegaskan bahwa kombinasi TF-IDF dan cosine similarity dalam content-based filtering mampu meningkatkan relevansi rekomendasi secara signifikan dengan menekankan pentingnya representasi fitur konten dan pengukuran kemiripan yang tepat [2]. Meskipun studi tersebut berfokus pada film, prinsip dasar yang digunakan bersifat domain-independent dan sangat relevan untuk diterapkan pada sistem rekomendasi musik, khususnya dalam pengolahan fitur deskriptif dan representasi vektor.

Berdasarkan hal tersebut, proyek ini berfokus pada perancangan dan analisis sistem rekomendasi musik Spotify berbasis content-based filtering dengan memanfaatkan fitur lagu dan metode cosine similarity. Pendekatan ini diharapkan mampu memberikan rekomendasi yang lebih personal, konsisten dengan preferensi pengguna, serta efektif dalam mengatasi permasalahan cold-start, sehingga dapat menjadi alternatif atau pelengkap terhadap sistem rekomendasi yang saat ini digunakan oleh Spotify.

Daftar Referensi (IEEE)

[1] J. T. Anthony, H. Lucky, G. E. Christian, D. Suhartono, and V. Evanlim, “The Utilization of Content Based Filtering for Spotify Music Recommendation,” Proc. International Conference on Informatics, Electrical and Electronics (ICIEE), IEEE, 2022.

[2] S. Shaikh and D. Dani, “Enhancing Movie Recommendation Systems through Demographic and Content-Based Filtering Using TF-IDF and Cosine Similarity,” Proc. International Conference on Artificial Intelligence and Quantum Computation-Based Sensor Application (ICAIQSA), IEEE, 2024.

## Business Understanding

Platform Spotify menyediakan koleksi lagu dalam jumlah yang sangat besar dengan beragam genre dan karakteristik musik. Kondisi ini membuat pengguna sering mengalami kesulitan dalam menemukan lagu yang sesuai dengan preferensi pribadi mereka secara efisien. Tanpa adanya sistem rekomendasi yang tepat, proses pencarian musik menjadi kurang optimal dan memakan waktu.

Untuk mengatasi permasalahan tersebut, diperlukan sistem rekomendasi yang mampu menyajikan musik secara personal berdasarkan karakteristik lagu yang telah didengarkan. Pendekatan content-based filtering memungkinkan sistem untuk menganalisis fitur konten musik, seperti karakteristik audio dan metadata lagu, seperti genre, artist dan sebagainya, serta kemudian mengukur tingkat kemiripan antar lagu. Dengan pendekatan ini, sistem dapat memberikan rekomendasi yang relevan dan konsisten dengan preferensi pengguna, sehingga meningkatkan kualitas pengalaman mendengarkan musik pada platform Spotify.

### Problem Statements
- Bagaimana merancang sistem rekomendasi musik Spotify berbasis content-based filtering yang mampu merepresentasikan preferensi pengguna berdasarkan karakteristik konten lagu?
- Bagaimana menentukan dan memanfaatkan fitur konten lagu yang relevan untuk meningkatkan kualitas rekomendasi musik?
- Bagaimana mengukur tingkat kemiripan antar lagu secara efektif dalam sistem rekomendasi musik berbasis konten?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- #### Membangun sistem rekomendasi musik Spotify berbasis content-based filtering  
  Tujuan ini berfokus pada perancangan dan implementasi sistem rekomendasi yang memanfaatkan karakteristik konten lagu sebagai dasar utama dalam memberikan rekomendasi. Sistem yang dibangun bertujuan untuk menganalisis kesamaan antara lagu yang telah didengarkan pengguna dengan lagu lain yang tersedia, sehingga rekomendasi yang dihasilkan bersifat personal dan sesuai dengan preferensi musik pengguna.
- #### Menentukan fitur konten lagu yang relevan dalam proses rekomendasi  
  Tujuan ini bertujuan untuk mengidentifikasi dan memilih fitur-fitur konten lagu yang paling representatif dalam menggambarkan karakteristik musik, seperti fitur audio dan metadata lagu. Pemilihan fitur yang tepat diharapkan dapat meningkatkan akurasi pengukuran kemiripan antar lagu dan menghasilkan rekomendasi yang lebih relevan.
- #### Mengevaluasi kinerja sistem rekomendasi yang dibangun  
  Tujuan ini bertujuan untuk menilai efektivitas sistem rekomendasi musik yang telah dikembangkan. Evaluasi dilakukan untuk mengetahui sejauh mana sistem mampu menghasilkan rekomendasi yang sesuai dengan preferensi pengguna, sehingga dapat digunakan sebagai dasar untuk menilai kualitas dan keandalan sistem rekomendasi berbasis content-based filtering.
### Solution statements
- #### Content-Based Filtering (Based on Audio & Metadata Features)
  Pendekatan utama yang digunakan adalah content-based filtering, di mana sistem rekomendasi dibangun berdasarkan karakteristik konten lagu. Sistem menganalisis fitur audio dan metadata lagu, kemudian menghitung tingkat kemiripan antar lagu untuk menghasilkan rekomendasi. Lagu yang memiliki kemiripan tertinggi dengan lagu yang telah dipilih atau disukai pengguna akan direkomendasikan. Pendekatan ini memungkinkan sistem memberikan rekomendasi yang personal dan relevan tanpa memerlukan data interaksi pengguna lain.
- #### Popularity-Based Recommendation  
  Pendekatan alternatif yang dapat digunakan adalah popularity-based recommendation. Pada pendekatan ini, sistem merekomendasikan lagu berdasarkan tingkat popularitas lagu secara global, seperti track popularity. Pendekatan ini tidak memerlukan data pengguna dan dapat berfungsi sebagai solusi dasar, khususnya ketika informasi preferensi pengguna terbatas atau belum tersedia. Meskipun tidak bersifat personal, pendekatan ini berguna sebagai pembanding terhadap sistem berbasis konten.

## Data Understanding
Dataset yang digunakan dalam penelitian ini terdiri dari `32.833 data` lagu Spotify dengan `23` atribut. Setiap data merepresentasikan satu lagu yang dilengkapi dengan informasi metadata, playlist, serta fitur audio. Secara umum, kondisi data berada dalam keadaan baik dengan jumlah missing values yang sangat minimal dan tidak signifikan. Fitur audio lagu berupa data numerik digunakan sebagai representasi konten lagu dalam sistem rekomendasi berbasis content-based filtering.

Link Dataset : [Spotify Songs](https://www.kaggle.com/datasets/joebeachcapital/30000-spotify-songs). 

Variabel-variabel pada Spotify Song dataset adalah sebagai berikut:
- `track_id` : Identitas unik untuk setiap lagu Spotify  
- `track_name` : Menyimpan nama atau judul lagu
- `track_artist` : Menyimpan nama artis atau musisi
- `track_popularity` : Menunjukkan tingkat popularitas lagu di Spotify
- `track_album_id` : Identitas unik album lagu
- `track_album_name` : Menyimpan nama album lagu
- `track_album_release_date` : Menyimpan informasi tanggal rilis album
- `playlist_name` : Menyimpan nama playlist tempat lagu berada
- `playlist_id` : Identitas unik playlist Spotify
- `playlist_genre` : Menunjukkan genre utama playlist
- `playlist_subgenre` : Menunjukkan subgenre playlist yang lebih spesifik
- `danceability` : Menggambarkan tingkat kesesuaian lagu untuk menari
- `energy` : Menunjukkan tingkat energi atau intensitas lagu
- `key` : Menyimpan informasi tangga nada utama lagu
- `loudness` : Menunjukkan tingkat kekerasan suara lagu dalam desibel
- `mode` : Menunjukkan modus musik lagu (mayor atau minor)
- `speechiness` : Mengukur tingkat elemen ucapan dalam lagu
- `acousticness` : Menunjukkan tingkat keakustikan lagu
- `instrumentalness` : Mengukur dominasi instrumen tanpa vokal
- `liveness` : Menunjukkan kemungkinan lagu direkam secara live
- `valence` : Menggambarkan tingkat emosi positif pada lagu
- `tempo` : Menunjukkan kecepatan lagu dalam BPM
- `duration_ms` : Menyimpan durasi lagu dalam milidetik

### Exploratory Data Analysis
- #### Memeriksa Dimensi Dataset
  Menggunakan `df.shape` untuk memeriksa jumlah baris dan kolom dataset  
  <img width="145" height="41" alt="image" src="https://github.com/user-attachments/assets/1c07b3d1-74c6-44b1-a4b6-f01b5297a636" />  
  Dataset menunjukkan ada 32833 Data dan 23 Kolom

- #### Melihat Nama Kolom
  Menampilkan semua nama kolom yang tersedia dalam dataset menggunakan `df.columns`
  <img width="905" height="205" alt="image" src="https://github.com/user-attachments/assets/ccec160f-6ed8-437a-bffa-caa1c75e24ee" />
  Menampilkan list nama kolom agar nanti nya berguna untuk mempermudah feature selection 

- #### Informasi Fitur dan Tipe Data
  Menggunakan fungsi info() untuk menampilkan:
  - Nama setiap kolom/fitur  
  - Tipe data setiap kolom  
  - Jumlah non-null values  
  - Penggunaan memori dataset
  - 
- #### Deteksi Missing Value
  Mengidentifikasi kolom yang memiliki nilai kosong (missing values) menggunakan
`isnull().sum()` dan memfilter hanya kolom dengan missing values > 0.  
  <img width="271" height="122" alt="image" src="https://github.com/user-attachments/assets/558b4c45-52da-452a-8750-c55cfede25d6" />  
  Pada dataset ini, terdapat 3 Kolom yang masing" memiliki 5 missing values


- #### Statistik Deskriptif
  Menggunakan fungsi `describe()` untuk menampilkan statistik deskriptif dari fitur numerik
  
- #### Distribusi Lagu per Genre
  <img width="1179" height="574" alt="image" src="https://github.com/user-attachments/assets/a35eddfe-a276-4b4f-901b-6ce3e97a79e8" />  
  Dataset memiliki 6 genre utama (pop, rap, rock, latin, R&B, dan EDM) dengan distribusi yang relatif seimbang. Tidak ada genre yang mendominasi secara signifikan, menunjukkan dataset yang cukup balanced. Kondisi ini menguntungkan untuk pengembangan sistem rekomendasi karena dapat mengurangi bias dan memastikan setiap genre memiliki representasi yang cukup untuk menghasilkan rekomendasi berkualitas. 
- #### Distribusi Lagu per Sub-Genre  
  <img width="1778" height="879" alt="image" src="https://github.com/user-attachments/assets/21946793-6385-421a-a4fe-bd90371a4a20" />  
Berbeda dengan genre utama, distribusi sub-genre menunjukkan variasi yang lebih tinggi dengan ketimpangan yang cukup signifikan. Beberapa sub-genre populer memiliki lebih dari 5000-6000 lagu, sementara sub-genre yang lebih spesifik atau niche hanya memiliki kurang dari 2000 lagu.

- #### Karakteristik Data Numerik  
  <img width="2144" height="363" alt="image" src="https://github.com/user-attachments/assets/bd9c2cb4-2fbb-4d40-b4b6-0dde29ac6482" />  

Dari statistik deskriptif, track popularity memiliki rata-rata 42.48 dengan standar deviasi 24.98, menunjukkan dataset mengandung campuran lagu populer dan tidak populer. Durasi lagu rata-rata 225.8 detik (≈3.76 menit) dengan sebagian besar lagu berdurasi normal, meskipun terdapat outlier dengan durasi sangat pendek (4 detik) hingga sangat panjang (8.63 menit).

- #### Korelasi Antar Fitur Numerik
  <img width="1226" height="976" alt="image" src="https://github.com/user-attachments/assets/b2faeaba-3838-4e7d-9501-6521340c2d10" />  

  - Korelasi Positif Kuat:

  Energy dan Loudness memiliki korelasi positif sangat kuat, menunjukkan lagu energik cenderung memiliki volume tinggi
Valence dan Danceability berkorelasi positif moderat, mengindikasikan lagu dengan mood ceria umumnya lebih cocok untuk menari

  - Korelasi Negatif Kuat:

  Energy dan Acousticness berkorelasi negatif kuat, lagu energik cenderung elektronik sedangkan lagu akustik lebih tenang
Loudness dan Acousticness juga berkorelasi negatif, lagu akustik umumnya memiliki volume lebih rendah

  - Fitur Independen:

  Tempo, Instrumentalness, dan Speechiness menunjukkan korelasi rendah dengan fitur lain, mengindikasikan mereka membawa informasi unik dan independen


## Data Preparation
Tahap ini menyiapkan data agar siap digunakan dalam pemodelan sistem rekomendasi. Proses diawali dengan data cleaning untuk menangani nilai kosong dan memastikan konsistensi data. Selanjutnya dilakukan pemilihan fitur dengan memilih fitur audio numerik dan atribut teks yang relevan dengan karakteristik lagu. Pada tahap preprocessing, fitur numerik dinormalisasi menggunakan Min-Max Scaling untuk menyamakan skala data, sedangkan fitur teks dibentuk dengan menggabungkan informasi artis, genre, dan subgenre. Setelah itu, dilakukan ekstraksi fitur teks menggunakan metode TF-IDF untuk mengubah data teks menjadi representasi numerik yang dapat digunakan dalam perhitungan kemiripan pada sistem rekomendasi berbasis content-based filtering.

### Proses Data Preparation :  
- #### Data Cleaning : 
  Tahap ini dilakukan untuk menangani nilai yang hilang _(missing values)_ pada dataset guna memastikan kualitas data tetap terjaga. Mengingat jumlah missing values pada dataset sangat sedikit, yaitu hanya 5 data, maka penanganan dilakukan dengan menghapus baris data yang memiliki nilai kosong menggunakan metode `df.dropna(inplace=True)`. 
- #### Feature Selection : 
  Tahap ini dilakukan untuk memilih fitur-fitur yang relevan dan berpengaruh dalam proses pembangunan sistem rekomendasi. Fitur numerik yang dipilih meliputi fitur audio lagu yang merepresentasikan karakteristik musik, sedangkan fitur teks dipilih dari atribut yang menggambarkan konteks lagu, seperti artis, genre, dan subgenre. Pemilihan fitur ini bertujuan untuk mengurangi kompleksitas data serta meningkatkan efektivitas sistem rekomendasi berbasis content-based filtering.
- #### Preprocessing :
  Tahap ini dilakukan untuk mempersiapkan data hasil seleksi fitur agar siap digunakan dalam pemodelan. Pada tahap ini, fitur numerik dinormalisasi menggunakan metode Min-Max Scaling untuk menyamakan skala nilai antar fitur sehingga tidak terjadi dominasi fitur tertentu. Selain itu, fitur teks dibentuk dengan menggabungkan informasi artis, genre, dan subgenre menjadi satu representasi konten lagu. Proses ini bertujuan untuk menghasilkan data yang terstandarisasi dan siap digunakan dalam sistem rekomendasi berbasis content-based filtering.
- #### Feature Extraction : 
  Tahap feature extraction dilakukan untuk mengubah fitur teks hasil preprocessing menjadi representasi numerik menggunakan metode TF-IDF (Term Frequency–Inverse Document Frequency). Fitur teks yang berisi gabungan informasi artis, genre, dan subgenre diekstraksi agar setiap lagu dapat direpresentasikan dalam bentuk vektor numerik yang mencerminkan karakteristik konten lagu. Proses ini bertujuan untuk menyediakan representasi data yang terstruktur sehingga sistem rekomendasi berbasis content-based filtering dapat menghitung tingkat kemiripan antar lagu secara objektif dan menghasilkan rekomendasi yang relevan.

### Hasil Data dari Tahap Data Preparation
<img width="1775" height="235" alt="image" src="https://github.com/user-attachments/assets/f6183d47-2432-4097-9c53-a1bb5f6f6099" />


## Modeling
- ### Content-Based Filtering
  Pada tahap content-based filtering, sistem rekomendasi dibangun dengan mengombinasikan fitur teks dan fitur numerik sebagai representasi akhir setiap lagu. Fitur teks diperoleh melalui ekstraksi TF-IDF, sedangkan fitur numerik berasal dari normalisasi atribut audio seperti danceability, energy, dan mood. Kedua jenis fitur ini digabungkan menggunakan metode horizontal stacking, sehingga terbentuk vektor fitur terpadu untuk setiap lagu. Representasi ini kemudian dikonversi ke dalam format Compressed Sparse Row (CSR) agar proses perhitungan menjadi lebih efisien, terutama untuk data berdimensi tinggi.

  Sistem menggunakan algoritma Nearest Neighbors dengan metrik cosine similarity dan metode pencarian brute force untuk menentukan lagu yang paling mirip. Proses rekomendasi dimulai dengan mencari indeks lagu acuan, kemudian menghitung jarak cosine antara lagu tersebut dengan seluruh lagu lainnya. Lagu-lagu dengan nilai cosine similarity tertinggi dipilih sebagai rekomendasi, dan hasilnya ditampilkan sesuai atribut yang dibutuhkan. Pendekatan ini memungkinkan sistem untuk memberikan rekomendasi berdasarkan kemiripan konten audio dan teks secara akurat.

- ### Popularity Based Recommendation
  Metode yang merekomendasikan lagu-lagu paling populer secara keseluruhan, tanpa mempertimbangkan kemiripan konten atau fitur audio. Popularitas lagu diukur berdasarkan fitur yang ada pada dataset yaitu `track_popularity`. 

- ### Hasil Top-N Recommendation
  #### Content Based Filtering
  <img width="869" height="171" alt="image" src="https://github.com/user-attachments/assets/7b41e43f-896a-4c2c-94eb-768f922d3b9a" />
  
  #### Popularity Based Recommendation
  <img width="747" height="239" alt="image" src="https://github.com/user-attachments/assets/344526df-e005-46d9-8921-0b6576b5ef53" />  

- ### Kelebihan dan Kekurangan
  - #### Content-Based Filtering : 
    ##### Kelebihan: 
    Sistem rekomendasi berbasis content-based filtering menekankan pada kemiripan konten audio dan teks, sehingga mampu memberikan rekomendasi yang sangat relevan dengan selera pengguna. Metode ini tidak bergantung pada interaksi pengguna lain, sehingga tetap efektif meskipun pengguna baru atau lagu baru dimasukkan ke dalam sistem. Selain itu, content-based filtering bersifat fleksibel karena dapat menggabungkan berbagai jenis fitur, seperti atribut audio, teks, dan metadata, sehingga representasi lagu menjadi lebih kaya dan akurat.

    ##### Kekurangan: 
    Meskipun relevan, metode ini cenderung terbatas pada lagu yang memiliki kemiripan dengan lagu yang sudah dikenal oleh pengguna, sehingga variasi rekomendasi dapat menjadi rendah. Selain itu, pendekatan ini memerlukan proses ekstraksi, normalisasi, dan representasi fitur yang akurat, yang bisa menjadi kompleks dan memerlukan waktu komputasi lebih tingg
  - #### Popularity Based Recommendation : 
    ##### Kelebihan: 
    Metode popularity-based recommendation sangat sederhana dan cepat, karena hanya menampilkan lagu-lagu yang paling populer berdasarkan track popularity. Pendekatan ini sangat efektif untuk memberikan rekomendasi awal bagi pengguna baru atau ketika data interaksi pengguna masih terbatas. Selain itu, rekomendasi berdasarkan popularitas cenderung meningkatkan kemungkinan pengguna menyukai lagu yang direkomendasikan, karena lagu populer biasanya diminati banyak orang, sehingga engagement pengguna bisa meningkat.

    ##### Kekurangan: 
    Popularity-based recommendation bersifat global dan tidak mempertimbangkan preferensi individu, sehingga relevansi terhadap selera spesifik pengguna menjadi rendah. Metode ini juga kurang fleksibel untuk merekomendasikan lagu-lagu baru, karena rekomendasi selalu didominasi oleh lagu populer, sehingga variasi konten menjadi terbatas.


## Evaluation

Dalam evaluasi sistem rekomendasi, beberapa metrik penting yang digunakan adalah **Precision@K**, **Recall@K**, dan **NDCG@K**. Metrik-metrik ini membantu mengukur seberapa baik sistem merekomendasikan lagu yang relevan dan sesuai preferensi pengguna.

---

### 1. Precision@K

**Definisi:** Precision@K mengukur proporsi item relevan di antara **top-K rekomendasi**. Artinya, dari K lagu yang direkomendasikan, berapa banyak yang benar-benar relevan dengan selera pengguna.

**Rumus:**

$$\text{Precision@K} = \frac{\text{Jumlah item relevan di top-K}}{K}$$

**Contoh:** Jika dari 5 lagu rekomendasi, 3 lagu relevan:

$$\text{Precision@5} = \frac{3}{5} = 0.6$$

---

### 2. Recall@K

**Definisi:** Recall@K mengukur proporsi item relevan yang berhasil direkomendasikan dibanding **total item relevan yang ada**.

**Rumus:**

$$\text{Recall@K} = \frac{\text{Jumlah item relevan di top-K}}{\text{Total item relevan}}$$



**Contoh:** Jika total lagu relevan = 7, dan 3 lagu muncul di top-5:

$$\text{Recall@5} = \frac{3}{7} \approx 0.429$$

---

### 3. NDCG@K (Normalized Discounted Cumulative Gain)

**Definisi:** NDCG@K mempertimbangkan **posisi ranking** dan **tingkat relevansi** (*graded relevance*). Item relevan yang muncul di posisi atas top-K dihargai lebih tinggi.

#### a. DCG@K (Discounted Cumulative Gain)

$$\text{DCG@K} = \sum_{i=1}^{K} \frac{2^{rel_i} - 1}{\log_2(i+1)}$$

* $rel_i$ = *graded relevance* item di posisi $i$

#### b. IDCG@K (Ideal DCG)

$$\text{IDCG@K} = \sum_{i=1}^{K} \frac{2^{rel_i^*} - 1}{\log_2(i+1)}$$

* $rel_i^*$ = *graded relevance* paling ideal (urut dari tertinggi ke terendah)



#### c. NDCG@K

$$\text{NDCG@K} = \frac{\text{DCG@K}}{\text{IDCG@K}}$$

**Contoh:** Top-5 rekomendasi dengan *graded relevance*: 2, 1, 2, 0, 1  
- DCG@5 $\approx$ 5.56  
- IDCG@5 (urut ideal: 2, 2, 1, 1, 0) $\approx$ 5.82

$$\text{NDCG@5} = \frac{5.56}{5.82} \approx 0.955$$

### Ringkasan Fungsi Metrik di Project

| Metrik       | Fungsi di project                                                                 |
|--------------|----------------------------------------------------------------------------------|
| Precision@K  | Mengukur akurasi top-K rekomendasi berdasarkan kesesuaian lagu dengan preferensi pengguna. |
| Recall@K     | Mengukur kemampuan sistem menemukan semua lagu relevan untuk pengguna.           |
| NDCG@K       | Menilai kualitas urutan rekomendasi, memberikan bobot lebih untuk lagu di posisi atas. |


### Hasil Metrik Evaluasi 
#### Content-Based Filtering  
<img width="881" height="202" alt="image" src="https://github.com/user-attachments/assets/2065f6a5-0cc5-486b-8075-892931bf8540" />  

#### Popularity Based Recommendation  
Metode ini merekomendasikan lagu-lagu paling populer berdasarkan play, likes, atau rating pengguna. Sistem ini bersifat global dan tidak personalisasi, sehingga tidak menggunakan metrik evaluasi seperti Precision@K, Recall@K, atau NDCG@K. Meskipun demikian, metode ini tetap berguna untuk menampilkan lagu-lagu populer dan memberikan rekomendasi awal bagi pengguna baru atau saat data interaksi terbatas.

