# 06 — Üretim Günlüğü

Her üretilen videonun kaydı. Amaç: hangi prompt/seed/model kombinasyonu işe yaradı, tekrar üretilebilir olsun.

---

## #001 — Altın Vadiler, Gün 1: Kale Kapısına Yaklaşma

| Alan | Değer |
|---|---|
| Tarih | 2026-07-07 |
| Bölge | Altın Vadiler |
| Format | At POV — imza (B1 + C1) |
| Durum | ✅ Pipeline testi tamamlandı |

**Pipeline adımları:**
1. **Görsel:** `cinematic_studio_2_5`, 9:16, 1K, 4 varyant (2 kredi/batch). İlk batch golden hour vurgusu zayıf çıktı → prompt'un **başına** "Low warm sunset sun bathing everything in golden orange light, long shadows" eklendi, ikinci batch çok daha iyi.
2. **Seçilen görsel:** job `d7cf806f-a13a-46ae-88ff-7cf4ad74c02a` (seed 35222) — temiz kompozisyon, at kulakları net, sancaklar okunur, golden hour güçlü.
3. **Animasyon:** `kling3_0`, 8 sn, std, ses kapalı → job `41e4b99d-574b-4594-b522-e6fa7c811db8`. Yürüyüş temposu + sancak dalgalanması + toz kalkması iyi tuttu.
4. **Upscale:** `bytedance` aigc preset, 2K, 24fps → job `2558db99-6b4a-43c7-bb2d-9524cb8565a8`. Final: **1440×2582**, 8 sn.

**Kullanılan görsel prompt (kazanan):**
```
Low warm sunset sun bathing everything in golden orange light, long shadows stretching across the road. First-person POV from horseback, the horse's chestnut ears and mane visible at the bottom of frame, approaching the massive arched gatehouse of a medieval castle, red heraldic banners glowing in the warm evening light against weathered limestone walls, ivy climbing the stonework, cobblestone road leading up to the gate, towering spires catching the last amber sunlight, low angle emphasizing monumental scale, golden hour, warm amber tones, muted color palette, shot on 35mm film, subtle film grain, cinematic composition, photorealistic, natural imperfections, soft atmospheric haze
```

**Kullanılan hareket prompt:**
```
Slow steady forward motion at walking horse pace toward the castle gate, gentle rhythmic sway matching horse gait, the horse's ears twitch and rotate naturally, the red heraldic banners ripple slowly in the evening wind, grass and dust stir faintly along the road, long shadows remain consistent, subtle handheld camera weight. No cuts, no zoom, constant walking speed throughout.
```

**Önerilen caption (yayında):**
```
Day 1 — The gates of the Golden Vale finally opened.
They say no one who enters the keep ever wants to leave.

Gün 1 — Altın Vadi'nin kapıları sonunda açıldı.
```
Hashtag: `#medievaltiktok #castlecore #fantasyworld #goldenbrown #pov`

---

## Öğrenilen Dersler (pipeline notları)

- **Golden hour prompt'un başında olmalı.** Stil çapasının sonundaki "golden hour" tek başına yetmiyor; sahne cümlesinin başına açık ışık tarifi ("low warm sunset sun, long shadows") koyunca model çok daha iyi tutuyor.
- **`cinematic_studio_2_5` bu estetik için çok uygun** — film grain ve 35mm hissi built-in geliyor, ekstra post gerektirmiyor. 4 varyant sadece 2 kredi.
- **`kling3_0` preset önerisini reddet** ("IN THE DARK" preset'i öneriyor) — `declined_preset_id` ile literal git, aksi halde stil bozuluyor.
- **Kredi maliyeti (video başına):** ~2 (görsel 4x) + ~12 (kling 8sn) + ~upscale = tur başına makul. 128 kredi ile onlarca video çıkar.
- **Seedance 2.0 pahalı** (36 kredi) — kling3_0 std daha ekonomik ve bu iş için yeterli.

## Sıradaki Üretim Kuyruğu
- [ ] #002 — Kuzey Geçitleri: karlı uçurum yolu (B1 Kuzey + C1)
- [ ] #003 — Sis Krallığı: söğüt + sisli kale reveal (B1 Sis + C2)
- [ ] #004 — Altın Vadiler varyant: aynı kapı, sisli sabah (varyasyon matrisi testi)
