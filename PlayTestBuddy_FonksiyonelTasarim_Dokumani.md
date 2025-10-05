# ⚙️ PlayTest Buddy – Fonksiyonel Tasarım Dokümanı (FDD)

**Hazırlayan:** İsmail ARICIOĞLU – BilKavTopluluk Üyesi  
**Sürüm:** v1.0  
**Model:** V-Model – Fonksiyonel Tasarım Aşaması  
**Tarih:** 04-10-2025  

---

## 1. 🎯 Amaç  
Bu doküman, *PlayTest Buddy* sisteminin fonksiyonel yapısını tanımlar.  
Her bir sistem fonksiyonunun işleyiş biçimi, girdileri, çıktıları ve kullanıcı etkileşimi düzeyi açıklanır.  
Ayrıca sistem modülleri arasındaki veri akışı ve ilişkiler tanımlanır.

---

## 2. 🧩 Sistem Modülleri  
Sistem aşağıdaki ana modüllerden oluşur:

| Modül Adı | Açıklama | Sorumlu Fonksiyonlar |
|------------|-----------|----------------------|
| **M1 – Kullanıcı Yönetimi** | Geliştirici ve tester hesaplarının oluşturulması, giriş ve kimlik doğrulama işlemleri. | Kayıt, Giriş, JWT Token üretimi |
| **M2 – Uygulama Paylaşım & Test Yönetimi** | Geliştiricinin uygulamasını test için paylaşması, test durumlarının izlenmesi. | Test başlatma, katılımcı daveti, test tamamlama |
| **M3 – SDK Doğrulama** | Test edilen uygulamada çalışan SDK’nın test olaylarını backend’e raporlaması. | SDK event gönderimi, kullanıcı doğrulaması |
| **M4 – Puanlama Servisi** | Kullanıcıların testlerden puan kazanması veya harcaması. | Puan ekleme, puan düşme, puan geçmişi |
| **M5 – Raporlama & Analitik** | Geliştiricilere test ilerleme ve katılım raporlarını sunar. | Rapor görüntüleme, istatistik üretimi |

---

## 3. 🔄 Fonksiyonel Akışlar

### **FA-001 – Kullanıcı Kaydı & Giriş**
**Amaç:** Kullanıcıların sisteme kayıt olup kimlik doğrulaması yapabilmesi.  
**Girdi:** Ad, e-posta, şifre (Google hesabı).  
**İşlem:**  
1. Kullanıcı kayıt formunu doldurur.  
2. Sistem e-posta doğrulaması ister.  
3. Girişte JWT token üretir.  
**Çıktı:** Kullanıcı erişimi sağlanır.  
**İlgili Modül:** M1  

---

### **FA-002 – Test Başlatma (Geliştirici)**
**Amaç:** Geliştiricinin yeni bir test süreci başlatması.  
**Girdi:** APK dosyası, test adı, açıklama, test süresi (otomatik 14 gün).  
**İşlem:**  
1. Geliştirici paylaşım ekranından uygulama detaylarını girer.  
2. Sistem 120 puanı düşer.  
3. Test ID oluşturulur.  
4. Katılımcı listesi başlatılır.  
**Çıktı:** Test süreci aktif hale gelir.  
**İlgili Modül:** M2, M4  

---

### **FA-003 – Teste Katılım (Tester)**
**Amaç:** Tester’ın mevcut test listesinde yer alan uygulamalardan birine katılması.  
**Girdi:** Test ID, kullanıcı ID.  
**İşlem:**  
1. Kullanıcı test listesinde bir uygulama seçer.  
2. Uygulama SDK’sı, test başlama bilgisini backend’e gönderir.  
3. Katılım kaydedilir.  
**Çıktı:** Katılımcı sayısı artar.  
**İlgili Modül:** M2, M3  

---

