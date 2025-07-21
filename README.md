# 🏷️ Adidas Satış ve Müşteri Analizi | Power BI Dashboard

📊 **Bu proje, bir e-ticaret veri seti üzerinden yalnızca *Adidas* markasına odaklanılarak hazırlanmış interaktif bir satış ve müşteri analiz raporudur.**  
Veri görselleştirme aracı olarak Power BI kullanılmış; kullanıcı, ürün, sipariş ve kategori verileri ilişkilendirilerek analiz edilmiştir.

---
📎 **Proje Linki:**  
👉 [Adidas Power BI Dashboard](https://app.powerbi.com/links/Qr0YWWKdK0?ctid=72fa878c-3962-491e-afd0-ee4c556df1b0&pbi_source=linkShare)

---

## 🎯 Proje Amacı

Bu çalışmanın temel amacı;  
**Adidas markasına ait satış verilerini anlamlandırmak**,  
**müşteri davranışlarını analiz etmek** ve  
**iş birimlerinin karar alma süreçlerine destek sağlayacak özet ve detaylı raporlar üretmektir.**

Rapor; zaman, lokasyon, müşteri ve ürün boyutlarında veri analizi sunmaktadır.

---

## 🧩 Kullanılan Veri Kaynakları

| Tablo Adı       | Açıklama |
|------------------|---------|
| `Users`          | Müşteri bilgileri (ID, cinsiyet, doğum tarihi, yaş vb.) |
| `Orders`         | Siparişlerin temel bilgileri (tarih, kullanıcı, adres) |
| `OrderDetail`    | Siparişlerdeki ürün detayı (ürün, adet, fiyat) |
| `Items`          | Ürün bilgileri (marka, kategori, fiyat vb.) |
| `Address`        | Müşteri adres verisi (şehir) |
| `Bölgeler`       | Şehir-bölge eşleşme verisi (harici olarak eklendi) |

---

## 🔄 Veri Dönüşüm Süreci (Power Query)

### ✅ Marka Filtresi
- **Sadece Adidas markasına ait ürünler** filtrelenerek analiz kapsamı daraltıldı.

### ✅ Sütun Temizleme ve Dönüşüm
- Gereksiz sütunlar kaldırıldı (`CREATEDDATE`, `PASSWORD_`, `TELNR2` gibi).
- Veri türleri düzeltildi (örn. `Birthdate` tarih formatına çevrildi).
- `USERNAME_`, `EMAIL`, `ID` gibi kullanıcıdan gizlenmesi gereken alanlar modelde gizlendi.

### ✅ Yeni Sütunlar ve Dönüştürmeler
- `Yaş`: `DATEDIFF` fonksiyonu ile doğum tarihinden yaş hesaplandı.
- `Cinsiyet`: `E` → "ERKEK", `K` → "KADIN"
- `Ad`, `Soyad`: `NameSurname` kolonundan ayrıştırıldı.
- `HaftaTipi`: `WEEKDAY` fonksiyonuyla haftasonu/haftaiçi ayrımı
- `Saat`: Sipariş saatinin tarih bilgisinden ayrılması
- `YaşGrubu`: 0-20 Genç, 20-35 Yetişkin, 35-55 Orta Yaş, 55+ Yaşlı
- `YeniAnaKategori`: Bazı kategori adları birleştirilerek “İçecekler” üst kategorisi oluşturuldu.

---

## 📊 Rapor Sayfaları

### 1️⃣ Giriş Sayfası
- Proje hakkında bilgilendirme metni
- Sayfalara yönlendirme yapan buton/kartlar
- Kullanıcı yalnızca bu sayfayı görerek diğerlerine yönlendirilir.

---

### 2️⃣ Özet Sayfa

#### 🧮 Kartlar
- **Toplam Satış Adedi**
- **Toplam Ciro**
- **Toplam Müşteri Sayısı**
- **Toplam Sipariş Sayısı**
- **Müşteri Başına Ortalama Ciro**
- **Müşteri Başına Satış Adedi**
- **Ortalama Sipariş Tutarı**

#### 📈 Grafikler
- Haftasonu / Haftaiçi Satış Adeti (Bar Chart)
- Bölgelere Göre Toplam Satış (Map / Column Chart)
- Saatlik Satış Tutarı (Line Chart)

---

### 3️⃣ Müşteri Perspektifi

#### 📌 Kartlar
- Tekil Müşteri Sayısı
- Kadın Müşteri Sayısı
- Erkek Müşteri Sayısı

#### 📊 Grafik ve Tablolar
- Yaş Grubuna Göre Satış Dağılımı
- Bölgelere Göre Müşteri Sayısı
- İstanbul'daki En Yüksek Ciroya Sahip 10 Müşteri (Tablo)

---

### 4️⃣ Kategori Perspektifi

#### 🌳 Ağaç Haritası
- **Filtreleme:** İstanbul’da yaşayan ve “Genç” yaş grubuna ait müşteriler
- **Analiz:** Bu müşteri segmentinin oluşturduğu toplam ciro, kategori bazında gösterildi

---

## 🧠 Kullanılan DAX Ölçüleri (Örnekler)

```DAX
ToplamCiro = SUM(OrderDetail[TotalPrice])

TekilMusteriSayisi = DISTINCTCOUNT(Users[UserID])

MusteriBasinaCiro = [ToplamCiro] / [TekilMusteriSayisi]

HaftaTipi = 
SWITCH(
    WEEKDAY(Orders[Date_], 2),
    6, "Haftasonu",
    7, "Haftasonu",
    "Haftaiçi"
)

YasGrubu = 
SWITCH(TRUE(),
    Users[Age] <= 20, "Genç",
    Users[Age] <= 35, "Yetişkin",
    Users[Age] <= 55, "Orta Yaş",
    "Yaşlı"
)
```
## 🔗 Kullanılan Teknolojiler

- Power BI Desktop
- Power Query (M Dili)
- DAX (Data Analysis Expressions)

---
