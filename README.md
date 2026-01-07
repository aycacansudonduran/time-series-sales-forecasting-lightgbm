# Store Sales Time Series Forecasting

##  Proje Özeti

Bu projede, Kaggle **Store Sales – Time Series Forecasting** veri seti kullanılarak günlük mağaza satışları tahmin edilmiştir. Çalışmanın amacı; klasik zaman serisi yaklaşımları ile modern makine öğrenmesi yöntemlerini karşılaştırmak ve **feature engineering** destekli modellerin tahmin performansını ortaya koymaktır.

Proje, uçtan uca bir veri bilimi sürecini kapsayacak şekilde tasarlanmıştır: veri temizleme, keşifsel veri analizi (EDA), baseline modeller, gelişmiş modelleme ve sonuçların değerlendirilmesi.

---

##  Kullanılan Veri Seti

* **Kaynak:** Kaggle – Store Sales Time Series Forecasting
* **Ana Veri:** Günlük toplam satışlar (2013–2017)
* **Ek Veriler:** Mağaza bilgileri, tatiller, petrol fiyatları, işlem sayıları

Bu projede odak, tüm mağazalar ve ürün aileleri bazında **toplam günlük satışların** tahmin edilmesidir.

---

##  Kullanılan Teknolojiler

* Python
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn
* LightGBM
* Google Colab

---

##  01 – Exploratory Data Analysis (EDA)

Bu aşamada:

* Tarih kolonu datetime formatına dönüştürüldü
* Günlük toplam satışlar hesaplandı
* Zaman serisi trendi incelendi
* Mağaza ve ürün ailesi bazlı satış davranışları analiz edildi
* Promosyonların satışlara etkisi gözlemlendi

EDA sonucunda satışlarda:

* Güçlü mevsimsellik
* Haftalık tekrar eden desenler
* Promosyon kaynaklı ani artışlar
  olduğu tespit edilmiştir.

---

##  02 – Baseline Forecast Modelleri

Modelleme öncesi karşılaştırma için iki temel yöntem uygulanmıştır:

* **Naive Forecast:** Son gözlemin geleceğe taşınması
* **Moving Average:** 7 günlük hareketli ortalama

### Baseline Sonuçları

| Model          | MAE     | RMSE    |
| -------------- | ------- | ------- |
| Naive          | 273,791 | 310,699 |
| Moving Average | 221,071 | 253,498 |

Bu sonuçlar, daha gelişmiş modellere ihtiyaç olduğunu göstermiştir.

---

##  03 – Feature Engineering & LightGBM Modeli

Tahmin performansını artırmak için aşağıdaki özellikler oluşturulmuştur:

### Zaman Tabanlı Özellikler

* Yıl, ay, gün
* Haftanın günü
* Yılın haftası

### Lag & Rolling Özellikleri

* Lag features: 7, 14, 28 gün
* Rolling mean: 7, 14, 28 gün

Bu özellikler ile **LightGBM Regressor** modeli eğitilmiştir.

---

## 04 – Model Performansı ve Karşılaştırma

### Model Sonuçları

| Model          | MAE        | RMSE        |
| -------------- | ---------- | ----------- |
| Naive          | 273,791    | 310,699     |
| Moving Average | 221,071    | 253,498     |
| LightGBM       | **81,514** | **107,323** |

LightGBM modeli, baseline modellere kıyasla **çok ciddi bir performans artışı** sağlamıştır.

---

##  Model Analizi

### Feature Importance

Modelin en önemli girdileri:

* Lag_7
* Rolling Mean (7 gün)
* Haftanın günü
* Ay bilgisi

Bu durum, satışların **kısa vadeli geçmişe ve haftalık döngülere güçlü şekilde bağlı** olduğunu göstermektedir.

### Residual Analizi

* Residual’lar sıfır etrafında dağılmıştır
* Belirgin bir trend veya yapı gözlenmemiştir
* Modelin sistematik hata üretmediği görülmüştür

---

## Sonuç

Bu projede:

* Zaman serisi problemleri için klasik ve modern yaklaşımlar karşılaştırılmıştır
* Feature engineering’in model performansına etkisi net biçimde gösterilmiştir
* LightGBM ile güçlü ve ölçeklenebilir bir tahmin modeli geliştirilmiştir

Bu çalışma, **Data Science / Machine Learning** pozisyonları için zaman serisi analizi, feature engineering ve model değerlendirme yetkinliklerini açıkça ortaya koymaktadır.

---

##  Gelecek Çalışmalar

* Çoklu mağaza / ürün bazlı modelleme
* Tatil ve promosyon değişkenlerinin modele dahil edilmesi
* Hyperparameter tuning
* Prophet ve SARIMA ile ek karşılaştırmalar

---
* Bu proje, zaman serisi problemlerinde feature engineering destekli makine öğrenmesi yaklaşımlarının gücünü göstermek amacıyla hazırlanmıştır.

