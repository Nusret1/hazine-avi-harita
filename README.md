# Hazine Avı · Canlı Pano

Alaşehir BİLSEM Hazine Avı oyununun bilgisayar, TV ve projeksiyon panosu.
Takımların ilerleyişini uydu haritası üzerinde, sıralamayı ve son olayları canlı gösterir.

## Kullanım

- **Demo:** Adresi parametresiz açın. Örnek verilerle çalışır.
- **Gerçek oyun:** Öğretmen uygulamasındaki **"Panoyu aç"** butonunun verdiği bağlantıyı açın:
  `.../hazine-avi-harita/?oyun=OYUN_ID&anahtar=PANO_ANAHTARI`
- **F** tuşu tam ekranı açar ve kapatır. **Uydu / Harita** düğmesi harita türünü değiştirir. **Ortala** düğmesi tüm istasyonları ekrana sığdırır.

## Nasıl çalışır

Pano Firebase'deki tek bir özet belgeyi dinler: `oyunlar/{oyun}/pano/{anahtar}`.
Bu belgeyi öğretmenin telefonu günceller. Pano öğrenci verilerinin tamamını görmez.
Öğrencilerin canlı GPS konumu kullanılmaz. Takım pulu, takımın son açtığı istasyonda durur.

Belgenin alanları:

| Alan | Açıklama |
|---|---|
| `ad` | Oyunun adı |
| `baslangic`, `bitis` | Başlangıç ve bitiş zamanı (ms) |
| `durum` | `canli` veya `bitti` |
| `baslangicNoktasi` | `{lat, lng}` |
| `istasyonlar` | `[{ad, lat, lng}]` |
| `takimlar` | `[{ad, renk, istasyon, puan, uye}]`. `istasyon` = tamamlanan istasyon sayısı |
| `olaylar` | `[{zaman, metin, tur}]`. `tur`: `""`, `ipucu`, `bitti`. `**kalın**` yazılabilir |
| `duyurular` | `["metin", ...]` |

## Harita kaynakları

Uydu görüntüsü: Esri World Imagery. Harita: © OpenStreetMap katkıcıları, © CARTO.
