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

**deskripsi statistik data**
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
