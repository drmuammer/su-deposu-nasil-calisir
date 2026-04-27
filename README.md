# Su Deposu — İnteraktif 3D Şema

Türkiye'deki tipik **iki bölmeli içme suyu deposunun** etkileşimli 3 boyutlu görselleştirmesi. Tek HTML dosyası, harici bir build adımı yok; doğrudan tarayıcıda açılır veya GitHub Pages üzerinden yayınlanır.

## Yapı

Sahne, gerçek bir prefabrik betonarme su deposu mantığıyla kurgulandı:

- **2 ayrı havuzluk bölmesi** — bir bölme bakım/temizliğe alınırken diğeri şebekeyi beslemeye devam edebilsin diye
- **Önde manevra odası** — tüm vanaların bulunduğu kuru kontrol odası
- Her bölmenin **kendi dolma + çıkış + dip savak** hattı (toplam 6 ana hat + 6+ vana)
- Her bölmenin **kendi tepe savağı** (yeşil eşik)
- **Ortak taşma tahliyesi** — her iki tepe savağından aşan suyu manevra odasından dışarı atar

## Etkileşim

- **Bileşen seçimi** — sol listeden ya da 3D sahnedeki numaralı etiketlere/elemanlara tıklayarak; sağ panelde Türkçe açıklama ve teknik özellikler
- **Doldur / Boşalt** — su seviyesini animasyonla yükseltir/alçaltır; her iki bölmede de eşzamanlı su seviyesi
- **Taşma animasyonu** — su tepe kotuna ulaştığında tepe savaklardan dökülmeye başlar, taşma tahliyesi borusunun ucundan dikey bir su jeti çıkar ve yerde birikinti oluşur
- **Döndür** — kameranın yörünge dönüşünü açar/kapatır
- **Kesit** — duvar saydamlığını artırarak iç yapıyı daha net gösterir
- **Sıfırla** — kamera, su seviyesi ve seçimi başlangıca alır

## Bileşenler (8 grup)

| # | Bölüm | Açıklama |
|---|---|---|
| 01 | Havuzluk Bölmeleri | İki bölmeli su haznesi |
| 02 | Manevra Odası | Vana ve kontrol bölmesi |
| 03 | Dolma Hatları (×2) | Her bölmeye ayrı giriş borusu |
| 04 | Çıkış Hatları (×2) | Her bölmeden ayrı şebeke çıkışı |
| 05 | Tepe Savaklar (×2) | Üst kot taşma eşikleri |
| 06 | Dip Savaklar (×2) | Taban boşaltma hatları |
| 07 | Taşma Tahliyesi | Aşırı yükselme çıkışı (ortak) |
| 08 | Vanalar | Akış kontrol elemanları (6+ adet) |

## Teknoloji

- **Three.js r0.160.0** (jsDelivr CDN üzerinden ES module)
- **CSS2DRenderer** — 3D sahnede HTML etiketler için
- **OrbitControls** — kamera kontrolü
- Saf vanilya JS, build adımı yok, dış paket bağımlılığı yok

## Yayınlama

Dosyayı `index.html` olarak `drmuammer/su-deposu-nasil-calisir` reposuna yükleyin → otomatik olarak `https://drmuammer.github.io/su-deposu-nasil-calisir/` adresinde yayınlanır. İlk build 1-3 dakika sürebilir.

## Hazırlayan

**Muammer Beslen** — Komparatör

Kaynak: PowerPoint sunum + iki bölmeli prefabrik betonarme su deposu referansları.
