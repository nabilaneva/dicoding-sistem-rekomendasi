# 📊 Machine Learning Project Report - Nabila Neva Rahmawati

## 🛍️ Project Overview

Dalam industri e-commerce kecantikan seperti Sociolla, konsumen dihadapkan pada ribuan pilihan produk yang dapat membingungkan. Proyek ini mengembangkan sistem rekomendasi produk berbasis **content-based filtering** untuk menyarankan produk serupa berdasarkan karakteristik seperti nama produk, kategori, dan deskripsi. Dengan menggunakan TF-IDF dan Cosine Similarity, sistem dapat merekomendasikan produk meski tanpa riwayat interaksi pengguna. Pendekatan ini relevan di e-commerce Indonesia dan dapat meningkatkan konversi penjualan di platform seperti Sociolla.

### 📚 Referensi:

- [1] Ridhwanullah, D., dkk. (2024) - _Content-Based Filtering pada Sistem Rekomendasi Buku Informatika_  
  👉 https://www.p3m.sinus.ac.id/jurnal/index.php/e-jurnal_SINUS/article/view/840
- [2] Pramesti, D.A.P.D. (2022) - _Penerapan Metode Content-Based Filtering dalam Sistem Rekomendasi Produk E-Commerce_  
  👉 https://ojs.unud.ac.id/index.php/jnatia/article/view/92555

---

## 💼 Business Understanding

### ❓ Problem Statement

Pengguna kesulitan menemukan produk sesuai preferensi karena banyaknya pilihan dan kurangnya personalisasi.

### 🎯 Goals

Memberikan rekomendasi produk yang relevan berdasarkan kategori yang disukai pengguna.

### 🧠 Solution Approach

- **Content-Based Filtering**
  - Menggunakan TF-IDF dan Cosine Similarity untuk menganalisis kesamaan antar produk.
- **Collaborative Filtering (alternatif)**
  - Berdasarkan perilaku pengguna lain menggunakan Matrix Factorization/SVD.

---

## 📊 Data Understanding

- **Sumber Data:** [Kaggle - Sociolla Product Catalog](https://www.kaggle.com/datasets/ibrahimhafizhan/sociolla-all-brands-products-catalog)
- **Jumlah data:** 7.636 baris × 19 kolom
- **Kolom penting:** `brand_name`, `product_name`, `price_range`, `average_rating`, `default_category`, dll.
- **Missing Values:**
  - `price_by_combinations`: 3.549
  - `active_date`: 2.102
  - `average_rating_by_types`: 1.846

---

## 🧹 Data Preparation

- Nilai kosong dihapus dengan `df.dropna()`
- Pengecekan ulang menggunakan `df.isna().sum()`
- Fitur teks (`default_category`) diekstrak dengan **TF-IDF Vectorizer**

---

## 🧠 Modeling

- **Representasi Fitur:**
  - Menggunakan TF-IDF Vectorizer
- **Algoritma Similarity:**
  - Cosine Similarity
- **Mekanisme Rekomendasi:**
  - Mengambil Top-N produk paling mirip berdasarkan skor similarity

### 🎯 Contoh Hasil Rekomendasi untuk "Aloe Vera Clay Mask":

| No  | Product Name                                        | Category  |
| --- | --------------------------------------------------- | --------- |
| 1   | Clay Mask Sebum Control                             | Clay Mask |
| 2   | Alaska Volcano Deep Pores Cleansing Clay Mask       | Clay Mask |
| 3   | [BUNDLE] Jacquelle Disney Princess Ariel edition    | Clay Mask |
| 4   | Butter Clay Mask Moist and Calming Clay Mask        | Clay Mask |
| 5   | Fresh Clarifying Clay Mask                          | Clay Mask |
| 6   | Freeman Bundle Bye, Pores! Mask                     | Clay Mask |
| 7   | Lightening Blue Clay Mask                           | Clay Mask |
| 8   | Feeling Beautiful Anti-Stress Dead Sea Mineral Mask | Clay Mask |
| 9   | Orange Blossom Clay Mask                            | Clay Mask |
| 10  | Rose and Sea Buckthorn Pink Mask                    | Clay Mask |

---

## ✅ Evaluation

- **Metode evaluasi:** Precision@k
- **Hasil:** Semua rekomendasi (10 produk) masuk dalam kategori yang sama (Clay Mask)
- **Precision@10 = 100%**

---

## ✅ Kelebihan & Kekurangan

### 👍 Kelebihan:

- Berfungsi meskipun data perilaku pengguna terbatas
- Mudah dipahami dan dapat menjelaskan alasan rekomendasi
- Cocok untuk produk baru

### 👎 Kekurangan:

- Tidak mempertimbangkan perilaku pengguna
- Terbatas pada produk yang sangat mirip
- Bergantung pada deskripsi/kategori produk

---
