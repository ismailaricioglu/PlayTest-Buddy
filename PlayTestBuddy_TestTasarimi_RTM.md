
# 🧪 PlayTest Buddy – Test Tasarımı ve RTM Dokümanı (Revize & Tutarlı)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Gözden Geçiren:** ChatGPT (Yapay Asistan)  
**Model:** V-Model – Test Aşaması  
**Tarih:** 06-10-2025  
**Durum:** Onay Adayı  

---

## 1. 🎯 Amaç  
Bu doküman, *PlayTest Buddy* sistemine ait tüm gereksinimlerin doğrulanabilir şekilde test edilmesini ve gereksinim–test eşleştirmesinin izlenebilirliğini sağlar.  
Test kapsamı **V-Model doğrulama evresinin dört temel seviyesini** içerir:

1. **Kabul Testleri (AT)** → İş Gereksinimleri (BRD)  
2. **Sistem Testleri (ST)** → Sistem Gereksinimleri (SRD)  
3. **Entegrasyon Testleri (IT)** → Fonksiyonel Tasarım (FDD)  
4. **Birim Testleri (UT)** → Alt Sistem / Parça Tasarımı (LLD)

---

## 2. 🧩 Test Seviyeleri ve Kapsam

| Test Seviyesi | Amaç | Referans Doküman | Sorumlu |
|----------------|------|------------------|----------|
| **AT – Kabul Testi** | İş hedeflerinin karşılandığını doğrular. | BRD | BilKavTopluluğu |
| **ST – Sistem Testi** | Sistemin genel fonksiyonlarını test eder. | SRD | Geliştirme Ekibi |
| **IT – Entegrasyon Testi** | Modüllerin etkileşimini test eder. | FDD | Backend & Mobil geliştiriciler |
| **UT – Birim Testi** | Her bileşenin bağımsız doğruluğunu test eder. | LLD | Geliştirici |

---

## 3. ⚙️ Test Stratejisi

| Boyut | Yaklaşım |
|--------|-----------|
| **Yöntem** | Fonksiyonel + doğrulama temelli testler |
| **Test Ortamı** | Android cihazlar (gerçek), Flask tabanlı backend |
| **Yürütme** | İlk sürümde manuel, ilerleyen sürümlerde otomatikleştirilebilir |
| **Başarı Kriteri** | Tüm test senaryolarının “PASSED” olması |
| **Hata Yönetimi** | Hatalar kaydedilir → analiz edilir → yeniden test yapılır |

---

## 4. 🧾 RTM (Requirement Traceability Matrix)

| Gereksinim ID | Gereksinim Tanımı | Test ID | Test Tipi | Başarı Kriteri |
|----------------|------------------|----------|------------|----------------|
| **GR-001** | Kullanıcı kayıt & giriş işlemleri yapılabilmelidir. | AT-001, UT-001 | Kabul, Birim | Kullanıcı kayıt ve giriş işlemi başarılı olmalıdır. |
| **GR-002** | Geliştirici uygulamasını test sürecine dahil edebilmelidir. | ST-001, IT-001 | Sistem, Entegrasyon | Test başlatma işlemi hatasız gerçekleşmelidir. |
| **GR-003** | Test süreci 12 katılımcı ile sınırlıdır. | ST-002, IT-002 | Sistem, Entegrasyon | 12. katılımcıdan sonra yeni katılım reddedilmelidir. |
| **GR-004** | Katılımcı doğrulaması SDK üzerinden yapılmalıdır. | UT-002, IT-003 | Birim, Entegrasyon | SDK yanıtı `verified=true` olmalıdır. |
| **GR-005** | Puanlama sistemi kullanıcı etkinliğine göre işlemelidir. | ST-003, UT-003 | Sistem, Birim | 120 puan düşümü ve 10 puan kazanımı doğru hesaplanmalıdır. |
| **GR-006** | Test tamamlandığında sistem süreci otomatik sonlandırmalıdır. | ST-004 | Sistem | 12 katılımcı tamamlanınca test durumu “closed” olmalıdır. |

---

## 5. 🧪 Test Senaryoları

