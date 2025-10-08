# 📘 PlayTest Buddy – İş Gereksinimi Dokümanı (BRD)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Sürüm:** v1.0  
**Model:** V-Model – İş Gereksinimi Aşaması  
**Tarih:** 01-10-2025  

---

## 1. 🎯 Proje Amacı  
Mobil uygulama geliştiricilerinin, Google Play politikaları doğrultusunda uygulamalarını test ettirme sürecini kolaylaştırmak.  
PlayTest Buddy, geliştiricilerin kendi toplulukları içinde test süreçlerini planlayabilmelerine ve katılımcı yönetimini sistematik hale getirmelerine olanak sağlar.

---

## 2. 💡 İhtiyacın Ortaya Çıkışı  
Google Play Console politikalarına göre bir uygulamanın yayınlanmadan önce:  
- En az **12 farklı kullanıcı** tarafından test edilmesi,  
- Bu test sürecinin **en az 14 gün** sürmesi,  
- Katılımcıların **Google hesaplarıyla doğrulanması**,  
gerekmektedir.

Bu süreç bağımsız geliştiriciler için zaman alıcı, dağınık ve manuel olarak yürütülmektedir.  
PlayTest Buddy bu süreci dijitalleştirir, kolaylaştırır ve geliştiriciler arasında iş birliği temelli bir ekosistem oluşturur.

---

## 3. 👥 Hedef Kitle  
- **Bağımsız (freelance) geliştiriciler:** Kendi uygulamalarını hızlı test ettirmek isteyen bireyler.  
- **Küçük yazılım ekipleri:** Ekip içi veya topluluk bazlı test yönetimi isteyen gruplar.  
- **Topluluk üyeleri:** Uygulama testlerine katılarak puan kazanmak isteyen kullanıcılar.  

---

## 4. 🧭 İş Hedefleri  
| No | Hedef | Ölçüt / Beklenen Sonuç |
|----|--------|--------------------------|
| **IH-001** | Google Play test gerekliliklerini otomatikleştirmek | 12 tester & 14 gün kriterlerinin sistem üzerinden takip edilmesi |
| **IH-002** | Katılımcı yönetimini kolaylaştırmak | Katılımcıların testlere otomatik atanabilmesi |
| **IH-003** | Geliştiriciler arası dayanışma sağlamak | Topluluk puanlama ve katkı sisteminin devreye alınması |
| **IH-004** | Test süreci görünürlüğü sağlamak | Geliştiricinin kendi test sürecini anlık izleyebilmesi |
| **IH-005** | Kullanıcı katılımını teşvik etmek | Tester’ların test başına puan kazanarak aktivasyon hakkı elde etmesi |

---

## 5. 🧩 İş Gereksinimleri (Business Needs)
| ID | Gereksinim Tanımı | Kapsam | Not |
|----|--------------------|---------|------|
| **BR-001** | Geliştirici yeni bir test süreci başlatabilmelidir | Uygulama paylaşımı | Minimum 120 puan gerektirir |
| **BR-002** | Tester bir uygulamaya katılabilmelidir | Test listesi üzerinden | SDK doğrulaması gerekir |
| **BR-003** | Katılımcı sayısı sistem tarafından takip edilmelidir | Test süreci yönetimi | 12 kişi tamamlanınca süreç kapanır |
| **BR-004** | Katılımcılar puan kazanmalıdır | Test tamamlandığında | +10 puan |
| **BR-005** | Sistem kullanıcı puanlarını yönetebilmelidir | Cüzdan modülü | Ledger tabanlı izleme |
| **BR-006** | Test sonuçları geliştiriciye raporlanmalıdır | Raporlama ekranı | Katılımcı listesi + genel durum |
| **BR-007** | Uygulama sahipliği doğrulanmalıdır | SDK → Server iletişimi | Test eden kullanıcı ve uygulama eşleşmesi gerekir |

---

## 6. 🚀 Beklenen Katma Değer  
- Test süreçlerinde harcanan manuel eforun azaltılması  
- Google Play gereksinimlerinin eksiksiz karşılanması  
- Yazılımcı topluluğu içinde dayanışma kültürünün güçlenmesi  
- Açık kaynaklı topluluk katkı modeline temel oluşturma  

---

## 7. 📊 Başarı Ölçütleri (KPI)  
| Ölçüt | Başarı Eşiği |
|--------|----------------|
| Minimum katılımcı sayısına ulaşan test oranı | ≥ %90 |
| Test edilen uygulamanın “Kapalı Test” süresine uygunluğu | ≥ 14 gün (ürün bazlı, kullanıcı bağımsız) |
| Topluluk içi aktif kullanıcı oranı | İzlenir; belirli bir hedef oran tanımlanmayacak |
| Puanlama sistemi doğruluk oranı | %100 (ledger ile doğrulanmış) |

---

## 8. 🧭 Sınırlar ve Varsayımlar  
**Sınırlar:**  
- İlk sürüm sadece Android tabanlı testleri kapsar.  
- Harici (profesyonel) tester desteği ilk fazda bulunmayacaktır.  

**Varsayımlar:**  
- Kullanıcılar Google hesaplarıyla giriş yapmaktadır.  
- Her tester gerçek bir Android cihaz kullanmaktadır.  

---

## 9. 📋 Onay & Dağıtım  
| Rol | Ad | Tarih | İmza |
|------|----|--------|-------|
| Proje Sahibi | İsmail ARICIOĞLU | 01-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 01-10-2025 | — |
| Onaylayan | BilKavTopluluğu | 01-10-2025 | — |

---

**Doküman Durumu:** Tamamlandı  
**Kapsam:** İş Gereksinimi (Business Requirements)  
**Bağlantılı Belgeler:** Sistem Gereksinimi Dokümanı, Use Case Tanımları, RTM  
