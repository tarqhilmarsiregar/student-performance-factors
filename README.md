# Laporan Proyek Machine Learning - Tarq Hilmar Siregar

## Domain Proyek

Pendidikan merupakan fondasi utama dalam membentuk masa depan generasi muda. Namun, tidak semua siswa mampu mencapai performa akademik yang optimal. Banyak faktor yang dapat memengaruhi pencapaian belajar siswa, seperti tingkat kehadiran, jam belajar, dukungan dari orang tua, hingga akses terhadap sumber daya pembelajaran. Kurangnya pemantauan dan intervensi dini dapat menyebabkan siswa berisiko mengalami ketertinggalan dalam proses belajar, yang pada akhirnya berdampak pada prestasi akademik mereka.

Untuk mengatasi tantangan ini, teknologi machine learning memberikan solusi yang menjanjikan. Dengan memanfaatkan data historis seperti jumlah jam belajar, kehadiran, tingkat keterlibatan orang tua, serta skor ujian sebelumnya, model prediktif dapat digunakan untuk mengidentifikasi siswa yang berpotensi mengalami kesulitan. Pendekatan ini memungkinkan pendidik melakukan intervensi secara lebih tepat dan cepat sebelum masalah menjadi lebih serius.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Mengidentifikasi dini siswa berisiko: Memprediksi performa akademik memungkinkan pendidik untuk mengenali siswa yang mungkin mengalami kesulitan belajar sebelum masalah tersebut menjadi serius dengan mengumpulkan data relevan seperti kehadiran, keterlibatan orang tua, akses ke sumber daya, jam belajar dan skor ujian sebelumnya. Kemudian, untuk menyelesaikan permasalahan tersebut, menurut studi oleh Orji dan Vassileva (2022), model machine learning dapat mencapai akurasi hingga 94,9% dalam memprediksi performa siswa, memungkinkan intervensi yang lebih efektif.
- Orji, F. A., & Vassileva, J. (2022). Machine learning approach for predicting students academic performance and study strategies based on their motivation. arXiv preprint arXiv:2210.08186.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana kita dapat memprediksi skor ujian akhir siswa berdasarkan faktor-faktor personal, sosial, dan akademik?
- Faktor-faktor apa yang paling berpengaruh terhadap performa ujian akhir siswa?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Membangun model regresi yang mampu memprediksi skor akhir siswa (Exam_Score) untuk mendukung intervensi pendidikan lebih awal
- Menggunakan model ML (seperti Random Forest) untuk menilai feature importance

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Menggunakan algoritma Random Forest dan K-Nearest Neighbour untuk membangun model dasar. Kemudian, membandingkan kinerja model berdasarkan metrik evaluasi seperti MSE dan MAE
    - Menerapkan teknik Encoding Fitur Kategori seperti Low, Medium, High

## Data Understanding
Proyek ini menggunakan dataset berjudul **Student Performance Factors** yang tersedia secara publik di platform [Kaggle](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors). Dataset ini berisi data siswa dengan berbagai faktor yang dapat memengaruhi performa akademik mereka, seperti jumlah jam belajar, tingkat kehadiran, keterlibatan orang tua, akses terhadap sumber daya pembelajaran, serta skor ujian.

Detail Dataset:
- Jumlah Data (Baris): 6.607 entri
- Jumlah Fitur (Kolom): 20 fitur input
- Target Prediksi: Exam_Score (Skor ujian)
- Format File: CSV (.csv)

