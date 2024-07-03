# Laporan Proyek Machine Learning - Kevin Christian Sepoetro

## Domain Proyek

Kinerja akademik siswa adalah aspek penting dalam pendidikan yang mempengaruhi peluang mereka di masa depan. Faktor-faktor yang mempengaruhi seperti jumlah jam belajar, skor ujian sebelumnya, kegiatan ekstrakurikuler, dan lain lain. Namun, memprediksi kinerja akademik secara akurat bisa sulit dilakukan secara manual. Oleh karena itu, diperlukan sistem yang bisa menganalisis data siswa untuk memprediksi kinerja siswa dengan lebih tepat.

**Mengapa Masalah ini harus diselesaikan ?**
Masalah ini harus diselesaikan karena :
- Peningkatan Kualitas Pendidikan.
Memahami faktor-faktor yang mempengaruhi kinerja akademik siswa dapat membantu pendidik dan lembaga pendidikan merancang kurikulum dan metode pengajaran yang lebih efektif, Sehingga dapat meningkatkan kualitas pendidikan.
- Identifikasi Dini Siswa Bermasalah
Melalui analisis data, dapat mengidentifikasi siswa yang mungkin menghadapi kesulitan dalam akademik sejak dini. Hal ini memungkinkan memberi dukungan lebih cepat, yang dapat membantu siswa mengatasi hambatan belajar dan mencapai potensi maksimal siswa.
- Optimalisasi penggunaan sumber daya lembaga pendidikan.
Karena hal ini dapat membantu sekolah (guru) dan lembaga pendidikan dalam mengalokasikan sumber daya dengan lebih efisien. Misalnya, program bimbingan atau dukungan tambahan dapat ditargetkan kepada siswa yang paling membutuhkan berdasarkan data yang ada.
- Optimalisasi Prestasi Siswa dan Kinerja Universitas
Dengan memahami faktor-faktor kinerja akademik siswa, Universitas atau sekolah dapat mengidentifikasi tren atau pola yang mempengaruhi kinerja siswa. Sehingga memungkinkan sekolah untuk mengembangkan strategi yang lebih efektif dalam proses seleksi, pengajaran, dan dukungan akademik, sehingga dapat meningkatkan prestasi siswa dan keseluruhan kinerja sekolah maupun universitas.

  Format Referensi: [Implementasi Algoritma K-Means untuk Klasterisasi Kinerja Akademik Mahasiswa](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/view/1571/568) 

## Business Understanding

Project ini ditujukan kepada lembaga pendidikan dengan karakteristik sebagai berikut:
+ Lembaga menyediakan dukungan Akademik dengan memberi bimbingan dan konseling untuk membantu siswa mencapai potensi maksimal
+ Lembaga dapat menggunakan Analisis data untuk menganalisis data kinerja siswa untuk meningkatkan strategi pengajaran
+ Lembaga Pendidikan dapat menyediakan Program Pendidikan seperti menawarkan berbagai tingkat pendidikan dan pelatihan kepada siswa

### Problem Statements

Latar Belakang Masalah :
- Dari segi serangkaian Features, Feature apa yang paling berpengaruh pada hasil kinerja Akademik siswa ?
- Bagaimana cara memproses data agar dapat digunakan secara efektif dalam model prediksi ?
- Berapa nilai kinerja akademik siswa yang diprediksi berdasarkan fitur-fitur tertentu ?

### Goals

