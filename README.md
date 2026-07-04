# Heart Disease Classification with Decision Tree

Proyek klasifikasi biner sederhana untuk memprediksi indikasi penyakit jantung pada pasien menggunakan algoritma **Decision Tree**, berdasarkan data medis numerik dari **UCI Heart Disease Dataset (Cleveland subset)**.

Proyek ini dibuat sebagai baseline yang mudah dipahami — fokus pada pemahaman alur klasifikasi dari nol, sebelum masuk ke teknik yang lebih kompleks seperti feature engineering, hyperparameter tuning, atau ensemble methods.

## Dataset

Dataset berisi **303 data pasien** dengan **13 fitur numerik** dan 1 target biner:

| Fitur | Keterangan |
|---|---|
| age | Usia pasien |
| sex | Jenis kelamin (1 = laki-laki, 0 = perempuan) |
| cp | Tipe nyeri dada (0–3) |
| trestbps | Tekanan darah saat istirahat (mm Hg) |
| chol | Kadar kolesterol serum (mg/dl) |
| fbs | Gula darah puasa > 120 mg/dl (1 = ya, 0 = tidak) |
| restecg | Hasil elektrokardiografi saat istirahat (0–2) |
| thalach | Detak jantung maksimum yang dicapai |
| exang | Angina akibat olahraga (1 = ya, 0 = tidak) |
| oldpeak | Depresi ST akibat olahraga relatif terhadap istirahat |
| slope | Kemiringan segmen ST puncak saat olahraga (0–2) |
| ca | Jumlah pembuluh darah utama yang terlihat via fluoroskopi (0–3) |
| thal | Kondisi thalassemia (1 = normal, 2 = defek tetap, 3 = defek reversibel) |
| **target** | 0 = tidak ada penyakit jantung, 1 = ada indikasi penyakit jantung |

Sumber: [UCI Machine Learning Repository - Heart Disease](https://archive.ics.uci.edu/dataset/45/heart+disease)

## Metodologi

Proyek ini sengaja dibuat sederhana untuk membangun pemahaman dasar terlebih dahulu:

- **Tanpa feature selection** — semua 13 fitur digunakan apa adanya
- **Tanpa scaling/normalisasi** — Decision Tree bekerja berdasarkan threshold split pada tiap fitur, sehingga tidak terpengaruh perbedaan skala data
- **Preprocessing minimal** — hanya pengecekan missing value, duplikat data, dan pembagian data latih/uji (80:20, stratified)
- **Model** — `DecisionTreeClassifier` dari scikit-learn dengan parameter default (tanpa hyperparameter tuning)

## Hasil

Model dievaluasi menggunakan accuracy, precision, recall, F1-score, dan confusion matrix. Detail lengkap beserta visualisasi (distribusi target, confusion matrix, feature importance, dan struktur pohon keputusan) dapat dilihat langsung di notebook.

Recall menjadi metrik yang perlu diperhatikan khusus dalam kasus ini, karena kesalahan *false negative* (pasien sakit tapi diprediksi sehat) memiliki risiko yang lebih besar dibanding *false positive* pada konteks medis.

## Struktur Repo

```
├── heart_disease_decision_tree.ipynb   # Notebook utama (analisis, training, evaluasi)
├── heart.csv                           # Dataset
└── README.md
```

## Cara Menjalankan

1. Clone repo ini
   ```bash
   git clone https://github.com/username/heart-disease-decision-tree.git
   cd heart-disease-decision-tree
   ```
2. Install dependency yang dibutuhkan
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
3. Jalankan notebook
   ```bash
   jupyter notebook heart_disease_decision_tree.ipynb
   ```

Atau langsung buka dan jalankan di [Google Colab](https://colab.research.google.com/) dengan mengunggah file notebook dan dataset.

## Keterbatasan & Rencana Pengembangan

Model ini adalah baseline awal dan memiliki beberapa keterbatasan:

- Tanpa hyperparameter tuning, Decision Tree cenderung *overfitting* terhadap data latih
- Evaluasi hanya bergantung pada satu kali pembagian data latih/uji (belum menggunakan cross-validation)
- Ukuran dataset relatif kecil, sehingga generalisasi ke populasi yang lebih luas perlu divalidasi lebih lanjut

Rencana pengembangan selanjutnya:
- Hyperparameter tuning menggunakan GridSearchCV
- Perbandingan dengan model lain (Random Forest, Logistic Regression, SVM)
- Penerapan cross-validation untuk evaluasi yang lebih stabil
- Analisis lanjutan terhadap fitur dengan importance tertinggi

## Lisensi

Dataset digunakan di bawah lisensi CC BY 4.0 dari UCI Machine Learning Repository.
