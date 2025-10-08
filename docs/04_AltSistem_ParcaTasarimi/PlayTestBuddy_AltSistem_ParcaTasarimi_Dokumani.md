# 🧠 PlayTest Buddy – Alt Sistem / Parça Tasarımı Dokümanı (LLD)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Sürüm:** v1.0  
**Model:** V-Model – Alt Sistem / Parça Tasarımı Aşaması  
**Tarih:** 05-10-2025  

---

## 1. 🎯 Amaç  
Bu dokümanın amacı, *PlayTest Buddy* sisteminin her bir alt bileşeninin teknik işleyişini tanımlamaktır.  
Burada açıklanan yapılar, sistemin geliştirme aşamasında doğrudan kullanılacak olan veri modeli, API sözleşmeleri ve SDK davranışlarını kapsar.

---

## 2. ⚙️ Mimarinin Genel Görünümü  
Sistem üç ana teknik katmandan oluşur:

| Katman | Açıklama | Örnek Teknolojiler |
|--------|-----------|--------------------|
| **Frontend (Mobil Uygulama)** | Kullanıcı arayüzü; Flutter veya Kotlin tabanlı. | Flutter SDK, Dart, Material UI |
| **Backend (API Sunucusu)** | İş mantığı, veri yönetimi ve doğrulama akışlarını barındırır. | Python (Flask / FastAPI), PostgreSQL |
| **SDK (Doğrulama Modülü)** | Test edilen uygulamaya gömülü modül; backend ile haberleşir. | Kotlin, Retrofit, JSON |

---

## 3. 🧩 Veri Modeli (Entity Relationship)

| Tablo / Koleksiyon | Açıklama | Ana Alanlar |
|--------------------|-----------|--------------|
| **users** | Geliştirici ve tester bilgilerini tutar. | id (PK), name, email, role, total_points, created_at |
| **apps** | Geliştiricinin paylaştığı test edilecek uygulamaları tutar. | id (PK), owner_id (FK→users), app_name, package_name, version, status |
| **tests** | Başlatılmış test süreçlerini temsil eder. | id (PK), app_id (FK→apps), start_date, end_date, max_testers=12, status |
| **participants** | Teste katılan kullanıcıların bilgileri. | id (PK), test_id (FK→tests), user_id (FK→users), verified (bool), joined_at |
| **transactions** | Puan hareketleri (kazanma, harcama). | id (PK), user_id (FK→users), amount, type (earn/spend), description, created_at |
| **sdk_logs** | SDK doğrulama olayları. | id (PK), user_id, app_id, test_id, event_type, timestamp, signature |

---

## 4. 🔗 İlişki Diyagramı (Metinsel Tanım)
- Bir **user**, birden fazla **app** paylaşabilir.  
- Her **app**, yalnızca bir **test** süreciyle ilişkilidir (aktif test başına).  
- Bir **test**, maksimum **12 participant** içerir.  
- Her **participant**, **sdk_logs** tablosuna bağlı doğrulama kayıtları üretir.  
- Her puan değişikliği **transactions** tablosuna yansır.  

---

## 5. 🌐 API Tasarımı

### 5.1 Kullanıcı Yönetimi
| Endpoint | Metod | Açıklama | Girdi | Çıktı |
|-----------|--------|-----------|--------|--------|
| `/api/auth/register` | POST | Yeni kullanıcı kaydı oluşturur. | `{name, email, password}` | `{user_id, token}` |
| `/api/auth/login` | POST | Kullanıcı girişi yapar. | `{email, password}` | `{token, role}` |
| `/api/user/info` | GET | Kullanıcı bilgilerini getirir. | `token` | `{id, name, total_points}` |

---

