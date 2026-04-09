# Credit Loss Prediction - Machine Learning Final Project
## Project Overview
Proyek ini bertujuan untuk membangun model machine learning yang mampu memprediksi probabilitas nasabah yang akan mengalami gagal bayar kredit (default). Proyek ini dikembangkan sebagai bagian dari AI-ML Weekly Class oleh Group 2.
## Business Case
Tujuan utama adalah mengidentifikasi nasabah berisiko tinggi untuk mendukung sistem pengambilan keputusan, deteksi dini risiko kredit, dan mengurangi potensi kerugian finansial perusahaan.

## Dataset Metadata
- Ukuran Data: 10.000 baris data nasabah.
- Fitur Utama: customer_id, credit_lines_outstanding, loan_amt_outstanding, total_debt_outstanding, income, years_employed, fico_score.
- Target Variabel: default (1: Gagal Bayar, 0: Lancar).
- Kondisi Data: Dataset bersifat imbalanced (tidak seimbang) dengan ~18.5% gagal bayar dan 81.5% lancar.

## Methodology & Feature Engineering
Proses pengolahan data difokuskan pada validasi integritas data dan stabilitas distribusi:
1. Data Cleaning: Memastikan tidak ada nilai yang hilang (missing values) atau duplikat.
2. Handling Outliers: Menggunakan metode Capping dengan teknik IQR (Interquartile Range) untuk memitigasi nilai ekstrem pada fitur finansial.
3. New Features:
   - Debt-to-Income (DTI) Ratio: Total utang dibandingkan pendapatan.
    - Loan-to-Income (LTI) Ratio: Jumlah pinjaman dibandingkan pendapatan.
4. Feature Binning: Mengelompokkan fico_score ke dalam kategori (Poor, Fair, Good, dll.) untuk menyederhanakan hubungan kompleks.
5. Encoding & Scaling: One-hot encoding untuk fitur kategorikal dan StandardScaler untuk fitur numerik.
6. Feature Selection: Menghapus fitur dengan multikolinearitas tinggi dan potensi data leakage (seperti credit_lines_outstanding dan total_debt_outstanding).

## Model & Evaluation
Model utama yang diuji meliputi Gradient Boosting, XGBoost, AdaBoost, Random Forest, dan Logistic Regression.
- Key Performance (Gradient Boosting):
- Akurasi: 82% pada data testing.Recall (Kelas Default): 0.19.
- Insight Model: Meskipun akurasi umum baik, model masih cenderung bias terhadap nasabah lancar dan lemah dalam mendeteksi nasabah berisiko tinggi karena ketidakseimbangan data.

## Insights & Recommendations
- Prediktor Utama: Beban utang total dan rasio keuangan terhadap pendapatan merupakan indikator risiko yang lebih akurat dibanding nominal pendapatan tahunan.
- Rekomendasi Bisnis: Model sebaiknya digunakan sebagai Decision Support System (alat pendukung), bukan penentu keputusan final.
- Pengembangan Lanjut: Diperlukan penyesuaian bobot kelas (class weight) atau teknik penanganan data imbalanced lainnya untuk meningkatkan recall pada nasabah gagal bayar.