Kondisi Data:
- Terdapat fitur dengan tipe kategorikal dan numerik
- Beberapa fitur perlu dilakukan encoding (seperti Parental_Involvement, dll)
- Distribusi nilai numerik cukup bervariasi, sehingga perlu pertimbangan normalisasi/standarisasi, terutama untuk algoritma berbasis jarak seperti KNN
- Terdapat missing value seperti pada kolom **Teacher_Quality**, **Parental_Education_Level**
- Terdapat Outlier seperti pada kolom **Hours_Studied** namun hal ini tidak menjadi permasalahan yang serius dikarenakan bisa saja hal tersebut benar benar terjadi pada students
- Pada dataset ini tidak ditemukan adanya data duplikat

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Student Performance Factors dataset adalah sebagai berikut:
- Hours_Studied: Jumlah jam yang dihabiskan untuk belajar per minggu
- Attendance: Persentase kelas yang dihadiri
- Parental_Involvement: Tingkat keterlibatan orang tua dalam pendidikan siswa (Rendah, Sedang, Tinggi)
- Access_to_Resources: Ketersediaan sumber daya pendidikan (Rendah, Sedang, Tinggi)
- Extracurricular_Activities: Partisipasi dalam kegiatan ekstrakurikuler (Ya, Tidak)
- Sleep_Hours: Jumlah rata-rata jam tidur per malam
- Previous_Scores: Skor dari ujian sebelumnya
- Motivation_Level: Tingkat motivasi siswa (Rendah, Sedang, Tinggi)
- Internet_Access: Ketersediaan akses internet (Ya, Tidak)
- Tutoring_Sessions: Jumlah sesi les yang dihadiri per bulan
- Family_Income: Tingkat pendapatan keluarga (Rendah, Sedang, Tinggi)
- Teacher_Quality: Kualitas guru (Rendah, Sedang, Tinggi)
- School_Type: Jenis sekolah yang dihadiri (Publik, Swasta)
- Peer_Influence: Pengaruh teman sebaya pada kinerja akademik (Positif, Netral, Negatif)
- Physical_Activity: Jumlah rata-rata jam aktivitas fisik per minggu
- Learning_Disabilities: Kehadiran ketidakmampuan belajar (Ya, Tidak)
- Parental_Education_Level: Tingkat pendidikan orang tua tertinggi (Sekolah Menengah, Perguruan Tinggi, Pascasarjana)
- Distance_from_Home: Jarak dari rumah ke sekolah (Dekat, Sedang, Jauh)
- Gender: Jenis kelamin siswa (Pria, Wanita)
- Exam_Score: Skor ujian akhir -> Target