### 5.2 Test Süreci Yönetimi
| Endpoint | Metod | Açıklama | Girdi | Çıktı |
|-----------|--------|-----------|--------|--------|
| `/api/test/start` | POST | Geliştirici yeni bir test başlatır. | `{app_id}` | `{test_id, start_date, status}` |
| `/api/test/join` | POST | Tester teste katılır. | `{test_id, user_token}` | `{status: joined}` |
| `/api/test/status/{id}` | GET | Test sürecinin durumunu döner. | `test_id` | `{participants, completed, remaining}` |
| `/api/test/complete/{id}` | POST | Sistem testin tamamlandığını işaretler. | `test_id` | `{status: closed}` |

---

### 5.3 SDK Doğrulama Servisi
| Endpoint | Metod | Açıklama | Girdi | Çıktı |
|-----------|--------|-----------|--------|--------|
| `/api/sdk/verify` | POST | SDK tarafından gönderilen doğrulama isteğini işler. | `{user_id, app_id, test_id, event_type, signature}` | `{verified: true}` |
| `/api/sdk/log` | POST | SDK eventlerini loglar. | `{event_type, user_id, timestamp}` | `{status: logged}` |

---

### 5.4 Puanlama Servisi
| Endpoint | Metod | Açıklama | Girdi | Çıktı |
|-----------|--------|-----------|--------|--------|
| `/api/points/add` | POST | Kullanıcıya puan ekler. | `{user_id, amount, reason}` | `{new_balance}` |
| `/api/points/deduct` | POST | Kullanıcının puanını düşer (ör. test başlatma). | `{user_id, amount, reason}` | `{new_balance}` |
| `/api/points/history` | GET | Kullanıcının puan geçmişini döner. | `user_token` | `[transactions...]` |

---

## 6. 🔒 Güvenlik Katmanı
- **Kimlik Doğrulama:** JWT token ile.  
- **Veri İletişimi:** HTTPS + TLS 1.2.  
- **SDK Doğrulama:** Her istek, `signature = SHA256(user_id + app_id + secret_key)` ile imzalanır.  
- **Yetkilendirme:**  
  - `/api/test/start` sadece “developer” rolüne açık.  
  - `/api/test/join` sadece “tester” rolüne açık.  
  - `/api/sdk/*` yalnızca SDK token’ı ile erişilebilir.  

---

## 7. ⚙️ Uygulama Akışı (Teknik Perspektif)
1. Geliştirici giriş yapar → `/api/test/start` çağrılır → 120 puan düşülür.  
2. Tester uygulamayı indirir → `/api/test/join` çağrılır → backend katılım kaydı oluşturur.  
3. SDK, uygulama çalıştığında `/api/sdk/verify` çağrısı yapar.  
4. 12 katılımcı tamamlanınca backend testi “closed” durumuna çeker.  
5. Katılımcılar puanlarını `/api/points/add` ile kazanır.  

---

## 8. 🧱 SDK Mimarisi (Örnek Pseudocode)

```kotlin
class PlayTestSDK(private val userId: String, private val appId: String, private val testId: String) {

    fun verifySession() {
        val payload = mapOf(
            "user_id" to userId,
            "app_id" to appId,
            "test_id" to testId,
            "event_type" to "verify"
        )
        ApiClient.post("/api/sdk/verify", payload)
    }

    fun logEvent(event: String) {
        val payload = mapOf(
            "user_id" to userId,
            "app_id" to appId,
            "test_id" to testId,
            "event_type" to event,
            "timestamp" to System.currentTimeMillis()
        )
        ApiClient.post("/api/sdk/log", payload)
    }
}
```

---

## 9. 📋 Onay & Dağıtım  
| Rol | Ad | Tarih | İmza |
|------|----|--------|-------|
| Proje Sahibi | İsmail ARICIOĞLU | 05-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 05-10-2025 | — |
| Onaylayan | BilKavTopluluğu |  | — |

---

**Durum:** Taslak  
**Aşama:** Alt Sistem / Parça Tasarımı (LLD)  
**Bağlantılı Belgeler:** BRD, SRD, FDD, RTM  
