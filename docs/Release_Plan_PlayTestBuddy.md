# 🚀 PlayTest Buddy – Release Plan (Sürüm Planı ve Yol Haritası)

## 📘 1. Amaç
Bu doküman, **PlayTest Buddy** projesinin sürüm planlamasını, yol haritasını ve sürümler arası geçiş stratejilerini tanımlar.  
Amaç, geliştirme sürecini düzenli, izlenebilir ve topluluk katkılarına açık biçimde yönetmektir.

## 🧭 2. Sürüm Stratejisi

| Sürüm Türü | Açıklama | Örnek |
|-------------|-----------|--------|
| **Major** | Yeni modül veya yapısal değişiklik. | v2.0 |
| **Minor** | Yeni özellik veya geliştirme. | v1.1 |
| **Patch** | Hata düzeltmesi veya güvenlik yaması. | v1.0.1 |
| **Beta / RC** | Test veya ön izleme sürümü. | v1.1-beta |

**Kural:**  
- Ana (major) sürümler yalnızca kabul testlerini (ATP) geçen özelliklerle yayımlanır.  
- Beta sürümleri topluluk tarafından test edilir.  
- Her sürüm öncesi “Release Candidate (RC)” adayı oluşturulur.

## 🧱 3. Sürüm Yönetimi Süreci

1. **Geliştirme Aşaması**  
   - Yeni özellik veya iyileştirme “feature/” branch’inde geliştirilir.  
2. **Kod İncelemesi (PR Review)**  
   - Her pull request, en az 1 topluluk üyesi tarafından onaylanmalıdır.  
3. **Test Aşaması**  
   - `tests/unit` ve `tests/integration` dizinlerinde tüm testler çalıştırılır.  
4. **Release Branch Oluşturma**  
   - Stabil sürümler `release/vX.Y.Z` olarak adlandırılır.  
5. **Yayınlama (Tagging)**  
   - GitHub tag formatı: `vX.Y.Z`  
6. **Dağıtım (Deployment)**  
   - CI/CD üzerinden `main` branch’e otomatik aktarım yapılır.

## 🧩 4. Sürüm Zaman Çizelgesi (Roadmap)

| Sürüm | Durum | Hedef Tarih | Ana Özellikler |
|--------|--------|--------------|----------------|
| **v1.0.0 (Core)** | ✅ Yayında | 01.10.2025 | Puan sistemi, Tester doğrulama, Raporlama |
| **v1.1.0 (Collab)** | 🛠️ Geliştirilecek | Q1 2026 | Test senaryosu paylaşımı, yorum sistemi |
| **v1.2.0 (Insights)** | ⏳ Planlı | Q2 2026 | İstatistik panosu, gelişmiş raporlama |
| **v2.0.0 (Pro)** | 🚧 Planlı | Q3 2026 | Profesyonel tester sistemi, ödeme modülü |
| **v2.1.0 (Global)** | 🧩 Planlı | Q4 2026 | Çok dil desteği, global topluluk entegrasyonu |

## 🔄 5. Sürüm Yaşam Döngüsü

```
Develop → Feature Branch → Pull Request → Test → Release Candidate → Stable → Maintenance
```

Her major sürüm için bakım süresi **6 ay**, güvenlik güncellemesi süresi **12 ay** olarak belirlenmiştir.

## 🧰 6. Sürüm Sonrası İşlemler

| Adım | Açıklama |
|------|-----------|
| 🔍 Test Raporu Yayımı | Test sonuçları `docs/tests/Release_Results.md` altında yayımlanır. |
| 📦 Paketleme | SDK sürümü `src/sdk/` altında güncellenir. |
| 🧾 Dokümantasyon Güncellemesi | Tüm rehberler (`User`, `Developer`, `Admin`) yeni sürüme göre güncellenir. |
| 🪪 Versiyon Etiketi | GitHub’da `vX.Y.Z` etiketi oluşturulur. |

## 🌐 7. Yayınlama Kanalları

| Kanal | Açıklama |
|--------|-----------|
| **GitHub Releases** | Kaynak kodun resmi dağıtım noktası. |
| **Google Play (Closed Test)** | Test grubu için uygulama dağıtımı. |
| **BilKavTopluluk Sitesi** | Duyurular, changelog ve topluluk katkı listeleri. |

## 💬 8. Geri Bildirim Döngüsü

- Her sürüm sonrası topluluk üyelerine **geri bildirim formu** gönderilir.  
- Yeni fikir ve iyileştirmeler, GitHub’daki **“Discussions”** veya **“Feature Requests”** bölümlerinde toplanır.  
- Onaylanan öneriler “Next Release” backlog’una eklenir.

## 🔐 9. Sürüm Güvenliği

| Önlem | Açıklama |
|--------|-----------|
| **Kod imzalama** | Mobil APK ve SDK sürümleri imzalanır. |
| **CI/CD doğrulaması** | Her build SHA256 checksum ile doğrulanır. |
| **Bağımlılık kontrolü** | `requirements.txt` ve `gradle.lockfile` güvenlik taraması yapılır. |
| **Rollback planı** | Hatalı sürümde 1 önceki sürüme otomatik dönüş mekanizması. |

## 🧭 10. Sürüm Denetimi (Governance)

| Sorumlu | Rol | Görev |
|----------|------|-------|
| **İsmail ARICIOĞLU** | Product Owner | Sürüm içeriği onayı |
| **Çet (AI Assistant)** | QA Mentor | Doğrulama ve izleme |
| **Topluluk Core Ekibi** | Contributor Council | Öneri, inceleme, test desteği |
| **DevOps Ekibi** | Release Ops | Dağıtım ve sürüm kontrolü |

---

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Her sürüm, bir adım ileri; her adım, topluluk için bir kazançtır.” 🚀
