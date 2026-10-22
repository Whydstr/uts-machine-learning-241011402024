# UTS Machine Learning – Linear & Logistic Regression

- **Nama**  : Wahyu Adi Satrio
- **NIM**   : 241011402024
- **Kelas** : Reg B (05TPLM001)
- **random_state** : 24

Notebook: [`tugas_UTS.ipynb`](tugas_UTS.ipynb) (sudah dijalankan, semua output dan grafik terlihat).
Semua model dan metrik diimplementasikan sendiri dengan NumPy; scikit-learn hanya dipakai di soal bonus.

## Ringkasan Hasil

### Bagian A – Linear Regression (`Ads_Data.csv`, 40 data, split 80:20)
- Persamaan (normal equation): `y_hat = 28.1439 + 9.1356 * BiayaIklan`
- Setiap kenaikan biaya iklan 1 juta Rp → penjualan naik rata-rata 9,14 juta Rp.

| Data | MAE | MSE | RMSE | R² |
|---|---|---|---|---|
| Training | 4.8490 | 41.6282 | 6.4520 | 0.9326 |
| Testing | 3.0299 | 13.6585 | 3.6957 | 0.9800 |

- Gradient descent (5000 iterasi): lr 0.001 terlalu lambat (belum konvergen), lr 0.02 pas (sama dengan normal equation), lr 0.1 divergen (overflow → NaN).
- Prediksi penjualan: biaya iklan 4,5 juta → 69.25 juta; 7 juta → 92.09 juta; 12 juta → 137.77 juta (ekstrapolasi, kurang dapat dipercaya).

### Bagian B – Logistic Regression (`Email_Data.csv`, 60 data, split 75:25)
- Persamaan: `P(Spam) = sigmoid(-11.4233 + 1.0424*JumlahLink + 0.8993*KataPromo)`
- Evaluasi data testing (threshold 0.5): accuracy 0.9333, precision 1.00, recall 0.8571, F1 0.9231; confusion matrix TN=8, FP=0, FN=1, TP=6.
- Threshold yang dipilih: **0.5** (FP dianggap lebih merugikan daripada FN).
- Prediksi email baru (threshold 0.5): E1 Bukan Spam, E2 Bukan Spam, E3 Spam, E4 Spam.

### Bagian C & Bonus
- Jawaban konsep ada di notebook (Bagian C).
- Bonus: Linear Regression scikit-learn identik dengan implementasi sendiri. Pada Logistic Regression koefisien berbeda karena scikit-learn memakai regularisasi L2 (`C=1.0`) secara default, sedangkan evaluasi pada data testing sama.

## Struktur Repositori
```
uts-machine-learning-241011402024/
├── README.md
├── tugas_UTS.ipynb
├── Ads_Data.csv
└── Email_Data.csv
```
