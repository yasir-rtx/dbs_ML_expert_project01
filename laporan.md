# Laporan Proyek Machine Learning - Muhammad Yasir

## Domain Proyek

Perkembangan teknologi dan pengetahuan manusia tentang antariksa telah mendorong peningkatan perhatian terhadap studi ilmiah mengenai Near Earth Objects (NEOs) dalam beberapa dekade terakhir. NEOs adalah komet dan asteroid yang orbitnya membawa mereka mendekati orbit bumi. Keberadaan NEOs ini penting untuk dipelajari karena mereka memiliki potensi untuk membahayakan bumi jika orbitnya mengarah pada tabrakan, yang bisa menyebabkan bencana besar.
Penelitian terkait NEOs sangat penting untuk memprediksi potensi ancaman dari setiap komet dan asteroid yang mendekati bumi. Dengan pemahaman yang lebih baik, langkah-langkah mitigasi dapat direncanakan untuk mengurangi risiko yang ditimbulkan. Proyek ini bertujuan untuk menerapkan algoritma machine learning guna mengkategorikan NEOs berdasarkan potensi bahayanya terhadap bumi, dengan mengeksplorasi pola-pola yang ada dalam dataset NEOs.
Mengapa masalah ini harus diselesaikan :

- Keamanan Global: NEOs yang berpotensi bertabrakan dengan bumi dapat menyebabkan kerusakan besar
- Pengetahuan Ilmiah: Memahami karakteristik dan perilaku NEOs membantu memperluas pengetahuan kita tentang tata surya
- Persiapan dan Mitigasi: Dengan melacak NEOs lebih dini, kita dapat merencanakan langkah-langkah mitigasi yang tepat

Bagaimana masalah ini harus diselesaikan:

- Pengumpulan data: Pengumpulan data dapat dilakukan melalui pengamatan menggunakan teleskop canggih untu mengumpulkan data terkait NEOs
- Analisis data dengan machine learning : Menggunakan algoritma machine learning untuk menemukan pola-pola dan karakteristik dari NEOs yang memiliki potensi bahaya sehingga dapat dilakukan indentifikasi atau prediksi pada komet dan asteroid yang berada di dekat bumi

Referensi:

- NASA Nearest Earth Object Classification Using Quantum Machine Learning: A Survey (https://link.springer.com/chapter/10.1007/978-981-99-8289-9_34)
- Predicting Satellite Close Approaches Using Statistical Parameters In The Context Of Artificial Intelligence (https://ntrs.nasa.gov/api/citations/20190029019/downloads/20190029019.pdf)

## Business Understanding

### Problem Statements

1. Identifikasi dan Klasifikasi Ancaman NEOs: Saat ini, tidak ada sistem otomatis yang dapat mengklasifikasikan Near Earth Objects (NEOs) secara efisien berdasarkan potensi ancaman mereka terhadap bumi. Hal ini menghambat kemampuan kita untuk mengambil tindakan pencegahan yang tepat waktu dan efektif.
2. Pola dan Karakteristik NEOs: Kurangnya pemahaman mendalam mengenai pola dan karakteristik NEOs dalam dataset yang tersedia membuat prediksi mengenai perilaku dan dampak potensial NEOs terhadap bumi menjadi sulit dan tidak akurat.
3. Pengolahan Data NEOs yang Efisien: Proses analisis data NEOs yang ada saat ini masih manual dan memakan waktu, sehingga membutuhkan solusi yang lebih efisien melalui penerapan teknologi machine learning untuk analisis dan prediksi yang lebih cepat dan akurat.

### Goals

1. Mengembangkan Model Klasifikasi NEOs: Menerapkan algoritma machine learning untuk mengembangkan model yang dapat mengklasifikasikan NEOs berdasarkan potensi ancamannya terhadap bumi. Model ini bertujuan untuk mengidentifikasi objek yang memerlukan perhatian segera.
2. Mengeksplorasi Pola dalam Dataset NEOs: Melakukan analisis mendalam terhadap dataset NEOs untuk menemukan pola dan karakteristik yang dapat membantu dalam prediksi perilaku dan dampak NEOs. Hasil analisis ini akan meningkatkan pemahaman kita tentang NEOs dan membantu dalam pengambilan keputusan yang lebih baik.
3. Meningkatkan Efisiensi Pengolahan Data NEOs: Mengimplementasikan teknologi machine learning untuk meningkatkan efisiensi pengolahan data NEOs, sehingga proses analisis menjadi lebih cepat dan akurat. Dengan demikian, kita dapat memantau dan memprediksi ancaman NEOs secara real-time dan lebih efektif.

## Data Understanding

Dataset "NASA Nearest Earth Objects" yang digunakan pada proyek ini adalah kumpulan data dari NASA yang mencakup informasi mengenai benda-benda langit yang mendekati orbit bumi, seperti asteroid dan komet. Dataset ini diunduh dari kaggle melalui link berikut : https://www.kaggle.com/datasets/sameepvani/nasa-nearest-earth-objects

### Variabel pada NEOs:

1. id: Identifier unik untuk setiap entri NEO di dataset.
2. name: Nama atau identifikasi lain dari NEO.
3. absolute_magnitude: Magnitudo absolut NEO yang menunjukkan kecerahan intrinsik objek. Biasanya berhubungan dengan ukuran atau diameter NEO.
4. estimated_diameter_min: Estimasi diameter minimum NEO dalam kilometer.
5. estimated_diameter_max: Estimasi diameter maksimum NEO dalam kilometer.
6. is_potentially_hazardous_asteroid: Indikator apakah NEO dianggap berpotensi berbahaya. Nilai boolean (true/false).
7. close_approach_date: Tanggal ketika NEO berada pada jarak terdekatnya dengan bumi.
8. epoch_date_close_approach: Tanggal dalam format epoch untuk pendekatan terdekat.
9. relative_velocity_kms: Kecepatan relatif NEO terhadap bumi dalam kilometer per detik pada saat pendekatan terdekat.
10. miss_distance_km: Jarak terdekat antara NEO dan bumi dalam kilometer pada saat pendekatan terdekat.
11. orbiting_body: Benda langit yang mengorbit bersama NEO, biasanya bumi.
12. sentry_object: Indikator apakah NEO masuk dalam daftar pengawasan Sentry (sistem pemantau NEO NASA). Nilai boolean (true/false).

## Data Preparation

## Modeling

## Evaluation
