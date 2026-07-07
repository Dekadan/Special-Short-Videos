# 03 — Prompt Kütüphanesi (Görsel + Video Hareket)

Promptlar İngilizce (üretim modelleri İngilizce'de çok daha iyi), açıklamalar Türkçe. Sistem iki katmanlı:

```
NİHAİ PROMPT = [SAHNE PROMPT'U] + [BÖLGE STİL ÇAPASI]
```

Stil çapası her bölge için SABİTTİR — asla değiştirilmez. Tutarlılığın sırrı budur.

---

## A. Bölge Stil Çapaları (her prompt'un sonuna aynen eklenir)

**1. Altın Vadiler:**
```
golden hour sunlight, warm amber tones, muted color palette, shot on 35mm film, subtle film grain, cinematic composition, photorealistic, natural imperfections, soft atmospheric haze
```

**2. Kuzey Geçitleri:**
```
overcast cold light, desaturated slate and bone tones, light snowfall, shot on 35mm film, subtle film grain, cinematic composition, photorealistic, harsh weathered textures, atmospheric depth fog
```

**3. Sis Krallığı:**
```
soft dawn light through heavy mist, pale rose and silver tones, muted color palette, shot on 35mm film, subtle film grain, dreamlike but photorealistic, layered fog depth
```

**4. Kara Şato:**
```
monochrome black and white, dramatic chiaroscuro lighting, gothic dark fantasy engraving mood, volumetric storm clouds, immense architectural scale, fine grain, cinematic
```

**5. Liman Şehri Meryn:**
```
late dusk blue hour, warm lantern glow against cool twilight, muted teal and amber palette, shot on 35mm film, subtle film grain, cinematic composition, photorealistic, wet cobblestone reflections
```

**6. Elf Ormanları:**
```
god rays through ancient canopy, deep emerald and soft gold tones, muted color palette, shot on 35mm film, subtle film grain, cinematic composition, photorealistic, floating dust motes in light shafts
```

**Negatif prompt (tüm bölgeler için ortak):**
```
oversaturated, HDR, glossy, plastic, smooth digital render, video game screenshot, cartoon, anime, distorted anatomy, extra limbs, malformed architecture, floating objects, text, watermark, close-up human face
```

---

## B. Sahne Promptları (görsel üretim, 9:16)

### B1. At POV — imza format (%60'lık dilim)

**Kale kapısına yaklaşma (Altın Vadiler):**
```
First-person POV from horseback, the horse's chestnut ears and mane visible at the bottom of frame, approaching the massive arched gatehouse of a medieval castle, red heraldic banners hanging from weathered limestone walls, ivy climbing the stonework, cobblestone road leading up worn stone steps, towering spires rising above, low angle emphasizing monumental scale
```

**Uçurum yolu (Kuzey Geçitleri):**
```
First-person POV from horseback, the horse's black ears visible at bottom of frame, narrow snow-dusted mountain trail along a sheer cliff edge, jagged rock spires flanking the path, a distant gothic citadel with impossibly tall spires half-hidden in freezing mist across the ravine, faint snowfall
```

**Söğütlerin altından (Sis Krallığı):**
```
First-person POV from horseback riding beneath a weeping willow, hanging leaves framing the top of the view, across the valley a white-walled castle perched on a sheer rock outcrop emerging from a sea of morning fog, pine forest below swallowed by mist
```

**Liman inişi (Meryn):**
```
First-person POV from horseback descending a curved cobblestone street toward a medieval harbor at dusk, timber-framed houses with glowing windows on both sides, hanging iron lanterns, tall ship masts and a lighthouse visible over the rooftops, wet stones reflecting lantern light
```

### B2. Reveal / manzara formatı (%30'luk dilim)

**Tepedeki kale, izleyen figür (Altın Vadiler — screenshot 2 formülü):**
```
Wide cinematic shot of rolling green hills at sunset, a grand medieval castle with towers crowning the highest hill, tiny farmhouses with red roofs scattered in the valley, a winding dirt road, a lone hooded figure seated on a camp chair in the foreground grass watching the castle from behind
```

**Dev köprü (Kara Şato):**
```
Extreme low angle view of a colossal gothic bridge spanning between cathedral-like towers, thousands of needle spires piercing storm clouds, a lone rider crossing the bridge in silhouette, light breaking through the clouds behind the central spire
```

**Taverna içi (iç mekan serisi):**
```
Interior of a cozy medieval tavern at night, massive stone hearth with crackling fire, long oak tables with candles and pewter mugs, hanging dried herbs and iron chandeliers, rain streaking the leaded glass windows, empty innkeeper's counter, viewed from the doorway
```

**Büyücü kütüphanesi (iç mekan serisi):**
```
Vast circular library inside a wizard's tower, spiral staircases of dark wood wrapping around towering bookshelves, floating candles, moonlight falling through a domed skylight onto an open ancient tome on a reading stand, dust motes in the light
```

### B3. Deney formatı (%10'luk dilim)

**Uzak ejderha (asla yakın çekim!):**
```
View from castle ramparts at dusk, guards' braziers burning along the wall, far across the misty valley a colossal winged silhouette gliding between mountain peaks, barely visible through atmospheric haze, birds scattering from the nearest forest
```

**Festival gecesi:**
```
Medieval town square at night during a harvest festival, strings of paper lanterns between timber houses, market stalls with warm candlelight, distant figures dancing around a bonfire, castle towers silhouetted against a starry sky, viewed from a side alley
```

---

## C. Video Hareket Promptları (image-to-video)

Kural: **tek ana hareket + 2-3 ikincil hareket**. İkincil hareketler slop'u öldüren şeydir.

### C1. At POV yürüyüşü (imza hareket)
```
Slow steady forward motion at walking horse pace, gentle rhythmic sway matching horse gait, the horse's ears twitch and rotate naturally, banners ripple slowly in the wind, ivy leaves tremble, subtle handheld camera weight. No cuts, no zoom, constant speed.
```

### C2. Sisin açılması (reveal)
```
Camera locked, very slow push-in. Fog drifts laterally and gradually thins, revealing the castle on the cliff. Willow branches sway gently in the foreground breeze. Light subtly brightens as mist clears. No cuts.
```

### C3. Yavaş pan (manzara)
```
Very slow horizontal pan from left to right across the valley, clouds drift slowly, grass ripples in waves of wind, smoke rises from farmhouse chimneys, the seated figure remains still. Constant speed for seamless loop. No cuts.
```

### C4. İç mekan ambiyansı
```
Camera locked or imperceptibly slow push-in, fire flickers casting moving shadows on stone walls, candle flames sway, rain runs down the window glass, dust motes drift through light. No cuts.
```

### C5. Dark fantasy yükseliş (Kara Şato)
```
Slow vertical tilt upward from the bridge to the storm clouds above the spires, clouds churn slowly, the rider silhouette moves at walking pace across the bridge, light pulses faintly behind the clouds. No cuts.
```

### Hareket YASAKLARI (slop üreten hareketler)
- ❌ Hızlı zoom / whip pan / drone spiral (AI kokusu)
- ❌ 360° dönüş, morph geçişleri
- ❌ Sahne içinde belirip kaybolan objeler
- ❌ Değişken hız (loop'u öldürür)
- ❌ İnsan yüzüne yaklaşan hareket

---

## D. Varyasyon Matrisi

Aynı sahneyi taze tutmanın formülü — bir eksende tek değişiklik:

| Eksen | Varyantlar |
|---|---|
| Saat | şafak / golden hour / blue hour / gece (fener-meşale) |
| Hava | açık / sis / yağmur / kar / fırtına yaklaşıyor |
| Mevsim | yaz / sonbahar (turuncu sarmaşık) / kış (karlı sancaklar) |
| Yön | kaleye yaklaşma / kaleden ayrılış (veda duygusu!) / surlardan bakış |
| Yaşam | boş yol / uzakta kervan / pazara giden köylüler / devriye |

Örnek: "Kale kapısı" sahnesi × 4 saat × 5 hava = tek konseptten 20 video.
