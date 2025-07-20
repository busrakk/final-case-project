# 📊 Adidas Satış ve Müşteri Analizi Raporu - Power BI

Bu proje, bir e-ticaret veri seti üzerinden yalnızca **Adidas** markasına odaklanılarak hazırlanmış bir **satış ve müşteri analizi raporudur.** Rapor Power BI kullanılarak oluşturulmuş ve kullanıcıya özet, müşteri ve kategori perspektiflerinden etkileşimli analiz sunmaktadır.

## 🔍 Amaç

Adidas markasına ait satış, müşteri ve ürün verilerinin;
- Zamansal dağılımının,
- Demografik kırılımlarının,
- Bölgesel performansının,
- Kategori bazlı satışlarının

görselleştirilerek analiz edilmesi ve karar destek mekanizmalarına katkı sağlanması.

## 🧩 Kullanılan Veri Kaynakları

- **siparis (Orders)**
- **siparisdetay (OrderDetail)**
- **urunler (Items)**
- **users (Kullanıcılar)**
- **adres**
- **bölgeler** (harici olarak internetten alınmıştır)

## 🔧 Power BI Dönüşümleri

Power Query'de gerçekleştirilen işlemler:
- `Adidas` markası için filtreleme
- Kullanılmayan sütunların kaldırılması
- `YENIANAKATEGORI` gibi koşullu sütunların oluşturulması
- Haftasonu/haftaiçi ve saatlik analiz için ek sütunlar
- Şehir-bölge eşleştirmesi

## 📁 Sayfa Yapısı

### 🟨 Giriş Sayfası
- Rapor hakkında bilgilendirme
- Sayfa yönlendirme kartları

### 🟦 Özet Sayfa
- Toplam Ciro, Sipariş Sayısı, Müşteri Sayısı
- Haftasonu/Haftaiçi Satış Grafiği
- Bölge Bazlı Satış Grafiği
- Saatlik Satış Grafiği
- Müşteri başına ortalama değerler

### 🟪 Müşteri Perspektifi
- Tekil müşteri sayısı
- Kadın/Erkek sayısı
- Yaş gruplarına göre satış
- İstanbul'daki Top 10 müşteri
- Bölgesel müşteri dağılımı

### 🟥 Kategori Perspektifi
- İstanbul ve genç müşteri grubuna göre kategori bazlı ciro (ağaç haritası)

## 📊 Ölçümler (DAX)

- `Toplam Satış Adeti`
- `Toplam Ciro`
- `Toplam Müşteri Sayısı`
- `HaftaTipi` (SWITCH ile)
- `Saat` (DateTime ayrıştırılarak)
- `Müşteri Başına Ciro`, `Ortalama Sipariş Tutarı`
- `Yaş Grubu` (Koşullu sütun)

## 🔗 Kullanılan Teknolojiler

- Power BI Desktop
- Power Query (M Dili)
- DAX

---
