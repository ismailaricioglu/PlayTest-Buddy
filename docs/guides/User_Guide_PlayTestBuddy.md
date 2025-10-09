# 📱 PlayTest Buddy – User Guide (Kullanıcı Rehberi)

## 🎯 Amaç
Bu rehber, PlayTest Buddy uygulamasını kullanmak isteyen **geliştiriciler**, **testerlar** ve **topluluk üyeleri** için adım adım kullanım talimatlarını içerir.

PlayTest Buddy, Google Play politikalarına uygun bir şekilde uygulama test sürecini **otomatikleştiren ve topluluk temelli olarak organize eden** bir platformdur.

---

## 👥 Kullanıcı Rolleri

| Rol | Açıklama |
|------|-----------|
| 👨‍💻 **Geliştirici (Developer)** | Kendi uygulamasını test ettirmek isteyen kullanıcı. |
| 🧪 **Tester (Katılımcı)** | Başkalarının uygulamalarını test ederek puan kazanan kullanıcı. |
| 🤝 **Topluluk Üyesi** | Her iki rolü de üstlenebilen aktif BilKav topluluk katılımcısı. |

---

## 🧾 1. Kayıt ve Giriş

### 📱 Mobil Uygulama Üzerinden
1. Uygulamayı Google Play üzerinden indirin.  
2. “Giriş Yap” butonuna dokunun.  
3. Google hesabınızı seçerek kayıt işlemini tamamlayın.  

✅ İlk kayıt sonrası sistem size **120 başlangıç puanı** tanımlar.

---

## 🚀 2. Geliştirici Olarak Uygulama Paylaşımı

### 📤 Uygulama Testi Başlatma
1. “Test Başlat” sekmesine gidin.  
2. Test etmek istediğiniz `.apk` dosyasını yükleyin.  
3. Uygulama adı, sürüm ve açıklamasını girin.  
4. Sistem otomatik olarak test sürecini oluşturur (12 tester gereklidir).  
5. 120 puan düşülür → test etkin hale gelir.  

📦 **Politika Gereği:**  
Test süresi **en az 14 gün**, **katılımcı sayısı minimum 12**’dir.  
Google Play politikası değişmedikçe bu sınırlamalar sabittir.

---

## 🧪 3. Tester Olarak Katılım

### 🔍 Uygulama Testine Katılma
1. Ana ekrandaki “Aktif Testler” bölümüne girin.  
2. Test etmek istediğiniz uygulamayı seçin.  
3. “Katıl” butonuna basarak katılımı onaylayın.  
4. APK otomatik olarak indirilir.  
5. Test tamamlandıktan sonra uygulama içinden “Testi Bitir” butonuna dokunun.  

Her tamamlanan test için:
- **+10 puan** kazanırsınız  
- Puanlarınız **puan cüzdanında** anlık olarak güncellenir  

---

## 💰 4. Puanlama Sistemi

| İşlem | Puan Değeri | Açıklama |
|--------|--------------|----------|
| Teste katılma | +10 | Her test sonrası otomatik eklenir |
| Kendi uygulamasını test ettirme | -120 | Test aktivasyonu sırasında düşülür |
| Minimum puan | 0 | Negatif puan oluşmaz |
| Başlangıç puanı | 120 | Yeni üyeler için tek seferlik |

📊 Puanlar sistemdeki `Puan Servisi API` tarafından doğrulanır.

---

## 📡 5. Test Doğrulama Mekanizması

Sistemde yer alan her test oturumu, **PlayTest Buddy SDK** aracılığıyla doğrulanır:

- SDK, test edilen uygulamanın içerisine eklenir.  
- Her tester’ın kimliği sistem log’larına işlenir.  
- Katılım sayısı API üzerinden doğrulanır.  

Örnek SDK kodu (Kotlin):
```kotlin
PlayTestVerifier.verify(
    testerId = "tester_001",
    appId = "com.example.myapp",
    sessionId = "PTB-2025-TEST-00012"
)
```

---

## 🧩 6. Raporlama ve Geri Bildirim

### 📈 Test Raporu
Geliştirici, test süreci tamamlandıktan sonra:
- Katılımcı sayısını,
- Ortalama test süresini,
- Tester geri bildirimlerini  
tek ekranda görebilir.

### 💬 Geri Bildirim Gönderme
Tester’lar uygulama hakkında kısa yorumlar gönderebilir.  
Bu veriler, sadece geliştirici ve sistem yöneticisi tarafından görüntülenir.

---

## 🔐 7. Güvenlik ve Gizlilik

| Politika | Açıklama |
|-----------|-----------|
| Veri gizliliği | Kullanıcı verileri yalnızca test doğrulama amacıyla loglanır. |
| Yetkilendirme | Sadece e-posta doğrulamalı kullanıcılar test paylaşabilir. |
| Açık kaynak SDK | SDK kodu herkese açık olup, güvenlik incelemesine açıktır. |

---

## 🔄 8. Puan Aktivasyonu Döngüsü (Örnek Senaryo)

```
Tester 12 farklı ürünü test eder → 120 puan kazanır
↓
Kendi uygulamasını test ettirmek ister
↓
Sistem 120 puan düşer
↓
Test oturumu başlatılır (12 yeni tester atanır)
↓
Test tamamlanınca rapor oluşturulur
```

Bu sistem, **dayanışma esaslı** bir döngü yaratır:  
> “Kazanarak katkı sağla, katkı sağlayarak test ettir.”

---

## 🧩 9. Sık Karşılaşılan Sorunlar (FAQ)

| Soru | Yanıt |
|------|-------|
| 🔹 Teste katıldım ama puanım artmadı | Uygulama içinde “Testi Bitir” butonuna basılmadıysa puan eklenmez. |
| 🔹 Test süresi dolmadan test bitti | Katılımcı sayısı dolduğunda test otomatik olarak kapanır. |
| 🔹 Uygulamayı yükleyemiyorum | APK dosyası Play Protect tarafından engellenmiş olabilir. |
| 🔹 SDK doğrulama başarısız | Geliştirici doğru `sessionId` parametresini girdiğinden emin olmalı. |

---

## 💬 10. Destek ve Topluluk

- **Destek:** support@bilkav.org  
- **Topluluk:** [BilKavTopluluk Discussions](https://github.com/BilKavTopluluk/PlayTestBuddy/discussions)  
- **Güvenlik:** security@bilkav.org  

---

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Bir test, sadece kodu değil; topluluğun gücünü de doğrular.” 💪
