# 🧑‍💻 PlayTest Buddy – Developer Guide (Geliştirici Rehberi)

## 📘 Amaç
Bu doküman, PlayTest Buddy projesine katkıda bulunacak geliştiriciler için çalışma ortamı, bağımlılıklar, API yapılandırması ve test süreçlerini tanımlar.

---

## 🧩 Genel Mimari Bileşenler

| Katman | Teknoloji | Açıklama |
|--------|------------|----------|
| Mobil Arayüz | Flutter | Test paylaşımı, katılım ve raporlama ekranları |
| SDK Modülü | Kotlin | Tester kimliği doğrulama bileşeni |
| Backend Servisi | Python (Flask) | API ve puan yönetimi servisi |
| Veritabanı | PostgreSQL | Test, kullanıcı ve puan verileri |
| CI/CD | GitHub Actions | Otomatik test ve dağıtım hattı |

---

## ⚙️ Ortam Kurulumu

### 1️⃣ Gereksinimler

| Bileşen | Minimum Sürüm |
|----------|----------------|
| Python | 3.10+ |
| Flutter SDK | 3.19+ |
| PostgreSQL | 15+ |
| Node.js (opsiyonel) | 20+ |
| Git | 2.40+ |

---

### 2️⃣ Proje Kopyalama

```bash
git clone https://github.com/BilKavTopluluk/PlayTestBuddy.git
cd PlayTestBuddy
```

---

### 3️⃣ Backend Kurulumu (Flask)

```bash
cd src/backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
flask run
```

📂 **Yapı:**
```
src/backend/
├── app.py
├── routes/
│   ├── points.py
│   ├── tests.py
│   └── users.py
├── models/
│   └── db_model.py
└── config.py
```

🧩 **API örnek çağrısı:**
```bash
POST /api/points/deduct
{
  "user_id": "dev_12345",
  "points": 120
}
```

✅ **Beklenen cevap:**
```json
{
  "success": true,
  "balance": 0
}
```

---

### 4️⃣ Mobil Uygulama Kurulumu (Flutter)

```bash
cd src/mobile_app
flutter pub get
flutter run
```

📂 **Yapı:**
```
src/mobile_app/
├── lib/
│   ├── main.dart
│   ├── screens/
│   │   ├── home_screen.dart
│   │   ├── share_test_screen.dart
│   │   └── points_screen.dart
│   └── services/
│       └── api_service.dart
└── pubspec.yaml
```

🧩 **API örnek entegrasyonu:**
```dart
final response = await http.post(
  Uri.parse('https://api.playtestbuddy.org/api/points/deduct'),
  headers: {'Content-Type': 'application/json'},
  body: jsonEncode({'user_id': 'dev_12345', 'points': 120}),
);
```

---

## 🧪 Test & Doğrulama

### Backend Testleri
```bash
pytest tests/
```
📂 `tests/` dizininde tüm API endpoint testleri yer alır.

### Flutter Testleri
```bash
flutter test
```
📂 `test/` klasöründe widget ve entegrasyon testleri bulunur.

---

## 🧰 Geliştirme Süreci (Branch & Merge Modeli)

| Aşama | Branch | Açıklama |
|--------|---------|----------|
| Yeni özellik | `feature/...` | Yeni işlevler eklenir |
| Hata düzeltme | `fix/...` | Mevcut hatalar giderilir |
| Dokümantasyon | `doc/...` | Döküman güncellemeleri |
| Yayın | `release/...` | Sürüm hazırlığı |
| Ana dal | `main` | Kararlı sürüm kodu |

Pull Request’ler **otomatik testten geçmeden** `main` dalına alınmaz.  
Tüm PR’ler GitHub Actions pipeline tarafından test edilir ✅

---

## 🧠 Geliştirici İpuçları

- Her fonksiyonun üstünde **docstring** bulunmalı  
- API endpoint’leri için **Swagger/OpenAPI** kullanımı önerilir  
- SDK entegrasyonu ayrı bir repo olarak geliştirilebilir (örnek: `playtestbuddy-sdk-kotlin`)  
- CI testleri localde şu komutla çalıştırılabilir:
  ```bash
  pytest && flutter test
  ```

---

## 📬 İletişim & Destek

- **Topluluk:** [GitHub Discussions](https://github.com/BilKavTopluluk/PlayTestBuddy/discussions)  
- **E-posta:** dev@bilkav.org  
- **Güvenlik Bildirimi:** security@bilkav.org  

---

Hazırlayan: **İsmail ARICIOĞLU**  
Teknik Danışman: **Çet – Yapay Asistan**  

> “Kod, sadece bir araçtır. Dayanışma, asıl gücümüzdür.” 💪  
