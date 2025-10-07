
# ✅ PlayTest Buddy – Kabul Testi Planı (ATP)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Gözden Geçiren:** ChatGPT (Yapay Asistan)  
**Tarih:** 08-10-2025  
**Model:** V-Model – Kabul Testi Planı Aşaması  
**Durum:** Onaylı  

---

## 1. 🎯 Amaç  

Bu doküman, *PlayTest Buddy* sisteminin kabul testlerini planlamak amacıyla hazırlanmıştır.  
Kabul testleri, geliştirilen sistemin iş gereksinimlerini karşıladığını **son kullanıcı düzeyinde doğrulamak** için yapılacaktır.

---

## 2. 📚 Referans Dokümanlar  

| Doküman | Kodu | Açıklama |
|----------|------|-----------|
| İş Gereksinimi Dokümanı | BRD | Temel hedefler ve kullanıcı ihtiyaçları |
| Sistem Gereksinimi Dokümanı | SRD | Sistem davranışlarının tanımı |
| Fonksiyonel Tasarım Dokümanı | FDD | Modül fonksiyonlarının tanımı |
| Detay Tasarım Dokümanı | DDD | Teknik detaylar, API ve veri akışı |
| Test Tasarımı ve RTM Dokümanı | TTD | Gereksinim–test bağlantıları |

---

## 3. 🧩 Kapsam  

Kabul testleri, sistemin **tüm uçtan uca senaryolarını** kapsar:  

1. Geliştiricinin uygulamasını test sürecine dahil etmesi  
2. Katılımcıların (tester) doğrulanması  
3. Puan sisteminin doğru çalışması (120 puan aktivasyon – 10 puan kazanım)  
4. Test sürecinin otomatik kapanması (12 katılımcı dolduğunda)  
5. Test raporlarının doğrulanabilir biçimde kayıt edilmesi  

> İlk sürümde yalnızca sayısal doğrulamalar yapılacaktır.  
> İleri sürümlerde kullanıcı kimlikleri ve istatistiksel analizler eklenebilir.

---

## 4. 🧪 Kabul Kriterleri  

| ID | Gereksinim | Kabul Kriteri | Başarı Ölçütü |
|----|-------------|---------------|----------------|
| **AC-001** | GR-001 | Geliştirici uygulamasını yükleyebilmelidir. | %100 doğru yükleme |
| **AC-002** | GR-003 | Test süreci 12 katılımcıya ulaştığında kapanmalıdır. | Katılımcı limiti tam 12 |
| **AC-003** | GR-004 | SDK doğrulaması doğru sonuç vermelidir. | Doğrulama oranı %100 |
| **AC-004** | GR-005 | Puanlama sistemi (+10 / -120) hatasız çalışmalıdır. | Hesaplanan bakiye doğru |
| **AC-005** | GR-002 | Sistem tüm isteklerde 3 saniye altında yanıt vermelidir. | Ortalama yanıt süresi ≤ 3s |

---

## 5. 🔧 Test Ortamı  

| Bileşen | Teknoloji | Versiyon |
|----------|------------|-----------|
| Mobil Arayüz | Flutter | 3.22.0 |
| Backend API | Python Flask | 2.3.x |
| Veritabanı | PostgreSQL | 15.x |
| SDK | Kotlin | 1.9.x |
| Test Platformu | Android 11+ | — |

> Not: İlk kabul testleri 12 gerçek katılımcıdan oluşan **BilKavTopluluk pilot grubunda** yürütülecektir.

---

## 6. ⚙️ Test Senaryoları  

| Test ID | Senaryo | Beklenen Sonuç |
|----------|----------|----------------|
| **AT-001** | Geliştirici uygulamayı yükler | Yükleme başarıyla tamamlanır |
| **AT-002** | Katılımcı test bağlantısı ile uygulamayı indirir | Katılım doğrulaması yapılır |
| **AT-003** | Test katılım sayısı 12’ye ulaşır | Sistem otomatik kapanır |
| **AT-004** | Kullanıcı puan kazanır | +10 puan eklenir |
| **AT-005** | Kullanıcı test başlatır | -120 puan düşülür |
| **AT-006** | Sistem tüm test sonuçlarını kaydeder | Veritabanında kayıt görünür |

---

## 7. ⏱️ Test Planı  

| Faaliyet | Sorumlu | Başlangıç | Bitiş |
|-----------|-----------|-----------|--------|
| Test Hazırlığı | BilKav QA Ekibi | 10-10-2025 | 11-10-2025 |
| Kabul Testleri | BilKav Pilot Grubu | 12-10-2025 | 14-10-2025 |
| Hata Düzeltmeleri | Geliştirme Ekibi | 15-10-2025 | 16-10-2025 |
| Nihai Gözden Geçirme | ChatGPT & BilKavTopluluk | 17-10-2025 | 18-10-2025 |

---

## 8. ✅ Kabul ve Onay  

| Rol | Ad | Tarih | İmza |
|------|----|--------|------|
| Test Yöneticisi | İsmail ARICIOĞLU | 08-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 08-10-2025 | — |
| Onaylayan | BilKavTopluluğu |  | — |

---

💡 **Not:** Bu doküman, “PlayTest Buddy” projesinin *ilk kabul testi planıdır*.  
Sistem kararlı sürüme geçtiğinde “Kabul Test Raporu (ATR)” ile tamamlanacaktır.
