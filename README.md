# Analisis Faktor Penentu Performa Siswa: Prediksi Skor Ujian

Proyek ini menganalisis berbagai faktor demografis, sosial, dan perilaku siswa untuk **mengidentifikasi variabel-variaribel kunci yang memengaruhi performa akademik**. Implementasi dilakukan menggunakan **Google Colab** untuk analisis data dan pemodelan Machine Learning.

## Daftar Isi

- [Latar Belakang](#latar-belakang)
- [Tujuan Proyek](#tujuan-proyek)
- [Dataset](#dataset)
- [Metodologi](#metodologi)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Struktur Proyek](#struktur-proyek)
- [Cara Menjalankan Proyek](#cara-menjalankan-proyek)
- [Hasil dan Insight](#hasil-dan-insight)
- [Kesimpulan](#kesimpulan)
- [Lisensi](#lisensi)

## Latar Belakang

Memahami faktor-faktor yang berkontribusi pada performa akademik siswa adalah krusial bagi pendidik, orang tua, dan pembuat kebijakan. Proyek ini bertujuan untuk menggali hubungan antara karakteristik siswa dan nilai akhir mereka untuk mengidentifikasi area intervensi yang potensial.

## Tujuan Proyek

-   Melakukan **eksplorasi data (EDA)** untuk memahami distribusi dan hubungan antar variabel.
-   Mengidentifikasi **faktor-faktor dominan** yang paling berpengaruh terhadap nilai siswa.
-   Membangun **model Machine Learning** regresi untuk memprediksi performa siswa berdasarkan exam_score.
-   Menyajikan **insight** yang dapat ditindaklanjuti bagi pihak yang berkepentingan.

## Dataset

Dataset yang digunakan berasal dari [Kaggle](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors). Dataset ini berisi informasi demografi (gender), faktor keluarga (parental_involvement, family_income, parental_education_level), faktor sekolah (access_to_resources, internet_access, teacher_quality, school_type), dan perilaku (hours_studied, attendance, extracurricular_activities, sleep_hours, motivation_level, physical_activity), serta exam_score siswa.

* **Ukuran Data**: 6.607 baris, 20 kolom.
* **Kolom Kunci**: `Hours_Studied`, `Attendance`, `Parental_Involvement`, `Access_to_Resources`, `Extracurricular_Activities`, `Sleep_Hours`, `Previous_Scores`, `Motivation_Level`, `Internet_Access`, `Tutoring_Sessions`, `Family_Income`, `Teacher_Quality`, `School_Type`, `Peer_Influence`, `Physical_Activity`, `Learning_Disabilities`, `Parental_Education_Level`, `Distance_from_Home`, `Gender`, `Exam_Score` (Target)

## Metodologi

Proyek ini mengikuti tahapan analisis data dan Machine Learning berikut:

1.  **Pengumpulan Data**: Dataset di-*load* langsung ke Google Colab.
2.  **Pembersihan dan Pra-pemrosesan Data**: Penanganan *missing values*, *outliers*, normalisasi/standarisasi data, dan *encoding* variabel kategorikal.
3.  **Eksplorasi Data Analitis (EDA)**: Analisis statistik deskriptif, visualisasi distribusi variabel, dan korelasi antar fitur.
4.  **Pemilihan Fitur (Feature Selection/Engineering)**: Identifikasi fitur paling relevan yang memengaruhi nilai siswa.
5.  **Pemodelan Machine Learning**:
    * **Jenis Model**: Random Forest Regressor dan K-Nearest Neighbors Regressor
    * **Evaluasi Model**: Metrik MAE (Mean Absolute Error) dan MSE (Mean Squared Error)
6.  **Interpretasi Model dan Insight**: Menganalisis *feature importance* dari model untuk menarik kesimpulan yang berarti.

## Teknologi yang Digunakan

-   **Platform**: Google Colab
-   **Bahasa Pemrograman**: Python
-   **Library Python**:
    -   `pandas`: Untuk manipulasi dan analisis data.
    -   `numpy`: Untuk operasi numerik.
    -   `matplotlib` & `seaborn`: Untuk visualisasi data.
    -   `scikit-learn`: Untuk pemodelan Machine Learning (pemisahan data, model, evaluasi).

## Struktur Proyek
```
.
├── student_performance_factors.ipynb       # Notebook Google Colab utama
├── student_performance_factors.py          # Notebook dalam format .py
└── requirements.txt                        # Daftar dependensi Python
```

## Cara Menjalankan Proyek

Proyek ini dikembangkan di Google Colab, sehingga sangat mudah untuk dijalankan:

1.  **Akses Notebook**: Klik tautan Google Colab berikut:
    https://colab.research.google.com/drive/1A9uFOqOCWPoSFGHrPih0p79uCAg5ZPBM?usp=sharing

2.  **Jalankan Semua Sel**: Setelah membuka notebook di Google Colab, Anda dapat menjalankan seluruh *pipeline* dengan mengklik `Runtime` -> `Run all`.

NB: Terlebih dahulu harus mendownload [Dataset](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors), Setelah itu upload ke dalam Google Colab

## Hasil dan Insight

Setelah melakukan analisis dan pemodelan, beberapa *insight* kunci yang ditemukan meliputi:

-   **Variabel Paling Berpengaruh**: `Hours_Studied`, `Attendance`
-   **Hubungan Korelasi**: Ditemukan korelasi positif yang baik antara `Hours_Studied` dengan `Exam_Score` dan `Attendance` dengan `Exam_Score`.
-   **Kinerja Model**: Model **Random Forest** mendapatkan nilai MSE (train dan test) masing masing sebesar **0.000992** dan **0.005163**, menunjukkan kemampuan yang baik dalam memprediksi performa siswa.
-   **Rekomendasi**: Berdasarkan temuan ini, sangat direkomendasikan untuk mendorong peningkatan waktu belajar dan kehadiran siswa di kelas guna meningkatkan skor ujian mereka secara signifikan.

**Visualisasi Kunci:**
*(Sertakan screenshot atau link ke grafik/plot penting dari notebook Anda yang menunjukkan insight)*

![Distribusi Nilai Akhir](link_gambar_distribusi_nilai.png)
*(Ganti dengan link ke gambar yang Anda upload ke repositori atau tempat lain)*

![Feature Importance Model](link_gambar_feature_importance.png)
*(Ganti dengan link ke gambar yang Anda upload ke repositori atau tempat lain)*

## Kesimpulan

Proyek ini berhasil mengidentifikasi dan memprediksi faktor-faktor yang secara signifikan memengaruhi performa siswa. Temuan ini dapat menjadi dasar untuk pengembangan strategi pendidikan yang lebih efektif dan intervensi yang ditargetkan untuk meningkatkan hasil belajar siswa.

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).