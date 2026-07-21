[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Benhard121/Game-Review-Sentiment-Analysis/blob/main/Notebook%20pelatihan%20model.ipynb)

# 🎮 Game Review Sentiment Analysis (Roblox Reviews)

Proyek *Machine Learning* dan *Natural Language Processing* (NLP) untuk melakukan klasifikasi otomatis sentimen ulasan pengguna terhadap gim (studi kasus: **Roblox**) pada Google Play Store. Model ini dirancang untuk mengelompokkan ulasan menjadi kategori **Positif** atau **Negatif** dengan akurasi tinggi menggunakan pendekatan *Text Preprocessing* khusus dan algoritma *Logistic Regression*.

---

## 📂 Struktur Proyek
```text
Proyek Analisis Sentimen/
│
├── File kode scraping.ipynb        # Notebook untuk pengumpulan data ulasan (Google Play Scraper)
├── Notebook pelatihan model.ipynb    # Notebook pembersihan data, pelabelan, ekstraksi TF-IDF, dan training model
├── Cell inference.ipynb            # Notebook / potongan kode untuk pengujian/prediksi ulasan mandiri
├── roblox_reviews_raw.csv          # Dataset mentah hasil scraping (3.500+ data)
└── requirements.txt                # Daftar dependensi pustaka Python
```

---

## 📊 Ringkasan Dataset & Metodologi
1. **Pengumpulan Data:** Mengambil sebanyak **3.500+ ulasan** terbaru dari aplikasi Roblox di Google Play Store menggunakan pustaka `google-play-scraper` [cite: 2].
2. **Pelabelan Otomatis (Labeling):**
   - **Rating 4 - 5 bintang** $
ightarrow$ **Positif (1)**
   - **Rating 1 - 2 bintang** $
ightarrow$ **Negatif (0)**
   - **Rating 3 bintang** $
ightarrow$ Dinetralkan/dihapus untuk mempertegas batas kelas (diperoleh 3.274 data bersih setelah pelabelan) [cite: 3].
3. **Pembersihan Teks (*Text Preprocessing* & Normalisasi *Slang*):**
   - *Case folding* (mengecilkan huruf) [cite: 3].
   - Pembersihan tautan URL, angka, dan simbol/karakter khusus [cite: 3].
   - **Kamus Normalisasi Slang Bahasa Indonesia** khusus gim (misal: mengubah *“gak”*, *“ga”*, *“gk”* $
ightarrow$ *“tidak”*; *“bgt”* $
ightarrow$ *“banget”*; *“lag”*, *“ngeleg”* $
ightarrow$ *“macet”*, dll.) untuk mendongkrak performa model [cite: 3].
4. **Ekstraksi Fitur & Pemodelan:**
   - **TF-IDF Vectorizer** dengan kombinasi n-gram `(1, 3)` untuk menangkap konteks frasa (misal: *“tidak bagus banget”*) [cite: 3].
   - **Logistic Regression** dengan parameter `class_weight='balanced'` untuk menangani ketimpangan data antara ulasan positif dan negatif [cite: 3].
   - **Akurasi Model:** Mencapai **85.42%** pada data uji (*testing set*) [cite: 3].

---

## 🛠️ Instalasi & Ketergantungan (*Requirements*)

Pastikan Anda telah menginstal pustaka Python yang dibutuhkan dengan menjalankan perintah berikut:

```bash
pip install -r requirements.txt
```

Isi dari `requirements.txt`:
```text
google-play-scraper
pandas
numpy
scikit-learn
matplotlib
seaborn
sastrawi
imbalanced-learn
```

---

## 🚀 Cara Menjalankan Proyek

1. **Scraping Data:** Buka dan jalankan sel di dalam `File kode scraping.ipynb` jika Anda ingin mengumpulkan ulang dataset segar dari Google Play Store [cite: 2, 4].
2. **Pelatihan Model:** Jalankan `Notebook pelatihan model.ipynb` secara berurutan mulai dari pembersihan teks, pembagian data (*train-test split* dengan rasio 85:15), hingga pelatihan model *Logistic Regression* [cite: 3, 4].
3. **Uji Coba Prediksi (*Inference*):** Gunakan kode pada `Cell inference.ipynb` untuk menguji model dengan kalimat ulasan baru secara mandiri [cite: 1, 4]:

```python
# Contoh Pengujian
prediksi_ulasan("Gamenya seru banget, grafiknya keren!")
prediksi_ulasan("Sering lag dan tiba-tiba keluar sendiri, payah!")
```

---

## 💡 Contoh Hasil Prediksi
```text
Ulasan: 'Gamenya seru banget, grafiknya keren!'
Hasil Prediksi: POSITIF (93.43%)
------------------------------
Ulasan: 'Sering lag dan tiba-tiba keluar sendiri, payah!'
Hasil Prediksi: NEGATIF (78.05%)
```

---
*Dikembangkan sebagai bagian dari eksplorasi Machine Learning dan Natural Language Processing (NLP).*
