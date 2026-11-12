# Lift-Up egzersiz animasyonu brifi

Lift-Up için 30 hareketlik, döngüsel egzersiz animasyonu seti istiyoruz. Animasyonlar uygulamanın hareket kartlarında, antrenman ekranında ve ana sayfada oynayacak.

## Proje hakkında

Lift-Up, spor salonunda ve evde ağırlık antrenmanı yapanlar için bir antrenman takip uygulaması (iOS ve Android, Flutter). Kullanıcı bir harekete dokunduğunda, hareketin doğru formunu gösteren kısa bir animasyon açılıyor. Hedef kitle 18–45 yaş arası, yeni başlayandan deneyimliye kadar her seviyeden sporcu.

## Görsel stil

- **Tarz:** Sade, düz (flat) ama hacimli illüstrasyon; abartılı karikatür değil, gerçekçi 3D de değil. Referans: Apple Fitness+, Nike Training Club.
- **Figür:** Cinsiyetsiz ya da iki versiyon (kadın ve erkek). Atletik ama aşırı kaslı olmayan vücut, sade yüz.
- **Kas vurgusu:** Hareketin ana çalışan kası hareket sırasında hafifçe parlasın.
- **Renkler:** Figür #1F262B, vurgu ve ekipman #FF6A2A, plakalar marka renklerinde (#2E9E4F, #F2B705, #1F5FD1, #E0334A). Koyu tema için açık renkli (#E9EEF1) figür versiyonu.
- **Arka plan:** Şeffaf; zemin çizgisi ve yumuşak gölge olabilir.
- **Açı:** Çoğunlukla yandan; lateral raise gibi hareketlerde önden.

## Teknik özellikler

| Özellik | İstenen |
| --- | --- |
| Format | Lottie (JSON) ya da Rive (.riv); kaynak dosyalar da teslim edilsin |
| Döngü | Kusursuz döngü: başlangıç ve bitiş karesi aynı |
| Süre | Bir tekrar 2,5–3,5 saniye; altta ve üstte kısa duraksama |
| Kare hızı | 30 fps |
| Boyut | 1:1 kare tuval (1024×1024), figür ortalı |
| Dosya boyutu | Her animasyon en fazla 150 KB, yalnızca vektör |
| Renk değişimi | Figür, vurgu ve ekipman ayrı katmanlarda |
| Küçük ikon | Her hareket için orta anı gösteren tek kare SVG |

## Hareket listesi

| # | Hareket | Ekipman | Açı |
| --- | --- | --- | --- |
| 1 | Squat | Bar | Yandan |
| 2 | Bench press | Bar, sehpa | Yandan |
| 3 | Deadlift | Bar | Yandan |
| 4 | Omuz press | Bar | Yandan |
| 5 | Barbell row | Bar | Yandan |
| 6 | Romanian deadlift | Bar | Yandan |
| 7 | Barfiks | Barfiks barı | Yandan |
| 8 | Dips | Paralel bar | Yandan |
| 9 | Şınav | — | Yandan |
| 10 | Dumbbell curl | Dambıl | Yandan |
| 11 | Triceps pushdown | Kablo | Yandan |
| 12 | Lateral raise | Dambıl | Önden |
| 13 | Lat pulldown | Kablo, oturak | Yandan |
| 14 | Leg press | Makine | Yandan |
| 15 | Lunge | — | Yandan |
| 16 | Hip thrust | Bar, sehpa | Yandan |
| 17 | Leg curl | Makine | Yandan |
| 18 | Calf raise | Basamak | Yandan |
| 19 | Mekik | — | Yandan |
| 20 | Bacak kaldırma | Barfiks barı | Yandan |
| 21 | Goblet squat | Dambıl | Yandan |
| 22 | Dambıl bench press | Dambıl, sehpa | Yandan |
| 23 | Tek kol dambıl row | Dambıl, sehpa | Yandan |
| 24 | Dambıl omuz press | Dambıl | Önden |
| 25 | Dambıl Romanian deadlift | Dambıl | Yandan |
| 26 | Bulgarian split squat | Dambıl, sehpa | Yandan |
| 27 | Vücut ağırlığı squat | — | Yandan |
| 28 | Glute bridge | — | Yandan |
| 29 | Pike şınav | — | Yandan |
| 30 | Superman | — | Yandan |

Her hareketin formu bir antrenör tarafından kontrol edilecek; ilk 3 hareket onaylandıktan sonra kalan set üretilsin.

## Teslim ve süreç

- [ ] Stil çalışması: 1 hareket (squat), 2 farklı stil seçeneğiyle
- [ ] Onaylanan stilde ilk 3 hareket (squat, bench press, deadlift)
- [ ] Form kontrolü ve düzeltmeler
- [ ] Kalan 27 hareket, açık ve koyu tema versiyonlarıyla
- [ ] Her hareket için tek kare SVG ikon
- [ ] Kaynak dosyalar ve kullanım hakkı devri

**Dosya adlandırma:** `liftup_squat_light.json`, `liftup_squat_dark.json`, `liftup_squat_icon.svg`.

**Haklar:** Animasyonların ticari bir mobil uygulamada sınırsız ve süresiz kullanım hakkı yazılı olarak Lift-Up'a devredilmeli.

## Bütçe ve süre

Fiyatlar tasarımcının deneyimine ve ülkesine göre çok değişir; hareket başına fiyat, toplam süre ve revizyon hakkını ayrı ayrı sor. En az 3 tasarımcıdan teklif al. Hazır lisanslı animasyon paketleri daha ucuz ve hızlıdır ama başka uygulamalarda da görülebilir.

## İlan metni

> **Mobil fitness uygulaması için 30 egzersiz animasyonu (Lottie / Rive)**
>
> Lift-Up adlı ağırlık antrenmanı uygulaması için 30 hareketlik, döngüsel egzersiz animasyonu seti arıyoruz. Sade, düz (flat) ama hacimli bir illüstrasyon dili; Apple Fitness+ ve Nike Training Club tarzı. Lottie ya da Rive formatında, açık ve koyu tema versiyonlarıyla, renkleri uygulama içinde değiştirilebilecek şekilde katmanlı teslim edilmesi gerekiyor. Önce 1 hareketlik stil çalışmasıyla başlayacağız. Başvururken daha önce yaptığın karakter animasyonlarını ve hareket başına fiyatını paylaş.
