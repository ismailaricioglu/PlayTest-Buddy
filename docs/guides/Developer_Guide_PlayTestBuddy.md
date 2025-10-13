# 🚀 PlayTest Buddy – Deployment & Environment Guide (Dağıtım ve Ortam Rehberi)

## 📘 1. Amaç
Bu doküman, **PlayTest Buddy** sisteminin geliştirme, test ve üretim ortamlarında nasıl dağıtılacağını açıklar.  
Amaç, projenin tüm bileşenlerini (API, SDK, mobil uygulama) kararlı, güvenli ve tekrarlanabilir biçimde kurabilmektir.

---

## 🧩 2. Sistem Bileşenleri

| Bileşen | Açıklama | Sorumlu |
|----------|-----------|----------|
| **API Sunucusu** | Flask tabanlı RESTful servis (Python 3.10+) | Backend Dev |
| **Veritabanı (DB)** | PostgreSQL 15+ | DB Admin |
| **Mobil Uygulama** | Flutter tabanlı Android App | App Developer |
| **SDK (Android)** | Kotlin tabanlı doğrulama modülü | SDK Maintainer |
| **CI/CD Pipeline** | GitHub Actions | DevOps Engineer |

---

## ⚙️ 3. Donanım Gereksinimleri

| Ortam | CPU | RAM | Depolama | Not |
|--------|-----|-----|-----------|-----|
| **Development** | 2 Core | 4 GB | 10 GB | Lokal veya Docker |
| **Testing** | 4 Core | 8 GB | 20 GB | Staging sunucusu |
| **Production** | 8 Core | 16 GB | 50 GB SSD | HTTPS zorunlu |

---

## 🌍 4. Yazılım Gereksinimleri

| Yazılım | Minimum Sürüm | Not |
|----------|----------------|-----|
| Python | 3.10 | API backend |
| PostgreSQL | 15 | Veritabanı |
| Flutter SDK | 3.16 | Mobil uygulama |
| Kotlin | 1.9 | SDK geliştirme |
| Node.js | 18 | Dokümantasyon scriptleri |
| Docker | 24.0+ | Konteyner yönetimi |
| Git | 2.34+ | Versiyon kontrol |

---

## 🧰 5. Ortam Yapılandırması

### 🧩 5.1. Dizim Yapısı
```
PlayTestBuddy/
├── src/
│   ├── api/
│   ├── sdk/
│   └── app/
├── tests/
├── docs/
│   ├── guides/
│   └── security/
├── .env.example
├── docker-compose.yml
└── requirements.txt
```

### 🧩 5.2. Ortam Değişkenleri (`.env`)
```bash
# Genel
APP_ENV=production
APP_DEBUG=false
APP_PORT=8080

# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=playtest_admin
DB_PASS=securepassword
DB_NAME=playtestdb

# Güvenlik
JWT_SECRET_KEY=supersecuretokenkey
TOKEN_EXPIRY_HOURS=1

# E-posta
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=admin@bilkav.org
SMTP_PASS=app_password
```

### 🧩 5.3. Örnek Docker Compose
```yaml
version: '3.9'

services:
  api:
    build: ./src/api
    ports:
      - "8080:8080"
    env_file:
      - .env
    depends_on:
      - db
  db:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_DB: playtestdb
      POSTGRES_USER: playtest_admin
      POSTGRES_PASSWORD: securepassword
    volumes:
      - ./data/db:/var/lib/postgresql/data
  redis:
    image: redis:7
    restart: always
```

---

## 🔄 6. CI/CD Pipeline (GitHub Actions)

### `.github/workflows/deploy.yml`
```yaml
name: Deploy to Production

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: |
          pip install -r requirements.txt

      - name: Run tests
        run: |
          pytest --maxfail=1 --disable-warnings -q

      - name: Deploy
        run: |
          echo "Deploying PlayTest Buddy to Production..."
```

---

## 🧩 7. Ortamlar Arası Farklar

| Özellik | Development | Testing (Staging) | Production |
|----------|--------------|------------------|-------------|
| Debug Modu | ✅ Açık | ⚠️ Kısıtlı | 🚫 Kapalı |
| Log Seviyesi | DEBUG | INFO | ERROR |
| DB Bağlantısı | Lokal | Cloud (RDS) | Cloud (RDS) |
| API Erişimi | Localhost | VPN / Test URL | SSL (443) |
| Puan Servisi | Mock | Gerçek | Gerçek |

---

## 🔐 8. Güvenli Dağıtım Kuralları
- Dağıtım yalnızca CI/CD pipeline üzerinden yapılır.  
- Her build imzalanır (`SHA256 checksum`).  
- API anahtarları `.env` dışında tutulmaz.  
- Her ortamın kendi **secret store’u** (ör. GitHub Secrets, Vault) olmalıdır.  
- Veri geçişlerinde yalnızca **TLS 1.3** kullanılmalıdır.  

---

## 🧾 9. Doğrulama Kontrol Listesi

| Kontrol | Açıklama | Durum |
|----------|-----------|--------|
| 🧱 DB Bağlantısı | PostgreSQL erişimi test edildi | ☐ |
| 🔐 API Token | JWT oluşturma doğrulandı | ☐ |
| 🚀 Build & Deploy | CI/CD çalışıyor | ☐ |
| 📊 Log İzleme | Log’lar Elastic üzerinde görülebiliyor | ☐ |
| 🔄 Rollback | Eski sürüm geri alınabiliyor | ☐ |

---

## 🧠 10. Sonuç
Bu dağıtım rehberi, PlayTest Buddy projesinin sürdürülebilir, güvenli ve ölçeklenebilir biçimde işletilmesini sağlar.  
Tüm ortamlar tutarlı yapılandırılmış, CI/CD entegrasyonu ile otomasyon sağlanmıştır.

---

Hazırlayan: **İsmail ARICIOĞLU**  
Danışman: **Çet – Yapay Asistan**

> “Dağıtım bir son değil, her gün tekrarlanan bir disiplindir.” ⚙️
