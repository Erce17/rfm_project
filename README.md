# 🛒 E-Ticaret Verisi Üzerinde RFM Analizi ile Müşteri Segmentasyonu

Bu proje, UCI Machine Learning Repository'den alınan gerçek bir e-ticaret veri seti üzerinde RFM (Recency, Frequency, Monetary) analizi ve K-Means kümeleme algoritması uygulanarak müşteri segmentlerinin belirlenmesini ve cohort analizi ile müşteri elde tutma örüntülerinin incelenmesini kapsamaktadır.

---

## 📊 Proje Özeti

| | |
|---|---|
| **Veri Seti** | UCI Online Retail Dataset (2010–2011) |
| **Ham Kayıt Sayısı** | 541.909 |
| **Temizlenen Kayıt** | 387.841 |
| **Benzersiz Müşteri** | 4.338 |
| **Yöntemler** | RFM Analizi, K-Means Kümeleme, Cohort Analizi |
| **Araçlar** | Python, pandas, scikit-learn, matplotlib, seaborn |

---

## 🔍 Temel Bulgular

- **Platin Müşteriler** toplam müşterilerin yalnızca **%31'ini** oluşturmasına rağmen toplam gelirin **%79,9'unu** üretiyor (Pareto ilkesi doğrulandı)
- K-Means ile **3 küme** (Platin / Altın / Gümüş) optimal olarak belirlendi (Silhouette skoru: 0.4165)
- Müşteriler RFM skorlamasıyla **8 segmente** ayrıldı: Şampiyonlar, Sadık Müşteriler, Potansiyel Sadıklar, Yeni Müşteriler, Risk Altındakiler, Kayıp Müşteriler, Pasif Müşteriler, Umut Vaad Edenler
- Ortalama birinci ay müşteri elde tutma oranı **%20,6** — en yüksek Aralık 2010 cohort grubunda **%36,6**

---

## 📁 Dosya Yapısı

```
rfm_project/
│
├── 01_veri_temizleme.ipynb       # Veri ön işleme ve temizleme
├── 02_rfm_hesaplama.ipynb        # RFM metriklerinin hesaplanması
├── 04_kmeans_kumeleme.ipynb      # K-Means kümeleme (Elbow + Silhouette)
├── 05_cohort_analizi.ipynb       # Aylık cohort ve elde tutma analizi
├── gorsellestirme.ipynb          # Görselleştirmeler
├── rfm_analysis.ipynb            # Tam analiz (birleşik notebook)
├── RFM.ipynb                     # Ana çalışma dosyası
├── main.py                       # Çalıştırma scripti
│
├── data.csv                      # Ham veri seti
├── data_clean.csv                # Temizlenmiş veri
├── data_returns.csv              # İade işlemleri
├── rfm_segments.csv              # RFM segment çıktıları
├── rfm_clusters.csv              # K-Means küme çıktıları
├── cohort_retention.csv          # Cohort elde tutma matrisi
│
├── figures/                      # Grafik ve görseller
└── rapor.pdf                     # Proje raporu (detaylı)
```

---

## ⚙️ Kurulum ve Çalıştırma

### Gereksinimler

```bash
Python >= 3.9
```

### Kurulum

```bash
git clone https://github.com/Erce17/rfm_project.git
cd rfm_project
pip install -r requirements.txt
```

### Çalıştırma

Notebook'ları sırasıyla çalıştırın:

```
01 → 02 → 04 → 05 → gorsellestirme
```

ya da doğrudan:

```bash
python main.py
```

---

## 🧪 Yöntemler

### RFM Analizi
Her müşteri için 3 metrik hesaplandı:
- **Recency** — Son alışverişten geçen gün sayısı (referans: 10 Aralık 2011)
- **Frequency** — Benzersiz sipariş sayısı
- **Monetary** — Toplam harcama tutarı (£)

Müşteriler 1–5 arası quantile tabanlı skorlama ile 8 segmente ayrıldı.

### K-Means Kümeleme
- Frequency ve Monetary değişkenlerine `log1p` dönüşümü uygulandı
- `StandardScaler` ile z-skoru normalleştirmesi yapıldı
- Elbow ve Silhouette yöntemleriyle optimal küme sayısı **k=3** olarak belirlendi

### Cohort Analizi
- Her müşterinin ilk alışveriş ayı cohort grubu olarak tanımlandı
- 13 aylık cohort matrisi ısı haritasıyla görselleştirildi

---

## 📈 Küme Sonuçları

| Küme | Müşteri | Ort. Recency | Ort. Frequency | Ort. Monetary | Gelir Payı |
|------|---------|-------------|----------------|---------------|------------|
| 🥇 Platin | 1.335 | 30 gün | 9,8 sipariş | £4.555 | %79,9 |
| 🥈 Altın | 2.022 | 54 gün | 2,0 sipariş | £578 | %15,4 |
| 🥉 Gümüş | 981 | 255 gün | 1,4 sipariş | £367 | %4,7 |

---

## 📄 Rapor

Projenin detaylı metodoloji, bulgular ve stratejik önerileri içeren tam raporu için: [`rapor.pdf`](./rapor.pdf)

---

## 👤 Yazar

**Ahmet Erce Kıyar**  
GitHub: [@Erce17](https://github.com/Erce17)
