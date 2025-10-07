
# 🧩 PlayTest Buddy – Detay Tasarım Dokümanı (DDD)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Gözden Geçiren:** ChatGPT (Yapay Asistan)  
**Model:** V-Model – Detay Tasarım Aşaması  
**Tarih:** 07-10-2025  
**Durum:** Onaylı  

---

## 1. 🎯 Amaç  
Bu doküman, *PlayTest Buddy* uygulamasının düşük seviye (detailed) tasarımını açıklamaktadır.  
Amaç, sistemin modüllerinin, veri akışlarının ve arayüzlerinin teknik detaylarını netleştirerek geliştirme aşamasına sağlam bir temel oluşturmaktır.

---

## 2. 📚 Referanslar  
| Doküman | Kod | Açıklama |
|----------|------|-----------|
| İş Gereksinimi | BRD | İş hedefleri |
| Sistem Gereksinimi | SRD | Sistem fonksiyonları |
| Fonksiyonel Tasarım | FDD | Modül işlevleri |
| Alt Sistem / Parça Tasarımı | LLD | Modül yapısı ve API tanımı |
| Test Tasarımı & RTM | TTD | Gereksinim-test izlenebilirliği |

---

## 3. 🧠 Genel Mimari Özeti  

**Mimari Model:** Katmanlı (Layered Architecture)  
- **Presentation Layer (Flutter)** – kullanıcı arayüzü ve SDK işlemleri  
- **Application Layer (Flask API)** – iş akış kontrolü, puanlama ve doğrulama servisleri  
- **Data Layer (PostgreSQL)** – kullanıcı, test ve puan tabloları  

```plaintext
[Flutter UI] → [Flask REST API] → [PostgreSQL]
```

---

## 4. 🧱 Bileşen Diyagramı  

| Katman | Modül | Sorumluluk | Girdi | Çıktı |
|---------|--------|-------------|--------|--------|
| UI | TestDashboard | Test süreçlerini görüntüleme | Kullanıcı kimliği | Test listesi |
| UI | WalletScreen | Puan bilgilerini gösterme | Kullanıcı ID | Güncel puan |
| API | PointsService | Puan kazandırma / düşürme işlemleri | user_id, action | Güncel puan |
| API | SDKVerifier | Katılımcı doğrulama işlemi | sdk_token | verified flag |
| API | TestOrchestrator | Test sürecini yönetme | app_id, participants | test_state |
| DB | Users | Kullanıcı bilgileri | — | — |
| DB | Points | Puan işlemleri | — | — |
| DB | Tests | Test süreçleri | — | — |

---

## 5. 🧩 Veri Modeli  

### 5.1 Tablolar

#### **Users**
| Alan | Tür | Açıklama |
|------|------|----------|
| user_id | UUID | Kullanıcı kimliği |
| email | VARCHAR(100) | Giriş e-postası |
| password_hash | VARCHAR(255) | Şifrelenmiş parola |
| points | INT | Mevcut puan |
| join_date | TIMESTAMP | Kayıt tarihi |

#### **Tests**
| Alan | Tür | Açıklama |
|------|------|----------|
| test_id | UUID | Test kimliği |
| app_name | VARCHAR(100) | Uygulama adı |
| developer_id | UUID | Geliştirici kimliği |
| participants | INT | Katılımcı sayısı |
| status | ENUM(‘open’, ‘closed’) | Test durumu |
| start_date | TIMESTAMP | Başlangıç tarihi |
| end_date | TIMESTAMP | Bitiş tarihi |

#### **PointsTransactions**
| Alan | Tür | Açıklama |
|------|------|----------|
| txn_id | UUID | İşlem kimliği |
| user_id | UUID | Kullanıcı ID |
| amount | INT | Puan miktarı |
| type | ENUM('earn', 'spend') | İşlem türü |
| description | VARCHAR(255) | Açıklama |
| txn_date | TIMESTAMP | İşlem tarihi |

---

## 6. ⚙️ API Tasarımı  

### 6.1 PointsService (Revize)

