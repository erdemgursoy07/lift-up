# Lift-Up teknik plan

## Özet

Lift-Up'ın ilk sürümü (v1.0), prototipteki kişisel antrenman takibini iOS ve Android'de gerçek bir uygulama olarak yayınlar. Prototipe eklenen oyunlaştırma, 3D anatomi ve vücut takibiyle hedef yaklaşık 17–21 haftada mağazalara çıkmak.

v1.0 tek kişilik bir antrenman günlüğüdür: kayıt, program, ilerleme grafikleri, kas haritası ve hareket kartları. Sosyal özellikler ve antrenör hesapları sonraki sürümlere kalır.

Varsayım: tek geliştirici ya da küçük bir ekip, tam zamanlı çalışıyor. Süreler buna göre tahmindir.

## Teknoloji seçimi

Öneri: mobilde Flutter ile tek kod tabanı, sunucu tarafında Supabase.

| Katman | Öneri | Neden | Alternatif |
| --- | --- | --- | --- |
| Mobil çatı | Flutter (Dart) | Tek kodla iOS ve Android; grafik, animasyon ve özel çizimlerde güçlü | React Native |
| Telefondaki veri | SQLite (drift paketi) | İnternet çekmeyen salonda da kayıt yapılabilir | Isar, Hive |
| Hesap ve sunucu | Supabase (PostgreSQL + Auth) | E-posta, Apple ve Google girişi hazır | Firebase |
| Hatırlatmalar | Yerel bildirimler (flutter_local_notifications) | Sunucu gerekmez | Firebase Cloud Messaging |
| Grafikler | fl_chart | Çizgi ve çubuk grafikler, animasyonlu çizim | Syncfusion Charts |
| 3D anatomi | GLB modelini gösteren bir 3D görüntüleyici | Prototipteki model aynı dosya biçimiyle taşınır | WebView içinde three.js |
| Kutlama efektleri | Lottie ya da Rive, haptics paketi | Tasarımcı dosyalarından oynatılır | Flutter animasyonları |
| Yapay zekâ koç | Claude API (sunucu tarafından çağrılır) | Kullanıcı verisiyle kişisel cevap ve program düzenleme | — |
| Ödeme | App Store ve Google Play abonelikleri (RevenueCat ile) | Deneme, plan ve iptal yönetimi hazır | Doğrudan mağaza API'leri |
| Çökme takibi | Firebase Crashlytics | Ücretsiz, kurulumu kolay | Sentry |

Paket adları 2026 ortasındaki bilgiye dayanır; başlamadan önce güncel durumları kontrol edilmeli.

## Mimari ve veri modeli

Uygulama önce telefona yazar, internet olunca sunucuyla eşitler (offline-first).

| Tablo | Önemli alanlar | Not |
| --- | --- | --- |
| users | id, ad, e-posta, boy, kilo, yaş, cinsiyet, tema, premium durumu | Supabase Auth hesabına bağlı |
| exercises | id, ad, kas grupları, ekipman, adımlar, uyarı | Sabit liste + kullanıcının kendi hareketleri |
| programs | id, user_id, ad, hedef, deneyim, yer, süre, kaçınılan bölgeler, sıradaki gün | Kullanıcının programları |
| program_days | id, program_id, sıra, ad, teknik etiket | Örnek: "Bacak, Göğüs ve Sırt" (Tüm vücut A) |
| program_exercises | id, day_id, exercise_id, set, tekrar, sıra, süperset | Hedef set ve tekrarlar |
| workouts | id, user_id, program_day_id, başlangıç, süre | Bir antrenman oturumu |
| workout_sets | id, workout_id, exercise_id, set no, kg, tekrar, RPE, tamamlandı | Rekorlar, grafikler ve kas haritası buradan hesaplanır |
| body_logs | id, user_id, tarih, kilo, ölçüler | Vücut takibi |
| photos | id, user_id, tarih, dosya | Yalnızca kullanıcının kendi deposunda |

- **Eşitleme:** Her satırda `updated_at` ve `deleted` alanı; çakışmada son yazan kazanır.
- **Güvenlik:** Supabase Row Level Security ile herkes yalnızca kendi satırlarını okur ve yazar.
- **Hesaplamalar:** Rekor, seri, hacim, kas haritası ve otomatik artış telefonda hesaplanır.

## Ekranlar ve özellikler

