# 🇩🇪 Almanca Kelime Öğrenme Web Uygulaması

Modern, responsive ve kullanıcı dostu bir Almanca kelime öğrenme platformu. 

## ✨ Özellikler

### 📇 Kelime Kartları Modu
- Kelimeleri ön yüz/arka yüz kartlar halinde görüntüleme
- Kartı çevirerek gramer kuralları ve örnek cümleleri görme
- Öğrenilen kelimeleri işaretleme ve ilerleme takibi

### 🎯 Quiz Modu
- Örnek cümle eşleştirme quizi
- Otomatik skor hesaplama
- Anlık geri bildirim (doğru/yanlış)

### 🔊 Ses Özellikleri
- Her kelimenin sesli telaffuzu
- Opus formatında yüksek kaliteli ses dosyaları
- Tek tıkla ses çalma

### 🎨 Filtreleme ve Arama
- Lektion'a göre filtreleme (1-10)
- Teil'e göre filtreleme (1-8)
- Kelime, gramer veya örnek cümlelerde arama
- Rastgele sıralama

### 💾 İlerleme Takibi
- Öğrenilen kelimeler tarayıcıda kaydedilir
- İstatistikler: Toplam/Öğrenilen/Kalan kelime sayısı
- İlerleme sıfırlama özelliği

### ⌨️ Klavye Kısayolları
- `←` / `→` : Önceki/Sonraki kelime
- `Space` : Kartı çevir
- `Enter` : Sesi çal

## 📊 İstatistikler

- **Toplam Kelime**: 626
- **Lektion Sayısı**: 10
- **Teil Sayısı**: 8
- **Ses Dosyası**: 327 adet

## 🚀 Nasıl Kullanılır?

### Lokal Kullanım

1. Bu klasördeki dosyaları indirin
2. `index.html` dosyasını bir web tarayıcısında açın
3. Kelimeleri öğrenmeye başlayın!

**Not**: Ses dosyalarının çalışması için dosyaları bir web sunucusunda çalıştırmanız gerekebilir.

### Web Sunucusu ile (Önerilen)

Python 3 ile basit web sunucusu:
```bash
python -m http.server 8000
```

Sonra tarayıcınızda: `http://localhost:8000`

### GitHub Pages ile (En İyi Çözüm)

Ücretsiz ve kolay! Detaylı talimatlar için `DEPLOYMENT.md` dosyasına bakın.

## 📁 Dosya Yapısı

```
.
├── index.html              # Ana web uygulaması (tek dosya)
├── kelimeler_web.json      # Kelime veritabanı (626 kelime)
├── sesler/                 # Ses dosyaları klasörü
│   ├── 1.opus
│   ├── 2.opus
│   └── ... (327 dosya)
├── vokabelliste-web-14.2.2026.xlsx  # Kaynak Excel dosyası
├── README.md               # Bu dosya
└── DEPLOYMENT.md           # GitHub Pages kurulum talimatları
```

## 🛠️ Teknik Detaylar

### Teknolojiler
- **Frontend**: Pure HTML5, CSS3, JavaScript (ES6+)
- **Stil**: Modern gradient tasarım, responsive layout
- **Veri**: JSON formatında kelime veritabanı
- **Ses**: Opus formatı (Chrome, Firefox, Edge destekler)

### Tarayıcı Uyumluluğu
- ✅ Chrome/Edge (önerilen)
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

### Responsive Tasarım
- 📱 Mobil telefonlar
- 📱 Tabletler
- 💻 Masaüstü bilgisayarlar

## 🎓 Kelime Veritabanı

Kelimeler Excel dosyasından (`vokabelliste-web-14.2.2026.xlsx`) JSON formatına dönüştürülür.

### Veri Yapısı
```json
{
  "id": 1,
  "wort": "schiefgehen",
  "grammatik": "geht schief, ging schief, ist schiefgegangen",
  "beispiel": "Gestern ging wirklich alles schief – was für ein Tag!",
  "lektion": 1,
  "audio": "1.opus",
  "teil": 1
}
```

### Yeni Kelime Eklemek

1. Excel dosyasını düzenleyin
2. Python scripti ile JSON'a dönüştürün:

```python
import pandas as pd
import json

df = pd.read_excel('vokabelliste-web-14.2.2026.xlsx')
# ... (DEPLOYMENT.md'deki kod)
```

## 🎨 Özelleştirme

### Renkleri Değiştirmek
`index.html` içindeki CSS bölümünde:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Yeni Özellik Eklemek
JavaScript bölümünü düzenleyerek:
- Farklı quiz tipleri
- Spaced repetition algoritması
- Çoklu dil desteği
- Vb.

## 📝 Lisans

Bu proje kişisel kullanım için geliştirilmiştir.

## 🤝 Katkıda Bulunma

1. Fork edin
2. Feature branch oluşturun (`git checkout -b feature/yeniOzellik`)
3. Commit edin (`git commit -m 'Yeni özellik eklendi'`)
4. Push edin (`git push origin feature/yeniOzellik`)
5. Pull Request açın

## 📧 İletişim

Sorularınız için GitHub Issues kullanabilirsiniz.

---

**Made with ❤️ for German language learners**

🇩🇪 Viel Erfolg beim Deutschlernen! 🎓
