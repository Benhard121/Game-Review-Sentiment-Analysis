📊 Ringkasan Dataset & MetodologiPengumpulan Data: Mengambil sebanyak 3.500+ ulasan terbaru dari aplikasi Roblox di Google Play Store menggunakan pustaka google-play-scraper [cite: 2].Pelabelan Otomatis (Labeling):Rating 4 - 5 bintang $\rightarrow$ Positif (1)Rating 1 - 2 bintang $\rightarrow$ Negatif (0)Rating 3 bintang $\rightarrow$ Dinetralkan/dihapus untuk mempertegas batas kelas (diperoleh 3.274 data bersih setelah pelabelan) [cite: 3].Pembersihan Teks (Text Preprocessing & Normalisasi Slang):Case folding (mengecilkan huruf) [cite: 3].Pembersihan tautan URL, angka, dan simbol/karakter khusus [cite: 3].Kamus Normalisasi Slang Bahasa Indonesia khusus gim (misal: mengubah “gak”, “ga”, “gk” $\rightarrow$ “tidak”; “bgt” $\rightarrow$ “banget”; “lag”, “ngeleg” $\rightarrow$ “macet”, dll.) untuk mendongkrak performa model [cite: 3].Ekstraksi Fitur & Pemodelan:TF-IDF Vectorizer dengan kombinasi n-gram (1, 3) untuk menangkap konteks frasa (misal: “tidak bagus banget”) [cite: 3].Logistic Regression dengan parameter class_weight='balanced' untuk menangani ketimpangan data antara ulasan positif dan negatif [cite: 3].Akurasi Model: Mencapai 85.42% pada data uji (testing set) [cite: 3].🛠️ Instalasi & Ketergantungan (Requirements)Pastikan Anda telah menginstal pustaka Python yang dibutuhkan dengan menjalankan perintah berikut:Bashpip install -r requirements.txt
Isi dari requirements.txt:Plaintextgoogle-play-scraper
pandas
numpy
scikit-learn
matplotlib
seaborn
sastrawi
imbalanced-learn
🚀 Cara Menjalankan ProyekScraping Data: Buka dan jalankan sel di dalam File kode scraping.ipynb jika Anda ingin mengumpulkan ulang dataset segar dari Google Play Store [cite: 2, 4].Pelatihan Model: Jalankan Notebook pelatihan model.ipynb secara berurutan mulai dari pembersihan teks, pembagian data (train-test split dengan rasio 85:15), hingga pelatihan model Logistic Regression [cite: 3, 4].Uji Coba Prediksi (Inference): Gunakan kode pada Cell inference.ipynb untuk menguji model dengan kalimat ulasan baru secara mandiri [cite: 1, 4]:Python# Contoh Pengujian
prediksi_ulasan("Gamenya seru banget, grafiknya keren!")
prediksi_ulasan("Sering lag dan tiba-tiba keluar sendiri, payah!")
💡 Contoh Hasil PrediksiPlaintextUlasan: 'Gamenya seru banget, grafiknya keren!'
Hasil Prediksi: POSITIF (93.43%)
------------------------------
Ulasan: 'Sering lag dan tiba-tiba keluar sendiri, payah!'
Hasil Prediksi: NEGATIF (78.05%)
Dikembangkan sebagai bagian dari eksplorasi Machine Learning dan Natural Language Processing (NLP).
