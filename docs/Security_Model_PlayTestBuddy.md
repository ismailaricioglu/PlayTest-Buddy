# 🛡️ Security Model – PlayTest Buddy (v1.0.0 MVP)

## 🌟 1. Amaç

Bu doküman, PlayTest Buddy platformunun güvenlik modelini tanımlar.
Amaç, **ilk sürüm (v1.0.0)** için gerekli minimum güvenlik gereksinimlerini sağlamak, kullanıcı verisini korumak ve sistem bütünlüğünü garanti altına almaktır.

---

## ⚙️ 2. Kapsam

* MVP sürümünde yer alan API, SDK ve mobil istemci
* Kimlik doğrulama, yetkilendirme, veri koruma ve gizli anahtar yönetimi
* CI/CD sürecinde kimlik bilgileri yönetimi

> 🚫 Bu doküman saldırı tespiti, log analizi veya refresh token yönetimi gibi ileri seviye güvenlik mekanizmalarını **kapsamaz**.
> Bu konular **Phase 2 (Hardening & Scalability)** notlarında ele alınacaktır.

---

## 🧬 3. Mimari Bileşenler

### 🔹 3.1 Authentication Service

**Amaç:** Kullanıcıların sisteme güvenli giriş yapmasını sağlamak.
**Yöntem:**

* Kullanıcı oturumları JWT (JSON Web Token) ile yönetilir.
* Parolalar `bcrypt` veya `SHA-256` algoritmasıyla hashlenir.
* Token süreleri kısa tutulur (15 dakika).
* Access token verildiğinde user ID, role ve timestamp payload içinde saklanır.

**Bağımlılıklar:**

* User Service
* DB (PostgreSQL)

---

### 🔹 3.2 Authorization Gateway

**Amaç:** Tüm API çağrılarında erişim kontrolünü merkezileştirmek.
**Yöntem:**

* Public (login/register) ve Private (test, puan, rapor) endpoint’ler ayrılır.
* Token doğrulaması middleware katmanında yapılır.
* Yetkisiz isteklerde `HTTP 401 / 403` kodları döner.
* Role tabanlı policy kontrolü için `accessPolicy.json` veya RBAC tablosu kullanılır.

---

### 🔹 3.3 Role-Based Access Controller (RBAC)

**Amaç:** Kullanıcı rollerine göre erişim seviyesini belirlemek.
**Roller:**

| Rol           | Yetki                            | Açıklama                                   |
| ------------- | -------------------------------- | ------------------------------------------ |
| `admin`       | Full Access                      | Tüm modüller üzerinde işlem yapabilir.     |
| `contributor` | Test başlatma / uygulama yükleme | Uygulama ekleyip test süreci başlatabilir. |
| `tester`      | Test katılımı / puan kazanma     | Teste katılabilir, puan toplayabilir.      |

**Politika Yönetimi:**
Roller merkezi bir JSON dosyası veya veritabanı üzerinden yönetilir.
Policy güncellemeleri CI/CD pipeline’ında migrate edilir.

---

### 🔹 3.4 Security Context Middleware

**Amaç:** Her istekte kimlik bilgilerini doğrulamak ve izlenebilirlik sağlamak.
**Yöntem:**

* Her `HTTP request` için context objesi oluşturulur.
* İçerik: `user_id`, `session_id`, `request_time`, `ip_address`.
* Bu bilgiler log kayıtlarına entegre edilir (Audit v2.0’da genişletilecek).

---

### 🔹 3.5 Secret Management

**Amaç:** Sistem içi hassas verilerin güvenli yönetimi.
**Yöntem:**

* `.env` dosyaları versiyon kontrolüne dahil edilmez.
* CI/CD ortam değişkenleri GitHub Secrets veya Vault üzerinde saklanır.
* API anahtarları sadece build time’da erişilebilir.
* Gerektiğinde otomatik rotasyon yapılabilir (Phase 2 önerisi).

---

## 🧱️ 4. Güvenlik Akışı (High-Level Flow)

```
[Client] → [Auth API] → [Token Issue] → [Gateway Validation] → [RBAC Check] → [Business Logic]
```

1. Kullanıcı kimlik doğrulaması yapılır.
2. Token üretilir ve client’a iletilir.
3. Her istek, Gateway katmanında doğrulanır.
4. RBAC politikaları uygulanır.
5. Yetkili kullanıcı iş mantığına erişir.

---

## 🚀 5. Faz Planlaması

| Faz                     | Bileşen                                       | Durum         | Açıklama                          |
| ----------------------- | --------------------------------------------- | ------------- | --------------------------------- |
| **Phase 1 (MVP)**       | Auth Service, Gateway, RBAC, Context, Secrets | ✅ Uygulanacak | Yayınlanabilir minimum yapı       |
| **Phase 2 (Hardening)** | Refresh Token, Audit, IDS/RateLimiter         | 🕓 Planlı     | Dayanıklılık ve ölçeklenme evresi |

---

## 🔒 6. Güvenlik Gereksinimleri (Özet)

| ID     | Gereksinim                                              | Türü        | Öncelik |
| ------ | ------------------------------------------------------- | ----------- | ------- |
| SEC-01 | JWT ile kimlik doğrulama sağlanmalı                     | Fonksiyonel | Yüksek  |
| SEC-02 | Token süresi 15 dakikayı geçmemeli                      | Fonksiyonel | Yüksek  |
| SEC-03 | RBAC yapısı tüm API çağrılarını kontrol etmeli          | Fonksiyonel | Yüksek  |
| SEC-04 | API anahtarları maskelenmeli ve .env dışına çıkarılmalı | Güvenlik    | Yüksek  |
| SEC-05 | Loglarda hassas veri (token, parola) yer almamalı       | Güvenlik    | Orta    |

---

## 📦 7. Dokümentasyon İlişkileri

| Doküman                           | Amaç                                |
| --------------------------------- | ----------------------------------- |
| `System_Requirements.md`          | Genel sistem bileşenleriyle uyum    |
| `Functional_Design.md`            | API endpoint ve servis ilişkisi     |
| `CI_CD_Pipeline_PlayTestBuddy.md` | Güvenli build ve deploy süreci      |
| `Release_Plan_PlayTestBuddy.md`   | Sürüm bazlı güvenlik faz planlaması |

---

## 🧭 8. Sonuç

Bu model, PlayTest Buddy’nin ilk sürümünde **gereken güvenlik temellerini** tanımlar.
Bu temeller, CI/CD pipeline’a entegre edilerek sürümden sürüme **güvenli sürdürülebilirlik** sağlar.

> “Güvenlik bir katman değil, bir kültürdür.” — Çet 🧠f
