
# 📘 PlayTest Buddy – Proje Süreç Özeti Raporu (README.md)

**Proje Adı:** PlayTest Buddy  
**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Gözden Geçiren:** ChatGPT (Yapay Asistan)  
**Model:** V-Model  
**Sürüm:** 1.0 – Dokümantasyon Final  
**Tarih:** 18-10-2025  

---

## 🧭 1. Proje Tanımı  

**PlayTest Buddy**, bağımsız geliştiricilerin mobil uygulamalarını Google Play politikalarına uygun şekilde test ettirmelerini kolaylaştıran bir test yönetim platformudur.  
Sistem, geliştiricilerin birbirlerinin uygulamalarını test ederek puan kazanabileceği dayanışma temelli bir ekosistem sunar.  

---

## 🧩 2. Uygulanan Geliştirme Modeli  

**Kullanılan Model:** V-Model (Verification & Validation Model)

```plaintext
İş Gereksinimleri
     ↓
Sistem Gereksinimleri
     ↓
Fonksiyonel Tasarım
     ↓
Alt Sistem / Parça Tasarımı
     ↓
Detay Tasarım
     ↓
Kodlama & Uygulama
     ↓
Test Tasarımı (RTM)
     ↓
Kabul Test Planı (ATP)
     ↓
Kabul Test Raporu (ATR)
```

---

## 🧱 3. Dokümanlar ve İlişkilendirmeler  

| No | Doküman Adı | Kod | Açıklama | İndirilebilir Bağlantı |
|----|--------------|------|-----------|----------------|
| 1 | İş Gereksinimi | BRD | Temel hedefler ve kullanıcı ihtiyaçları | [📄 BRD](PlayTestBuddy_IsGereksinimi.md) |
| 2 | Sistem Gereksinimi | SRD | Sistem davranış ve fonksiyonları | [📄 SRD](PlayTestBuddy_SistemGereksinimi.md) |
| 3 | Fonksiyonel Tasarım | FDD | Modül akışları ve fonksiyonel yapı | [📄 FDD](PlayTestBuddy_FonksiyonelTasarim.md) |
| 4 | Alt Sistem / Parça Tasarımı | LLD | Alt modül ilişkileri ve API yapısı | [📄 LLD](PlayTestBuddy_AltSistem_ParcaTasarimi_Dokumani.md) |
| 5 | Detay Tasarım | DDD | Veri modeli, API endpointleri, güvenlik | [📄 DDD](PlayTestBuddy_DetayTasarim_Dokumani.md) |
| 6 | Test Tasarımı ve RTM | TTD | Gereksinim-test izlenebilirliği | [📄 TTD](PlayTestBuddy_TestTasarimi_RTM.md) |
| 7 | Kabul Testi Planı | ATP | Kabul kriterleri, test planı | [📄 ATP](PlayTestBuddy_KabulTestiPlani_ATP.md) |
| 8 | Kabul Test Raporu | ATR | Gerçek test sonuçları ve nihai doğrulama | [📄 ATR](PlayTestBuddy_KabulTestRaporu_ATR.md) |

---

## 🧩 4. Süreç Zaman Çizelgesi  

| Aşama | Tarih | Sorumlu | Durum |
|--------|--------|-----------|--------|
| İş Gereksinimleri (BRD) | 01-10-2025 | İsmail ARICIOĞLU | ✔ Tamamlandı |
| Sistem Gereksinimleri (SRD) | 02-10-2025 | İsmail ARICIOĞLU | ✔ Tamamlandı |
| Fonksiyonel Tasarım (FDD) | 03-10-2025 | İsmail ARICIOĞLU | ✔ Tamamlandı |
| Alt Sistem / Parça Tasarımı (LLD) | 04-10-2025 | İsmail ARICIOĞLU | ✔ Tamamlandı |
| Detay Tasarım (DDD) | 07-10-2025 | İsmail ARICIOĞLU | ✔ Tamamlandı |
| Test Tasarımı & RTM | 08-10-2025 | BilKav QA Ekibi | ✔ Tamamlandı |
| Kabul Test Planı (ATP) | 09-10-2025 | BilKav QA Ekibi | ✔ Tamamlandı |
| Kabul Test Raporu (ATR) | 18-10-2025 | BilKav QA Ekibi | ⏳ Test bekliyor |

---

## ⚙️ 5. Sistem Bileşenleri  

| Katman | Teknoloji | Açıklama |
|---------|------------|-----------|
| Frontend | Flutter | Mobil kullanıcı arayüzü |
| Backend | Python (Flask) | RESTful API ve iş mantığı |
| SDK | Kotlin | Android doğrulama bileşeni |
| Database | PostgreSQL | Kalıcı veri katmanı |
| Authentication | JWT | Kimlik doğrulama mekanizması |

---

## 🧮 6. Test Sonuç Durumu (Geçici)  

| Metrik | Değer | Hedef | Durum |
|--------|--------|--------|--------|
| Toplam Test | 6 | — | — |
| Başarılı | 0 | 6 | ⏳ |
| Kısmen Başarılı | 0 | 0 | ⏳ |
| Başarısız | 0 | 0 | ⏳ |
| Başarı Oranı | 0% | ≥95% | ⏳ |

---

## 🧾 7. Sonuç  

> Tüm analiz, tasarım ve planlama aşamaları tamamlanmıştır.  
> Sistem kabul testleri öncesi hazır durumdadır.  
> **Bir sonraki adım:** Gerçek kullanıcılarla **pilot test süreci (12 kişi, 14 gün)**.  

---

## 🪶 8. Onay  

| Rol | Ad | Tarih | İmza |
|------|----|--------|------|
| Proje Yöneticisi | İsmail ARICIOĞLU | 18-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 18-10-2025 | — |
| Onaylayan | BilKavTopluluğu |  | — |

---

💡 **Not:**  
Bu özet doküman, PlayTest Buddy projesinin **GitHub ana README.md** dosyası olarak kullanılabilir.  
Tüm alt doküman bağlantıları aktif hale getirilerek proje deposunda tam izlenebilirlik sağlanmalıdır.
