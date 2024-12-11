# Laporan Proyek Machine Learning - Muhammad Yasir

## Domain Proyek

Kualitas udara yang buruk telah menjadi salah satu isu lingkungan paling mendesak di banyak kota besar di seluruh dunia, termasuk di Indonesia. Polusi udara memiliki dampak signifikan terhadap kesehatan manusia, ekosistem, dan perubahan iklim. Dataset "Air Quality and Pollution Assessment" dari Kaggle menyediakan data yang berharga mengenai berbagai parameter polusi udara, seperti konsentrasi PM2.5, PM10, NO2, SO2, CO, serta faktor lingkungan lainnya seperti suhu, kelembaban, dan kepadatan penduduk. Dengan menganalisis data ini, kita dapat mengembangkan model prediktif yang dapat memproyeksikan kualitas udara berdasarkan faktor-faktor tersebut, yang berguna untuk perencanaan kota dan kebijakan lingkungan.
Untuk membuat model prediktif kualitas udara, beberapa algoritma machine learning yang akan diterapkan untuk kemudian dilihat algoritma mana yang memiliki performa terbaik terhadap data. Algoritma Logistic Regression digunakan sebagai baseline karena kesederhanaannya dan kemampuannya dalam menangani masalah klasifikasi multi-kelas. Selanjutnya, algoritma Random Forest dan Gradient Boosting diterapkan untuk meningkatkan akurasi prediksi dengan memanfaatkan pendekatan ensemble yang menangkap interaksi kompleks antar fitur. Selain itu, Support Vector Machine (SVM) diterapkan untuk menemukan hyperplane optimal yang memisahkan kategori kualitas udara yang berbeda. Evaluasi menunjukkan bahwa model ensemble, khususnya Random Forest dan Gradient Boosting, memberikan performa terbaik dalam memprediksi kualitas udara, menjadikannya pilihan utama untuk implementasi lebih lanjut.

## Business Understanding

### Problem Statements

1. Kualitas udara yang buruk telah menjadi ancaman kesehatan yang serius di seluruh dunia termasuk Indonesia. Bagaimana ancaman ini dapat diatasi?
2. Bagaimana cara menentukan faktor-faktor yang mempengaruhi kualitas udara guna dapat digunakan dalam model yang akan dibangun?

### Goals

1. Menganalisis faktor-faktor utama yang berkontribusi terhadap kualitas udara dan memahami pola-pola polusi udara.
2. Mengembangkan model prediktif yang akurat untuk memproyeksikan kualitas udara berdasarkan berbagai parameter lingkungan dan polusi.Menganalisis faktor-faktor utama yang berkontribusi terhadap kualitas udara dan memahami pola-pola polusi udara.

### Solution Statement

1. Penggunaan berbagai algoritma untuk memprediksi kualitas udara
   Melatih model dengan menggunakan berbagai algoritma guna mencari algoritma mana yang memiliki peforma terbaik untuk diimplemntasikan dengan melihat laporan klasifikasinya berupa recall, precision, dan f1-score. Algoritma yang akan digunakan adalah Logistic Regression, Support Vector Machine, Random Forest, Gradient Boosting, dan K-Nearest Neighbours.
2. Pengoptimalan model dengan hyperparameter
   Setelah semua model dilatih, maka akan dipilih algoritma dengan peforma terbaik guna dilakukan pengoptimalan hyperparameter untuk peningkatan akurasi.

## Data Understanding

Dataset ini berfokus pada kualitas penilaian kualitas udara di berbagai wilayah dengan menangkap faktor lingkungan dan demografis kritis yang memengaruhi tingkat polusi. Dataset ini berisi 5000 sampel yang terdiri dari 5000 bari dan 10 kolom.

