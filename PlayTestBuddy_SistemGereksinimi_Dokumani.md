# 🧩 PlayTest Buddy – Sistem Gereksinimi Dokümanı (SRD)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Sürüm:** v1.0  
**Model:** V-Model – Sistem Gereksinimi Aşaması  
**Tarih:** 03-10-2025  

---

## 1. 🎯 Amaç  
Bu dokümanın amacı, *PlayTest Buddy* sisteminin iş gereksinimlerini teknik düzeyde somutlaştırmaktır.  
Burada tanımlanan gereksinimler, sistemin tasarım, geliştirme, test ve doğrulama süreçlerinin temelini oluşturur.

---

## 2. 🧭 Sistem Kapsamı  
PlayTest Buddy, geliştiricilerin mobil uygulamalarını test ettirmek için kullandıkları bir platformdur.  
Sistem aşağıdaki ana bileşenlerden oluşur:

1. **Kullanıcı Arayüzü (Mobil Uygulama)**  
   - Test paylaşımı, katılım ve raporlama ekranlarını içerir.  
2. **Sunucu (Backend API)**  
   - Test süreçlerini, kullanıcı puanlarını ve SDK doğrulamasını yönetir.  
3. **SDK Doğrulama Modülü**  
   - Test edilen uygulamaya entegre edilen küçük bir kod parçasıdır.  
   - Test etkinliğini sunucuya raporlar.  
4. **Puanlama Servisi**  
   - Tester’ların kazandığı ve kullandığı puanları kaydeder.  
5. **Raporlama ve İzleme Modülü**  
   - Test süreçlerinin ilerleme durumunu geliştiriciye gösterir.

---

## 3. 📦 Sistem Gereksinimleri

| ID | Sistem Gereksinimi | Tür | Öncelik | İlgili İş Gereksinimi |
|----|---------------------|------|-----------|--------------------------|
| **SR-001** | Sistem, her kullanıcıya başlangıçta 120 puan tanımlamalıdır. | Fonksiyonel | Orta | BR-001 |
| **SR-002** | Sistem, 12 katılımcıya ulaşıldığında test sürecini otomatik kapatmalıdır. | Fonksiyonel | Yüksek | BR-003 |
| **SR-003** | Sistem, test edilen uygulamada SDK’dan gelen kullanıcı doğrulama bilgisini kaydetmelidir. | Fonksiyonel | Yüksek | BR-007 |
| **SR-004** | Kullanıcı bir test tamamladığında sistem 10 puan eklemelidir. | Fonksiyonel | Yüksek | BR-004 |
| **SR-005** | Sistem, her test sürecini benzersiz bir ID ile takip etmelidir. | Fonksiyonel | Yüksek | BR-002 |
| **SR-006** | Puanlama geçmişi (kazanım/harcama) kullanıcı cüzdanında listelenmelidir. | Fonksiyonel | Orta | BR-005 |
| **SR-007** | Geliştirici, kendi test süreçlerini listeleyebilmelidir. | Fonksiyonel | Orta | BR-006 |
| **SR-008** | Sistem, 14 günlük ürün test süresini takip etmelidir (ürün bazlı). | Fonksiyonel | Düşük | BR-003 |
| **SR-009** | Sunucu, SDK doğrulama isteği almadığında testi geçersiz saymalıdır. | Fonksiyonel | Orta | BR-007 |
| **SR-010** | Sistem, API isteklerinde JWT tabanlı kimlik doğrulama kullanmalıdır. | Güvenlik | Yüksek | — |
| **SR-011** | Kullanıcı puan bilgileri SHA256 ile hashlenmelidir. | Güvenlik | Yüksek | — |
| **SR-012** | Sunucu logları 30 gün süreyle saklanmalıdır. | Operasyonel | Orta | — |
| **SR-013** | Sistem günlük 10.000 API isteğini destekleyebilmelidir. | Performans | Orta | — |
| **SR-014** | Uygulama 5 saniyeden kısa sürede açılmalıdır. | Performans | Düşük | — |

---

## 4. ⚙️ Sistem Kısıtları  
- SDK yalnızca Android için Kotlin/Java tabanlı olarak sağlanacaktır.  
- Flutter desteği ileri sürümlerde opsiyonel olarak planlanabilir.  
- Tüm API çağrıları HTTPS üzerinden yapılmalıdır.  
- Sunucu altyapısı ilk fazda tek bir bölgede (örn. eu-central) barındırılacaktır.

---

## 5. 🔒 Güvenlik Gereksinimleri  
- Tüm kullanıcı kimlikleri JWT (JSON Web Token) ile doğrulanacaktır.  
- SDK – Sunucu iletişimi HTTPS (TLS 1.2 veya üstü) ile korunacaktır.  
- Puan transferleri ledger (denetlenebilir kayıt defteri) mantığında tutulacaktır.  
- Yetkisiz kullanıcılar test verilerine erişemeyecektir.  

---

## 6. 🧠 Kullanılabilirlik Gereksinimleri  
- Mobil arayüzde test akışları maksimum 3 adımda tamamlanabilir olmalıdır.  
- Puan cüzdanı ve test listesi ekranları çevrimdışı görüntülenebilir olmalıdır.  
- Hata mesajları kullanıcı dostu ve açıklayıcı formatta gösterilmelidir.

---

## 7. 🧩 Sistem Akış Özeti
1. Geliştirici uygulamasını paylaşır → sistem 120 puan düşer.  
2. Katılımcılar test davetini alır → SDK doğrulaması yapılır.  
3. 12 kişi testi tamamladığında süreç otomatik kapanır.  
4. Katılımcılar puanlarını kazanır → geliştirici rapor alır.  

---

## 8. 📋 Onay & Dağıtım  
| Rol | Ad | Tarih | İmza |
|------|----|--------|-------|
| Proje Sahibi | İsmail ARICIOĞLU | 03-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 03-10-2025 | — |
| Onaylayan | BilKavTopluluğu | 03-10-2025 | — |

---

**Durum:** Tamamlandı  
**Aşama:** Sistem Gereksinimi Tanımlama  
**Bağlantılı Belgeler:** İş Gereksinimi Dokümanı (BRD), Use Case Tanımları, RTM  
