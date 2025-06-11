

# 💠 TUCE-X IDS - Saldırı Tespit Sistemi

**TUCE-X**, ID3 karar ağacı algoritmasını kullanarak ağ trafiğini analiz eden ve potansiyel saldırı türlerini sınıflandıran bir siber güvenlik aracıdır. `id3.py` ile model oluşturulur, `tool.py` ile bu model üzerinden analiz ve log işlemleri gerçekleştirilir.

---

## 📦 requirements.txt

```txt
pandas
numpy
matplotlib
scikit-learn
joblib
rich
```

---
## 📂 Proje Yapısı

```bash
tool/
├── tool.py               # Arayüzlü tahmin, analiz ve loglama
├── id3_model2.pkl        # Eğitilmiş ID3 modeli
├── label_encoder2.pkl    # Etiket dönüşüm modeli
├── requirements.txt      # Bağımlılıklar
├── logs/                 # Tahmin loglarının saklandığı klasör
└── README.md             # Proje dökümantasyonu

Performans/
├── ıd3.py
├── veri_filtered.csv
├── diğer karşılaştırmalar için yazılmış kodlar ve veri setleri.

```

---

## ⚙️ Kurulum
Linux ortamında: 
1. Python ortamı oluşturun (isteğe bağlı):

```bash
python3 -m venv venv
source venv/bin/activate
```

2. Gerekli paketleri yükleyin:

```bash
pip install -r requirements.txt
```

---

## 🚀 Kullanım

### 🔧 1. Model Eğitimi

`id3.py` dosyasını çalıştırarak ID3 karar ağacı modeli oluşturulur: (Windows Ortamında yaptım Performans klasörünün içerisinde bulunuyor.)

```bash
python id3.py
```

Bu işlem sonucunda:

* `id3_model2.pkl` → Model dosyası
* `label_encoder2.pkl` → Etiket dönüştürücü
  oluşturulur.

---

### 🤖 2. Tahmin ve Saldırı Tespiti
Windows ortamında oluşturulan model ve label linux ortamına aktarılarak uygulama çalıştırılır.

```bash
python tool.py
```

Açılan menüde:

* \[1] CSV dosyası yükleyip analiz yapabilir
* \[3] Sonuçları `.csv` olarak loglayabilir
* \[4] Log dosyasını görüntüleyebilir
* \[5] Log dosyasını silebilirsiniz

Girdi CSV dosyasının `"Attack Type"` ve 20 özelliği içermesi beklenir:

```text
Flow Duration, Total Fwd Packets, Fwd Packets/s, ..., Destination Port, Attack Type
```

---

## 📊 Kullanılan Özellikler

Model aşağıdaki 20 özellik üzerinden tahmin yapar:

```
Flow Duration, Total Fwd Packets, Fwd Packets/s, Bwd Packets/s, Flow Bytes/s, Flow Packets/s,
Fwd Packet Length Mean, Bwd Packet Length Mean, Fwd Packet Length Max, Bwd Packet Length Max,
Min Packet Length, Max Packet Length, ACK Flag Count, FIN Flag Count, PSH Flag Count,
Idle Mean, Idle Min, Active Mean, Flow IAT Min, Destination Port
```

---

## 🧠 Model Bilgisi

* **Algoritma**: ID3 (Information Gain tabanlı karar ağacı)
* **Doğruluk (Accuracy)**: %97
* **Model Derinliği**: 5
* **Model Görselleştirme**: Eğitimin sonunda matplotlib ile sunulur. Kodların içerisinde mevcuttur. 
Diğer Modeller ile ilgili karşılaştırmalar ve veri setleri "performans" klasörünün içerisindedir.
---

## 📚 Loglama ve Kayıt

Her analiz sonrası log dosyasını `logs/` klasörüne kaydedebilir, görüntüleyebilir ya da silebilirsiniz. Log dosyaları CSV formatındadır ve her satırda:

```csv
Veri, Gerçek, Tahmin, Durum
```

bilgileri yer alır.



## 👤 Geliştirici

**Gülşen Çintuğlu** 

---

