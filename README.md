<p align="center"><img src="assets/logo.svg" width="96" alt="Lift-Up logosu"></p>

<h1 align="center">Lift-Up</h1>
<p align="center"><b>Her antrenmanda biraz daha ağır.</b><br>Ağırlık antrenmanı yapanlar için akıllı antrenman takip uygulamasının tıklanabilir prototipi.</p>

---

## Bu depoda ne var?

| Dosya | Açıklama |
|---|---|
| `index.html` | Uygulamanın tek dosyalık, tarayıcıda çalışan prototipi |
| `docs/teknik-plan.md` | Gerçek uygulama için teknik plan: teknoloji, veri modeli, ekranlar, yol haritası, maliyetler |
| `docs/animasyon-brifi.md` | Egzersiz animasyonlarını yaptırmak için tasarımcı brifi |
| `assets/logo.svg` | Logo |
| `icons/` | Uygulama ikonları: iOS (1024, 180), Android (512, 192, uyarlanabilir ön plan 432) ve favicon |
| `server/` | Koç.ai için Gemini sunucusu (Cloudflare Workers) ve kurulum rehberi |
| `NOTICE.md` | Kullanılan üçüncü taraf içeriklerin lisansları ve kaynakları |

## Prototipi çalıştırmak

`index.html` dosyasını herhangi bir tarayıcıda açman yeterli; kurulum gerekmiyor. Telefonda denemek için GitHub Pages ile yayınlayabilirsin (aşağıda).

### GitHub Pages ile canlı yayın

1. Depoda **Settings → Pages** bölümüne git.
2. **Source** olarak `Deploy from a branch`, branch olarak `main` ve klasör olarak `/ (root)` seç, kaydet.
3. Bir iki dakika sonra prototip `https://<kullanıcı-adın>.github.io/<depo-adı>/` adresinde açılır.

## Öne çıkan özellikler

- **Kişiye özel program:** Hedef, deneyim, haftalık gün sayısı, ekipman, süre ve kaçınılacak bölgeye göre otomatik program
- **Otomatik ağırlık artışı:** Tüm setler tamamlanınca ağırlık artar, zorlanınca sabit kalır, takılınca hafifler; RPE'ye göre karar verir
- **Antrenman ekranı:** Odaklı tek hareket görünümü, plaka göstergesi, ısınma setleri, süperset, dinlenme sayacı, rehberli ilk antrenman turu
- **Kas haritası:** 2D yoğunluk ve toparlanma haritası, gerçek anatomik 3D model
- **Koç.ai:** Kullanıcının verilerini bilen, programı düzenleyebilen sohbet koçu
- **İlerleme:** Animasyonlu grafikler, tahmini 1RM, vücut ölçüleri, ilerleme fotoğrafları, takvim
- **Oyunlaştırma:** Seviye ve XP, rozetler, alevli seri, rekor kutlamaları, Lift-Up Wrapped
- **Premium modeli:** Ücretsiz ve Premium ayrımı, 7 günlük deneme ekranı

## Prototipin sınırları

- Veriler yalnızca tarayıcının kendi hafızasında (localStorage) saklanır; hesap ve sunucu yoktur.
- **Koç.ai**, claude.ai'da Claude ile; GitHub Pages ve telefon sürümünde `server/` klasöründeki sunucu üzerinden Gemini ile çalışır. Kurulum için `server/README.md`.
- **Dosya indirme** özelliği yalnızca claude.ai üzerindeki yayınlanmış sürümde çalışır.
- Ödeme alınmaz; Premium denemesi butona basınca hemen açılır.
- 3D motor (three.js) ilk açılışta internetten yüklenir.

## Yol haritası

Gerçek uygulama Flutter ve Supabase ile geliştirilecek. Ayrıntılar `docs/teknik-plan.md` içinde.

## Lisans

Bu deponun içeriği aksi belirtilmedikçe tüm hakları saklıdır. Üçüncü taraf içerikler (3D anatomi modeli, three.js) kendi lisanslarına tabidir; bkz. `NOTICE.md`.
