# PlayTest Buddy

**Mobil Uygulama Test Süreçlerini Kolaylaştıran Topluluk Platformu**

---

## 🧩 Proje Tanımı

**PlayTest Buddy**, bağımsız geliştiricilerin ve topluluk üyelerinin bir araya gelerek mobil uygulama test süreçlerini kolaylaştırmalarını sağlayan açık kaynaklı bir platformdur.

Bu uygulama, Google Play Console politikaları gereği zorunlu olan test katılımcısı (tester) süreçlerini daha erişilebilir, organize ve topluluk tabanlı bir hale getirir.

---

## 🎯 Proje Amacı

* Mobil uygulamaların *kapalı test* süreçlerini otomatikleştirmek.
* Geliştiriciler arasında karşılıklı test desteği sağlamak.
* Katılımcı sayısını, test süresini ve puan tabanlı sistemleri dijital olarak yönetmek.

---

## 🧠 Genel Özellikler

* 12 katılımcı tabanlı test yönetimi (Google Play Console politikalarına uygun).
* Katılımcı doğrulama SDK’sı (Flask tabanlı Receiver API + Kotlin SDK).
* Puan sistemi: Katılımcı test yaptıkça puan kazanır, kendi uygulamasını test ettirmek için puan harcar.
* Topluluk odaklı büyüme modeli.

---

## 🧱 Sistem Yapısı

Proje, modüler bir mimari üzerine kuruludur:

* **Backend (Flask API)** → Test süreci, puan yönetimi, kullanıcı doğrulama.
* **Client SDK (Kotlin)** → Geliştirici uygulamasına gömülü doğrulama paketi.
* **Database (PostgreSQL)** → Katılımcı, test ve puan kayıtları.
* **CI/CD Pipeline** → GitHub Actions ile otomatik test, build ve dokümantasyon yayını.

---

## 📘 Dokümantasyon İçeriği

Bu rehber, V-Model süreçlerine göre hazırlanmış proje dokümantasyonunu içerir:

| Aşama                       | Doküman                                                        |
| --------------------------- | -------------------------------------------------------------- |
| İş Gereksinimi              | [Business Requirements](docs/System_Requirements.md)           |
| Sistem Gereksinimi          | [System Requirements (SRD)](docs/System_Requirements.md)       |
| Fonksiyonel Tasarım         | [Functional Design (FDD)](docs/Functional_Design.md)           |
| Alt Sistem / Parça Tasarımı | [Subsystem Design](docs/SubSystem_Design.md)                   |
| Detay Tasarım               | [Detailed Design (DDD)](docs/Detailed_Design.md)               |
| Test Tasarımı ve RTM        | [Test Design & RTM](docs/Test_Design_RTM.md)                   |
| Kabul Test Planı            | [Acceptance Test Plan (ATP)](docs/Acceptance_Test_Plan.md)     |
| Kabul Test Raporu           | [Acceptance Test Report (ATR)](docs/Acceptance_Test_Report.md) |

---

## 👥 Rehberler

* [Geliştirici Rehberi](docs/guides/Developer_Guide_PlayTestBuddy.md)
* [Kullanıcı Rehberi](docs/guides/User_Guide_PlayTestBuddy.md)
* [Yönetici Rehberi](docs/guides/Admin_Guide_PlayTestBuddy.md)
* [Katkı Rehberi](CONTRIBUTING.md)

---

## 🌐 Topluluk ve Açık Kaynak

PlayTest Buddy, **Bilgisayar Kavramları Topluluğu (BilKavTopluluk)** iş birliğiyle açık kaynak olarak geliştirilmektedir.

Katkıda bulunmak isteyen geliştiriciler için GitHub üzerinde issue ve pull request süreçleri aktiftir.

📍 GitHub: [https://github.com/<your-username>/PlayTestBuddy](https://github.com/<your-username>/PlayTestBuddy)

---

## 📄 Lisans

Bu proje [MIT Lisansı](LICENSE) altında yayımlanmıştır.
