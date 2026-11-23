# EEM-465 Gömülü Sistemler Dersi Final Projesi

## STM32F407 Tabanlı İki Kanallı Dijital Osiloskop Tasarımı

<!-- **Teslim Tarihi:** Daha sonra duyurulacaktır. -->

## 1. Projenin Konusu ve Amacı

- Projede, STM32F4 Discovery kartı kullanılarak iki kanallı, bilgisayar destekli bir dijital osiloskop sistemi geliştirilecektir.

- Geliştirilecek sistem, iki farklı analog girişe uygulanan elektrik sinyallerini mikrodenetleyicinin ADC (Analog-to-Digital Converter) birimi aracılığıyla sayısal verilere dönüştürecektir. Elde edilen veriler USART üzerinden bilgisayara aktarılacak ve bilgisayarda geliştirilecek bir arayüz yardımıyla gerçek zamanlı olarak grafik üzerinde görüntülenecektir.

- Projenin temel amacı, derste öğrenilen mikrodenetleyici programlama konularının bir arada kullanıldığı, çalışan bir gömülü sistem geliştirilmesidir.

## 2. Teknik Gereksinimler

- Projede, tek bir ADC biriminin iki kanalı veya iki ayrı ADC birimi kullanılabilir.

- ADC girişlerine uygulanan gerilimler, mikrodenetleyicinin izin verilen sınırlarını aşmamalıdır. Proje kapsamında giriş sinyalleri 0–3.3 V aralığında tutulacaktır. Negatif gerilimler veya 3.3 V üzerindeki sinyaller ADC girişlerine doğrudan uygulanmamalıdır.

- ADC örnekleme işleminin belirli ve düzenli zaman aralıklarında gerçekleştirilmesi gerekmektedir. Bu amaçla STM32F407 mikrodenetleyicisinin Timer birimlerinden yararlanılacaktır.

- ADC kanallarından elde edilen sayısal veriler USART üzerinden bilgisayara gönderilecektir.

- Bilgisayar tarafında, seri port üzerinden gelen verileri okuyarak grafik üzerinde görüntüleyen bir uygulama geliştirilecektir.

- Projenin mikrodenetleyici tarafındaki yazılımı, derste gösterildiği gibi **register seviyesinde** geliştirilecektir.

- Geliştirilen sistemin çalışması gerçek analog sinyaller kullanılarak gösterilecektir. Uygun genlik ve DC ofsete sahip sinüs sinyalleri uygulanacak ve bilgisayar ortamında görüntülenecektir.

- Uygulanacak sinyalin uygunluğu, öncelikle bir osiloskop yardımıyla kontrol edilecek, ardından STM32F4 Discovery kartı ile ölçüm gerçekleştirilecektir.

- Giriş geriliminin devreye zarar vermemesi için gerilim bölücü devre gibi gerekli koruyucu önlemler alınması gerekebilir.

- **Geliştirilen cihaz, 100 Hz'e kadar olan sinyalleri ölçebilmeli ve dalga biçimlerini görüntüleyebilmelidir.**

## 3. Proje Raporu

Her öğrenci, gerçekleştirdiği çalışmayı açıklayan bir proje raporu hazırlayacaktır. Rapor aşağıdaki bölümlerden oluşmalıdır.

### 3.1. Giriş ve Projenin Amacı

Projenin amacı ve kapsamı açıklanacaktır.

### 3.2. Sistem Tasarımı

Bu bölümde aşağıdaki konulara yer verilmelidir:

- Sistemin blok diyagramı
- Kullanılan donanımlar
- ADC girişleri ve pin bağlantıları
- Giriş koruma elemanları
- USART bağlantıları
- Bilgisayar ile haberleşme yapısı
- Yapılan çalışmanın algoritması
gibi...

Sistemin genel blok diyagramı ve gerekli devre/bağlantı şemaları bu bölümde bulunmalıdır.

### 3.3. Mikrodenetleyici Yazılımı

GPIO, ADC, Timer ve USART yapılandırmaları açıklanacaktır.

Aşağıdaki soruların cevaplarına yer verilmelidir:

- Hangi ADC kanalları kullanılmıştır?
- ADC hangi çalışma modunda yapılandırılmıştır?
- Timer örnekleme periyodunu nasıl belirlemektedir?
- Timer'ın prescaler ve auto-reload register değerleri nasıl hesaplanmıştır?
- USART baud rate değeri nasıl belirlenmiştir?
- Örnekleme ve veri gönderme işlemleri nasıl organize edilmiştir?
- Veriler bilgisayara hangi formatta gönderilmektedir?

