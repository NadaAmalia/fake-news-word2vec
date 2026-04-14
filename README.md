
# Fake News Detection (Word2Vec + Support Vector Classification)
## 📌 Deskripsi

Proyek ini mengimplementasikan **End-to-End Data Pipeline** pada platform **Amazon Web Services (AWS)** untuk mendeteksi berita hoaks menggunakan teknik NLP. Sistem ini memanfaatkan **Word2Vec** untuk ekstraksi fitur teks dan **Linear Support Vector Classifier (SVC)** sebagai model klasifikasi. Dengan memanfaatkan infrastruktur *Cloud Computing*, proyek ini menjamin skalabilitas dalam menangani data besar serta pengelolaan alur kerja data yang aman dan terstruktur melalui pemisahan fungsi *storage*, *compute*, dan *visualization*.

## 🏗️ Arsitektur Sistem

Sistem ini dibangun dengan arsitektur berlapis untuk memastikan keamanan dan efisiensi pengolahan data:

1.  **Security Layer (IAM):** Pengaturan akses menggunakan kredensial IAM dengan prinsip *minimal permission*.
2.  **Data Collecting Layer:** Pengambilan data dari Kaggle dan pembersihan awal menggunakan Python.
3.  **Storage Layer (S3):** Penyimpanan data mentah (`/raw`) dan data hasil olahan (`/processed`) dengan fitur *versioning*.
4.  **Processing Layer (SageMaker/EC2):** Tahap pemodelan, *training*, dan evaluasi model menggunakan pustaka Boto3 dan Scikit-Learn.
5.  **Visualization Layer:** Penyajian insight melalui dashboard interaktif di Looker Studio.

## 🛠️ Pipeline AWS

Alur kerja data dikelola secara profesional di lingkungan cloud[cite: 66]:

  * **Collecting:** Menggunakan Python & Pandas untuk memuat dataset CSV dari Kaggle dan melakukan *cleaning* dasar (penanganan *missing values*, normalisasi teks, dan *lowercase*).
  * **Storage:** Memanfaatkan **Amazon S3** untuk penyimpanan terpusat. Bucket diatur dengan struktur folder yang rapi dan penamaan konsisten untuk integritas sumber data.
  * **Processing:** Pemrosesan dilakukan di **AWS SageMaker Studio Lab**. Data ditarik secara *programmatic* menggunakan **boto3**, kemudian diproses melalui pipeline machine learning (Word2Vec + Linear SVC).
  * **Accessing & Visualizing:** Hasil prediksi dan performa model divisualisasikan menggunakan **Matplotlib** di notebook, serta diintegrasikan ke **Looker Studio** untuk pemantauan metrik secara visual.

## 📊 Dataset

Proyek ini menggunakan **Fake News Dataset** dari Kaggle yang terdiri dari 6.335 artikel berita.

  * **Fitur:** `title`, `text`, dan `label` (Real/Fake).
  * **Proporsi:** Dataset sangat seimbang dengan rasio 49,9% berita Fake dan 50,1% berita Real.
  * **Sumber:** [Fake News Prediction Dataset](https://www.kaggle.com/datasets/rajatkumar30/fake-news/data).

## 🚀 Cara Menjalankan

1.  Clone repositori ini:
    ```bash
    git clone https://github.com/NadaAmalia/fake-news-word2vec.git
    ```
2.  Instal dependensi yang diperlukan:
    ```bash
    pip install -r requirements.txt
    ```
3.  Pastikan Anda telah mengatur kredensial AWS pada file `.env`:
    ```env
    AWS_ACCESS_KEY_ID=your_access_key
    AWS_SECRET_ACCESS_KEY=your_secret_key
    AWS_DEFAULT_REGION=your_region
    S3_BUCKET_NAME=your_bucket_name
    ```
4.  Jalankan notebook pada folder `notebooks/` untuk memulai pipeline.

## 📺 Demo & Hasil

  * **Video Demo:** [Tonton di YouTube](https://youtu.be/VLIyquz5p4g)
  * **Interactive Dashboard:** [Looker Studio Report](https://lookerstudio.google.com/embed/reporting/e8136141-a181-4982-ae41-4e0a2ffbb16d/page/pm63q9t54bd)
  * **Performa Model:** Akurasi mencapai **89,9%** dalam mendeteksi berita hoaks.

## 👥 Kontributor

Proyek ini disusun oleh tim mahasiswa Sains Data UPN "Veteran" Jawa Timur:

  * **Alifah Zuhrah U. S. (24083010033):** Cloud Infrastructure & Security Specialist.
  * **Aisyah Amalia Hamid (24083010034):** Modelling Lead & Visualization.
  * **Nada Amalia Choiro (24083010066):** Data Engineer & Cloud Processing.
