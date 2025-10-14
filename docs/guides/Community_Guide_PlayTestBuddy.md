# 🌍 PlayTest Buddy – Topluluk Katkı Kılavuzu (Community Guide)

Bu doküman, **BilKav Topluluğu** üyeleri ve açık kaynak katkıcıları için **PlayTest Buddy** projesinde katkı yapma süreçlerini özetler.
Amaç, herkesin katkılarını verimli, düzenli ve keyifli bir şekilde sunabilmesini sağlamaktır. 🙌

---

## 🧩 1. Katkı Felsefesi

PlayTest Buddy, **dayanışma odaklı bir test platformu** projesidir. Her geliştirici hem ürününü test ettirir, hem de başkalarının test süreçlerine katkı sağlar.
Bu ruh, açık kaynak yaklaşımına da yansır: **"Birlikte geliştir, birlikte test et!"** 💪

Katkılar sadece kod değil; dokümantasyon, tasarım, test ve fikir paylaşımı da bu sürecin önemli parçalarıdır.

---

## 🧱 2. Katkı Ön Koşulları

Katkı yapmadan önce aşağıdaki dosyaları incelemeni öneriyoruz:

| Dosya                                                                    | Açıklama                    |
| ------------------------------------------------------------------------ | --------------------------- |
| [`CODE_OF_CONDUCT.md`](../../CODE_OF_CONDUCT.md)                         | Topluluk davranış kuralları |
| [`CONTRIBUTING.md`](../../CONTRIBUTING.md)                               | Katkı süreci adımları       |
| [`README_PlayTestBuddy.md`](../README_PlayTestBuddy.md)                  | Proje genel bilgisi         |
| [`Developer_Guide_PlayTestBuddy.md`](./Developer_Guide_PlayTestBuddy.md) | Geliştirici kurulum rehberi |

---

## 🛠️ 3. Katkı Türleri

Katkılar birçok farklı biçimde olabilir:

| Katkı Türü       | Açıklama                                                 |
| ---------------- | -------------------------------------------------------- |
| 💻 Kodlama       | Yeni modül, API veya SDK geliştirmesi                    |
| 🧪 Test          | Yeni test senaryoları, otomasyon veya RTM güncellemeleri |
| 📘 Dokümantasyon | Kullanıcı veya geliştirici rehberleri oluşturma          |
| 💬 Öneri         | Issue açarak yeni fikir paylaşımı                        |
| 🎨 Tasarım       | Mockup, UI/UX veya logo tasarımı                         |

---

## ⚙️ 4. Katkı Süreci

### 1️⃣ Fork & Clone

```bash
git fork https://github.com/BilKavTopluluk/PlayTestBuddy.git
git clone https://github.com/<kullanıcı-adın>/PlayTestBuddy.git
```

### 2️⃣ Branch Aç

```bash
git checkout -b feature/yeni-ozellik
```

### 3️⃣ Geliştir & Test Et

```bash
pytest tests/
```

### 4️⃣ PR Gönder

GitHub’da Pull Request (PR) aç ve şablonu doldur.
Tüm testlerin başarılı geçtiğinden emin ol.

---

## 🧭 5. Issue & PR Şablonları

GitHub üzerinde yeni bir **Issue** veya **Pull Request** açarken aşağıdaki şablonlar otomatik olarak yüklenir:

| Şablon                        | Açıklama            | Konum                     |
| ----------------------------- | ------------------- | ------------------------- |
| 🐛 `bug_report.yml`           | Hata bildirim formu | `.github/ISSUE_TEMPLATE/` |
| 💡 `feature_request.yml`      | Özellik öneri formu | `.github/ISSUE_TEMPLATE/` |
| 🔀 `PULL_REQUEST_TEMPLATE.md` | PR açıklama şablonu | `.github/`                |

Bu sistem, GitHub’ın **Issue Forms** standardına tam uyumludur (2025 sürümü).

---

## 🔒 6. Güvenlik Bildirimi

Güvenlik açıkları veya veri ihlalleriyle ilgili bildirimleri **genel Issue yerine özel olarak** şu e-posta adresine gönder:
📧 **[bilkav.security@proton.me](mailto:bilkav.security@proton.me)**

---

## 🌐 7. İletişim ve Topluluk

* 💬 [Discussions](https://github.com/BilKavTopluluk/PlayTestBuddy/discussions)
* 🧠 [Wiki](https://github.com/BilKavTopluluk/PlayTestBuddy/wiki)
* 📢 [BilKav Discord Kanalı](https://discord.gg/bilkav)

Topluluk yöneticileri genellikle 24 saat içinde geri dönüş yapar.

---

## 🧠 8. Kapanış Notu

Katkı, sadece kod yazmak değil; bilgiyi paylaşmak, dokümantasyonu güçlendirmek ve ekip ruhunu büyütmektir. 💙
Her katkı, PlayTest Buddy’nin daha iyi bir platform olmasını sağlar.

> "Bir satır kod, bir satır belge, bir satır iyileştirme – hepsi aynı değerde."
> — **BilKav Topluluğu, 2025**