Register ayarlarının hangi amaçla ve nasıl yapıldığı açıklanmalıdır.

**Kaynak kodların tamamının tek seferde rapora eklenmesi uygun değildir.** Kodlar ilgili bölümlerde ele alınmalı, hangi kodun ne amaçla kullanıldığı açıklanmalıdır.

### 3.4. Bilgisayar Uygulaması

Bilgisayar arayüzünü geliştirmek için uygun bir programlama dili kullanılabilir. Örneğin Python tercih edilebilir.

Bu bölümde geliştirilen uygulamanın çalışma prensibi, veri alma ve grafik arayüz görüntüleri, işlevleri olmalıdır. Bilgisayardaki programın ayrıntılı açıklanması gerekmemektedir.

### 3.5. Deneysel Sonuçlar

Bu bölümde aşağıdaki bilgilere yer verilmelidir:

- Kullanılan test sinyalleri
- Sinyallerin frekansları ve gerilim aralıkları
- Seçilen örnekleme frekansı
- Bilgisayarda elde edilen grafik görüntüleri
- Varsa gözlemlenen hatalar veya sınırlamalar

### 3.6. Sonuç ve Değerlendirme

Projenin hangi gereksinimleri karşıladığı, karşılaşılan sorunlar ve geliştirilebilecek özellikler kısaca açıklanacaktır.

### 3.7. Kaynaklar

Varsa yararlanılan kaynaklar belirtilecektir.

## 4. Proje Sunumu ve Uygulamalı Gösterim

Her öğrenci projesini uygulamalı olarak sunacaktır.

**Sunum süresi yaklaşık 10-15 dakikadır.**

Sunum sırasında projede hangi birimlerin kullanıldığı açıklanacak ve geliştirilen sistemin çalışması gösterilecektir.

Öğrencilere proje, yazılım ve kullanılan donanım birimleriyle ilgili sorular yöneltilecektir. Bu sorulara verilen cevaplar, projenin çalışması ve proje raporu birlikte değerlendirilerek proje notu belirlenecektir.

Örneğin, öğrencilerden aşağıdaki işlemleri gerçekleştirmeleri veya açıklamaları istenebilir:

- ADC giriş kanalının değiştirilmesi
- Timer örnekleme frekansının değiştirilmesi
- USART baud rate değerinin değiştirilmesi
- Kullanılan bir register'ın işlevinin açıklanması

**Proje değerlendirmesinde yalnızca sistemin çalışması değil, öğrencinin geliştirdiği kodu anlaması ve açıklayabilmesi de dikkate alınacaktır.**

## 5. Teslim Edilecek Dosyalar

Proje kapsamında aşağıdaki dosyalar teslim edilecektir:

1. **STM32 kaynak kodları:** Mikrodenetleyici tarafında geliştirilen projenin kaynak kodları.
2. **Bilgisayar uygulaması:** Osiloskop arayüzünün kaynak kodları ve çalıştırılması için gerekli bilgiler.
3. **Proje raporu:** PDF formatında hazırlanmış rapor.

Dosyalar aşağıdaki isimlendirme biçimine uygun olarak teslim edilmelidir:

- `OgrenciNo_Ad_Soyad_gomulu.zip`
- `OgrenciNo_Ad_Soyad_gui.zip`
- `OgrenciNo_Ad_Soyad_rapor.pdf`

## 6. Akademik Dürüstlük ve Kod Kullanımı

Proje bireysel olarak gerçekleştirilecektir.

Öğrenciler ders notlarından, mikrodenetleyicinin Reference Manual dokümanından, teknik kaynaklardan ve açık kaynak kod örneklerinden yararlanabilirler.

Ancak teslim edilen yazılımın öğrenci tarafından anlaşılması, uyarlanması ve çalışır hale getirilmesi gerekmektedir.

Yapay zeka araçlarından öğrenme, hata ayıklama ve geliştirme amacıyla yararlanılabilir. Ancak öğrenciler, kullandıkları kodların çalışma prensiplerini anlamak, açıklamak ve gerektiğinde değiştirerek uygulayabilmekle sorumludur.

**Yapay zeka araçlarıyla oluşturulan kodları anlayamayan, açıklayamayan veya gerektiğinde değiştiremeyen öğrenciler proje değerlendirmesinde yeterli not alamayabilirler.**

**Her durumda mikrodenetleyici tarafındaki kodlamalar, derste anlatılan register seviyesinde programlama yaklaşımına uygun olmak zorundadır.**