# 🔐 PlayTest Buddy – Security Model (Güvenlik Modeli ve Tehdit Analizi)

## 📘 1. Amaç
Bu doküman, **PlayTest Buddy** sisteminin güvenlik modelini, tehdit analizini ve alınacak önlemleri tanımlar.  
Amaç; kullanıcı verilerinin, test süreçlerinin ve puan işlemlerinin bütünlüğünü korumaktır.

---

## 🧩 2. Güvenlik İlkeleri
| İlke | Açıklama |
|------|-----------|
| **Gizlilik (Confidentiality)** | Verilerin yalnızca yetkili kişiler tarafından erişilebilir olması. |
| **Bütünlük (Integrity)** | Verilerin izinsiz değiştirilmemesi. |
| **Erişilebilirlik (Availability)** | Sistemin her zaman erişilebilir olması. |
| **Doğrulanabilirlik (Accountability)** | Her işlemin kim tarafından yapıldığının izlenebilmesi. |
| **Savunma Derinliği (Defense in Depth)** | Güvenlik katmanlarının çoklu düzeyde uygulanması. |

---

## ⚙️ 3. Sistem Bileşenleri ve Güvenlik Düzeyi

| Bileşen | Kritik Seviyesi | Koruma Yöntemi |
|----------|-----------------|----------------|
| **API Sunucusu** | 🔥 Yüksek | JWT tabanlı erişim, SSL, rate limiting |
| **Mobil Uygulama** | ⚡ Orta | SDK imzası, oturum anahtarı doğrulama |
| **Veritabanı (DB)** | 🔥 Yüksek | Şifreli bağlantı, veri anonimleştirme |
| **Puan Servisi** | ⚡ Orta | Transactional kayıt, replay attack önleme |
| **SDK Paketleri** | 🔒 Kritik | Kod imzalama, hash doğrulama |
| **CI/CD Pipeline** | 🔒 Kritik | Erişim anahtarı gizliliği, çevresel değişken koruması |

---

## 🧠 4. Tehdit Modelleme (STRIDE Analizi)

| Kategori | Tanım | Örnek Tehdit | Önlem |
|-----------|--------|---------------|--------|
| **S – Spoofing** | Kimlik sahtekarlığı | Sahte tester hesabı oluşturma | OAuth + MFA zorunluluğu |
| **T – Tampering** | Veri manipülasyonu | Puanın manuel değiştirilmesi | Hash + DB log izleme |
| **R – Repudiation** | İşlem reddi | “Ben o testi yapmadım” iddiası | Log imzalama, UUID kayıt |
| **I – Information Disclosure** | Bilgi sızıntısı | E-posta veya uygulama adı sızması | Maskelenmiş veriler |
| **D – Denial of Service** | Servis kesintisi | API istek fırtınası (flood attack) | Rate limiting, cache fallback |
| **E – Elevation of Privilege** | Yetki yükseltme | Normal kullanıcı admin gibi davranıyor | RBAC, token denetimi |

---

## 🔑 5. Kimlik Doğrulama & Yetkilendirme Modeli

- **JWT (JSON Web Token)** kullanılacaktır.  
- Her erişim isteği `Authorization: Bearer <token>` başlığı ile doğrulanır.  
- Token süresi 1 saat, yenileme süresi 30 gündür.  
- Roller:
  - `Admin`: tüm modüller
  - `Developer`: uygulama ekleme / puan kullanma
  - `Tester`: test katılımı ve raporlama
- Her endpoint, role-based erişim kontrolü (RBAC) ile sınırlandırılır.

---

## 🧮 6. Puan Servisi Güvenliği

| Risk | Önlem |
|------|--------|
| Puan manipülasyonu | Tüm işlem veritabanında transaction olarak tutulur. |
| Tekrarlanan çağrılar (replay attack) | Her işlem benzersiz `transaction_id` içerir. |
| Yetkisiz puan düşümü | Sadece oturum token sahibi işlem yapabilir. |

---

## 🧰 7. API Güvenliği

| Katman | Önlem |
|---------|--------|
| **Ağ Katmanı** | HTTPS + HSTS zorunlu, SSL pinning |
| **İstemci Katmanı** | API anahtarları gizlenmiş (obfuscation) |
| **Sunucu Katmanı** | Rate limiting (60 req/dk), CORS kontrolü |
| **Veri Katmanı** | AES-256 ile hassas veri şifreleme |

---

## 🧩 8. Veri Koruma & Gizlilik

- Kullanıcı verileri yalnızca test süreciyle ilgili olarak işlenir.  
- Kişisel veriler (isim, e-posta) **hash veya masked** biçimde tutulur.  
- 90 gün boyunca aktif olmayan hesaplar otomatik olarak anonimleştirilir.  
- GDPR ve KVKK uyum kontrolü yapılır.  

---

## 🧱 9. İzleme ve Olay Müdahalesi

| Olay | Tepki | Sorumlu |
|-------|--------|----------|
| Şüpheli giriş (IP değişikliği) | E-posta bildirimi | Güvenlik Ekibi |
| API aşırı istek | Otomatik IP engelleme | DevOps |
| DB erişim hatası | Snapshot + geri yükleme | DB Admin |
| SDK sahteciliği | Hash doğrulama ve raporlama | QA |

---

## 🧮 10. Güvenlik Test Planı

| Test ID | Hedef | Yöntem | Sıklık |
|----------|--------|--------|--------|
| **SEC-001** | API erişim doğrulama | Penetrasyon testi | Aylık |
| **SEC-002** | JWT manipülasyonu | Token injection test | 3 ayda bir |
| **SEC-003** | Puan verisi bütünlüğü | Transaction replay testi | Her sürüm sonrası |
| **SEC-004** | SDK kod güvenliği | Hash mismatch kontrolü | Her build sonrası |

---

## 🔐 11. Sonuç ve Değerlendirme
PlayTest Buddy platformu; savunma derinliği, kimlik doğrulama, veri bütünlüğü ve güvenli işlem tasarımı ilkeleriyle korunmaktadır.  
Sistem, gelecekte üçüncü taraf penetrasyon testlerine açık olacak şekilde tasarlanmıştır.

---

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Güvenlik, sistemin görünmeyen mimarisidir.” 🔒