Informasi lebih lanjut dapat dilihat di [Air Quality and Pollution Assessment](https://www.kaggle.com/datasets/mujtabamatin/air-quality-and-pollution-assessment).

### Fitur-fitur Utama:

1. Suhu (°C): Rata-rata suhu wilayah.
2. Kelembaban (%): Kelembaban relatif yang direkam di wilayah tersebut.
3. Konsentrasi PM2.5 (µg/m³): Tingkat partikel halus.
4. Konsentrasi PM10 (µg/m³): Tingkat partikel kasar.
5. Konsentrasi NO2 (ppb): Tingkat nitrogen dioksida.
6. Konsentrasi SO2 (ppb): Tingkat sulfur dioksida.
7. Konsentrasi CO (ppm): Tingkat karbon monoksida.
8. Jarak dari Area Industri (km): Jarak terdekat ke zona industri.
9. Kepadatan Penduduk (orang/km²): Jumlah orang per kilometer persegi di wilayah tersebut.

### Variabel Target: Tingkat Kualitas Udara

1. Baik: Udara bersih dengan tingkat polusi rendah.
2. Sedang: Kualitas udara yang dapat diterima tetapi dengan beberapa polutan.
3. Buruk: Polusi yang terlihat dan mungkin menyebabkan masalah kesehatan bagi kelompok sensitif.
4. Berbahaya: Udara yang sangat terkontaminasi yang menimbulkan risiko kesehatan serius bagi populasi.

### Eksplorasi Data Analysis (EDA)

- Ringkasan statistik deskriptif:
  ![deksripsi_dataset](https://github.com/user-attachments/assets/9249d0bf-8a6c-4ea6-ab50-39bcc133c261)
  Tabel 1. Deskripsi Statistik
  
  Dengan keterangan sebagai berikut:
  * count : jumlah data
  * mean : nilai rata-rata
  * std : standar deviasi
  * min : nilai minimum dari suatu fitur
  * 25% : Q1 (kuartil pertama)
  * 50% : Q2 (kuartil kedua)
  * 75% : Q3 (kuartil ketiga)
  * max : nilai maximum dari suatu fitur

- Missing Values
  Untuk melihat apakah dataset memiliki missing value atau tidak, dapat menggunakan syntax berikut :
  ```
  df.isna().sum()
  ```
  ![EDA_missing_values](https://github.com/user-attachments/assets/77d2c88a-a426-4c74-b273-f1af7ff6bff6)

  Berdasarkan output dari syntax yang kita jalankan tadi, dapat diketahui bahwa dataset tidak memiliki missing value di setiap fiturnya.


- Diagram Pairplot untuk Melihat Korelasi antar Fitur
  ![pairplot](https://github.com/user-attachments/assets/9f982954-5d4f-4c1e-85f2-9519b5bc0f3e)
  Gambar 1. Diagram pairplot

  Berdasarkan diagram pairplot di atas kita dapat melihat hubungan antara fitur "Air Quality" dengan fitur-fitur lainnya. Berikut adalah informasi yang didapat dari diagram pairplot di atas:
1. Kualitas Udara dan PM2.5: Terdapat korelasi positif yang jelas antara kualitas udara dan konsentrasi PM2.5. Ini menunjukkan bahwa peningkatan PM2.5 berhubungan dengan penurunan kualitas udara.
2. Kualitas Udara dan PM10: Mirip dengan PM2.5, konsentrasi PM10 juga menunjukkan korelasi positif dengan kualitas udara. Semakin tinggi konsentrasi PM10, semakin buruk kualitas udara.
3. Kualitas Udara dan NO2: Terdapat hubungan positif antara NO2 dan kualitas udara. NO2 merupakan polutan yang berkontribusi signifikan terhadap penurunan kualitas udara.
4. Kualitas Udara dan SO2: Konsentrasi SO2 juga berhubungan dengan kualitas udara, dengan korelasi positif yang menunjukkan bahwa peningkatan SO2 berkorelasi dengan penurunan kualitas udara.
5. Kualitas Udara dan CO: Hubungan antara CO dan kualitas udara menunjukkan tren yang mirip, di mana peningkatan kadar CO berkaitan dengan penurunan kualitas udara.
6. Kualitas Udara dan Faktor Lingkungan Lainnya:
   * Kedekatan dengan Area Industri: Plot ini menunjukkan bahwa area yang dekat dengan industri cenderung memiliki kualitas udara yang lebih buruk.
   * Suhu dan Kelembapan: Ada korelasi yang lebih kompleks antara faktor cuaca ini dengan kualitas udara. Tren ini bisa bervariasi berdasarkan kondisi lokal dan aktivitas manusia.

- Diagram Heatmap
  ![diagram_heatmap](https://github.com/user-attachments/assets/07dbfa76-53ad-4b1c-8719-7daf0bdba0f8)
  Gambar 2. Diagram Heatmap
  
  Gambar di atas menunjukkan heatmap yang menggambarkan korelasi antara berbagai variabel dalam dataset kualitas udara dan polusi. Berikut adalah penjelasan dan informasi yang bisa kita dapatkan dari heatmap tersebut:
1. Korelasi Positif
   - Temperature: Korelasi positif sebesar 0.75 dengan kualitas udara menunjukkan bahwa suhu yang lebih tinggi cenderung berhubungan dengan kualitas udara yang lebih baik.
   - Humidity: Korelasi positif sebesar 0.63 menunjukkan bahwa kelembapan yang lebih tinggi berhubungan dengan kualitas udara yang lebih baik.
   - PM2.5: Korelasi positif sebesar 0.42 menunjukkan bahwa peningkatan konsentrasi 			-PM2.5 berhubungan dengan kualitas udara yang lebih buruk.
   -PM10: Korelasi positif sebesar 0.56 menunjukkan bahwa peningkatan konsentrasi PM10 berhubungan dengan kualitas udara yang lebih buruk.
   - NO2: Korelasi positif sebesar 0.79 menunjukkan bahwa peningkatan konsentrasi NO2 berhubungan dengan kualitas udara yang lebih buruk.
   - SO2: Korelasi positif sebesar 0.74 menunjukkan bahwa peningkatan konsentrasi SO2 berhubungan dengan kualitas udara yang lebih buruk.
   - CO: Korelasi positif sebesar 0.91 menunjukkan bahwa peningkatan konsentrasi CO berhubungan dengan kualitas udara yang lebih buruk.
   - Population Density: Korelasi positif sebesar 0.65 menunjukkan bahwa peningkatan densitas populasi berhubungan dengan kualitas udara yang lebih buruk.

2. Korelasi Negatif
   - Proximity to Industrial Areas: Korelasi negatif sebesar -0.77 menunjukkan bahwa lokasi yang lebih dekat dengan area industri cenderung memiliki kualitas udara yang lebih buruk.

- Diagram Boxplot untuk Melihat Outliers
  ![diagram_outliers](https://github.com/user-attachments/assets/f387cbd7-d3c3-46cf-9c1a-886623c0033d)
  Gambar 3. Diagram Boxplot

  Informasi yang bisa didapat dari diagram boxplot di atas adalah sebagai berikut:
	* Temperature (Suhu): Terdapat beberapa outlier di atas 50 derajat, yang menunjukkan suhu ekstrem yang jarang terjadi.
	* Humidity (Kelembaban): Terdapat beberapa outlier di atas 100%, yang mungkin menunjukkan kesalahan pengukuran atau data.
	* PM2.5: Terdapat banyak outlier di atas 100, bahkan mencapai hampir 300, menunjukkan beberapa lokasi dengan tingkat polusi sangat tinggi.
	* PM10: Terdapat banyak outlier di atas 100, bahkan mencapai hampir 300, menunjukkan polusi partikel yang tinggi di beberapa lokasi.
	* Population Density (Kepadatan Penduduk): Terdapat beberapa outlier di atas 800, menunjukkan area dengan kepadatan penduduk yang sangat tinggi.
	* NO2: Terdapat banyak outlier di atas 40, menunjukkan beberapa area dengan polusi NO2 yang signifikan.
	* SO2: Terdapat banyak outlier di atas 20, menunjukkan beberapa area dengan polusi SO2 yang tinggi.
 	* CO: Terdapat beberapa outlier di atas 3, menunjukkan adanya lokasi dengan konsentrasi CO yang tinggi.
	* Proximity to Industrial Areas (Kedekatan dengan Area Industri): Terdapat beberapa outlier di atas 20, menunjukkan beberapa pengukuran yang sangat dekat dengan area industri.

   IQR method akan digunakan dalam proyek ini untuk mengatasi outliers. IQR adalah singkatan dari Inter Quartile Range. Berikut adalah persamaan IQR method:
	
    Batas bawah = Q1 - 1.5 * IQR
   	
    Batas atas = Q3 + 1.5 * IQR
   
    Dan berikut potongan kode bagaimana IQR method diimplementasikan :
    ```
   Q1 = df[features].quantile(0.25)
   Q3 = df[features].quantile(0.75)
   IQR = Q3 - Q1
   df = df[~((df[features]<(Q1-1.5*IQR))|(df[features]>(Q3+1.5*IQR))).any(axis=1)]
   ```
   
   Setelah outliers dibersihkan, tentu terjadi pengurangan jumlah data yang awalnya terdapat 5000 data turun menjadi 4407 data.

## Data Preparation

### Label Encoding
Label encoding adalah proses penting dalam machine learning terutama ketika bekerja dengan data kategorikal. Algoritma machine learning membutuhkan data dalam format numerik agar dapat bekerja dengan baik.
Berikut adalah nilai-nilai yang terdapat pada fitur target "Air Quality":
1. Good
2. Moderate
3. Poor
4. Hazardous

Setiap nilai akan di encoding menjadi nilai numerik dengan rentang [1-4] menggunakan syntax berikut:
```
df["Air Quality"] = df["Air Quality"].replace({'Good': 1, 'Moderate': 2, 'Poor': 3, 'Hazardous': 4}).infer_objects(copy=False)
```

### Seleksi Fitur

Karena semua fitur memiliki korelasi yang tinggi atau setidaknya sedang, maka semua fitur akan digunakan untuk pelatihan. Fitur-fitur tersebut adalah suhu, kelembaban, konsentrasi PM2.5, konsentrasi PM10, konsentrasi NO2, konsentrasi SO2, konsentrasi CO, jarak dan kepadatan penduduk. Sementara Aur Quality akan menjadi label atau fitur target.

### Splitting Dataset

Dataset akan dibagi menjadi data latih dan data uji. Data latih digunakan untuk melatih model, sedangkan data uji digunakan untuk menguji kinerja model pada data yang belum pernah dilihat sebelumnya. Dalam proyek ini, data latih akan memiliki ukuran 80% dari dataset dan untuk data latih sebesar 20% dari dataset. Data akan dibagi menggunakan fungsi train_test_split dari library scikit-learn. Jumlah total dataset adalah 4407 data, sehingga data latih akan berjumlah 3525 dan data uji berjumlah 882.

### Standarisasi

Standarisasi adalah teknik praproses data dalam machine learning yang mengubah fitur-fitur dalam dataset sehingga memiliki distribusi dengan rata-rata 0 dan standar deviasi 1. Ini dilakukan untuk memastikan bahwa setiap fitur memiliki skala yang sama. Proses standarisasi membantu meningkatkan konvergensi algoritma machine learning dan performa model dengan mengurangi bias yang disebabkan oleh skala fitur yang berbeda.

# Modelling

Pada tahap ini akan dibangun lima model AI yang menggunakan algoritma yang berbeda-beda untuk kemudian ditentukan model mana yang memiliki performa terbaik terhadap data. Algoritma-algoritma tersebut adalah Logistic Regression, Support Vector Machine, Random Forest, Gradient Boosting, dan K-Nearest Neighbours. Semua algoritma akan dilatih menggunakan parameter default dari library scikit-learn. Kemudian performa akan diukur dari precision, recall, f1-score dan accuracy menggunakan fungsi classification_report dari library scikit-learn.

1. Logistic Regression: Logistic Regression merupakan model dasar yang dapat digunakan untuk klasifikasi multi-kelas. Walaupun sederhana, algoritma ini seringkali memberikan hasil yang cukup baik sebagai baseline. Berikut paramter yang digunakan:
   * penalty=l2 (menentukan jenis regularisasi yang akan diterapkan)
   * C=1.0 (parameter regularisasi yang mengontrol kekuatan regularisasi)
   * solver=lbfgs (algoritma yang akan digunakan untuk mengoptimalkan masalah)
   * random_state=42 (kontrol shuffling dan inisialisasi untuk reproduksibilitas)

2. Random Forest: Random Forest adalah algoritma ensemble yang kuat, yang menggabungkan banyak pohon keputusan untuk meningkatkan akurasi prediksi dan mengurangi overfitting. Berikut adalah parameter yang digunakan:
   * n_estimators=100 (jumlah pohon keputusan dalam hutan)
   * criterion=gini (fungsi untuk mengukur kualitas split)
   * max_depth=None (kedalaman maksimum pohon keputusan)
   * min_samples_split=2 (jumlah minimum sampel yang diperlukan untuk membagi internal node)
   * random_state=42 (kontrol shuffling dan inisialisasi untuk reproduksibilitas)

3. Gradient Boosting: Gradient Boosting adalah teknik ensemble yang menggunakan pendekatan boosting untuk meningkatkan performa model dengan membangun serangkaian model yang memperbaiki kesalahan model sebelumnya. Berikut adalah parameter yang digunakan:
   * loss=log_loss (fungsi untuk mengoptimisasi model)
   * learning_rate=0.1 (mengontrol kontribusi setiap pohon pada model akhir)
   * n_estimators=100 (jumlah boosting stages yang akan dilakukan)
   * subsample=1.0 (fraksi sampel yang digunakan untuk menumbuhkan tiap pohon)
   * criterion=friedman_mse (fungsi untuk mengukur kualitas split)
   * random_state=42 (kontrol shuffling dan inisialisasi untuk reproduksibilitas)

4. Support Vector Machine: SVM adalah algoritma klasifikasi yang menemukan hyperplane optimal untuk memisahkan kelas-kelas yang berbeda. Ini bisa efektif untuk dataset dengan kelas yang terdefinisi jelas. Berikut adalah parameter yang digunakan:
   * C=1.0 (parameter regularisasi yang mengontrol trade-off)
   * kernel=rbf (fungsi kernel yang menentukan tipe ruang transformasi)
   * gamma=1.2 (skala untuk menentukan radius pengaruh data tunggal)
   * random_state=42 (kontrol shuffling dan inisialisasi untuk reproduksibilitas)

5. K-Nearest Neighbors: KNN adalah algoritma sederhana yang mengklasifikasikan data berdasarkan kedekatan dengan contoh pelatihan dalam ruang fitur. Berikut adalah parameter yang digunakan:
   * n_neighbors=4 (jumlah tetangga terdekat yang digunakan untuk voting dalam klasifikasi atau untuk regresi)
   * weights=uniform (fungsi bobot yang digunakan dalam prediksi)
   * algorithm=auto (algoritma yang digunakan untuk menghitung tetangga terdekat)
   * leaf_size=30 (ukuran daun yang memengaruhi kecepatan konstruksi dan query)
   * n_job=-1 (jumlah pekerjaan paralel yang digunakan untuk melakukan query KNN)

# Evaluasi

Setelah semua model dilatih, langkah selanjutnya adalah membandingkan performa dari setiap model. Metrik yang akan digunakan untuk mengukur performa dari setiap model adalah precision, recall, f1-score, dan accuracy. Metrik didapatkan menggunakan fungsi classification_report dari library scikit-learn. Berikut penjelasan dari setiap metrik yang digunakan :
   1. precision : proporsi dari prediksi positif yang benar-benar positif. Precision mengukur akurasi dari prediksi positif
   2. recall : proporsi dari semua sampel positif yang berhasil diidentifikasi oleh model
   3. f1-score : rata-rata harmonis dari precision dan recall
   4. accuracy : proporsi dari semua prediksi yang benar (baik positif maupun negatif) dari keseluruhan sampel

![models](https://github.com/user-attachments/assets/2081e750-27bc-4b88-a2d1-b15a71e74be2)


Tabel 2. Performa dari Semua Model 

Berdasarkan tabel di atas dapat dilihat bahwa model yang dibangun menggunakan algoritma Logistic Regression memiliki peforma terbaik. Langkah selanjutnya kita akan melakukan pengoptimalan hyperparameter dengan metode Grid Search. 
Grid search adalah metode pencarian hyperparameter yang sistematis dan ekstensif yang digunakan dalam pelatihan model machine learning. Tujuan utama grid search adalah untuk menemukan kombinasi optimal dari hyperparameter yang dapat meningkatkan performa model secara signifikan. Hyperparameter adalah parameter yang tidak dipelajari dari data, melainkan ditentukan sebelum proses pelatihan.

### Tahapan Grid Search:

1. Definisikan Ruang Hyperparameter: Tentukan range atau set nilai hyperparameter yang ingin diuji.
   Berikut cakupan parameter untuk algoritma logistic regression :
    - 'penalty': ['l1', 'l2', 'elasticnet', 'none'],
    - 'C': [1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0],
    - 'max_iter': [100, 200, 300],
    - 'tol': [1e-4, 1e-5, 1e-6, 1e-7],
    - 'fit_intercept': [True, False],
    - 'class_weight': [None, 'balanced'],
    - 'solver': ['lbfgs', 'liblinear', 'newton-cg', 'newton-cholesky', 'sag', 'saga']

2. Eksplorasi Semua Kombinasi: Grid search akan mencoba setiap kombinasi dari nilai hyperparameter yang telah ditentukan. Untuk algoritma random forest memiliki 20736 kombinasi.

3. Pilih Kombinasi Terbaik: Kombinasi hyperparameter yang menghasilkan performa terbaik pada validasi silang dipilih sebagai kombinasi optimal. Model final kemudian dibangun menggunakan hyperparameter tersebut.
Berikut parameter terbaik untuk algoritma logistic regression:
	* 'C': 3.0,
	* 'class_weight': None,
	* 'fit_intercept': True,
	* 'max_iter': 100,
	* 'penalty': 'l2',
	* 'solver': 'saga',
	* 'tol': 0.0001

Kemudian model terbaik akan diuji kembali dengan data uji untuk melihat performanya. Berikut adalah hasil pengujian terhadap model terbaik bersama dengan performa awal model agar dapat dilihat perbedaanya:

![opt](https://github.com/user-attachments/assets/9f6e7438-69bf-49bb-b4ea-701e16fcea29)

Tabel 3. Performa Model Logistic Regression sebelum dan sesudah optimisasi

Dari tabel di atas dapat dilihat terjadi peningkatan akurasi lebih kurang 1% untuk setiap metrik evaluasi.

## Kesimpulan

### Problem Statements Answers
Problem statement pertama adalah bagaimana cara mengatasi kualitas udara yang buruk? Solusi yang ditawarkan proyek ini adalah dengan mengembangkan sebuah model machine learning yang mampu memproyeksikan kualitas udara di suatu wilayah dengan parameter-parameter yang telah ditentukan. Model yang dihasilkan dari proyek ini memiliki akurasi yang tinggi dengan angka 95.12%. Jika model ini diterapkan dalam upaya penanggulangan kualitas udara, model akan menentikan kualitas udara di suatu wilayah kemudian pihak yang berwenang dapat membuat tindakan yang tepat berdasarkan kualitas udara di wilayah tersebut.

Kemudian problem statement kedua adalah bagaimana cara menentukan faktor-faktor yang mempengaruhi kualitas udara? Hal ini tentu dapat dilakukan dengan melakukan penelitian ilmiah untuk mencari polutan apa saja yang menyebabkan kualitas udara menurun. Beruntungnya sudah banyak jurnal ilmiah yang membahas masalah ini. Analisa statistik terhadap dataset juga dapat dilakukan untuk mendapatkan jawaban dari pertanyaan ini. Dengan menggunakan diagram pairplot dan heatmap didapat bahwa PM2.5, PM10, NO2, SO2, dan CO merupakan faktor-faktor utama yang menyebabkan kualitas udara di suatu wilayah memburuk.

### Goals Achievement
Tujuan proyek ini adalah menganalisa faktor-faktor yang berkontribusi terhadap kualitas udara dan mengembangkan model machine learning yang mampu memprediksi kualitas udara berdasarkan parameter yang telah ditentukan. 
1. Berdasarkan hasil analisa fitur menggunakan diagram pairplot dan heatmap didapat kesimpulan sebagai berikut:
   * Polutan utama: PM2.5, PM10, NO2, SO2, dan CO merupakan polutan utama yang berdampak signifikan terhadap kualitas udara
   * Industri dan Polusi: Kedekatan dengan area industri adalah faktor yang penting dalam menurunkan kualitas udara
   * Cuaca dan Polusi: Faktor cuaca seperti suhu dan kelembapan juga memiliki pengaruh, meskipun kompleksitas hubungan ini memerlukan analisis lebih lanjut.
2. Berdasarkan laporan performa menggunakan classification report pada algoritma logistic regression yang telah dioptimisasi hyperparamter-nya didapat model machine learning yang kampu memproyeksikan kualitas udara berdasarkan parameter suhu, kelembaban, konsentrasi PM2.5, konsentrasi PM10, konsentrasi NO2, konsentrasi SO2, konsentrasi CO, jarak dan kepadatan penduduk dengan akurasi sebesar 95.12%, precision sebesar 89%, recall sebesar 88.87% dan f1-score sebesar 88.98%.

### Dampak Penelitian
Solution statement yang ditawarkan pada proyek ini adalah dengan melatih berbagai algoritma machine learning untuk menemukan algoritma dengan peforma terbaik. Model terbaik kemudian akan dioptimisasi hyperparameternya untuk lebih meningkatkan akurasi prediksi. Algoritma dengan performa terbaik adalah Random Forest dengan akurasi sebesar 95.12%. Jika model ini diterapkan dalam upaya penanggulangan kualitas udara tentu akan memberi dampak yang sangat besar. Karena model ini dapat menentukan kualitas udara di suatu wilayah dengan sangat baik sehingga pemerintah dapat mengambil tindakan yang tepat untuk mengatasinya. Regulasi juga dapat dibuat dan diterapkan berdasarkan hasil proyeksi dari model. Namun, tentu hasil dari model ini perlu diawasi oleh tenaga ahli di bidangnya untuk memastikan pengambilan tindakan yang tepat.
