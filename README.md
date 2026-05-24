# App Review Sentiment Analysis: MyXL Application

## 🎯 Overview
Proyek ini melakukan analisis sentimen end-to-end terhadap ulasan pengguna aplikasi MyXL yang diambil dari Google Play Store. Menggunakan metode text mining dan algoritma klasifikasi machine learning, proyek ini bertujuan untuk memetakan kepuasan pengguna serta mengekstrak feedback penting bagi pengembangan kualitas aplikasi.

---

## 💻 Metodologi (STAR Framework)

### 1. Situation & Task
Membaca ulasan pengguna satu per satu pada aplikasi populer seperti MyXL sangat tidak efisien. Proyek ini bertujuan untuk otomatisasi klasifikasi ulasan ke dalam sentimen Positif dan Negatif guna mendapatkan insight operasional secara cepat dan akurat.

### 2. Action (Data & Text Preprocessing)
* **Data Acquisition:** Mengambil data ulasan Google Play Store menggunakan library `google_play_scraper` di Python (Total: 50.000 data ulasan awal).
* **Data Selection & Labeling:** Memfilter ulasan khusus tahun 2023 dan melakukan pelabelan berdasarkan rating. Skor <= 3 dikategorikan sebagai **Negatif**, sedangkan skor > 3 sebagai **Positif**. Setelah pembersihan data hilang, diperoleh total **30.648 data bersih**.
* **Text Preprocessing:** 1. *Case Folding:* Menyeragamkan seluruh teks ulasan menjadi huruf kecil.
  2. *Stop Word Removal:* Menghapus kata umum yang tidak memiliki makna kontekstual (seperti "yang", "dan", "di", "dari").
  3. *Tokenizing:* Memecah teks ulasan menjadi potongan token kata.
  4. *Stemming:* Mengubah kata berimbuhan menjadi kata dasar menggunakan library `Sastrawi` (Algoritma Nazief & Adriani).
* **Modeling:** Melakukan pelatihan model klasifikasi menggunakan algoritma **Multinomial Naïve Bayes (MultinomialNB)**.

### 3. Result & Business Insights
* **Performa Model:** Algoritma MultinomialNB berhasil menghasilkan performa klasifikasi yang sangat baik dengan **Akurasi 87%**, **Precision 87%**, **Recall 90%**, dan **F1-Score 88%**.
* **Proporsi Sentimen:** Ditemukan bahwa kelas Negatif mendominasi dengan **17.127 ulasan**, sedangkan kelas Positif sebanyak **13.521 ulasan**. Ini menandakan mayoritas pengguna rata-rata menyampaikan keluhan operasional sepanjang 2023.
* **Analisis Word Cloud:**
  * Pada ulasan **Positif**, kata yang paling sering muncul adalah *"bagus"*, *"mantap"*, dan *"ok"*.
  * Pada ulasan **Negatif**, keluhan berpusat pada kata kunci operasional seperti *"paket"*, *"kuota"*, *"beli"*, *"gagal"*, dan *"eror"*. Insight ini sangat berharga bagi tim developer untuk melakukan perbaikan sistem transaksi paket dan kuota.
