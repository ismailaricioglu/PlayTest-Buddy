# PlayTest Buddy – Katkı Rehberi (Contributing Guide)

Bu belge, **Bilgisayar Kavramları Topluluğu (BilKav)** üyeleri ve topluluğa dışarıdan katkı yapmak isteyen geliştiriciler için hazırlanmıştır.
Amaç; projeye yapılan katkıların tutarlı, kaliteli ve sürdürülebilir bir şekilde ilerlemesini sağlamaktır.

---

## 💡 Katkı Türleri

Projeye şu şekillerde katkı yapabilirsiniz:

* 🧱 **Kod geliştirme**: Yeni özellik ekleme, hata düzeltme, performans iyileştirmesi.
* 🤪 **Test katkısı**: Test senaryoları oluşturma veya mevcut testleri genişletme.
* 📘 **Dokümentasyon**: Rehberleri güncelleme, örnekler ekleme.
* 💬 **Geri bildirim**: Öneri, hata bildirimi veya geliştirme fikri sunma.

---

## 🔧 Geliştirme Ortamı Kurulumu

### 1. Depoyu Forkla ve Klonla

```bash
git fork https://github.com/bilkav/PlayTestBuddy.git
git clone https://github.com/<kullanıcı-adın>/PlayTestBuddy.git
cd PlayTestBuddy
```

### 2. Geliştirme Dalı (Branch) Aç

```bash
git checkout -b feature/yeni-ozellik
```

### 3. Gereksinimleri Kur

```bash
# Python (Receiver API)
pip install -r requirements.txt

# Android SDK (Kotlin Modülü)
# Android Studio ile aç ve Gradle senkronizasyonunu tamamla
```

### 4. Testleri Çalıştır

```bash
pytest tests/
```

---

## 🧩 Kodlama Kuralları

* Python tarafında **PEP8** standartlarına uyun.
* Commit mesajlarını kısa ve açıklayıcı tutun:

  * ✅ `feat:` yeni özellik
  * 🐛 `fix:` hata düzeltmesi
  * 🧹 `refactor:` kod düzenleme
  * 🤪 `test:` test ekleme
* Yeni modül ekliyorsanız, ilgili `.md` dokümanını da güncelleyin (örneğin `Functional_Design.md`).

---

## 🔄 Katkı Gönderme (Pull Request)

1. Kodunuzu tamamlayın, testlerin geçtiğinden emin olun.

2. Değişikliklerinizi commit edin ve GitHub’a gönderin:

   ```bash
   git push origin feature/yeni-ozellik
   ```

3. GitHub üzerinden **Pull Request (PR)** açın.
   PR açıklamasında:

   * Yaptığınız değişiklikleri özetleyin
   * İlgili issue varsa belirtin (`Fixes #12` gibi)
   * Test kapsamını kısaca açıklayın

4. İnceleme (review) sürecinde gelen geri bildirimleri uygulayın.

---

## ✅ Katkı Onay Süreci

* En az bir proje yöneticisi (BilKav Core Team üyesi) tarafından onaylanmalıdır.
* Kod, test ve dokümentasyon incelemesinden geçer.
* CI/CD pipeline’da tüm testlerin başarılı olması gerekir.

---

## ⚙️ İletişim & Destek

* GitHub **Discussions** sekmesinden toplulukla iletişime geçebilirsin.
* E-posta: **[bilkav.community@gmail.com](mailto:bilkav.community@gmail.com)**

---

**Teşekkürler 💙**
PlayTest Buddy’ye katkı sağladığın için BilKav Topluluğu seni takdir ediyor!
