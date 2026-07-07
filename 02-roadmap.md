# 02 — Anti-Slop Üretim Roadmap'i

Amaç: İzleyicinin "yine AI çöpü" deyip geçmediği, "bu nasıl yapılmış?" dediği görsel kalite. Slop hissinin sebepleri bilinir ve her biri pipeline'da bir adımla engellenir.

## 1. AI Slop'un 7 Belirtisi ve Panzehirleri

| Slop belirtisi | Panzehir |
|---|---|
| Aşırı doygun, plastik renkler | Sabit LUT/renk paleti; prompt'a `muted color palette, film grain` ; post'ta doygunluğu -10/-15 çek |
| Fizik hatası (eriyen taşlar, imkansız mimari) | Görseli üretirken 4-8 varyant al, mimariyi ZOOM'layarak denetle; hatalıyı asla animate etme |
| Ölü, steril sahne (rüzgar yok, canlılık yok) | Motion prompt'a mutlaka ikincil hareket: sancak dalgalanması, yaprak, sis akışı, at kulağı seğirmesi |
| Uncanny insan yüzleri | İnsanları uzak/arkadan/silüet göster; yüz yakın çekimi YASAK |
| Tutarsız stil (her video başka evrenden) | Bölge başına sabit stil çapası cümlesi (bkz. 03) — her prompt'un sonuna aynen yapıştırılır |
| Aşırı pürüzsüz "AI kamerası" | `handheld subtle shake` / doğal kamera ağırlığı; post'ta hafif grain + vignette |
| Anlamsız detay enflasyonu | Kompozisyonda negatif alan bırak; sis, gökyüzü, düz duvar = göz dinlenme alanları |

## 2. Üretim Pipeline'ı (video başına ~20-30 dk)

```
[1] KONSEPT     → 05'teki takvimden günün bölgesi + sahne fikri
[2] GÖRSEL      → 03'teki prompt şablonu ile 4 varyant üret (9:16, yüksek çözünürlük)
                  Higgsfield: generate_image (Soul/benzeri fotoreal model)
[3] DENETİM     → Zoom kontrol: mimari mantık, ufuk çizgisi, at anatomisi
                  4 varyanttan en iyisi seçilir; hepsi kötüyse prompt revize, tekrar
[4] ANİMASYON   → Seçilen görsel + 03'teki motion prompt → image-to-video
                  Higgsfield: generate_video (kling3_0 / seedance — 5-10 sn, 9:16)
[5] UPSCALE     → upscale_video (aigc preset, 2K) — TikTok sıkıştırması kaliteyi yer,
                  yüksek kaynak = net sonuç
[6] POST        → CapCut: ses senkronu (beat'e reveal), grain, hafif vignette,
                  doygunluk -10, loop kesimi (ilk ve son kare akışı test et)
[7] ÖN KONTROL  → Higgsfield virality_predictor (hook gücü / retention riski)
[8] YAYIN       → Caption (04'ten) + 3-5 hashtag + doğru saat
[9] ÖLÇÜM       → 24 saat sonra metrikleri takvim dosyasına işle
```

## 3. Araç Seti

| İş | Birincil | Alternatif |
|---|---|---|
| Görsel üretim | Higgsfield (MCP hazır) | Midjourney v7 (--ar 9:16 --style raw), FLUX |
| Image-to-video | Higgsfield kling3_0 / seedance | Runway, Hailuo, Veo |
| Upscale | Higgsfield (bytedance aigc / topaz) | Topaz standalone |
| Kurgu + ses | CapCut (TikTok ses kütüphanesine direkt erişim) | Premiere |
| Viralite ön testi | Higgsfield virality_predictor | — |
| Rakip/ses takibi | TikTok Creative Center (ücretsiz trend sesler) | — |

> Not: Higgsfield MCP bu oturuma bağlı — istediğinde ilk test videosunu birlikte üretebiliriz: görsel → animasyon → upscale zincirini ben çalıştırırım.

## 4. Fazlar

### Faz 0 — Kimlik Kurulumu (1-2 gün)
- [ ] Hesap adı + profil: gezgin süvari evreni ("X Diyarları'ndan kayıtlar" tarzı bio)
- [ ] 6 bölgenin stil çapası cümleleri donduruldu (03'te hazır — değiştirme, tutarlılık her şey)
- [ ] Renk kimliği: her bölge için 1 LUT/filtre preset'i CapCut'ta kaydet
- [ ] İlk 6 video stoklandı (her bölgeden 1) — hesap açılışında art arda değil, günde 1-2 yayın

### Faz 1 — Doğrulama (Hafta 1-2): günde 2 video
- %80 kanıtlanmış format (at POV + kale). A/B: bölgeler, saatler, caption dilleri
- Hedef: hangi bölge + saat + ses kombinasyonu tamamlanma oranını maksimize ediyor → veri

### Faz 2 — Seri Kimliği (Hafta 3-6): günde 1-2 video
- En iyi 2-3 bölgeye ağırlık ver, "yolculuk günlüğü" numaralandırmasını başlat (Gün 1, Gün 2...)
- Haftada 1 "lore bombası": evrenin haritası, bölge tanıtımı, "bugüne kadarki yolculuk" derlemesi (15-30 sn)
- Hedef: 10K takipçi, follow sebebi = hikayeyi takip etmek

### Faz 3 — Genişleme (Hafta 7+)
- İç mekan serileri (taverna gece, büyücü kütüphanesi, taht odası) — save mıknatısı
- Sezonluk arc'lar: "Kuzeye kış geldi" (tüm bölgeler karlı versiyonlarına döner) — evrenin canlı olduğu hissi, kimse yapmıyor
- Ses çeşitlendirme + Instagram Reels / YouTube Shorts'a çapraz yayın (aynı dosya, sıfır ek maliyet)
- İleri aşama: izleyici oylamalı yol ayrımları ("Süvari hangi yöne gitsin? Yorumlara yaz") — interaktif lore

## 5. Kalite Kapıları (yayın öncesi checklist)

Her video yayından önce bu 6 soruyu geçmeli:

1. İlk kare tek başına ekran görüntüsü olarak "kaydedilesi" mi?
2. Zoom'da mimari/anatomi hatası var mı? (varsa yayınlama — tek slop video hesabın algısını bozar)
3. İkincil hareket var mı (sancak/sis/yaprak/kulak)?
4. Loop dikişsiz mi?
5. Bölgenin renk kimliğine uyuyor mu?
6. Caption lore'a bir tuğla ekliyor mu, yoksa boş açıklama mı?
