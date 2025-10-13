# PlayTest Buddy – Security Model

## 1. Amaç
Bu doküman, PlayTest Buddy sisteminde yer alan tüm güvenlik mekanizmalarının tanımını, kapsamını ve uygulanma biçimlerini açıklar.

## 2. Güvenlik Katmanları
(JWT, SDK verification, API key rotation, IP allowlist gibi detaylı yapı)

## 3. Servis Bazlı Güvenlik
PointsService, TestSessionService, Receiver API güvenlik politikaları.

## 4. Operasyonel Güvenlik
Veri güvenliği, loglama, yedekleme, rate limit, şifreleme.

## 5. Politika ve Güncelleme
- Her sürüm öncesi güvenlik taraması yapılır.
- Token’lar test ortamında “ephemeral” (geçici) olarak tutulur.
- Güvenlik ihlali durumunda rollback + key reset uygulanır.