### **FA-004 – SDK Doğrulama**
**Amaç:** Test edilen uygulamanın gerçekten indirildiğini ve çalıştırıldığını doğrulamak.  
**Girdi:** SDK Event (user_id, app_id, timestamp).  
**İşlem:**  
1. SDK backend’e doğrulama isteği yollar.  
2. Backend bu isteği test ID ile eşleştirir.  
3. Doğrulama log’u oluşturulur.  
**Çıktı:** Kullanıcı doğrulanmış olarak işaretlenir.  
**İlgili Modül:** M3  

---

### **FA-005 – Puan Kazanımı**
**Amaç:** Tester’ın bir testi tamamladığında puan kazanması.  
**Girdi:** Test ID, kullanıcı ID, SDK doğrulama onayı.  
**İşlem:**  
1. Sistem testin tamamlandığını SDK loglarından teyit eder.  
2. Kullanıcıya +10 puan eklenir.  
3. Puan cüzdanı güncellenir.  
**Çıktı:** Yeni puan bakiyesi görünür hale gelir.  
**İlgili Modül:** M4  

---

### **FA-006 – Rapor Görüntüleme**
**Amaç:** Geliştiricinin test durumunu ve katılım sayısını izlemesi.  
**Girdi:** Test ID.  
**İşlem:**  
1. Geliştirici rapor sekmesine girer.  
2. Sistem test durumu (aktif, tamamlandı, iptal) ve katılımcı listesi döner.  
3. Puan ve test istatistikleri sunulur.  
**Çıktı:** Görsel rapor ekranı.  
**İlgili Modül:** M5  

---

## 4. 🔗 Modüller Arası Etkileşim  
| Kaynak Modül | Hedef Modül | Veri / İşlev | Açıklama |
|---------------|--------------|---------------|------------|
| M2 | M4 | test_id, user_id, puan | Test tamamlandığında puan ekleme |
| M3 | M2 | user_id, event | SDK doğrulama bildirimi |
| M1 | M4 | user_token | Puanlama işlemleri için kimlik doğrulama |
| M2 | M5 | test_id | Raporlama için test durum verisi |

---

## 5. 📊 Kullanıcı Rolleri & Yetkiler  
| Rol | Yetkiler | Kısıtlar |
|------|-----------|-----------|
| **Geliştirici** | Uygulama paylaşımı, test başlatma, rapor görüntüleme | 120 puan şartı |
| **Tester** | Teste katılma, puan kazanma | Maksimum 3 aktif test |
| **Sistem (Arka Plan)** | Puan hesaplama, doğrulama, süreç kapatma | Manuel müdahale yok |

---

## 6. ⚙️ Fonksiyonel Kısıtlar  
- Her kullanıcı en fazla 3 testte aynı anda yer alabilir.  
- Aynı testte bir kullanıcı birden fazla kez yer alamaz.  
- **Test süreci, Google Play Console politikalarına uygun olarak 12 katılımcı ile sınırlandırılmıştır.**  
  Politikalar değişmediği sürece minimum ve maksimum katılımcı sayısı **12 olarak sabittir.**  
- SDK doğrulaması yapılmayan testler geçersiz sayılır.  

---

## 7. 🧭 Geleceğe Yönelik Planlı Fonksiyonlar  
| Kod | Fonksiyon | Açıklama |
|------|------------|-----------|
| **FA-FUT-01** | Tester Profili & Rozet Sistemi | Katkı puanlarına göre rozet kazanımı |
| **FA-FUT-02** | Test Senaryosu Paylaşımı | Otomatik test adımı oluşturma |
| **FA-FUT-03** | Ekip Testleri | Ekip bazlı puan havuzu paylaşımı |

---

## 8. 📋 Onay & Dağıtım  
| Rol | Ad | Tarih | İmza |
|------|----|--------|-------|
| Proje Sahibi | İsmail ARICIOĞLU | 04-10-2025 | — |
| Gözden Geçiren | ChatGPT (Yapay Asistan) | 04-10-2025 | — |
| Onaylayan | BilKavTopluluğu | 04-10-2025 | — |

---

**Durum:** Tamamlandı  
**Aşama:** Fonksiyonel Tasarım  
**Bağlantılı Belgeler:** BRD, SRD, RTM, Mockup Görselleri  
