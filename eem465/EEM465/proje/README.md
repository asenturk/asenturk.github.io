
# EEM-465 Gömülü Sistemler Dersi Final Projesi

STM32F407 Tabanlı İki Kanallı Dijital Osiloskop Tasarımı

<!-- **Teslim Tarihi:** Daha sonra duyurulacaktır. -->


- Projede STM32F4 Discovery Kartı kullanılarak iki kanallı, bilgisayar destekli bir dijital osiloskop sistemi geliştirilecektir.

- Geliştirilecek sistem, iki farklı analog girişe uygulanan elektrik sinyallerinin mikrodenetleyicinin ADC (Analog-to-Digital Converter) birimi aracılığıyla sayısal verilere dönüştürecektir. Elde edilen veriler USART ile  bilgisayara aktarılacak ve bilgisayarda geliştirilecek bir arayüz yardımıyla gerçek zamanlı olarak grafik üzerinde görüntülenecektir.

- Projenin temel amacı, derste öğrenilen mikrodenetleyici programlama konularının bir arada kullanıldığı çalışan bir gömülü sistem geliştirilmesidir.

- Projede iki  ADC  kanalı veya 2 ADC kullanılabilir.

- ADC girişlerine uygulanan gerilimler mikrodenetleyicinin izin verilen sınırlarını aşmamalıdır. Proje kapsamında giriş sinyalleri 0–3.3 V aralığında tutulacaktır. Negatif gerilim veya 3.3 V üzerindeki sinyaller ADC girişlerine doğrudan uygulanmamalıdır.


- ADC örnekleme işleminin belirli ve düzenli zaman aralıklarında gerçekleştirilmesi gerekmektedir. Bu amaçla STM32F407 mikrodenetleyicisinin timer birimlerinden yararlanılacaktır.


- ADC kanallarından elde edilen sayısal veriler USART üzerinden bilgisayara gönderilecektir.

- Bilgisayar tarafında seri port üzerinden gelen verileri okuyarak grafik üzerinde görüntüleyen bir uygulama geliştirilecektir.


- Projenin mikrodenetleyici tarafındaki yazılımı, derste gösterildiği gibi **register seviyesinde** geliştirilecektir.


Geliştirilen sistemin çalışması gerçek analog sinyaller kullanılarak gösterilecektir. Uygun genlik ve DC ofsete sahip sinüs sinyalleri uygulanacak ve bilgisayar ortamında görüntülenecektir.


Gelistirdiğiniz cihaz 100 Hz'e kadar sinyalleri ölçebilmelidir.


Her öğrenci gerçekleştirdiği çalışmayı açıklayan bir proje raporu hazırlayacaktır. Raporunuz aşağıdaki bölümlerde oluşmaldır:

- Giriş ve Projenin Amacı


- Sistem Tasarımı


    - Sistemin blok diyagramı
    - Kullanılan donanımlar
    - ADC girişleri ve pin bağlantıları
    - USART bağlantıları
    - Bilgisayar ile haberleşme yapısı

Bu bölümde sistemin genel blok diyagramı ve gerekli bağlantı şemaları bulunmalıdır.

- Mikrodenetleyici Yazılımı

- GPIO, ADC, Timer ve USART yapılandırmaları açıklanacaktır.
- Hangi ADC kanalları kullanılmıştır?
- ADC hangi çalışma modunda yapılandırılmıştır?
- Timer örnekleme periyodunu nasıl belirlemektedir?
- Timer'ın prescaler ve auto-reload register değerleri nasıl hesaplanmıştır?
- USART baud rate değeri nasıl belirlenmiştir?
- Örnekleme ve veri gönderme işlemleri nasıl organize edilmiştir?
- Veriler bilgisayara hangi formatta gönderilmektedir?

Register ayarlarının hangi amaçla yapıldığı açıklanmalı ve kullanılan önemli register'lar belirtilmelidir.

Kaynak kodların tamamının rapora eklenmesi gerekli değildir. Önemli kod bölümlerine yer verilmesi yeterlidir.

### 7.4. Bilgisayar Uygulaması

Bilgisayar arayüzünün gerçekleştirilmesinde kullanılan yazılım ortamı ve kütüphaneler açıklanacaktır.

Seri porttan alınan verilerin nasıl ayrıştırıldığı ve grafiğe aktarıldığı anlatılacaktır.

Geliştirilen arayüzün ekran görüntülerine yer verilmelidir.

### 7.5. Deneysel Sonuçlar