| Endpoint | Metod | Parametre | Açıklama | Örnek Yanıt |
|-----------|--------|------------|------------|--------------|
| `/api/points/add` | POST | user_id, amount=10 | Kullanıcıya **+10 puan** kazandırır (ör. test katkısı) | `{ "success": true, "balance": 130 }` |
| `/api/points/deduct` | POST | user_id, amount=120 | Kullanıcının bakiyesinden **120 puan** düşer (ör. yeni test aktivasyonu) | `{ "success": true, "balance": 10 }` |
| `/api/points/balance` | GET | user_id | Güncel puanı döner | `{ "balance": 10 }` |

---

### 6.2 SDKVerifier  

| Endpoint | Metod | Parametre | Açıklama | Örnek Yanıt |
|-----------|--------|------------|------------|--------------|
| `/api/sdk/verify` | POST | sdk_token, app_id | Katılımcı doğrulama isteği | `{ "verified": true }` |

---

### 6.3 TestOrchestrator  

| Endpoint | Metod | Parametre | Açıklama | Örnek Yanıt |
|-----------|--------|------------|------------|--------------|
| `/api/test/start` | POST | developer_id, app_id | Yeni test başlatır | `{ "test_id": "...", "status": "open" }` |
| `/api/test/join` | POST | test_id, user_id | Katılımcı ekler | `{ "participants": 12, "status": "open" }` |
| `/api/test/close` | POST | test_id | Testi kapatır | `{ "status": "closed" }` |

---

## 7. 🧮 Algoritma Taslakları  

### 7.1 Puan Güncelleme (Debit/Credit)
```python
def update_points(user_id, amount, type):
    user = db.users.get(user_id)
    if type == "earn":
        user.points += amount
    elif type == "spend":
        if user.points >= amount:
            user.points -= amount
        else:
            raise ValueError("Insufficient balance")
    db.points_transactions.insert(user_id, amount, type)
    return user.points
```

---

### 7.2 Test Katılım Yönetimi
```python
def join_test(test_id, user_id):
    test = db.tests.get(test_id)
    if test.participants >= 12:
        return {"error": "Katılımcı limiti dolmuştur."}
    test.participants += 1
    db.tests.update(test_id, participants=test.participants)
    if test.participants == 12:
        test.status = "closed"
        db.tests.update(test_id, status="closed")
    return {"participants": test.participants, "status": test.status}
```

---

## 8. 🔒 Güvenlik Özeti  

| Alan | Uygulama |
|------|-----------|
| **Kimlik Doğrulama** | JWT (Bearer Token) |
| **Veri Şifreleme** | TLS 1.3 (API), bcrypt (şifre) |
| **Doğrulama Mantığı** | SDK → API imza eşleşmesi |
| **Hata Yönetimi** | 400: Bad Request, 401: Unauthorized, 409: Limit Error |

---

## 9. 🔍 Tasarım Doğrulama ve Eşleştirme Tablosu  

| Test ID | Gereksinim | Doğrulama Yöntemi | Eşleştirme Durumu | Açıklama |
|----------|-------------|--------------------|--------------------|-----------|
| **UT-003** | GR-005 | Birim Test | ✔ | Gereksinim → API (PointsService) → Test senaryosu bağlantısı tamam. |
| **IT-003** | GR-004 | Entegrasyon Test | ✔ | SDK doğrulama akışı API seviyesinde tanımlandı. |
| **ST-002** | GR-003 | Sistem Test | ✔ | Katılımcı limiti (12 kişi) tasarımda belirtildi ve sistem akışına işlendi. |

> Bu tablo, testlerin uygulanma aşamasından önceki **tasarım-doğrulama eşleştirmesini** gösterir.  
Henüz testler çalıştırılmamıştır, ancak gereksinimler ve tasarım arasında tam izlenebilirlik sağlanmıştır.  

---

## 10. 🧾 Onay  

| Rol | Ad | Tarih | İmza |
|------|----|--------|------|
| Tasarımcı | İsmail ARICIOĞLU | 07-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 07-10-2025 | — |
| Onaylayan | BilKavTopluluğu | 07-10-2025 | — |

---