### **AT-001 – Kullanıcı Kaydı Kabul Testi**
| Başlık | Kullanıcı kayıt işleminin doğrulanması |
|--------|----------------------------------------|
| **Ön Koşul** | Sistem aktif, kayıt formu erişilebilir. |
| **Adımlar** | 1. Kullanıcı kayıt formuna girer.<br>2. Ad, e-posta, şifre girilir.<br>3. “Kaydol” butonuna basılır. |
| **Beklenen Sonuç** | Kayıt başarılı, kullanıcı oturum açabilir. |

---

### **ST-002 – Katılımcı Sınırlandırma Testi**
| Başlık | Katılımcı sayısı 12 olduğunda sistemin yeni katılımı engellemesi |
|--------|-------------------------------------------------------------|
| **Ön Koşul** | Test süreci aktif, 11 katılımcı mevcut. |
| **Adımlar** | 1. Yeni tester katılım isteği gönderir.<br>2. Backend doğrular.<br>3. Katılım sayısı sınırdaysa reddedilir. |
| **Beklenen Sonuç** | Katılım reddedilir, mesaj: *“Katılımcı limiti dolmuştur.”* |

---

### **IT-003 – SDK Doğrulama Akışı**
| Başlık | SDK doğrulama isteğinin backend’e iletilmesi |
|--------|----------------------------------------------|
| **Ön Koşul** | SDK yapılandırılmış, geçerli `test_id` atanmış. |
| **Adımlar** | 1. SDK `verifySession()` çağrısı yapar.<br>2. `/api/sdk/verify` endpoint’i çağrılır.<br>3. Backend imzayı doğrular. |
| **Beklenen Sonuç** | `{verified: true}` döner, log kaydı oluşur. |

---

### ✅ **UT-003 – Puan Güncelleme İşlevi (Güncel)**
| Başlık | Puan ekleme ve düşürme işlemlerinin doğrulanması |
|--------|---------------------------------------------------|
| **Ön Koşul** | Kullanıcı sistemde kayıtlı, başlangıç puanı = 120. |
| **Adımlar** |  
1️⃣ `/api/points/add` çağrısı yapılır (+10 puan – test katkısı).  
2️⃣ `/api/points/deduct` çağrısı yapılır (–120 puan – test başlatma). |
| **Beklenen Sonuç** |  
- İlk işlem sonrası bakiye = **130 puan**  
- İkinci işlem sonrası bakiye = **10 puan**  
Ayrıca `transactions` tablosuna doğru kayıt eklenmelidir. |

**Beklenen DB Kaydı:**
```plaintext
+----+----------+--------+---------+-----------------------------+
| ID | user_id  | amount | type    | description                 |
+----+----------+--------+---------+-----------------------------+
|  1 |   U001   | +10    | earn    | "Test katkısı"              |
|  2 |   U001   | -120   | spend   | "Yeni test aktivasyonu"     |
+----+----------+--------+---------+-----------------------------+
```

---

## 6. 📈 Test Başarı Kriterleri

| Kategori | Ölçüt |
|-----------|--------|
| **Kapsam** | %100 gereksinim–test bağlantısı sağlanmış olmalı |
| **Kabul** | Kritik testlerin tümü başarıyla geçmeli |
| **Performans** | API yanıt süresi < 300 ms, SDK doğrulama < 1 sn |
| **Güvenlik** | Tüm token’lar TLS 1.2+ üzerinden şifrelenmeli |
| **İzlenebilirlik** | Her test, RTM üzerinden ilgili gereksinime izlenebilir olmalı |

---

## 7. 🧾 Onay & İzleme  

| Rol | Ad | Tarih | İmza |
|------|----|--------|------|
| Test Koordinatörü | İsmail ARICIOĞLU | 06-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 06-10-2025 | — |
| Onaylayan | BilKavTopluluğu | 06-10-2025 | — |

---

## 🔗 Bağlantılı Belgeler  
- **BRD:** İş Gereksinimi Dokümanı  
- **SRD:** Sistem Gereksinimi Dokümanı  
- **FDD:** Fonksiyonel Tasarım Dokümanı  
- **LLD:** Alt Sistem / Parça Tasarımı Dokümanı  

---

✅ **Tutarlılık Özeti:**
- 120 puan düşüm mantığı (GR-005) ile tüm testler uyumlu.  
- SDK doğrulama süreci (GR-004) testlerle birebir bağlı.  
- Katılımcı sınırlaması (GR-003) politikaya uygun biçimde sabit 12 kişi.  
- RTM tablosu tüm gereksinim zincirini kapatıyor.  
