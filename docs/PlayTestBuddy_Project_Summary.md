# 🌐 PlayTest Buddy – Project Summary (Proje Özeti ve Portföy Entegrasyonu)

## 📘 1. Proje Tanımı
**PlayTest Buddy**, mobil uygulama geliştiricilerinin Google Play politikalarına uygun şekilde test süreçlerini kolaylaştıran bir platformdur.  
Yazılımcılar, diğer geliştiricilerle dayanışma içinde test oturumları başlatabilir, katılım puanları toplayabilir ve kendi uygulamalarını test ettirebilir.

---

## 🧩 2. Proje Amacı
- Geliştiricilerin test sürecinde yaşadığı **katılımcı bulma ve doğrulama** sorunlarını çözmek.  
- Google Play’in zorunlu test politikalarını (en az 12 tester – 14 gün süre) kolay yönetilebilir hale getirmek.  
- Topluluk tabanlı, şeffaf ve puan temelli bir test ekosistemi oluşturmak.

---

## 🧠 3. Temel Özellikler
| Modül | Açıklama |
|--------|-----------|
| **Tester Katılım Takibi** | Minimum 12 tester katılımı doğrulanır. |
| **Puanlama Sistemi (GR-005)** | Her kullanıcı test katılımı ile puan kazanır, 120 puan ile test başlatabilir. |
| **Uygulama Paylaşımı** | Geliştirici test linkini paylaşır, tester’lar katılır. |
| **Raporlama** | Katılım durumu ve puan hareketleri izlenir. |
| **Güvenlik** | JWT, TLS 1.3, hash imzalama, RBAC kontrolleri uygulanır. |
| **SDK Doğrulama Paketi** | Test edilen uygulamaya entegre edilir, sistem loglarıyla doğrulama sağlar. |

---

## ⚙️ 4. Teknik Mimarî
**Teknolojiler:**
- Backend: Python (Flask)
- Database: PostgreSQL  
- SDK: Kotlin (Android)
- Mobile Client: Flutter  
- CI/CD: GitHub Actions  
- Loglama: Elastic Stack  

**Genel Yapı:**
```
Client (Flutter) 
   ↕ 
API (Flask, REST)
   ↕ 
PostgreSQL (DB)
   ↕ 
CI/CD (GitHub Actions)
```

---

## 🔐 5. Güvenlik Modeli
- **STRIDE Analizi** (Spoofing, Tampering, Repudiation, Information Disclosure, DoS, Elevation of Privilege) uygulanmıştır.  
- **JWT tabanlı kimlik doğrulama** ve **RBAC erişim kontrolü** sağlanır.  
- Tüm veriler **AES-256** ile şifrelenir.  
- **TLS 1.3** ve **CI/CD imzalama (SHA256)** aktif kullanımdadır.  

---

## 🧪 6. Test ve Doğrulama
| Test Aşaması | Belge | Durum |
|---------------|--------|--------|
| İş Gereksinimi → Kabul Testi | ✅ `Acceptance_Test_Plan.md` | Tamamlandı |
| Sistem Gereksinimi → Sistem Testi | ✅ `Test_Design_and_RTM.md` | Tamamlandı |
| Fonksiyonel Tasarım → Entegrasyon Testi | ✅ `Functional_Design.md` | Tamamlandı |
| Güvenlik Testleri | ✅ `Security_Model_PlayTestBuddy.md` | Planlandı |
| Kabul Raporu (ATR) | ✅ `Acceptance_Test_Report.md` | Tamamlandı |

---

## 🧱 7. Sürüm ve Yol Haritası
| Sürüm | Durum | Özellikler | Hedef |
|--------|--------|-------------|--------|
| v1.0.0 (Core) | ✅ Yayında | Puan sistemi, tester doğrulama, raporlama | 01.10.2025 |
| v1.1.0 (Collab) | 🛠️ Geliştirilecek | Test senaryosu paylaşımı | Q1 2026 |
| v2.0.0 (Pro) | 🚧 Planlı | Profesyonel tester, ödeme entegrasyonu | Q3 2026 |

---

## 🧰 8. Dokümantasyon Listesi
| Kategori | Dosya Adı | Konum |
|-----------|------------|--------|
| İş Gereksinimi | `Business_Requirements.md` | `docs/` |
| Sistem Gereksinimi | `System_Requirements.md` | `docs/` |
| Fonksiyonel Tasarım | `Functional_Design.md` | `docs/` |
| Alt Sistem / Parça Tasarımı | `Subsystem_Design.md` | `docs/` |
| Detay Tasarım | `Detailed_Design.md` | `docs/` |
| Test Tasarımı & RTM | `Test_Design_and_RTM.md` | `docs/` |
| Kabul Test Planı | `Acceptance_Test_Plan.md` | `docs/` |
| Kabul Test Raporu | `Acceptance_Test_Report.md` | `docs/` |
| Güvenlik Modeli | `Security_Model_PlayTestBuddy.md` | `docs/` |
| Deployment Guide | `Deployment_Guide_PlayTestBuddy.md` | `docs/guides/` |
| Developer Guide | `Developer_Guide_PlayTestBuddy.md` | `docs/guides/` |
| User Guide | `User_Guide_PlayTestBuddy.md` | `docs/guides/` |
| Admin Guide | `Admin_Guide_PlayTestBuddy.md` | `docs/guides/` |
| Release Plan | `Release_Plan_PlayTestBuddy.md` | `docs/` |

---

## 🌐 9. Topluluk & Katkı
**BilKav Topluluğu** çatısı altında geliştirilmektedir.  
Katkı sağlamak isteyen geliştiriciler GitHub üzerinde şu adımlar izleyebilir:  
1. `fork` → `branch` oluştur  
2. Değişiklik yap, testleri çalıştır  
3. `pull request` oluştur  
4. Kod incelemesi sonrası merge edilir  

📫 İletişim:  
- info@bilkav.org  
- https://github.com/BilKavTopluluk/PlayTestBuddy  

---

## 🧠 10. Sonuç
PlayTest Buddy; test süreçlerinde dayanışmayı, güvenliği ve verimliliği merkezine alan bir topluluk projesidir.  
Tüm geliştirme ve test aşamaları belgelendirilmiş, açık kaynak ilkeleriyle uyumlu şekilde yürütülmüştür.

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Dokümantasyon sadece geçmişi değil, geleceği de tasarlar.” 📘
