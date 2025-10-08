# 🤝 PlayTest Buddy Katkı Rehberi

PlayTest Buddy açık kaynak bir projedir. Katkılarınız bu topluluğun büyümesini sağlar 💪  

## 🔧 Nasıl Katkı Sağlanır?
1. **Fork** oluşturun (`Fork this repository`)
2. **Yeni branch** açın:  
   ```bash
   git checkout -b feature/yeni-ozellik
   ```
3. **Değişiklikleri yapın**
4. **Testleri çalıştırın**  
   ```bash
   pytest tests/
   flutter test
   ```
5. **Pull Request (PR)** gönderin

## 📋 Kodlama Kuralları
- Kodlar açıklamalı (comment) olmalıdır  
- Branch isimlendirmesi: `feature/`, `fix/`, `doc/`
- PR açıklamaları net ve kısa tutulmalıdır
- Tüm testler geçmeden merge yapılmaz

## 🧪 Test Standartları
| Teknoloji | Test Aracı | Komut |
|------------|-------------|--------|
| Backend (Flask) | Pytest | `pytest tests/` |
| Mobil (Flutter) | flutter_test | `flutter test` |
| SDK (Kotlin) | JUnit | Android Studio test |

## 📬 İletişim
Topluluk tartışmaları ve destek:  
[BilKavTopluluk – Discussions](https://github.com/BilKavTopluluk/PlayTestBuddy/discussions)
