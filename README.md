# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[NI KADEK DWIPAYANTI]`
- **NIM:** `[2515091124]`
- **Program Studi:** `[SISTEM INFORMASI]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

Dataset yang digunakan adalah “data_startup_saas.csv” yang berisi 650 observasi dengan 6 variabel. Fokus analisis adalah hubungan antara pendapatan tahunan (Pendapatan_Tahunan_Miliar_IDR) sebagai variabel dependen dan biaya akuisisi pelanggan (Biaya_Akuisisi_Pelanggan_Juta_IDR) sebagai variabel independen. Tujuan proyek: menggambarkan karakteristik data (deskriptif), menguji kekuatan dan arah hubungan (korelasi), serta memodelkan dan mengevaluasi kemampuan prediksi (regresi linier).     
---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...* dari Pendapatanan_Tahunan_Miliar_IDR di dapatkan Mean:31,88, Median:31,31, Modus:1,87
  - *Interpretasi:* Nilai mean sebesar 31,88 miliar IDR diperoleh dari hasil pembagian total pendapatan tahunan seluruh startup dengan jumlah observasi. Nilai median sebesar 31,31 miliar IDR merupakan nilai tengah setelah data diurutkan. Sementara itu, nilai modus sebesar 1,87 miliar IDR menunjukkan pendapatan yang paling sering muncul dalam dataset.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - *Interpretasi:* Nilai standar deviasi sebesar 19,79 miliar IDR menunjukkan bahwa pendapatan tahunan startup memiliki variasi yang cukup tinggi dari nilai rata-ratanya. Nilai range sebesar 65,9 miliar IDR (1 hingga 66,9 miliar IDR) menandakan rentang pendapatan yang sangat lebar. Selain itu, jarak antar kuartil yang cukup besar (Q3 − Q1), yaitu dari 14,3 miliar IDR hingga sekitar 48 miliar IDR, menunjukkan bahwa sebagian besar data tersebar luas di sekitar nilai tengah. Hal ini mengindikasikan bahwa pendapatan startup tidak homogen, di mana sebagian besar berada pada tingkat menengah, sementara sebagian lainnya memiliki pendapatan yang jauh lebih tinggi.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results/histogram_Pendapatan_Tahunan_Miliar_IDR
  - /results/boxplot_Pendapatan_Tahunan_Miliar_IDR
  - *Interpretasi:* Histogram menunjukkan sebaran pendapatan tahunan yang cukup luas dan tidak sepenuhnya simetris, dengan nilai rata-rata (mean) sebesar 31,88 miliar IDR yang berada pada rentang pendapatan menengah. Boxplot memperlihatkan jarak antar kuartil yang cukup besar (Q3 − Q1), yang menandakan variasi pendapatan startup yang tinggi.
### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*147e-14
  - *Interpretasi:* Nilai p-value adalah 1,47e-14 lebih kecil dari tingkat signifikansi 0,05, sehingga dapat disimpulkan bahwa data tidak terdistribusi normal. Implikasinya, asumsi normalitas tidak terpenuhi, namun analisis korelasi dan regresi tetap dapat dilakukan karena jumlah sampel yang besar.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results/qqplot_Pendapatan_Tahunan_Miliar_IDR
  - *Interpretasi:* Terlihat bahwa titik-titik data tidak sepenuhnya mengikuti garis lurus. Penyimpangan paling jelas terjadi pada bagian bawah grafik, yang merepresentasikan pendapatan rendah pada kisaran 0–10 miliar IDR, sesuai dengan nilai modus sebesar 1,87 miliar IDR sebagai pendapatan yang paling sering muncul. Pada bagian tengah grafik, titik-titik relatif lebih mendekati garis diagonal, menunjukkan bahwa sebagian data berada di sekitar nilai tengah, meskipun nilai mean sebesar 31,88 miliar IDR jauh lebih tinggi dibandingkan modus. Sementara itu, pada bagian atas grafik tampak penyimpangan yang disebabkan oleh keberadaan beberapa startup dengan pendapatan sangat tinggi, yaitu di atas 65 miliar IDR. Pola ini diperkuat oleh standar deviasi sebesar 19,79 milia…
### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*Koefisien Korelasi (r): 0,996
  - *Interpretasi:* korelasi antara Pendapatan_Tahunan_Miliar_IDR dan Biaya_Akuisisi_Pelanggan_Juta_IDR korelasinya positif kuat.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR
  - *Interpretasi:* Pola pada scatter plot mendukung hasil koefisien korelasi yang diperoleh. Titik-titik data membentuk pola menaik yang hampir linear, di mana peningkatan pendapatan tahunan startup diikuti oleh peningkatan biaya akuisisi pelanggan. Garis tren linear berwarna merah yang sejajar dengan sebaran titik menunjukkan adanya hubungan positif yang sangat kuat antara kedua variabel. Selain itu, titik-titik data relatif rapat di sekitar garis tren, yang mengindikasikan bahwa hubungan antar variabel bersifat konsisten dan sejalan dengan nilai koefisien korelasi yang tinggi, sehingga hasil visualisasi memperkuat temuan analisis korelasi secara statistik.
### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Biaya_Akuisisi_Pelanggan_Juta_IDR = 3,57 + 3,02 Pendapatan_Tahunan_Miliar_IDR
  - *Interpretasi:* Persamaan regresi menunjukkan bahwa intercept (b₀) sebesar 3,57 menandakan biaya akuisisi pelanggan diperkirakan sebesar 3,57 juta IDR ketika pendapatan tahunan startup = 0 miliar IDR; nilai ini bersifat matematis karena secara praktis startup dengan pendapatan nol tetap memerlukan biaya akuisisi. Sementara itu, slope (b₁) sebesar 3,02 menunjukkan bahwa setiap kenaikan 1 miliar IDR pada pendapatan tahunan akan meningkatkan biaya akuisisi pelanggan sekitar 3,02 juta IDR, menandakan adanya hubungan positif yang kuat antara pendapatan dan biaya akuisisi pelanggan.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*0.991
  - *Interpretasi:* Variasi dari variabel dependen yang dapat dijelaskan oleh model regresi 99.1%
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results/plot_regresi_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR
  - *Interpretasi:* Berdasarkan scatter plot dengan garis regresi, terlihat bahwa titik-titik data menyebar mengikuti pola linear yang jelas, di mana peningkatan pendapatan tahunan diikuti oleh peningkatan biaya akuisisi pelanggan. Garis regresi merah merepresentasikan tren linear hubungan kedua variabel, memperkuat hasil analisis regresi dan menunjukkan bahwa model dapat digunakan untuk memprediksi biaya akuisisi pelanggan berdasarkan pendapatan tahunan startup.
---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
Berdasarkan hasil analisis deskriptif, uji normalitas, korelasi, dan regresi, dapat disimpulkan bahwa Pendapatan_Tahunan_Miliar_IDR memiliki sebaran yang luas dan tidak homogen, dengan sebagian besar startup berada pada tingkat pendapatan menengah, namun terdapat beberapa startup dengan pendapatan sangat tinggi. Nilai mean sebesar 31,88 miliar IDR jauh lebih tinggi dibanding modus 1,87 miliar IDR, didukung oleh standar deviasi 19,79 miliar IDR dan jarak antar kuartil yang cukup besar, menunjukkan variasi pendapatan yang tinggi. Uji Shapiro-Wilk dan plot Q-Q menegaskan bahwa data Pendapatan_Tahunan_Miliar_IDR tidak terdistribusi normal, namun analisis korelasi dan regresi tetap valid karena jumlah sampel besar. Analisis korelasi menunjukkan hubungan positif yang sangat kuat (r = 0,996) antara Pendapatan_Tahunan_Miliar_IDR dan Biaya_Akuisisi_Pelanggan_Juta_IDR, yang diperkuat oleh scatter plot dengan pola menaik hampir linear. Model regresi linier sederhana menegaskan bahwa setiap kenaikan 1 miliar IDR pada Pendapatan_Tahunan_Miliar_IDR meningkatkan Biaya_Akuisisi_Pelanggan_Juta_IDR sebesar 3,02 juta IDR, dengan Adjusted R-squared 0,991, menandakan bahwa 99,1% variasi Biaya_Akuisisi_Pelanggan_Juta_IDR dapat dijelaskan oleh Pendapatan_Tahunan_Miliar_IDR. Secara keseluruhan, temuan ini menegaskan bahwa pendapatan startup sangat bervariasi, dan pengelolaan biaya akuisisi pelanggan perlu disesuaikan dengan tingkat pendapatan untuk mendukung pertumbuhan finansial yang optimal.
