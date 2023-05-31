# Home Credit Default Risk
Pada case ini, kami menggunakan metode CRISP-DM dalam pemecahan masalah.
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/CRISP-DM.jpg)

## Business Understanding
Permasalahan yang dihadapi oleh Home Credit adalah risiko churn, yaitu pelanggan yang kemungkinan besar akan meninggalkan layanan Home Credit atau melunasi pinjaman mereka tidak sesuai dari jangka waktu yang diharapkan. Untuk menghadapi permasalahan ini, diperlukan analisis Churn Prediction untuk faktor-faktor yang dapat menyebabkan churn, sehingga Home Credit dapat menyusun langkah-langkah dapat diambil untuk mencegah churn dan memastikan pertumbuhan bisnis yang berkelanjutan.

## Data Understanding
### **Dataset**
| Dataset | Deskripsi |
| --- | --- |
|[application_{train/test}](https://www.kaggle.com/competitions/home-credit-default-risk/data) | The main training and testing data with information about each loan application at Home Credit. Every loan has its own row and is identified by the feature `SK_ID_CURR`. The training application data comes with the TARGET indicating 0: the loan was repaid or 1: the loan was not repaid.|
|[bureau](https://www.kaggle.com/competitions/home-credit-default-risk/data) | Data concerning client's previous credits from other financial institutions. Each previous credit has its own row in bureau, but one loan in the application data can have multiple previous credits.|
|[bureau_balance](https://www.kaggle.com/competitions/home-credit-default-risk/data) | Monthly data about the previous credits in bureau. Each row is one month of a previous credit, and a single previous credit can have multiple rows, one for each month of the credit length.|
|[installments_payments](https://www.kaggle.com/competitions/home-credit-default-risk/data) | Payment history for previous loans at Home Credit. There is one row for every made payment and one row for every missed payment.|
|[credit_card_balance](https://www.kaggle.com/competitions/home-credit-default-risk/data) | Monthly data about previous credit cards clients have had with Home Credit. Each row is one month of a credit card balance, and a single credit card can have many rows.|
|[pos_cash_balance](https://www.kaggle.com/competitions/home-credit-default-risk/data)| Monthly data about previous point of sale or cash loans clients have had with Home Credit. Each row is one month of a previous point of sale or cash loan, and a single previous loan can have many rows.|
|[previous_application](https://www.kaggle.com/competitions/home-credit-default-risk/data)| previous applications for loans at Home Credit of clients who have loans in the application data. Each current loan in the application data can have multiple previous loans. Each previous application has one row and is identified by the feature `SK_ID_PREV`.|

### **Relationship**
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/RELATIONSHIP_home_credit.png)

### **Exploratory Data Analysis (EDA)**
Penjelasan lengkap tetang [EDA](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/Exploratory%20Data%20Analysis%20(EDA).ipynb)

## Data Prepocesing
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/Flow.jpg)

## Modeling dan Evaluasi
### **Modeling**
Pada tahap modeling, kami menguji beberapa model yang belum di hyperparameter tuning seperti `logistic regression`, `decision tree`, `naive bayes`, `random forest classifier`, `extreme gradient boost`, `KNN` dan `LighGBM`. Setelah model tersebut diuji, kami melakukan evaluasi secara menyeluruh dan didapatkan tiga model dengan akurasi yang relevan diantaranya : 
| Model | Akurasi(%) | AUC ROC (%) | 
| --- | --- | --- |
| `LightGBM` | 73.02 | 89.98 |
| `KNN` | 82.07 | 89.09 |
| `Extreme Gradient Boost` | 86.3 | 85.66 |

Akurasi terbaik pada Model LightGBM yaitu memiliki akurasi sebesar 73.02% dan AUC ROC sebesar 89.98% sehingga menjadi model terbaik

### **Feature Importance**
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/FEATURE%20IMPORTANCE.jpg)
Melalui model LightGBM, didapatkan beberapa fitur yang paling berpengaruh, tidak adanya kecondongan dalam salah satu fitur, mengindikasikan model yang cukup stabil


## Deployment 
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/Dasboard.png)
Hasil deployment dapat dilihat pada [DASHBOARD](https://app.powerbi.com/view?r=eyJrIjoiNGM1NDNhMjMtN2ZkOS00MDZlLWJmNGMtYTIzZTBkMzFjOGM0IiwidCI6ImFmMmMwNzM0LWNiNDItNDY0Zi1iNmJmLTJhMjQxYjZhZGE1NiIsImMiOjEwfQ%3D%3D) ini 

## Hasil Prediksi
Untuk memudahkan Home Credit dalam menganalisis customer, dapat menggunakan pengelompokkan churn berdasarkan kuartil sebagai berikut :
![image](https://github.com/DanielAndresSmg/Home-Credit-Default-Risk/blob/main/Insight.png)
| Kuartil | Deskripsi |
| --- | --- |
| 0-25 | Enggange them (sebanyak 11.9%)|
| 26-50 | Almost gone (sebanyak 17.7%) |
| 51-75 | Need to attention (sebanyak 34.5%) |
| 76-10 | Un healthy customer (sebanyak 32.6%) |

## Rekomendasi 
Berdasarkan pengelompokkan churn diatas, kami dapat menentukan  rekomendasi penanganan yang tepat untuk customer churn sebagai berikut:
1. **Engage Them Churn Rate 0-25%**,
   Hubungi pelanggan, berikan insentif, berikan pelayanan optimal
2. **Rekomendasi Almost Gone Churn Rate 26-50%**,
   Memikat kembali pelanggan, mengedepankan keunggulan nilai unik, mengajukan permintaan umpan balik
3. **Rekomendasi Need Attention Churn Rate 51-75%**,
   Melakukan komunikasi proaktif, menawarkan program loyalitas, meningkatkan layanank
4. **Rekomendasi Unhealthy Customer Churn Rate 76-100%**,
   Membuat strategi khusus, sediakan manajer akun, melakukan penyelidikan yang komprehensif

