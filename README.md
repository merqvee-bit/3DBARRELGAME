# Karlı Köy: Şarap Varili Teslimatı

## Bağlantılar
- **GitHub Release (proje dosyası):** https://github.com/merqvee-bit/3DBARRELGAME/releases/tag/v1.0
- **itch.io (tarayıcıda oyna):** https://merqvee-bit.itch.io/vize

## Özet
Karlı bir köyde akşam güneşi batarken köyün şarap dağıtıcısısın. Haritaya dağılmış 10 şarap varilini radar yardımıyla bulup evlerin yanındaki sarı yuvalara itmelisin. 60 saniye dolmadan hepsini yerleştirirsen kazanırsın.

Hazırlayan: **Yiğit Efe Erkişi**. Bu oyun 3B Oyun Geliştirme dersi için hazırlandı.

## Kontroller
| Tuş | İşlev |
|---|---|
| W / S | İleri / geri yürü |
| A / D | Sola / sağa dön |
| E | Yakındaki varili itmeye başla / bırak (yakında varil yoksa radar taraması) |
| Space | Oyunu başlat |
| R | Oyun bitince tekrar oyna |
| Esc | Oyun bitince oyundan çık |

## Bölümler / Görevler
- **Giriş:** Başla ekranında görev ve kontroller anlatılır. Başlangıç noktasının yakınında birkaç varil ve yuva bulunur. Oyuncu burada itmeyi ve radar taramasını öğrenir.
- **Final:** Kalan variller köyün uzak köşelerinde ve evlerin arasında. Oyuncu bu varilleri radarla bulup dar yerlerden geçirerek yuvalara iter. Son 10 saniyede sayaç kırmızıya döner.
- **Kazanma:** 60 saniye içinde 10 varilin hepsini yerleştirmek.
- **Kaybetme:** Süre bittiğinde yerleştirilmemiş varil kalması.

## Projeyi Açma
1. **Unity Hub**'ı aç ve **Unity 6000.3.1f1** sürümünün yüklü olduğundan emin ol. Bu sürüm yoksa Installs bölümünden yükle.
2. **Add → Add project from disk** seçeneğine tıkla ve bu klasörü (içinde `Assets` bulunan klasör) seç.
3. Proje açılınca `Assets/Scenes/SampleScene` sahnesini aç ve **Play**'e bas.

İlk açılışta Unity `Library` klasörünü yeniden oluşturduğu için birkaç dakika sürebilir.

## Klasör Düzeni
```
Assets/
  Character/   Karakter prefabı, avatar, Idle/Walk animasyonları, Animator Controller
  Materials/   Çimen, taş ve gökyüzü materyalleri
  Models/      Varil modeli
  Prefabs/     Varil ve Yuva prefabları
  Resources/   Arka plan müziği
  Scenes/      Oyun sahnesi (SampleScene)
  Scripts/     Oyun kodları
  Settings/    URP ve build ayarları
Packages/        Unity paket listesi
ProjectSettings/ Proje ayarları
```

## Önemli Kod Dosyaları (`Assets/Scripts`)
| Dosya | Ne yapar |
|---|---|
| `GameManager.cs` | Oyun akışını yönetir: başla ekranı, 60 saniyelik sayaç, skor, bitiş ekranı, müzik, R ile tekrar oynama, Esc ile çıkış. |
| `PlayerController.cs` | Karakter hareketini (W/S ileri-geri, A/D dönüş) ve Idle/Walk animasyon geçişini (`Speed` parametresi) yönetir. |
| `CameraFollow.cs` | Karakteri arkadan ve yukarıdan yumuşak takip eden kamera. Duvarlara girmez, haritadaki fazladan kameraları kapatır. |
| `BarrelCarrier.cs` | E tuşu: varili önde tutup düz itme ve radar taraması. Taranan varillerin üstünde ok işareti gösterir. |
| `Barrel.cs` | Varilin fizik ayarları. Zeminden düşerse varili son sağlam yerine geri koyar. |
| `BarrelSocket.cs` | Evlerin yanındaki yuva. Varil girince varili kilitler, yuvayı yeşile çevirir ve skoru artırır. |
| `Radar.cs` | Sol alttaki radar. Boş yuvaları sarı, dolu yuvaları yeşil, taranan varilleri kırmızı gösterir. |
| `UIKit.cs` | Arayüz kartları, daire ve üçgen görselleri ile metinleri kodla oluşturan yardımcı sınıf. |

## Kullanılan Hazır Asset'ler ve Lisans Notu
- **Karakter ve animasyonlar:** Karakter, ders kapsamında Pusula'da paylaşılan modeldir. Idle/Walk animasyonları ücretsiz kullanım izni olan bir animasyon kütüphanesinden alınmıştır. Yalnızca eğitim amaçlı kullanılmıştır.
- **Harita (karlı şehir) ve varil modeli:** Blender'da hazırlanmıştır.
- **Arka plan müziği (`koy_muzigi.ogg`):** Bu proje için üretilmiştir.
- **TextMeshPro ve LiberationSans fontu:** Unity paketidir. Font, SIL Open Font License (OFL) ile lisanslıdır (`Assets/TextMesh Pro/Fonts/LiberationSans - OFL.txt`).
- **Unity Input System ve URP:** Unity'nin resmî paketleridir.