Gerçekleştirilen testler ve elde edilen sonuçlar sunulacaktır.

Bu bölümde:

- Kullanılan test sinyalleri
- Sinyallerin frekansları ve gerilim aralıkları
- Seçilen örnekleme frekansı
- Bilgisayardaki grafik görüntüleri
- Varsa gözlemlenen hatalar veya sınırlamalar

açıklanmalıdır.

Elde edilen sonuçların beklenen sinyal özellikleriyle uyumu değerlendirilmelidir.

### 7.6. Sonuç ve Değerlendirme

Projenin hangi gereksinimleri karşıladığı, karşılaşılan sorunlar ve geliştirilebilecek özellikler kısaca açıklanacaktır.

### 7.7. Kaynaklar

Yararlanılan kaynaklar belirtilecektir.

Özellikle STM32F407 Reference Manual, veri sayfaları, ders notları ve kullanılan diğer teknik kaynaklara yer verilmelidir.

## 8. Proje Sunumu ve Uygulamalı Gösterim

Her öğrenci projesini uygulamalı olarak sunacaktır.

Sunum süresi yaklaşık 8 dakika, soru-cevap ve uygulamalı değerlendirme süresi ise yaklaşık 4 dakika olacaktır.

Sunumda aşağıdaki işlemler gerçekleştirilecektir:

1. Projenin genel yapısının açıklanması.
2. Donanım bağlantılarının gösterilmesi.
3. ADC, Timer ve USART yapılandırmalarının açıklanması.
4. Mikrodenetleyici yazılımının çalıştırılması.
5. İki analog kanal üzerinden veri alınması.
6. Verilerin bilgisayarda gerçek zamanlı görüntülenmesi.
7. Sinyal frekansı veya genliği değiştirilerek sistemin tepkisinin gösterilmesi.

Sunum sırasında öğrenciden yazılım üzerinde küçük değişiklikler yapması istenebilir.

Örneğin:

- ADC giriş kanalının değiştirilmesi,
- Timer örnekleme frekansının değiştirilmesi,
- USART baud rate değerinin değiştirilmesi,
- Kullanılan bir register'ın işlevinin açıklanması

gibi uygulamalar yaptırılabilir.

**Proje değerlendirmesinde yalnızca sistemin çalışması değil, öğrencinin geliştirdiği kodu anlaması ve açıklayabilmesi de dikkate alınacaktır.**

Çalışan bir projeyi sunmak yeterli değildir. Öğrenci, kullandığı çevre birimlerinin nasıl yapılandırıldığını ve sistemin nasıl çalıştığını açıklayabilmelidir.

## 9. Teslim Edilecek Dosyalar

Proje tesliminde aşağıdaki dosyalar bulunmalıdır:

1. **STM32 kaynak kodları:** Mikrodenetleyici tarafında geliştirilen projenin kaynak kodları.
2. **Bilgisayar uygulaması:** Osiloskop arayüzünün kaynak kodları ve çalıştırılması için gerekli bilgiler.
3. **Proje raporu:** PDF formatında hazırlanmış rapor.
4. **Çalışma videosu:** Geliştirilen sistemin iki kanallı ölçüm gerçekleştirdiğini gösteren kısa bir video.

Bütün dosyalar tek bir ZIP arşivi içerisinde teslim edilecektir.

Dosya isimlendirme biçimi:

`OgrenciNo_Ad_Soyad_EEM465_Proje.zip`

Projelerin derlenebilir ve çalıştırılabilir durumda olması gerekmektedir.


## 11. Akademik Dürüstlük ve Kod Kullanımı

Proje bireysel olarak gerçekleştirilecektir.

Öğrenciler ders notlarından, mikrodenetleyici Reference Manual dokümanından, teknik kaynaklardan ve açık kaynak örneklerden yararlanabilirler.

Ancak teslim edilen yazılımın öğrenci tarafından anlaşılması, uyarlanması ve çalışır hâle getirilmesi gerekmektedir.

Hazır proje kodlarının doğrudan kopyalanması veya başka öğrencilere ait çalışmaların teslim edilmesi akademik dürüstlük ihlali olarak değerlendirilecektir.

Yapay zekâ araçlarından öğrenme, hata ayıklama ve geliştirme amacıyla yararlanılabilir. Ancak kullanılan kodun çalışma prensiplerinden öğrencinin kendisi sorumludur.

Proje sunumunda kodu açıklayamayan veya gerekli değişiklikleri gerçekleştiremeyen öğrencilerin notları buna göre değerlendirilecektir.


