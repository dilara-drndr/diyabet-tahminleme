# Diyabet Tahminleme Sistemi

Kişilerin sağlık verilerine (glikoz, kan basıncı, BMI, yaş vb.) bakarak diyabet hastası olup olmadığını tahmin eden bir makine öğrenmesi projesidir. Random Forest sınıflandırıcısı kullanılmıştır.

## İş Problemi

Özellikleri belirtildiğinde kişilerin diyabet hastası olup olmadıklarını tahmin edebilecek bir makine öğrenmesi modeli geliştirilmesi hedeflenmiştir. Model geliştirilmeden önce gerekli veri analizi ve özellik mühendisliği (feature engineering) adımları gerçekleştirilmiştir.

## Veri Seti

Veri seti, ABD Ulusal Diyabet-Sindirim-Böbrek Hastalıkları Enstitüleri tarafından toplanan, Arizona/Phoenix'te yaşayan 21 yaş ve üzeri Pima Indian kadınları üzerinde yapılan diyabet araştırmasına aittir.

**768 gözlem, 9 değişken**

| Değişken | Açıklama |
|---|---|
| Pregnancies | Hamilelik sayısı |
| Glucose | Oral glikoz tolerans testinde plazma glikoz konsantrasyonu |
| BloodPressure | Kan basıncı (mm Hg) |
| SkinThickness | Cilt kalınlığı |
| Insulin | 2 saatlik serum insülini (mu U/ml) |
| BMI | Vücut kitle endeksi |
| DiabetesPedigreeFunction | Soydaki kişilere göre diyabet olma ihtimalini hesaplayan fonksiyon |
| Age | Yaş |
| Outcome | Hedef değişken — diyabet pozitif (1) / negatif (0) |

> Veri seti boyut nedeniyle bu repoya dahil edilmemiştir. [Kaggle - Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) üzerinden indirilip `datasets/diabetes.csv` yoluna yerleştirilmelidir.

## Yapılan Adımlar

**1. Keşifçi Veri Analizi (EDA)**
- Genel veri yapısının incelenmesi
- Numerik ve kategorik değişkenlerin yakalanması
- Hedef değişken analizi
- Aykırı gözlem ve eksik gözlem analizi
- Korelasyon analizi

**2. Feature Engineering**
- Glikoz, insülin gibi değişkenlerdeki anlamsız "0" değerlerinin eksik veri (NaN) olarak işaretlenip medyan ile doldurulması
- Yaş, BMI ve glikoz değerlerinden yeni kategorik değişkenler türetilmesi (örn. yaş grubu, BMI sınıfı, glikoz-yaş kombinasyonu)
- Label encoding ve one-hot encoding uygulanması
- Sayısal değişkenlerin standartlaştırılması (StandardScaler)

**3. Modelleme**
- **Random Forest Classifier** ile model eğitimi
- Performans metrikleri: Accuracy, Recall, Precision, F1, AUC
- Feature importance analizi ile en etkili değişkenlerin belirlenmesi

## Sonuçlar

| Metrik | Base Model | Geliştirilmiş Model |
|---|---|---|
| Accuracy | 0.77 | 0.79 |
| Recall | 0.706 | 0.711 |
| Precision | 0.59 | 0.67 |
| F1 | 0.64 | 0.69 |
| AUC | 0.75 | 0.77 |

Feature engineering adımları sonrasında modelin tüm metriklerde iyileşme gösterdiği görülmüştür.

## Kullanılan Teknolojiler

- Python
- Pandas, NumPy
- Scikit-learn (RandomForestClassifier, StandardScaler, LabelEncoder)
- Matplotlib, Seaborn

## Çalıştırma

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
python diabetes_feature_engineering.py
```
