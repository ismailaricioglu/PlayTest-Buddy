
# 🧾 PlayTest Buddy – Kabul Test Raporu (ATR)

**Hazırlayan:** BilKav QA Ekibi  
**Gözden Geçiren:** ChatGPT (Yapay Asistan)  
**Tarih:** 18-10-2025  
**Model:** V-Model – Kabul Test Raporu Aşaması  
**Durum:** Taslak  

---

## 1. 🎯 Amaç  

Bu rapor, *PlayTest Buddy* uygulamasının **Kabul Testi Planı (ATP)** kapsamında yürütülen testlerin sonuçlarını belgelemektedir.  
Amaç, sistemin iş gereksinimlerini ve kabul kriterlerini tam olarak karşıladığını doğrulamaktır.

---

## 2. 📚 Referans Dokümanlar  

| Doküman | Kod | Açıklama |
|----------|------|-----------|
| İş Gereksinimi | BRD | Temel hedefler |
| Sistem Gereksinimi | SRD | Fonksiyonel tanımlar |
| Fonksiyonel Tasarım | FDD | İşlevsel akışlar |
| Detay Tasarım | DDD | Teknik detaylar |
| Kabul Testi Planı | ATP | Test senaryoları ve kriterler |

---

## 3. ⚙️ Test Ortamı  

| Bileşen | Teknoloji | Versiyon | Not |
|----------|------------|-----------|------|
| Mobil Arayüz | Flutter | 3.22.0 | — |
| Backend API | Python Flask | 2.3.x | — |
| Veritabanı | PostgreSQL | 15.x | — |
| SDK | Kotlin | 1.9.x | — |
| Test Platformu | Android 11+ | 12 katılımcı | BilKav Pilot Grubu |

---

## 4. 🧪 Test Senaryoları ve Sonuçları  

| Test ID | Senaryo | Beklenen Sonuç | Gerçek Sonuç | Durum | Not |
|----------|----------|----------------|---------------|--------|------|
| **AT-001** | Geliştirici uygulamayı yükler | Yükleme başarıyla tamamlanır | _Henüz test edilmedi_ | ⏳ | — |
| **AT-002** | Katılımcı test bağlantısı ile uygulamayı indirir | Katılım doğrulaması yapılır | _Henüz test edilmedi_ | ⏳ | — |
| **AT-003** | Test katılım sayısı 12’ye ulaşır | Sistem otomatik kapanır | _Henüz test edilmedi_ | ⏳ | — |
| **AT-004** | Kullanıcı puan kazanır | +10 puan eklenir | _Henüz test edilmedi_ | ⏳ | — |
| **AT-005** | Kullanıcı test başlatır | -120 puan düşülür | _Henüz test edilmedi_ | ⏳ | — |
| **AT-006** | Sistem tüm test sonuçlarını kaydeder | Veritabanında kayıt görünür | _Henüz test edilmedi_ | ⏳ | — |

> “Durum” sütunundaki işaretler: ✔ = Başarılı | ❌ = Hatalı | ⚠️ = Kısmen başarılı | ⏳ = Beklemede  

---

## 5. 📈 Test Sonuç Özeti  

| Metrik | Değer | Hedef | Durum |
|--------|--------|--------|--------|
| Toplam test sayısı | 6 | — | — |
| Başarılı test sayısı | 0 | 6 | ⏳ |
| Kısmen başarılı test sayısı | 0 | 0 | ⏳ |
| Başarısız test sayısı | 0 | 0 | ⏳ |
| Toplam başarı oranı | 0% | ≥ 95% | ⏳ |

---

## 6. ⚠️ Gözlemler ve Hata Kayıtları  

| Hata ID | Test ID | Tanım | Ciddiyet | Durum |
|----------|----------|--------|-----------|---------|
| — | — | — | — | — |

> Bu bölüm testler tamamlandığında BilKav QA ekibi tarafından doldurulacaktır.

---

## 7. 🧾 Sonuç ve Değerlendirme  

> Kabul testleri tamamlandığında bu bölümde sistemin “Yayına Hazır / Düzeltme Gerekiyor / Reddedildi” şeklinde genel sonucu belirtilecektir.

**Geçici Sonuç:**  
Kabul testleri henüz yürütülmedi.  
Bu doküman, test yürütme süreci için **ön hazırlık raporu** olarak oluşturulmuştur.

---

## 8. ✅ Onay  

| Rol | Ad | Tarih | İmza |
|------|----|--------|------|
| Test Yöneticisi | İsmail ARICIOĞLU | 18-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 18-10-2025 | — |
| Onaylayan | BilKavTopluluğu |  | — |

---

💡 **Not:**  
Bu doküman, *PlayTest Buddy* projesinin son V-Model aşamasıdır.  
Uygulama sürüm 1.0 olarak yayına alınmadan önce bu raporun **güncel test sonuçlarıyla** revize edilmesi zorunludur.
