## Klasifikasi Kebutuhan Pendampingan Belajar Mahasiswa
## 1. Judul dan Deskripsi Proyek
Judul: Klasifikasi Kebutuhan Pendampingan Belajar Mahasiswa Berdasarkan Aktivitas Akademik

Proyek ini menerapkan Machine Learning untuk mengklasifikasikan mahasiswa ke dalam dua kategori, yaitu “Ya” (terindikasi membutuhkan pendampingan belajar) dan “Tidak” (belum terindikasi membutuhkan pendampingan), berdasarkan indikator aktivitas dan performa akademik. Algoritma yang digunakan adalah Decision Tree dan Random Forest.
Proyek ini dibuat sebagai contoh penerapan teknologi untuk membantu mengenali indikator akademik yang dapat menjadi bahan pertimbangan awal dalam memberikan dukungan belajar.
## 2. Anggota Kelompok
Nama anggota kelompok:
1. CHINTIA ANDANA LESTARI - F1G125027
2. NADIA ILMIRAH          - F1G125044
3. AMAL                   - F1G125024

## 3. Latar Belakang dan Keterkaitan dengan SDGs 4
Setiap mahasiswa memiliki kondisi dan kebiasaan belajar yang berbeda. Kehadiran, waktu belajar, penyelesaian tugas, dan nilai ujian dapat menjadi beberapa indikator untuk melihat apakah mahasiswa mungkin memerlukan dukungan akademik. Namun, mengenali kebutuhan tersebut secara konsisten bukan hal yang selalu mudah.

Melalui proyek ini, data akademik dianalisis menggunakan algoritma klasifikasi untuk menghasilkan indikasi awal kebutuhan pendampingan belajar. Hasilnya dapat membantu proses identifikasi, tetapi tidak dimaksudkan untuk menggantikan penilaian dosen, pembimbing akademik, atau mahasiswa itu sendiri.

Proyek ini berkaitan dengan Sustainable Development Goals (SDGs) 4: Pendidikan Berkualitas, yang mendorong pendidikan yang inklusif, adil, dan berkualitas serta kesempatan belajar sepanjang hayat. Pemanfaatan data untuk mengenali kemungkinan kebutuhan dukungan belajar dapat menjadi salah satu langkah pendukung peningkatan layanan akademik. Meski demikian, proyek ini merupakan prototipe dan belum membuktikan secara langsung peningkatan hasil pendidikan.

## 4. Tujuan
- Menerapkan algoritma Machine Learning untuk klasifikasi kebutuhan pendampingan belajar.
- Menggunakan indikator aktivitas dan performa akademik sebagai fitur model.
- Membandingkan performa algoritma Decision Tree dan Random Forest.
- Menghasilkan prediksi awal yang dapat menjadi bahan pertimbangan dalam merancang dukungan belajar.
- Menunjukkan contoh penerapan teknologi berbasis data yang relevan dengan SDGs 4.
## 5. Dataset
Nama file dataset: student_performance_clean.csv
Dataset yang digunakan berisi 12.467 baris dan 16 kolom awal. 
Dataset berisi indikator terkait aktivitas belajar dan performa akademik.
Fitur yang digunakan model:
Nama kolom	Keterangan
StudyHours	Jam belajar
Attendance	Kehadiran
AssignmentCompletion	Penyelesaian tugas
OnlineCourses	Aktivitas/jumlah kursus online
Discussions	Aktivitas diskusi
ExamScore	Nilai ujian


Target klasifikasi
Membuat kolom target Perlu_Pendampingan menggunakan aturan berikut:
- Ya: jika Attendance < 70, atau AssignmentCompletion < 60, atau ExamScore < 60, atau StudyHours < 10.
- Tidak: jika tidak ada kondisi tersebut yang terpenuhi.
Hasil pembentukan target pada dataset:
- Ya: 7.540 data
- Tidak: 4.927 data
Pemeriksaan awal menunjukkan tidak ada nilai kosong dan tidak ada baris duplikat pada dataset yang digunakan.
Catatan metodologis: label target dibentuk langsung dari ambang batas beberapa fitur yang juga digunakan untuk melatih model. Karena itu, skor evaluasi yang sangat tinggi dapat terjadi karena model mempelajari kembali aturan tersebut. Skor ini belum membuktikan bahwa model mampu mengenali kebutuhan pendampingan nyata. Untuk pengembangan lebih lanjut, gunakan label yang divalidasi secara independen dan uji pada data yang sesuai.
## 6. Hasil Evaluasi Model
Dataset dibagi menjadi 80% data training dan 20% data testing dengan random_state=42 serta stratifikasi target.
- Data training: 9.973 baris
- Data testing: 2.494 baris
Hasil evaluasi yang tercatat pada notebook:
Metrik	Decision Tree	Random Forest
Accuracy	1,00 (100%)	1,00 (100%)
Precision	1,00 (100%)	1,00 (100%)
Recall	1,00 (100%)	1,00 (100%)
F1-score	1,00 (100%)	1,00 (100%)


Kedua model memprediksi seluruh 2.494 data testing dengan benar berdasarkan label target yang dibuat. Hasil ini sesuai dengan output evaluasi.
## 7. Kesimpulan Performa
Decision Tree dan Random Forest sama-sama memperoleh accuracy, precision, recall, dan F1-score sebesar 100%. Jadi, berdasarkan pengujian tersebut, belum ada perbedaan performa di antara kedua model.
Namun, nilai sempurna perlu ditafsirkan secara hati-hati karena label Perlu_Pendampingan dibentuk menggunakan ambang batas pada Attendance, AssignmentCompletion, ExamScore, dan StudyHours, yang juga menjadi fitur input. Kondisi ini membuat tugas klasifikasi relatif mudah bagi model dan berisiko menghasilkan evaluasi yang terlalu optimistis untuk penggunaan nyata.
Kesimpulan: kedua algoritma berhasil mempelajari aturan target yang diterapkan. Validasi menggunakan label independen dan data yang lebih representatif masih diperlukan sebelum model digunakan untuk menentukan kebutuhan pendampingan mahasiswa secara nyata.
## 8. Teknologi yang Digunakan
- Python — bahasa pemrograman.
- Google Colab / Jupyter Notebook — lingkungan menjalankan kode.
- Pandas — membaca dan mengolah dataset.
- NumPy — operasi numerik dan pembentukan target.
- Matplotlib dan Seaborn — visualisasi hasil dan confusion matrix.
- Scikit-learn — pembagian data, pelatihan model, prediksi, dan evaluasi.
- Joblib — menyimpan model yang telah dilatih dalam format .pkl.
## 9. Cara Menjalankan
1. Buka notebook Klasifikasi Kebutuhan Pendampingan Belajar (1).ipynb di Google Colab.
2. Siapkan file dataset student_performance_clean.csv.
3. Jalankan sel notebook secara berurutan.
4. Saat diminta, unggah dataset CSV.
5. Periksa proses pemahaman data dan preprocessing.
6. Jalankan pelatihan Decision Tree dan Random Forest.
7. Amati tabel evaluasi, grafik perbandingan, dan confusion matrix.
8. Coba bagian prediksi data mahasiswa baru.
Notebook juga menyimpan model sebagai:
- model_decision_tree_pendampingan.pkl
- model_random_forest_pendampingan.pkl# Proyek_AI
