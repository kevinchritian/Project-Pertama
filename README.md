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

Dapat dilihat bahwa dari Corelation Matrix diatas Feature Previous score terhadap Perfoma Index memiliki kolerasi tinggi yaitu(0.92). Sedangkan pada feature Sleep hours serta Sample Question Papers Practiced terhadap Perfomance Index sangat. (0.05 (Sleep Hours) dan 0.04(Sample Question Papers Practice)). Sehingga  feature Sleep hours dan Sample Question Papers Practiced di hapus. Hasilnya sebagai berikut :

![Screenshot (581)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/d1cc8f98-c511-4b95-b26d-e6f6ab7d771d)


## Data Preparation
- One Hot Encoding
One hot encoding adalah teknik mengubah data kategorik menjadi data numerik dimana setiap kategori menjadi kolom baru dengan nilai 0 atau 1. Fitur yang akan diubah menjadi numerik pada proyek ini adalah Extracurricular Activities.

- Train Test Split
Train test split aja proses membagi data menjadi data latih dan data uji. Data latih akan digunakan untuk membangun model, sedangkan data uji akan digunakan untuk menguji performa model. Pada proyek ini dataset dibagi menjadi 80% train dan 20% test. Sehingga total train dataset 7898 dan total test dataset: 1975

- Normalization
Algoritma machine learning akan memiliki performa lebih baik dan bekerja lebih cepat jika dimodelkan dengan data seragam yang memiliki skala relatif sama. Salah satu teknik normalisasi yang digunakan pada proyek ini adalah Standarisasi dengan sklearn.preprocessing.StandardScaler. 

## Modeling
Modeling yang digunakan ada 3 yaitu KNN, Random Forest, dan Boosting

**KNN**

Knn adalah algoritma yang cukup sederhana dibandingkan algoritma lain. KNN dapat digunakan untuk tugas klasifikasi. KNN bekerja dengan membandingkan jarak antara satu sample data dengan sample data train  lain dengan cara memilih sejumlah k tentangga terdekat. Pemilihan nilai K sangat penting dan berpengaruh terhadap perfoma model. Jika k terlalu rendah  maka akan menghasilkan model overfit dan hasil prediksinya memiliki varians tinggi. Jika K terlalu tinggi model menjadi underfit atau bias. 
Pada model KNN ini menggunakan Sklearn dengan Metrik ukuran jarak yang digunakan adalah Minkowski distance. Kemudain pada modeling KNN ini, menggunakan :
- nilai k=10

**Random Forest**

Random Forest adalah salah satu algorimta supervised learning. Random forest dapat digunakan unutk menyelesaikan masalah klasifikasi dan regresi. Random Forest pada dasarnya adalah versi bagging dari algoritma decison tree. Jadi algoritma Random Forest disusun dari banyak Decision Tree  yang pembagian data dan fiturnya dipilih secara acak.
Model parameter random forest :
-	n_estimator: n_estimator=50.
-	max_depth: 16
-	random_state: 55
-	n_jobs: -1

**Boosting**

Algoritma Boosting membangun model dari data latih. Kemudian membuat model yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau mencapai jumlah maksimum model untuk ditambahkan. Pada model Boosting menggunakan Adaptive Boosting.
Adaptive Boosting bekerja dengan semua kasus dalam data latih memiliki bobot yang sama. Pada setiap tahapan, model akan observasi yang dilakukan sudah benar atau belum. Bobot yang lebih tinggi kemudian diberikan pada model yang salah, sehingga mereka akan dimasukan ke dalam tahapan selnjutnya. Proses ini berlanjut sampai model akurasi yang diinginkan.
Model Parameter :
- learning_rate: 0.05
- random_state: 55

**Kelebihan dan Kelemahan**

KNN (K-Nearest Neighbors)
- Kelebihan: Sederhana dan mudah dipahami. Tidak memerlukan asumsi khusus tentang distribusi data atau parameter model, sehingga bisa digunakan dalam berbagai masalah klasifikasi dan regresi.
- Kekurangan: Lambat dalam prediksi pada dataset besar 

Random Forest
- Kelebihan: Mengurangi overfitting dibandingkan dengan model pohon keputusan tunggal dengan membangun banyak pohon keputusan dan menggabungkan hasilnya.
- Kekurangan: Model dapat menjadi sangat besar dan memerlukan banyak memori serta waktu komputasi, terutama dengan banyak pohon dan fitur.

Boosting
- Kelebihan: Dapat memperbaiki kesalahan model sebelumnya secara iteratif.
- Kekurangan: Bisa rentan terhadap overfitting jika tidak diatur dengan benar, dan proses pelatihan bisa memakan waktu lama karena model dilatih secara berurutan.

## Evaluation
Metrik evaluasi yang digunakan pada proyek ini adalah akurasi dan mean squared error (MSE). Akurasi menentukan tingkat kemiripan antara hasil prediksi dengan nilai / data yang sebenarnya. Mean squared error (MSE) mengukur error dalam model statistik dengan cara menghitung rata-rata error dari kuadrat hasil aktual dikurang hasil prediksi. 
Berikut adalah rumus MSE :

![Screenshot (587)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/1be82688-9581-4a4e-bde5-5f30ce01a1cb)

Berikut adalah hasil MSE dari 3 model (KNN, Random Forest, Boosting):

![Screenshot (584)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/48d2755b-6443-4ac8-82b5-8de850356bfd)

Berikut dalam bentuk plot:

![Screenshot (585)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/7d562d17-fe4a-4163-8db1-4caccec66d7f)

Dari hasil Plot diatas dapat dilihat bahwa MSE pada train model Random Forest lebih kecil daripada yang lain. Sedangkan pada MSE test Model KNN lebih kecil dari pada yang lain. Berikut adalah pengujian model :

![Screenshot (586)](https://github.com/kevinchritian/Project-Pertama/assets/93351620/bd2c9611-4337-4815-b009-0bd3e7c89cf3)

Dari hasil prediksi tersebut yang paling mendekati adalah Random Forest dan KNN. tetapi yang paling mendekati adalah **Random Forest**. 
