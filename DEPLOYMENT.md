# 🚀 GitHub Pages ile Web Uygulamasını Yayınlama

## 📋 Gereksinimler
- GitHub hesabı (ücretsiz)
- Git kurulu olmalı (bilgisayarınızda)

## 🎯 Adım Adım Kurulum

### 1️⃣ GitHub Repository Oluşturma

1. [GitHub.com](https://github.com)'a gidin ve giriş yapın
2. Sağ üst köşeden **"+"** simgesine tıklayın ve **"New repository"** seçin
3. Repository ayarları:
   - **Repository name**: `almanca-kelime-ogrenme` (veya istediğiniz isim)
   - **Public** seçili olmalı (GitHub Pages için gerekli)
   - **"Initialize this repository with a README"** kutusunu işaretlemeyin
4. **"Create repository"** butonuna tıklayın

### 2️⃣ Dosyaları GitHub'a Yükleme

#### Terminal/Komut İstemi ile:

```bash
# Bu klasöre gidin (dosyalarınızın bulunduğu yer)
cd /mnt/workspace/ymouDWGp88rutwm3GUmSWsPswspPaCC

# Git repository'sini başlatın
git init

# Tüm dosyaları ekleyin
git add index.html kelimeler_web.json sesler/

# İlk commit'i yapın
git commit -m "İlk yükleme: Almanca kelime öğrenme uygulaması"

# GitHub repository'nizin URL'sini ekleyin (aşağıdaki URL'yi kendi repository URL'nizle değiştirin)
git remote add origin https://github.com/KULLANICI_ADINIZ/almanca-kelime-ogrenme.git

# Ana branch ismini main olarak ayarlayın
git branch -M main

# Dosyaları GitHub'a gönderin
git push -u origin main
```

**Not**: İlk push'ta GitHub kullanıcı adı ve şifreniz (veya personal access token) istenecektir.

#### GitHub Web Arayüzü ile (Alternatif):

1. Oluşturduğunuz repository sayfasında **"Add file"** > **"Upload files"** seçin
2. Aşağıdaki dosyaları sürükleyip bırakın:
   - `index.html`
   - `kelimeler_web.json`
   - `sesler/` klasörü (tüm ses dosyaları ile birlikte)
3. Alttaki **"Commit changes"** butonuna tıklayın

### 3️⃣ GitHub Pages Aktifleştirme

1. Repository sayfanızda **"Settings"** (⚙️) sekmesine gidin
2. Sol menüden **"Pages"** seçin
3. **"Source"** bölümünde:
   - **Branch**: `main` seçin
   - **Folder**: `/ (root)` seçin
4. **"Save"** butonuna tıklayın
5. Birkaç dakika bekleyin

### 4️⃣ Web Sitenize Erişim

Birkaç dakika sonra sayfayı yenileyin. Üstte yeşil bir kutu içinde sitenizin adresi görünecek:

```
✅ Your site is live at https://KULLANICI_ADINIZ.github.io/almanca-kelime-ogrenme/
```

🎉 **Tebrikler!** Web uygulamanız artık canlı!

## 🔄 Güncelleme Yapma

Kelimelerinizi veya uygulamayı güncellemek isterseniz:

```bash
# Değişikliklerinizi ekleyin
git add .

# Commit oluşturun
git commit -m "Kelimeler güncellendi"

# GitHub'a gönderin
git push
```

Birkaç dakika içinde değişiklikler otomatik olarak web sitenize yansıyacaktır.

## 📱 Mobil Kullanım

Web uygulamanız responsive tasarıma sahip, yani:
- ✅ Telefondan kullanılabilir
- ✅ Tabletlerden kullanılabilir
- ✅ Masaüstü bilgisayarlardan kullanılabilir

### Ana Ekrana Kısayol Ekleme (Mobil)

**iPhone/iPad:**
1. Safari'de sitenizi açın
2. Alttaki paylaş butonuna (□↑) tıklayın
3. "Add to Home Screen" seçin

**Android:**
1. Chrome'da sitenizi açın
2. Sağ üst köşedeki menüye (⋮) tıklayın
3. "Add to Home screen" seçin

## 🎨 Özellikler

✅ **Kelime Kartları Modu**: Kelimeleri kartlar halinde gösterir, çevirerek öğrenirsiniz
✅ **Quiz Modu**: Bilginizi test edin
✅ **Ses Çalma**: Her kelimenin telaffuzunu dinleyin (.opus formatı desteklenir)
✅ **İlerleme Takibi**: Hangi kelimeleri öğrendiğiniz tarayıcınızda kaydedilir
✅ **Filtreleme**: Lektion ve Teil'e göre filtreleyin
✅ **Arama**: Kelime, gramer veya örnek cümlelerde arama yapın
✅ **Karıştırma**: Kelimeleri rastgele sırada gösterin
✅ **Klavye Kısayolları**: ← → (ileri/geri), Space (çevir), Enter (ses çal)

## 🛠️ Özelleştirme

### Yeni Kelime Eklemek

1. Excel dosyanızı (`vokabelliste-web-14.2.2026.xlsx`) güncelleyin
2. Aşağıdaki Python kodunu çalıştırın:

```python
import pandas as pd
import json

df = pd.read_excel('vokabelliste-web-14.2.2026.xlsx')
kelimeler = []

for idx, row in df.iterrows():
    try:
        lektion = int(float(row['Lektion'])) if pd.notna(row['Lektion']) and row['Lektion'] != '' else 1
    except:
        lektion = 1
    
    try:
        teil = int(float(row['Teil'])) if pd.notna(row['Teil']) and row['Teil'] != '' else 1
    except:
        teil = 1
    
    kelime = {
        'id': idx + 1,
        'wort': str(row['Wort']) if pd.notna(row['Wort']) else '',
        'grammatik': str(row['Grammatikregel']) if pd.notna(row['Grammatikregel']) else '',
        'beispiel': str(row['Beispielsatz']) if pd.notna(row['Beispielsatz']) else '',
        'lektion': lektion,
        'audio': str(row['Audio']) if pd.notna(row['Audio']) else '',
        'teil': teil
    }
    kelimeler.append(kelime)

with open('kelimeler_web.json', 'w', encoding='utf-8') as f:
    json.dump(kelimeler, f, ensure_ascii=False, indent=2)

print(f"✓ {len(kelimeler)} kelime JSON'a dönüştürüldü")
```

3. Değişiklikleri GitHub'a yükleyin (yukarıdaki "Güncelleme Yapma" bölümüne bakın)

## 💾 Yedekleme

Tüm dosyalarınız GitHub'da güvenle saklanır. İstediğiniz zaman:
1. Repository sayfasında **"Code"** > **"Download ZIP"** ile indirebilirsiniz
2. Veya `git clone https://github.com/KULLANICI_ADINIZ/almanca-kelime-ogrenme.git` komutu ile yerel kopya oluşturabilirsiniz

## ❓ Sorun Giderme

### Ses dosyaları çalışmıyor
- Tarayıcınızın .opus formatını desteklediğinden emin olun (Chrome, Firefox, Edge destekler)
- Ses dosyalarının `sesler/` klasöründe olduğunu kontrol edin

### Kelimeler görünmüyor
- Browser console'u açın (F12) ve hata mesajlarına bakın
- `kelimeler_web.json` dosyasının doğru yüklendiğini kontrol edin

### Değişiklikler yansımıyor
- GitHub'a push yaptıktan sonra 2-5 dakika bekleyin
- Tarayıcınızın cache'ini temizleyin (Ctrl+Shift+R)

## 🆓 Ücretsiz Alternatif Platformlar

Eğer GitHub Pages dışında alternatif isterseniz:

1. **Netlify** (netlify.com)
   - GitHub ile entegre
   - Sürükle-bırak ile deploy
   - Otomatik SSL sertifikası

2. **Vercel** (vercel.com)
   - GitHub ile entegre
   - Hızlı deployment
   - Ücretsiz domain

3. **Cloudflare Pages** (pages.cloudflare.com)
   - GitHub entegrasyonu
   - Hızlı CDN
   - Sınırsız bandwidth

## 📞 İletişim ve Destek

Herhangi bir sorunuz varsa:
- GitHub repository'nizde **Issues** sekmesinden destek alabilirsiniz
- Uygulamayı fork edip kendi özelleştirmelerinizi yapabilirsiniz

---

**Başarılar! Almanca öğrenmenizde bol şans! 🇩🇪📚**