- Mengidentifikasi fitur yang paling berpengaruh pada hasil kinerja akademik siswa.
- Menyiapkan data agar dapat digunakan secara efektif oleh model prediksi. Termasuk pembersihan, transformasi, dan pemilihan fitur, sehingga model machine learning dapat dilatih dengan efisien dan memberikan hasil yang akurat.
- Membuat model machine learning yang dapat memprediksi nilai kinerja akademik siswa dengan akurat

    ### Solution statements
    - Solusi nya yaitu menggunakan tiga Algoritma untuk membandingkan kinerja model mana yang lebih baik untuk memprediksi nilai kinerja akademik siswa. 3 Algoritma tersebut yaitu KNN, Random Forest, dan Boosting
    - Menerapkan Feature Scaing yang bertujuan memastikan bahwa semua fitur memiliki skala yang seragam, yang penting untuk algoritma seperti KNN yang sensitif terhadap skala fitur.
    - Untuk evaluasi menggunakan MSE, dan memilih MSE terendah sebagai model yang terbaik. Selain itu Evaluasi efek dari feature scaling pada MSE untuk memastikan bahwa penerapan scaling meningkatkan performa model dibandingkan dengan model yang tidak menggunakan scaling.

## Data Understanding
Dataset yang digunakan adalah Student Performance, berasal dari Kaggle, sumber data dataset: [Student Performance (Multiple Linear Regression)]([https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data](https://www.kaggle.com/datasets/nikhil7280/student-performance-multiple-linear-regression)).

Berikut informasi pada dataset :
- Dataset memiliki format CSV (Comma-Seperated Values).
- Dataset memiliki 10000 sample dengan fitur.
- Dataset memiliki 6 fitur.
- Tidak ada missing value dalam dataset.

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
Variable Features:
- Jam Belajar: Jumlah total jam yang dihabiskan setiap siswa untuk belajar.
- Skor Sebelumnya: Skor yang diperoleh siswa pada tes sebelumnya.
- Kegiatan Ekstrakurikuler: Apakah siswa berpartisipasi dalam kegiatan ekstrakurikuler (Ya atau Tidak).
- Jam Tidur: Jumlah rata-rata jam tidur yang dimiliki siswa per hari.
- Contoh Soal yang Dilatih: Jumlah contoh soal yang dipraktikkan siswa.
  
Variable Target:
- Indeks Kinerja: Ukuran kinerja keseluruhan setiap siswa. Indeks kinerja mewakili kinerja akademik siswa dan telah dibulatkan ke bilangan bulat terdekat. Indeksnya berkisar antara 10 hingga 100, dengan nilai yang lebih tinggi menunjukkan kinerja yang lebih baik.

### Evaluasi Data
**Informasi Pada Data**

Mengecek informasi pada dataset dengan fungsi info() berikut :
![Screenshot (566)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/91a55fc3-b119-4a6b-b5f7-346241ce3d6d)

Dari hasil informasi dapat disimpulkan :
- Terdapat 4 data bertipe Int (Previous Scores, Sleep Hours, Sample Question Papers Practiced)
- Terdapat 1 data bertipe Float (Performance Index)
- Terdapat 1 data bertipe Object (Extracurricular Activities)

**Deskripsi Statistik Data**

Melihat deskripsi pada dataset dengan Fungsi describe(), sebgai berikut hasilnya :
![Screenshot (567)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/c75ce43c-a79c-4edf-bf80-edb422dfc94b)

Fungsi describe() diatas memberikan informasi statistik pada masing-masing kolom feature :
- Count  adalah jumlah sampel pada data.
- Mean adalah nilai rata-rata.
- Std adalah standar deviasi.
- Min yaitu nilai minimum setiap kolom.
- 25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval dalam empat bagian sebaran yang sama.
- 50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
- 75% adalah kuartil ketiga.
- Max adalah nilai maksimum.


**Menangani Duplikat Data**

Pada bagian ini, melihat apakah ada data data yang terduplikat atau tidak. Fungsi melihat data terduplikat atau tidak dengan .duplicate(). Sedangkan unutk mengetahui jumlah yang terdupikat adalah .duplicate().sum().

![Screenshot (568)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/c541e1ea-1683-45ea-b0c4-f6af2fb53bb1)

Ternyata ada data yang terduplikat sebanyak 127. Data yang terduplikat bisa mempengaruhi kinerja model. Data duplikat juga dapat menambah ukuran dataset tanpa menambah informasi baru, yang dapat memperlambat proses pelatihan model dan memperbesar beban komputasi. Sehingga menghapus data duplikat dapat membantu memastikan bahwa data yang digunakan untuk pelatihan model adalah unik dan representatif. Untuk menghapus data duplikat bisa menggunakan drop_duplicates().
![Screenshot (569)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/0ee53efe-428d-40e8-9c6f-5def70093148)

Data Terduplikat sudah tidak ada lagi.


**Melihat apakah ada data yang Null atau tidak**

![Screenshot (570)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/fe6ab0be-3718-4190-9c29-13159ea66291)

Tidak ada data yang Null pada setiap kolom atau feature. Selenjutnya melihat informasi statistik.
![Screenshot (571)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/130d0b89-08f8-4533-abe4-4e8b251ad456)

Dari hasil informasi statistik, terdapat perubahan setelah dilakukan penghapusan Duplikat data. Seperti jumlah data menjadi 9873, perubahan rata rata, dan Standart devasi.

### Outlier
![Screenshot (572)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/f0c6710d-3fd7-4d0b-ac21-891ca428711c)
![Screenshot (573)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/8335a588-ac49-4f1e-8bee-cc8f4d1b76b9)
![Screenshot (574)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/7d545513-2f95-432b-8605-1958a30ff1ce)
![Screenshot (575)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/9f0d2d8c-64cc-4673-ba90-ab10467735eb)

Untuk masalah outlier dapat dilihat, bahwa tidak ada sampel yang nilainya sangat jauh dari cakupan umum data utama.

### Univariate
Univariate melakukan analisis data dengan 1 feature saja. Untuk feature dibagi menjadi 2 yaitu Numeric (Hours Studied, Previous Scores, Sleep Hours, Sample Question Papers Practiced, Performance Index) dan kategori yaitu Extracurricular Activities.
**Feature Kategori**

![Screenshot (576)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/396ec5d6-fdcf-4470-9913-46dc5de10536)

Dapat dilihat bahwa antara siswa ikut ectracurricular atau tidak berbeda tipis. Dimana jumlah yang ikut 4887 dan tidak ikut 4986.

**Feature Numeric**
Selanjutnya, untuk fitur numerik, kita akan melihat histogram masing-masing fiturnya

![Screenshot (577)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/4fd56320-a040-4e32-9ebb-b3ca5becdffe)

### Multivariate
Multivariate adalah analisis data dengan melibatkan beberapa feature.
**Feature Kategori**

![Screenshot (578)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/13fdaee1-f0d5-45b7-9e9e-d05c65295eb4)

Pada feature kategori Extracurricular Activities terhadap peforma index siswa, rata rata cenderung mirip. Grade tertinggi yaitu yang no daripada yang yes.

**Feature Numeric**

![Screenshot (579)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/f67a0671-b4e7-4a4f-926d-dfbf1c9fe89b)

Dapat dilihat bahwa dari grafik diatas bahwa Previous score memiliki kolerasi yang tinggi terhadap Index Perfomance. Sedangkan Feature Hours Studied agak lemah, Dan feature Sleep hours serta Sample Question Papers Practiced terhadap Perfomance Index sangat lemah kolerasinya.

![Screenshot (580)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/00325f7e-2206-4665-94c9-5b907c478b80)

Dapat dilihat bahwa dari Corelation Matrix Feature Previous score terhadap Perfoma Index memiliki kolerasi tinggi yaitu(0.92). Sedangkan pada feature Sleep hours serta Sample Question Papers Practiced terhadap Perfomance Index sangat. (0.05 (Sleep Hours) dan 0.04(Sample Question Papers Practice)). Sehingga  feature Sleep hours dan Sample Question Papers Practiced di hapus.

![Screenshot (581)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/d1cc8f98-c511-4b95-b26d-e6f6ab7d771d)


## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.  

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.
