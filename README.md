# Klasifikasi Spesies Iris

Proyek machine learning untuk mengklasifikasikan spesies bunga Iris menggunakan algoritma **Decision Tree** dan **Random Forest**.

---

## Deskripsi

Dataset Iris terdiri dari 150 sampel bunga Iris dengan 4 fitur pengukuran morfologi. Tujuan proyek ini adalah membangun dan membandingkan model klasifikasi untuk memprediksi spesies bunga berdasarkan fitur-fitur tersebut.

**Spesies yang diklasifikasikan:**
- Iris-setosa
- Iris-versicolor
- Iris-virginica

---

## Struktur Proyek

```
KlasifikasiSpesiesIris.ipynb   # Notebook utama
README.md                      # Dokumentasi proyek
```

---

## Dataset

Dataset yang digunakan: [Iris Species](https://www.kaggle.com/datasets/uciml/iris) — tersedia di Kaggle (`Iris.csv`)

| Fitur          | Deskripsi                     |
|----------------|-------------------------------|
| SepalLengthCm  | Panjang sepal (cm)            |
| SepalWidthCm   | Lebar sepal (cm)              |
| PetalLengthCm  | Panjang petal (cm)            |
| PetalWidthCm   | Lebar petal (cm)              |
| Species        | Label spesies (target)        |

**Pembagian data:** 70% data latih / 30% data uji (`random_state=42`)

---

## Library yang Digunakan

```
pandas
scikit-learn
matplotlib
seaborn
```

---

## Alur Kerja

### 1. Memuat dan Mempersiapkan Data
- Memuat dataset `Iris.csv` menggunakan pandas
- Memeriksa nilai yang hilang
- Mengkodekan label target dengan `LabelEncoder`
- Membagi data menjadi data latih dan data uji

### 2. Decision Tree Classifier
- Melatih model `DecisionTreeClassifier`
- Evaluasi menggunakan akurasi, confusion matrix, dan classification report
- Visualisasi struktur pohon keputusan

### 3. Random Forest Classifier
- Melatih model `RandomForestClassifier`
- Evaluasi menggunakan akurasi, confusion matrix, dan classification report
- Analisis pentingnya fitur (`feature_importances_`)

### 4. Analisis dan Perbandingan Model
- Membandingkan akurasi kedua model
- Diskusi kelebihan dan kekurangan masing-masing algoritma
- Pengaruh parameter `n_estimators` pada Random Forest

---

## Hasil

Kedua model berhasil mencapai akurasi sempurna pada data uji:

| Model          | Akurasi |
|----------------|---------|
| Decision Tree  | 1.0000  |
| Random Forest  | 1.0000  |

### Fitur Terpenting (Random Forest)
Berdasarkan `feature_importances_`, fitur yang paling berpengaruh dalam klasifikasi adalah:
1. **PetalLengthCm** — paling dominan
2. **PetalWidthCm** — sangat signifikan
3. SepalLengthCm
4. SepalWidthCm

> Ini konsisten dengan pengetahuan botani bahwa dimensi kelopak (petal) merupakan pembeda utama antar spesies Iris.

---

## Perbandingan Model

| Aspek                  | Decision Tree        | Random Forest              |
|------------------------|----------------------|----------------------------|
| Interpretasi           | ✅ Mudah             | ❌ Sulit                   |
| Kecepatan pelatihan    | ✅ Cepat             | ❌ Lebih lambat            |
| Normalisasi data       | ✅ Tidak diperlukan  | ✅ Tidak diperlukan        |
| Overfitting            | ❌ Rentan            | ✅ Lebih tahan             |
| Akurasi                | Tinggi               | Lebih stabil & tinggi      |
| Kebutuhan memori       | Rendah               | Lebih besar                |

---

## Catatan

Akurasi 1.0000 pada dataset Iris perlu diwaspadai sebagai potensi **overfitting**, terutama pada Decision Tree. Dataset Iris memang tergolong sederhana dan mudah dipisahkan, sehingga hasil sempurna tidak serta-merta berarti model akan bekerja optimal pada data baru yang belum pernah dilihat sebelumnya.

---

## Cara Menjalankan

1. Clone atau unduh repositori ini
2. Pastikan semua library sudah terpasang:
   ```bash
   pip install pandas scikit-learn matplotlib seaborn
   ```
3. Letakkan file `Iris.csv` di direktori `/content/sample_data/` (Google Colab) atau sesuaikan path-nya
4. Jalankan notebook `KlasifikasiSpesiesIris.ipynb` secara berurutan dari sel pertama
