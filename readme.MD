# Screendump Fix for iOS 15+ (Palera1n)

Bu rehber, iOS 15 ve üzeri sürümlerde (özellikle Palera1n Jailbreak ile) Screendump tweak'inin çalışmama sorununu giderir. 

Cihaz: iPhone 6s (iOS 15.6.1 / 15.7.5)  
Yöntem: Yetkilendirme dosyasını manuel imzalama.

--------------------------------------------------
1. GEREKSİNİMLER (Sileo/Zebra'dan İndirin)
--------------------------------------------------
1. screendump (Repo: http://julioverne.github.io/)
2. curl
3. ldid (veya Link Identity Editor)
4. NewTerm (Terminal uygulaması)

--------------------------------------------------
2. TERMİNAL İŞLEMLERİ (Düzeltme Adımı)
--------------------------------------------------
a) NewTerm uygulamasını açın.
b) Root yetkisi almak için şu komutu yazın ve Enter'a basın:
   sudo su

c) Şifre isteyecektir. Varsayılan şifre: alpine
   (Şifreyi yazarken ekranda harf görünmez, yazıp Enter'a basın)

d) Satır başı kare (#) işaretine döndüğünde, aşağıdaki uzun komutu TEK SEFERDE kopyalayıp yapıştırın (Newtermde yapıştırmak için 3 Parmakla aynı anda basın ekrana) ve Enter'a basın:

```
curl https://raw.githubusercontent.com/thesteveway/screendump/master/screendump/en.plist -o en.plist && ldid -Sen.plist /usr/libexec/screendumpd
```
```
curl -L "https://gitlab.com/alias20/screendump/-/raw/rootless/screendump/en.plist" -o en.plist && ldid -Sen.plist /var/jb/usr/libexec/screendumpd
```
(Hata mesajı almazsanız işlem başarılıdır.)

--------------------------------------------------
3. AYARLAR (SETTINGS)
--------------------------------------------------
Ayarlar > Screendump menüsüne gidin:

- Enabled: AÇIK yapın.
- Authentication: Bir şifre belirleyin (Örn: 1234).
- Resolution (iPhone 6s için en iyi ayar):
    Width: 750
    Height: 1334
  (Eğer çok donarsa bu değerleri: 375 ve 667 olarak değiştirin)

--------------------------------------------------
4. BAĞLANTI (Bilgisayardan)
--------------------------------------------------
a) Bilgisayara TightVNC Viewer veya RealVNC indirin.
b) Telefondan IP adresinizi bulun (Ayarlar > Wi-Fi > 'i' ikonu).
c) VNC programına IP adresini (Örn: 192.168.1.35) yazıp bağlanın.
d) Screendump şifrenizi girin.

--------------------------------------------------
SORUN GİDERME
--------------------------------------------------
Hata: "Authentication refused" / "su: sorry"
Çözüm: Şifreniz 'alpine' değilse sıfırlayın.
Komut: sudo passwd root
(Eskiye 'alpine' yazın, yeniye kendi şifrenizi belirleyin, sonra tekrar deneyin.)