**Rubrik/Kriteria Tambahan (Opsional)**:
1. Deskripsi Variabel <br>
   ![eda-deskripsi-variabel](https://github.com/user-attachments/assets/314350c1-5d96-40e2-9b5a-10dc14b94e9f)

2. Memeriksa Missing Value <br>
   ![eda-missing-value](https://github.com/user-attachments/assets/bbedd64d-d059-4298-9a11-2487b56993e4)

3. Mendeteksi Outlier <br>
   ![eda-outlier](https://github.com/user-attachments/assets/709f5a8b-1055-450a-b468-0ce557041f02)

4. Univariate Analysis (Numerical & Categorical) <br>
   ![eda-univariate-numerical](https://github.com/user-attachments/assets/7079414f-4e24-4616-bd23-c00143a1efa7) <br>
   ![eda-univariate-categorical](https://github.com/user-attachments/assets/042d2a4f-b83e-4803-b6ad-7ee8f6d58e9e)

5. Multivariate Analysis (Numerical & Categorical) <br>
   ![eda-multivariate-numerical](https://github.com/user-attachments/assets/91377e86-eb72-4534-8243-a0d011ebf716) <br>
   ![eda-multivariate-categorical](https://github.com/user-attachments/assets/02f78d29-1ba7-4630-afdb-7a7203fbc016)

6. Correlation Matrix <br>
   ![corr_matrix](https://github.com/user-attachments/assets/4a68597a-0ba0-4203-98d8-f03f7f92de29)

7. Drop Kolom Numerik yang Tidak Memiliki Korelasi atau dengan Korelasi Rendah mendekati 0 <br>
   ![drop-kolom-dengan-korelasi-rendah-dan-tidak-ada-korelasi](https://github.com/user-attachments/assets/6b45bb5a-2656-478d-b349-ad631eadb454)

## Data Preparation
Sebelum membangun model machine learning, dilakukan beberapa tahap persiapan data untuk memastikan bahwa data dalam kondisi optimal untuk dilatih dan diuji oleh algoritma. Hal hal lain seperti **menghapus data dengan missing value** telah dianalisis dan dilakukan pada tahapan EDA, kemudian pemilihan fitur yang relevan tersebut telah dilakukan pada tahapan EDA juga melalui **correlation matrix** sehingga dari fitur numerik yang ada menjadi tahu mana yang memiliki korelasi baik dengan **variabel target**. Berikut teknik-teknik data preparation yang digunakan secara berurutan seperti **One Hot Encoding**, **Train-Test Split**, dan **Standarisasi (Standardization)**

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Pada tahapan data preparation ini, saya menggunakan teknik **one-hot-encoding** untuk melakukan encoding fitur kategori dikarenakan hal ini penting dilakukan mengingat bahwa model machine learning hanya akan memproses data dengan tipe data numerik
- Di tahapan **train-test-split** ini saya membagi dataset dengan proporsi 90:10 agar data uji tidak diambil banyak dari data latih
- Kemudian, saya melakukan standarisasi fitur numerik seperti **Hours_Studied** dan **Attendance** menggunakan **StandardScaler** untuk membuat rentang nilai menjadi mean 0 dan standar deviasi 1, mengingat pada projek ini saya akan menggunakan algoritma Random Forest dan KNN. Pada standarisasi ini pula saya hanya menerapkan pada data latih saja dikarenakan untuk menghindari kebocoran informasi pada data uji

## Modeling
Untuk menyelesaikan permasalahan prediksi skor ujian siswa, dilakukan beberapa tahapan pemodelan machine learning secara sistematis. Dua algoritma digunakan: Random Forest Regressor dan K-Nearest Neighbors Regressor (KNN). Berikut penjelasan tiap tahapan dan parameter yang digunakan:

1. Random Forest Regressor: Algoritma ensemble berbasis banyak pohon keputusan (decision tree)<br>
    Parameter yang digunakan:
    - n_estimators = 50: Ini berarti model akan membangun 50 pohon keputusan (decision trees), semakin banyak pohon, umumnya hasil prediksi jadi lebih stabil, tapi waktu komputasi juga meningkat. Angka 50 adalah jumlah yang relatif seimbang antara performa dan efisiensi komputasi.
    - max_depth=16: Membatasi kedalaman maksimum tiap pohon sampai 16 level. Tujuannya adalah menghindari overfitting, karena pohon yang terlalu dalam bisa terlalu menyesuaikan data latih. Depth 16 cukup dalam untuk mempelajari pola, namun tetap menjaga generalisasi.
    - random_state=55: Digunakan untuk menetapkan seed agar hasil eksperimen konsisten setiap kali dijalankan. Tidak memengaruhi performa, tapi penting untuk reproduktibilitas.
    - n_jobs=-1: Artinya model akan menggunakan seluruh core CPU yang tersedia secara paralel saat melatih model. Ini akan mempercepat proses pelatihan, terutama pada dataset besar.
<br>
    Model dilatih menggunakan data yang telah melalui one-hot encoding (tanpa standarisasi karena Random Forest tidak sensitif terhadap skala).

2. K-Nearest Neighbors Regressor<br>
    Parameter yang digunakan:
    - n_neighbors=10: Ini berarti model KNN akan menggunakan 10 tetangga terdekat untuk memprediksi nilai target (exam score). Skor prediksi dihitung sebagai rata-rata dari nilai target ke-10 data yang paling mirip (terdekat) dengan data uji. Nilai 10 dipilih untuk mencoba mencapai keseimbangan antara bias dan variansi:
        - Jika terlalu kecil (misal 1), model bisa terlalu sensitif terhadap noise.
        - Jika terlalu besar, model bisa jadi terlalu "rata" dan kehilangan detail penting.
<br>
    Fitur harus distandarisasi sebelum pelatihan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Kelebihan algoritma Random Forest yakni akurasi tinggi karena menggunakan banyak decision tree sehingga hasil prediksi lebih stabil. Kekurangan nya yakni lebih lambat untuk prediksi karena menggunakan banyak pohon yang harus dievaluasi
- Kelebihan algoritma KNN yakni sederhana dan mudah dipahami serta diimplementasikan, namun kekurangan nya adalah sensitif terhadap skala data maka dari itu harus distandarisasi terlebih dulu. 
- Berdasarkan gambar di bawah ini, terlihat bahwa model Random Forest (RF) memberikan nilai error yang paling kecil. Sedangkan model dengan algoritma KNN memiliki error yang paling besar (berdasrkan grafik, angkanya di atas 0.006). Sehingga model Random Forest (RF) yang akan saya pilih sebagai model terbaik untuk melakukan prediksi **Exam_Score** <br>
  ![rf-vs-knn](https://github.com/user-attachments/assets/dc6a9049-d204-4c14-ba61-17819eff242f)

## Evaluation
Saya memilih kasus regresi dan menggunakan metrik MAE (Mean Absolute Error) dan MSE (Mean Squared Error)

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penggunaan metrik MSE untuk memberikan penalti lebih besar pada kesalahan yang jauh sehingga dapat membantu model lebih peka terhadap prediksi yang jauh melesat. Pada kasus ini, hasil metrik MSE yang didapatkan pada data train dan test dapat dilihat pada gambar di bawah ini. <br>
  ![hasil-metrik-mse-submission1-mlt](https://github.com/user-attachments/assets/3bc163f7-9fdd-401a-b243-cd0024624786)

- Penggunaan metrik MAE untuk menghitung rata rata dari selisih absolut antara nilai prediksi dengan nilai sebenarnya sehingga hasilnya lebih mudah dipahami, hasil metrik MAE yang didapatkan pada kasus proyek ini dapat dilihat pada gambar di bawah ini. <br>
  ![hasil-metrik-mae-submission1-mlt](https://github.com/user-attachments/assets/751ceee5-96a1-4abc-9c71-4f326836a559)

- Dalam kasus prediksi nilai **Exam_Score**, model Random Forest (RF) dan KNN menunjukkan performa yang cukup baik dengan prediksi yang mendekati nilai aktual. Namun, jika dibandingkan berdasarkan dua metrik evaluasi, berikut penilaiannya: <br>
  ![hasil-prediksi-proyek](https://github.com/user-attachments/assets/e6a4ad29-196a-484e-a0c8-d03bb104e7e2) <br>
      - Random Forest memiliki nilai MAE dan MSE yang lebih kecil dibandingkan KNN, yang berarti prediksi dari Random Forest lebih akurat dan stabil. <br>
      - MAE Random Forest sebesar 0.2 menunjukkan bahwa rata-rata kesalahan prediksi hanya sekitar 0.2 poin dari nilai sebenarnya, sedangkan KNN meleset sekitar 0.4 poin. <br>
      - Dari sisi MSE, Random Forest juga lebih baik (0.04 vs 0.16), yang menunjukkan bahwa model ini kurang rentan terhadap kesalahan ekstrem.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- MAE (Mean Absolute Error) <br>
  ![mae](https://github.com/user-attachments/assets/b994ab4d-6943-420b-bd65-6af009568a8c) <br>
  Formula dari metrik ini digunakan untuk menghitung selisih absolut antara nilai aktual dengan nilai prediksi kemudian semua selisih nya dijumlahkan, lalu dirata ratakan

- MSE (Mean Squared Error) <br>
  ![mse](https://github.com/user-attachments/assets/b2d99ddd-c9b8-49c0-8355-d4cad4a3afcb) <br>
  Formula dari metrik ini digunakan untuk menghitung rata rata dari kuadrat selisih antara nilai aktual dengan nilai prediksi. Hal ini sama dengan MAE, namun hasilnya akan dikuadratkan. Karena, dikuadratkan maka kesalahan besar akan dihukum / penalti lebih keras

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

