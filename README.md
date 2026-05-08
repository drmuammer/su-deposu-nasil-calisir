# Su Deposu • İnteraktif 3D Şema

İçme suyu deposunun bölümlerini ve elemanlarını anlatan, tarayıcıda çalışan **tek dosyalık** etkileşimli 3 boyutlu sahne. Türkiye'deki tipik iki bölmeli betonarme depoyu — **havuzluk + manevra odası + tüm boru sistemi** — gerçek geometrisine yakın gösterir.

> **🌐 Canlı demo:** [drmuammer.github.io/su-deposu-nasil-calisir](https://drmuammer.github.io/su-deposu-nasil-calisir)

---

## Neyi gösteriyor?

Sahnede iki havuzluk bölmesi (`T1`, `T2`) ve önündeki manevra odası var. Manevra odasında her hat için armatürler şu sırada dizili:

`vana → demontaj parçası → debimetre → motorlu akış ayar vanası`

11 ayrı bileşen grubu numaralı etiketlerle işaretli — her birine tıklayınca sol panelde işlevini, malzemesini ve teknik detaylarını okuyabilirsiniz.

| # | Bileşen | İşlev |
|---|---|---|
| 01 | Havuzluk Bölmeleri | İki gözlü betonarme su haznesi |
| 02 | Manevra Odası | Vana ve kontrol bölmesi (3 katmanlı boru sistemi) |
| 03 | Dolma Hatları | Giriş boruları (×2, krepe yöntemiyle dökülür) |
| 04 | Çıkış Hatları | Şebekeye su veren isale hatları (×2) |
| 05 | Tepe Savaklar | Üst kotta taşma eşikleri |
| 06 | Dip Savaklar | Tabandaki çamur tahliye hatları (×2) |
| 07 | Taşma Tahliyesi | Aşırı yükselme çıkışı |
| 08 | Vanalar | Manuel kelebek + motorlu akış ayar vanaları |
| 09 | Debimetreler | Elektromanyetik debi ölçerler (FIT-101, FIT-102, FT-201, FT-202) |
| 10 | Bypass Hattı | İki bölme arası su aktarımı için kollektör |
| 11 | Krepinler | 316 paslanmaz çelik çıkış filtreleri |

---

## Kontroller

Sayfa açıldığında sahne tertemiz başlar — tüm paneller varsayılan kapalı. Sağ-altta `⚙` (kontroller), sol-altta `☰` (bileşen listesi), sol-üstte `☰` (açıklama paneli) ve sahne içinde `⇄` (bypass toggle) butonları var.

| Kontrol | Ne yapar? |
|---|---|
| **Doldur / Boşalt** | Su seviyesini animasyonlu yükseltir/indirir; debimetreler canlı değer gösterir (m³/h) |
| **Bypass** | İki bölme arası bağlantı vanasını açar/kapatır; LED kırmızı ↔ yeşil değişir, çıkış debileri paylaşıma geçer |
| **Etiketler** | 11 numaralı 3D pin etiketini gösterir/gizler |
| **Döndür** | Otomatik sahne dönüşünü açar/kapatır |
| **Kesit** | Manevra odası duvarlarını yarı-saydam yapar (iç görünüm) |
| **Sıfırla** | Kamera, su seviyesi, bypass durumunu varsayılana döndürür |

Sahnede mouse ile sürükleyip döndürebilir, scroll ile zoomlayabilirsiniz (mobilde tek/çift parmak).

---

## Teknik

- **Tek HTML dosyası** — bağımlılık yok, build adımı yok
- [Three.js](https://threejs.org/) `r0.160.0` (CDN, ES modules)
- `OrbitControls` — kamera kontrolü
- `CSS2DRenderer` — sahne içine yerleşen HTML etiketler (numaralı pinler, debimetre LCD ekranları, ölçü etiketleri, bypass toggle)
- Saf vanilla JS — framework yok
- Web fontlar: Bricolage Grotesque (başlık), IBM Plex Sans (gövde), JetBrains Mono (mono)

### Boru renkleri (akışkan cinsine göre)

| Renk | Akışkan |
|---|---|
| 🔵 Mavi | Dolma (giriş) |
| 🔴 Kırmızı | Çıkış (isale) |
| 🟣 Mor | Dip savak |
| 🟢 Yeşil | Tepe savak / taşma tahliyesi |
| 🟡 Sarı | Bypass |

---

## Geliştirme

Tek dosya olduğu için herhangi bir static server ile yerelde çalıştırılabilir:

```bash
# Python ile
python3 -m http.server 8000

# Node ile
npx serve .

# Ya da VS Code'da Live Server eklentisi
```

Tarayıcıda `http://localhost:8000` açın.

### Debug konsolu

Tarayıcı konsolunda `window.depo3d` üzerinden:

```js
depo3d.fill();              // sahneyi doldur
depo3d.drain();             // sahneyi boşalt
depo3d.setWaterLevel(0.7);  // 0-1 arası seviye
depo3d.toggleBypass();      // bypass aç/kapa
```

---

## Lisans

MIT — özgürce kullanın, yayın, eğitim, sunum için referans verin.

## Teşekkür

Hazırlayan: **Muammer Beslen** ([muammerbeslen.com](https://muammerbeslen.com))