| Ekran | v1.0'da | Sonraya |
| --- | --- | --- |
| İlk açılış | Hedef, deneyim, vücut bilgileri, gün sayısı, yer, süre, kaçınılacak bölge, hesap, otomatik program | Başlangıç güç testi |
| Ana sayfa | Sıradaki antrenman kartı, seri, haftalık hedef, seviye, akıllı uyarılar | Ana ekran widget'ı |
| Antrenman | Odaklı hareket görünümü, otomatik artış, ısınma setleri, süperset, RPE, plaka göstergesi, dinlenme sayacı, rehberli tur | Kilit ekranında dinlenme sayacı |
| İlerleme | 2D kas haritası (yoğunluk, toparlanma), 3D anatomi, grafikler, vücut takibi, takvim | Apple Health ve Google Fit |
| Koç | Yapay zekâ sohbet, program düzenleme, haftalık rapor | Sesli koç |
| Profil | Hesap, seviye ve rozetler, ayarlar, Premium | Veri dışa aktarma geliştirmeleri |

## Ücretsiz ve Premium

| | Ücretsiz | Premium |
| --- | --- | --- |
| Antrenman kaydı, program, otomatik artış | ✓ | ✓ |
| Isınma, süperset, 1RM hesaplayıcı | ✓ | ✓ |
| Grafikler, takvim, rozetler, 2D kas ve toparlanma haritası | ✓ | ✓ |
| Wrapped ve paylaşım görselleri | ✓ | ✓ |
| Yapay zekâ koç | 3 mesaj/hafta | Sınırsız |
| Kayıtlı program / kendi hareketin | 1 / 3 | Sınırsız |
| Akıllı program, takılma tespiti | – | ✓ |
| 3D anatomi, gelişmiş analiz | – | ✓ |
| Fotoğraf karşılaştırma, Excel, vurgu renkleri | – | ✓ |

Fiyatlar (prototipte örnek): aylık 149,99 TL, yıllık 999,99 TL, 7 gün ücretsiz deneme.

## Yol haritası

| Aşama | Süre | İçerik |
| --- | --- | --- |
| 1. Hazırlık | 1 hafta | Hesaplar, kurulum, tasarım dosyası |
| 2. Çekirdek | 4–5 hafta | Veri modeli, set kaydı, program ve antrenman akışı |
| 3. İlerleme | 4–5 hafta | Grafikler, rekorlar, kas haritası, 3D anatomi, oyunlaştırma |
| 4. Hesap ve eşitleme | 2–3 hafta | Apple ve Google girişi, Supabase eşitlemesi |
| 5. Cila ve beta | 4 hafta | İlk açılış, hareket kartları, koç, Premium, 10–20 kişiyle kapalı beta |
| 6. Yayın | 1–2 hafta | Mağaza incelemesi, v1.0 |

Beta onayı geçilmeden mağazaya gönderilmez: kritik hata kalmamalı ve geri bildirimler işlenmiş olmalı.

## Maliyetler ve yasal konular

| Kalem | Yaklaşık tutar |
| --- | --- |
| Apple Developer Program | 99 USD / yıl |
| Google Play geliştirici hesabı | 25 USD, bir kerelik |
| Supabase | Başlangıçta ücretsiz, büyüyünce aylık ~25 USD'den |
| Alan adı | 10–20 USD / yıl |
| Yapay zekâ koç | Mesaj başına kullanım ücreti (Premium gelirinden karşılanır) |
| Tasarım ve animasyon | Değişken, isteğe bağlı |

Tutarlar 2026 ortasındaki bilgiye dayanır; ödeme öncesi resmi sayfalardan kontrol edilmeli.

- **KVKK:** Boy, kilo ve fotoğraflar kişisel veridir; sağlıkla ilgili veriler özel nitelikli sayılabilir. Aydınlatma metni, açık rıza ve gizlilik politikası gerekir; bir hukukçuya danışılmalı.
- **Mağaza kuralları:** Gizlilik politikası, veri güvenliği beyanı ve uygulama içinden hesap silme zorunlu.
- **Sağlık uyarısı:** Uygulama ve koç tıbbi tavsiye vermez.
- **3D model:** BodyParts3D, CC BY 4.0; uygulamada kaynak gösterilmesi zorunlu.

## Riskler

| Risk | Önlem |
| --- | --- |
| Kapsam büyümesi | v1.0 listesini dondur, yeni fikirleri sonraki sürüme yaz |
| Eşitleme hatası | Erken yaz, iki telefonla test et |
| 3D performansı | Modeli uygulamayla ver, zayıf cihazlarda 2D haritaya geç |
| Yapay zekâ maliyeti | Ücretsiz kullanıcıya haftalık mesaj sınırı |
| Mağaza reddi | Gizlilik politikası ve hesap silmeyi en baştan ekle |

## İlk adımlar

- [ ] "Lift-Up" adının mağazalarda, alan adlarında ve sosyal medyada boş olduğunu kontrol et
- [ ] Apple ve Google geliştirici hesaplarını aç
- [ ] Flutter'ı kur, boş bir projeyi telefonda çalıştır
- [ ] Supabase projesini oluştur, tabloları kur
- [ ] Prototipteki hareket listesini ve program mantığını veri dosyalarına taşı
- [ ] İlk gerçek ekran olarak antrenman kaydını yaz
