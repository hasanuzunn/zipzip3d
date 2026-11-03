# Zıp Zıp 3D: Android projesi

Bu klasör, Capacitor ile hazırlanmış bir Android Studio projesidir. Oyunun kendisi `www/` klasöründedir (Three.js dahil, internetsiz çalışır).

## APK oluşturma (Android Studio)
1. Android Studio'yu kur (Hedgehog veya daha yeni). İlk açılışta Android SDK'yı indirmesine izin ver.
2. Android Studio'da **File > Open** ile bu klasördeki `android` klasörünü aç.
3. Gradle senkronizasyonunun bitmesini bekle (ilk seferde birkaç dakika sürer).
4. Telefonu USB ile bağla (Geliştirici seçenekleri > USB hata ayıklama açık) ve ▶ **Run**'a bas. Ya da
   **Build > Build Bundle(s) / APK(s) > Build APK(s)** ile `android/app/build/outputs/apk/debug/app-debug.apk` dosyasını al.

## Oyunu güncelledikten sonra
`www/index.html` değişirse, proje klasöründe şu komutları çalıştır:
```
npm install
npx cap sync android
```

## Play Store'a yükleme
1. **Build > Generate Signed Bundle / APK > Android App Bundle** ile imzalı `.aab` üret (yeni bir keystore oluştur ve sakla, her güncellemede aynısı gerekir).
2. Google Play Console'da (tek seferlik 25 $) uygulama oluştur, `.aab` dosyasını yükle.
3. `android/app/build.gradle` içindeki `versionCode` değerini her yüklemede 1 artır.

## Ayarlar
- Paket adı: `com.zipzip.game` (Play Store'dan önce değiştirmek istersen `capacitor.config.json` ve `android/app/build.gradle` içinden değiştir).
- Ekran dikey kilitli, tam ekran ve ekran açık kalıyor (`MainActivity.java`).
- Yazı tipleri internet varsa Google Fonts'tan yüklenir, yoksa telefonun yazı tipi kullanılır.

## APK'yı GitHub'da derletme (Android Studio gerekmez)
1. GitHub'da yeni bir depo aç ve bu zip'in **içindeki tüm dosyaları** (gizli `.github` klasörü dahil) depoya yükle.
2. Depoda **Actions** sekmesine gir; "APK derle" işi otomatik başlar (yaklaşık 5 dakika).
3. İş yeşil olunca işin sayfasının altındaki **Artifacts** bölümünden `ZipZip3D-apk` dosyasını indir, içindeki `app-debug.apk`'yı telefona at ve kur (Bilinmeyen kaynaklardan yüklemeye izin ver).
