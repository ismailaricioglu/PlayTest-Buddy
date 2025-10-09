# 🧩 PlayTest Buddy
**Mobil Uygulama Geliştiricileri İçin Otomatik Test Organizasyon Sistemi**

> Bağımsız geliştiricilerin Google Play politikalarına uygun test süreçlerini kolayca yürütmesini sağlar.
> Test paylaşımı, katılımcı takibi ve puanlama sistemi tek bir çatı altında toplanmıştır.

---

## 🚀 Amaç

Google Play Store üzerinde bir uygulamayı yayımlayabilmek için,
uygulamanın **en az 12 farklı cihazda** ve **en az 14 gün boyunca** test edilmesi gerekir.

PlayTest Buddy, bu test sürecini **topluluk içinde organize eden** bir sistemdir:
- Geliştirici uygulamasını paylaşır
- Diğer üyeler test eder
- Sistem katılımı ve süreci otomatik olarak doğrular
- Geliştirici puan kazanarak kendi uygulamasını test ettirme hakkı elde eder

---

## 🧱 Özellikler

| Modül | Açıklama |
|--------|-----------|
| 🧪 **Test Süreci Yönetimi** | Geliştiricilerin testlerini paylaşma ve katılımcıların uygulamayı indirme sürecini yönetir. |
| 👥 **Katılımcı Takibi** | Katılımcı sayısı, süre ve test tamamlama oranlarını log’lar. |
| 🎯 **Puanlama & Aktivasyon** | Tester’lar testlere katıldıkça puan kazanır, puanları ile kendi testlerini başlatabilir. |
| 🔐 **Doğrulama SDK’sı** | Uygulamaya entegre edilen küçük bir SDK, tester kimliğini sistem log’larıyla doğrular. |
| 📊 **Raporlama (Opsiyonel)** | Test katılımları, süreler ve puan istatistikleri toplanabilir. |

---

## 🧩 Mimari Genel Görünüm

```
+--------------------+         +------------------------+
|  Mobil Uygulama   | <--->   |   PlayTestBuddy SDK     |
+--------------------+         +------------------------+
          |                               |
          |                               |
          v                               v
+--------------------+         +------------------------+
|    Flask API       | <---->  |   Veritabanı (PostgreSQL) |
+--------------------+         +------------------------+
          |
          v
   CI/CD Pipeline (GitHub Actions)
```

---

## ⚙️ Kurulum & Hızlı Başlangıç

### 1️⃣ Depoyu klonlayın
```bash
git clone https://github.com/BilKavTopluluk/PlayTestBuddy.git
cd PlayTestBuddy
```

### 2️⃣ Ortamı hazırlayın
**Backend:**
```bash
pip install -r requirements.txt
flask run
```

**Mobil (Flutter):**
```bash
flutter pub get
flutter run
```

### 3️⃣ Testleri çalıştırın
```bash
pytest tests/
flutter test
```

---

## 📘 Proje Dokümantasyonu

| Doküman | Açıklama |
|----------|-----------|
| 📄 [İş Gereksinimi](./docs/01_IsGereksinimi.md) | İş ihtiyacının tanımı |
| ⚙️ [Sistem Gereksinimi](./docs/02_SistemGereksinimi.md) | Sistem kapsamı ve teknik isterler |
| 🧠 [Fonksiyonel Tasarım](./docs/03_FonksiyonelTasarim.md) | Uygulama davranışları |
| 🧩 [Alt Sistem / Parça Tasarımı](./docs/04_AltSistemParcaTasarimi.md) | Modül mimarisi |
| 🧾 [Detay Tasarım (DDD)](./docs/05_DetayTasarim.md) | API & SDK teknik detayları |
| 🧪 [Test Tasarımı & RTM](./docs/06_TestTasarimRTM.md) | Gereksinim-test ilişkileri |
| ✅ [Kabul Test Planı & Raporu](./docs/07_KabulTestRaporu.md) | Kabul testleri sonuçları |

---

## 🌍 Açık Kaynak Politikası

Bu proje **MIT Lisansı** altında paylaşılmaktadır.
Katkıda bulunmak isteyenler için rehberler:

- [LICENSE](./LICENSE)
- [CONTRIBUTING.md](./CONTRIBUTING.md)
- [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)
- [SECURITY.md](./SECURITY.md)

---

## 🛣️ Yol Haritası

| Sürüm | İçerik | Durum |
|--------|--------|--------|
| ✅ v1.0.0 | MVP – İşlevsel Temel Sürüm | Tamamlandı |
| 🚧 v1.1.0 | CI/CD + Açık Kaynak Yönetimi | Devam Ediyor |
| ⏳ v1.2.0 | Topluluk Test Davetleri | Planlandı |
| 💡 v2.0.0 | Global API + Plugin Desteği | Gelecek |

---

## 👨‍💻 Proje Ekibi

| Rol | İsim | Organizasyon |
|------|------|--------------|
| Proje Sahibi | İsmail ARICIOĞLU | BilKav Topluluğu |
| Yapay Asistan | ChatGPT (Çet) | OpenAI |
| Geliştirici Topluluğu | BilKav Üyeleri | Açık Katkı Modeli |

---

## 💬 Topluluk & İletişim

- 💡 [GitHub Discussions](https://github.com/BilKavTopluluk/PlayTestBuddy/discussions)
- 🐞 [Issue Tracker](https://github.com/BilKavTopluluk/PlayTestBuddy/issues)
- 📧 İletişim: info@bilkav.org

---

Hazırlayan: **İsmail ARICIOĞLU**
Danışman: **Çet – Yapay Asistan**

> “Gerçek dayanışma, geliştiricinin geliştiriciye desteğidir.” 💪
