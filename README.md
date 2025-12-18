# 📈 Proyek MLOps: Prediksi Arah Harga Saham

Selamat datang di **Proyek MLOps – Prediksi Arah Harga Saham**.
Proyek ini dibuat untuk menunjukkan implementasi **pipeline MLOps end-to-end** dengan fokus utama pada **operasionalisasi model (deployment, CI/CD, dan monitoring)**, bukan pada kompleksitas pemodelan.

Aplikasi akhir berupa **web app Streamlit** yang dapat memprediksi **arah harga saham (Naik / Turun)** berdasarkan data historis saham.

---

## 🎯 Tujuan Proyek

Tujuan utama proyek ini adalah:

* Menerapkan konsep **MLOps** dalam proyek Machine Learning sederhana
* Mengintegrasikan proses **training → versioning → deployment** model
* Menyediakan aplikasi prediksi dalam bentuk **web app (Streamlit)**
* Mengemas aplikasi menggunakan **Docker** agar environment konsisten
* Menerapkan **CI/CD menggunakan GitHub Actions**
* Menjamin aplikasi **reproducible & mudah dijalankan** oleh user lain

Proyek ini dirancang agar **mudah dipahami oleh pemula**, khususnya untuk tugas kelompok mata kuliah MLOps.

---

## 🏗️ Arsitektur Sistem

```
User (Browser)
     ↓
Streamlit Web App
     ↓
Load Trained Model
     ↓
Prediksi Arah Harga Saham (Up / Down)
     ↓
Hasil Ditampilkan ke User
```

Alur pengembangan model:

```
Data Historis Saham
        ↓
Preprocessing Data
        ↓
Feature Engineering
        ↓
Training Model
        ↓
Model Terbaik (model.pkl)
        ↓
Deployment (Streamlit + Docker)
        ↓
CI/CD (GitHub Actions)
```

---

## 🖥️ Tampilan Aplikasi

Aplikasi dapat diakses melalui browser dan memiliki fitur:

* Input **ticker saham** (contoh: `ASII.JK`)
* Tombol **Prediksi**
* Output berupa **arah harga saham (Naik / Turun)**

Judul aplikasi:

> **Prediksi Arah Harga Saham**
> Model MLOps – Multi-Stock Price Direction Prediction

---

## 📂 Struktur Repository

```
.

├── data/
│   └── multistock_tuning_data.csv
│   └── sample_data.csv
├── models/
│   └── best_model.pkl
├── src/
│   └── serving/
│       └── app.py
├── predictions/
├── train.py
├── tune.py
├── predict.py
├── config.yaml
├── requirements.txt
├── Dockerfile
├── README.md
└── .github/
    └── workflows/
        └── ci.yml
```

---

## 🚀 Menjalankan Aplikasi Secara Lokal

### 1️⃣ Clone Repository

```bash
git clone https://github.com/<username>/mlops-stock-direction-prediction.git
cd mlops-stock-direction-prediction
```

---

### 2️⃣ Install Dependency

Pastikan Python **3.8+** sudah terinstal.

```bash
pip install -r requirements.txt
```

---

### 3️⃣ Menjalankan Aplikasi Streamlit

```bash
streamlit run app.py
```

Aplikasi akan berjalan di:

```http
https://stock-updown-prediction.streamlit.app/
```

---

## 🐳 Menjalankan dengan Docker

### Build Docker Image

```bash
docker build -t mlops-stock-app .
```

### Run Container

```bash
docker run -p 8501:8501 mlops-stock-app
```

Akses aplikasi di browser:

```http
http://localhost:8501
```

---

## 🔁 CI/CD Pipeline

Proyek ini menggunakan **GitHub Actions** untuk Continuous Integration.

Pipeline dijalankan otomatis setiap kali terjadi **push ke repository**, dengan tahapan:

* Checkout source code
* Install dependency
* Validasi aplikasi Streamlit
* Build Docker image

CI/CD memastikan aplikasi:

* Selalu dalam kondisi siap dijalankan
* Tidak error akibat dependency
* Konsisten antar environment

---

## 📊 Monitoring & Logging

Monitoring dilakukan secara sederhana melalui:

* Logging proses prediksi
* Error handling pada aplikasi Streamlit

Pengembangan lanjutan (future work):

* Integrasi Prometheus & Grafana
* Logging terpusat
* Monitoring performa model (data drift)

---

## 👥 Pembagian Tugas Tim

| Nama                   | NIM       | Peran          | Tanggung Jawab                             |
| ---------------------- | --------- | -------------- | ------------------------------------------ |
| Salwa Farhanatussaidah | 122450011 | Data Engineer  | Data collection, preprocessing             |
| Tria Yunanni           | 122450062 | ML Engineer    | Training model, evaluasi                   |
| Meira Listyaningrum    | 122450055 | MLOps Engineer | Streamlit app, Docker, deployment          |
| Chalifia Wananda       | 122450076 | DevOps / PM    | CI/CD, monitoring, dokumentasi, koordinasi |

---

## 📜 Lisensi

Proyek ini menggunakan **MIT License**.

---
