# Su Deposu • İnteraktif 3D Şema

Komparatör projesinin bir parçası olarak hazırlanan, içme suyu deposunun bölümlerini ve elemanlarını 3 boyutlu, etkileşimli olarak tanıtan tek dosyalık bir web sayfası.

## Neler var?

8 bileşen tıklanabilir, etiketli ve açıklamalı:

1. **Havuzluk** — Su depolama haznesi
2. **Manevra Odası** — Vana ve kontrol bölmesi
3. **Dolma (Alım) Hattı** — Giriş borusu
4. **Çıkış (İsale) Hattı** — Şebekeye su verme
5. **Tepe Savak** — Üst düzey taşma eşiği
6. **Dip Savak** — Dip boşaltma vanası
7. **Taşma Tahliyesi** — Aşırı yükselme çıkışı
8. **Vanalar** — Akış kontrol elemanları

Sahne ile etkileşimler:
- Fareyle döndür / kaydır / yakınlaştır (OrbitControls)
- Sol panelde otomatik açıklama, sağ altta su seviyesi göstergesi
- **Doldur / Boşalt** butonları → su animasyonu
- **Döndür** → otomatik dönüş aç/kapa
- **Kesit** → duvar şeffaflığını artır
- **Sıfırla** → görünümü başa al
- Sahnedeki her etiket veya soldaki listeden bir bileşene tıkla → kamera vurgular, bilgi paneli güncellenir

## GitHub Pages'e nasıl koyarım?

İki yol var:

**1. Doğrudan repo köküne** (en kolay):
```
git add su-deposu-3d.html
git commit -m "su deposu 3d şema"
git push
```
GitHub repo ayarlarından **Settings → Pages** sekmesinde Pages'i aktif edin (branch: `main`, folder: `/ (root)`). Sonra:
```
https://<kullanıcı-adınız>.github.io/<repo-adı>/su-deposu-3d.html
```

**2. Mevcut sitenize bir alt sayfa olarak**:
- Dosyayı sitenizin uygun klasörüne kopyalayın
- Bir menü/link bağlantısı ekleyin: `<a href="su-deposu-3d.html">3D Depo Şeması</a>`

## Yerel test

Three.js modüllerinin ES module CORS kuralı nedeniyle, dosyaya **çift tıklayarak** açmak çalışmaz. Yerel test için bir HTTP sunucu gerekir:

```bash
# Klasöre girin, sonra:
python3 -m http.server 8000
# Tarayıcıdan: http://localhost:8000/su-deposu-3d.html
```

GitHub Pages'a yüklendiğinde sorun olmaz — orası normal HTTP servisi.

## Bağımlılıklar

- Three.js r160 — `cdn.jsdelivr.net` üzerinden CDN ile yüklenir (internet bağlantısı gerektirir)
- Google Fonts (Bricolage Grotesque, IBM Plex Sans, JetBrains Mono) — yine CDN
- Hiçbir build adımı yok, ek dosya yok

## Tarayıcı uyumluluğu

Modern tarayıcılar: Chrome, Firefox, Safari, Edge (son 2-3 yılki sürümler). Mobilde de çalışır, panel düzeni dar ekrana adapte olur.

## Özelleştirme

Açıklamaları değiştirmek için dosyada `const COMPONENTS = { ... }` bloğunu düzenleyin (satır ~640 civarı). Türkçe metinleri burada bulabilirsiniz.

Renk paletini değiştirmek için en üstteki `:root { --bg-0: ...; }` CSS değişkenleri.

Geometri ölçüleri için `HAVUZ_W`, `MANEV_W` vs. değerleri (Three.js bölümünün başında).
