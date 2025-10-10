# 🧩 PlayTest Buddy – Admin & Maintenance Guide (Yönetici ve Bakım Rehberi)

## 📘 1. Amaç
Bu doküman, **PlayTest Buddy** sisteminin sürekliliğini, veri güvenliğini ve güncel kalmasını sağlamak için sistem yöneticileri ve bakım ekibine rehberlik eder.  
Amaç; test platformunun stabil, ölçeklenebilir ve güvenli bir şekilde işletilmesini sağlamaktır.

---

## 🧱 2. Sistem Bileşenleri

| Alt Sistem | Açıklama | Sorumlu |
|-------------|-----------|----------|
| **API Sunucusu** | Tester doğrulama, puan işlemleri ve raporlama isteklerini yönetir. | Backend Admin |
| **Mobil Uygulama** | Tester ve geliştirici arayüzü. | App Developer |
| **Veritabanı (DB)** | Katılımcı, puan, test ve log verilerini saklar. | DB Admin |
| **SDK (Android)** | Uygulamalara entegre edilen doğrulama modülü. | SDK Maintainer |
| **CI/CD Pipeline** | Otomatik test, build ve deployment süreçleri. | DevOps Engineer |

---

## ⚙️ 3. Sunucu Yapılandırması

| Bileşen | Önerilen Teknoloji | Not |
|----------|--------------------|-----|
| API | Python / Flask | Hafif ve genişletilebilir yapı |
| DB | PostgreSQL | Transactional log desteği |
| Cache | Redis | Puan ve oturum doğrulama için |
| Loglama | ELK Stack (Elastic, Logstash, Kibana) | Denetim ve analiz amaçlı |
| CI/CD | GitHub Actions | Otomatik test + build + deploy |

---

## 🔑 4. API Anahtar Yönetimi

- Her geliştirici ve test oturumu için **benzersiz API anahtarı** oluşturulur.  
- Anahtarlar yalnızca HTTPS üzerinden iletilir.  
- Anahtar geçerliliği **30 gün** ile sınırlıdır.  
- Yenileme işlemleri “/api/auth/renew” endpoint’i üzerinden yapılır.  

🧠 **İpucu:**  
Gereksiz anahtar saklamayı önlemek için `cron` tabanlı otomatik silme mekanizması önerilir.

---

## 🧮 5. Veri Yedekleme & Kurtarma

| Kapsam | Sıklık | Saklama Süresi | Yöntem |
|--------|--------|----------------|--------|
| Veritabanı | Günlük | 30 gün | `pg_dump` ile incremental backup |
| Log Dosyaları | Haftalık | 90 gün | Sıkıştırılmış JSON arşiv |
| Yapılandırma | Her değişiklik sonrası | Süresiz | Git versiyon kontrolü |

**Felaket Kurtarma (DR Planı):**
1. DB snapshot’larını farklı bir bölgede depola (ör. AWS S3).  
2. Sunucu kaybı durumunda en son snapshot’tan geri yükle.  
3. Test ortamında doğrulama yapılmadan canlıya alınmaz.  

---

## 📊 6. İzleme ve Loglama

- **API Logları:** Her istek `request_id` ile etiketlenir.  
- **Tester Aktivite Logları:** Her oturumda SDK doğrulama kayıtları tutulur.  
- **Uyarı Mekanizması:**  
  - Puan düşüm başarısız → e-posta bildirimi  
  - Test oturumu hatası → Slack/Webhook bildirimi  

📈 **KPI İzleme:**
- Aktif test sayısı  
- Başarısız doğrulama oranı  
- Ortalama puan dönüş süresi  

---

## 🧩 7. Sürüm Yönetimi

| Sürüm | Durum | Özellikler | Yayın Tarihi |
|--------|--------|-------------|--------------|
| v1.0.0 | Yayında | Puan sistemi, tester doğrulama, raporlama | 01.10.2025 |
| v1.1.0 | Planlandı | Test senaryosu paylaşımı | — |
| v2.0.0 | Planlandı | Profesyonel tester sistemi, ödeme entegrasyonu | — |

**Sürüm Stratejisi:**  
- Major: Yeni özellik veya yapısal değişiklik  
- Minor: İyileştirme veya hata düzeltmesi  
- Patch: Güvenlik ve bakım güncellemesi  

---

## 🧰 8. Bakım Planı

| Görev | Sıklık | Sorumlu | Açıklama |
|--------|--------|----------|----------|
| DB Temizliği | Haftalık | DB Admin | Eski log kayıtlarını silme |
| API Güncelleme | Aylık | Backend Admin | Güvenlik yamaları |
| Test Doğrulama | Her sürüm sonrası | QA Ekibi | SDK – API uyumluluk testi |
| Sunucu Sağlık Kontrolü | Günlük | DevOps | CPU, RAM, uptime izlemesi |

---

## 🧩 9. Erişim Yetkilendirme Politikası

| Rol | Yetki | Kısıtlama |
|------|-------|-----------|
| System Admin | Tüm modüller | MFA zorunlu |
| API Admin | API anahtarı oluşturma | Sadece backend erişimi |
| DB Admin | Veritabanı erişimi | Salt okunur sorgular dışında işlem kısıtı |
| Community Manager | Rapor görüntüleme | Veri değiştirme yetkisi yok |

---

## 🔐 10. Güvenlik Önlemleri

- HTTPS + HSTS zorunlu  
- Tüm erişimlerde JWT tabanlı oturum doğrulama  
- API rate limiting (60 istek/dk)  
- Güvenlik denetimi için OWASP ASVS kontrol listesi kullanılmalıdır  

---

## 🧠 11. Sorun Giderme (Troubleshooting)

| Durum | Olası Neden | Çözüm |
|--------|--------------|--------|
| API yanıt vermiyor | Redis veya DB bağlantısı kopuk | Servisleri yeniden başlat |
| Puan güncellenmiyor | Queue tıkanmış olabilir | “points_worker” servisini kontrol et |
| SDK doğrulama başarısız | Geçersiz sessionId | Yeni session anahtarı oluştur |
| Raporlama boş dönüyor | Zaman aralığı hatalı | Tarih filtresini kontrol et |

---

## 💬 12. İletişim ve Destek
- **Sistem Yöneticisi:** admin@bilkav.org  
- **Geliştirici Desteği:** devsupport@bilkav.org  
- **Güvenlik Bildirimi:** security@bilkav.org  

---

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Bakım, yazılımın ömrünü uzatır; düzen, güveni sağlar.” ⚙️  
