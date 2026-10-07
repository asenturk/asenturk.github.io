# C# Windows Forms ile SCADA Arayüzü Tasarımı

- Bu projeden tüm öğrenciler sorumludur. Tüm öğrenciler projelerini bireysel olarak gerçekleştirecektir. Proje sunumu için 10 dakika süre verilecektir. Proje, ara sınavın %60'ını oluşturacaktır. Her hafta 20 kişi sunum yapacaktır. Sadece işyeri eğitiminde olan öğrenciler ara sınav haftası sunumlarını yapacaktır. Raporlar, sunum yapılacak tarihten önce gönderilmelidir. Sunumlar belirlenen ders saatinde yapılmalıdır. Raporun veya sunumun belirlenen tarihten sonra gerçekleştirilmesi durumunda notlandırma %50 üzerinden yapılacaktır.

## Proje Yönergesi

## 1. SCADA Nedir?

SCADA (*Supervisory Control and Data Acquisition – Gözetleyici Kontrol ve Veri Toplama*), endüstriyel tesislerde bulunan cihazların, sensörlerin ve makinelerin izlenmesi ve gerektiğinde kontrol edilmesi amacıyla kullanılan sistemlerin genel adıdır.

Bir SCADA sistemi aracılığıyla operatör;

- sıcaklık, basınç, seviye, debi gibi ölçüm değerlerini izleyebilir,
- pompa, motor, vana ve ısıtıcı gibi ekipmanların çalışma durumlarını görebilir,
- belirli cihazları çalıştırabilir veya durdurabilir,
- kritik durumları ve alarmları takip edebilir,
- tesisin genel çalışma durumunu grafiksel bir arayüz üzerinden gözlemleyebilir.

Gerçek SCADA sistemlerinde bilgiler PLC, sensör, mikrodenetleyici veya diğer endüstriyel cihazlardan alınmaktadır. Bu projede gerçek bir endüstriyel cihaz kullanılmayacaktır. Bunun yerine C# programı içerisinde **Timer, Random ve benzeri programlama yapıları kullanılarak gerçek sensörlerden veri geliyormuş gibi bir simülasyon oluşturulacaktır.**

Bu nedenle hazırlanacak çalışma, gerçek bir SCADA sisteminin basitleştirilmiş bir **operatör arayüzü (HMI – Human Machine Interface)** olarak düşünülebilir.

## 2. Projenin Amacı

Bu projenin temel amacı, C# Windows Forms ortamında;

- Form tasarımı,
- Label,
- Button,
- TextBox,
- ProgressBar,
- Panel ve benzeri görsel bileşenler,
- Timer kullanımı,
- koşul ifadeleri,
- değişkenler,
- rastgele sayı üretimi,
- olay tabanlı programlama,
- kullanıcı etkileşimi,
- temel hata kontrolü

gibi konuları bir arada kullanarak **endüstriyel bir tesis için SCADA benzeri bir kontrol ve izleme arayüzü geliştirmeleridir.**

Çalışmada yalnızca programın çalışması yeterli değildir. Hazırlanan arayüzün aynı zamanda **düzenli, anlaşılır, görsel olarak uygun ve kolay kullanılabilir** olması beklenmektedir.

## 3. Uygulama Senaryosu

Projede küçük ölçekli bir endüstriyel tesisin kontrol ve izleme sistemi tasarlanacaktır.

Örneğin sistem aşağıdaki ekipmanlardan oluşabilir:

- bir **sıvı tankı**,
- bir **pompa**,
- bir **kontrol vanası**,
- bir **ısıtıcı veya kazan**,
- sıcaklık sensörü,
- basınç sensörü,
- tank seviye sensörü.

Sistem gerçek cihazlara bağlı olmayacaktır. Sensör değerleri yazılım içerisinde üretilecektir.

Örneğin;

- tank seviyesi %0–100 arasında,
- sıcaklık 20–100 °C arasında,
- basınç 0–10 bar arasında

değişebilir.

Bu değerler yalnızca örnektir. Öğrenciler hazırladıkları senaryoya uygun farklı değer aralıkları kullanabilirler.

## 4. Arayüz Tasarımı

Hazırlanacak Windows Forms uygulamasının bir endüstriyel kontrol ekranını çağrıştırması beklenmektedir.

Arayüzde çok fazla bileşen kullanılarak gereksiz karmaşıklık oluşturulmamalı, ancak yalnızca birkaç bileşenden oluşan çok basit bir uygulama da hazırlanmamalıdır.

Orta düzeyde bir SCADA ekranı oluşturulması beklenmektedir.

Arayüzde örneğin aşağıdaki bileşenler kullanılabilir:

- **Label:** sıcaklık, basınç, seviye ve cihaz durumlarının gösterilmesi,
- **ProgressBar:** tank seviyesi, sıcaklık veya benzeri bir büyüklüğün görsel olarak gösterilmesi,
- **Button:** pompa çalıştırma/durdurma, sistemi başlatma/durdurma, alarm sıfırlama vb.,
- **TextBox veya NumericUpDown:** kullanıcı tarafından sınır veya set değeri girilmesi,
- **Panel, PictureBox veya geometrik şekiller:** tank, boru, kazan, vana gibi cihazların temsil edilmesi,
- **Timer:** sensör değerlerinin belirli zaman aralıklarında güncellenmesi,
- **Chart:** belirli bir sensör değerinin zaman içerisindeki değişiminin gösterilmesi.

Her bileşenin sistemin işleyişinde bir görevi bulunmalıdır.

## 5. Simülasyonun Oluşturulması

Gerçek sensörler kullanılmayacağından sistem verileri program içerisinde üretilecektir.

Örneğin bir Timer kullanılarak her 500 ms veya 1000 ms'de sensör değerleri güncellenebilir.

Rastgele değer üretmek için C# içerisindeki `Random` sınıfından yararlanılabilir.

Ancak değerlerin tamamen anlamsız ve birbirinden bağımsız şekilde değişmesi yerine mümkün olduğunca gerçek bir sistem davranışı oluşturulması önerilmektedir.

Örneğin:

- pompa çalışıyorsa tank seviyesi yavaşça artabilir,
- çıkış vanası açıksa tank seviyesi azalabilir,
- ısıtıcı çalışıyorsa sıcaklık artabilir,
- ısıtıcı kapatıldığında sıcaklık yavaşça azalabilir,
- tank seviyesi yükseldikçe belirli ölçüde basınç artabilir.

Böylece yalnızca ekrana rastgele sayı yazdıran bir program yerine **sistem davranışını taklit eden küçük bir simülasyon** oluşturulmuş olacaktır.

## 6. Sistem Kontrolleri

Kullanıcı arayüzü üzerinden sistemde bulunan bazı cihazların kontrol edilebilmesi gerekmektedir.

Örneğin aşağıdaki kontrollerden yararlanılabilir:

- **Sistemi Başlat**
- **Sistemi Durdur**
- **Pompayı Çalıştır**
- **Pompayı Durdur**
- **Isıtıcıyı Aç/Kapat**
- **Vanayı Aç/Kapat**
- **Alarmı Sıfırla**

Her projede bunların tamamının bulunması zorunlu değildir. Hazırlanan senaryoya uygun sayıda kontrol bulunması yeterlidir.

Bir cihazın çalışıp çalışmadığı yalnızca metinle değil, mümkünse görsel olarak da ifade edilmelidir.

Örneğin;

- çalışan bir pompanın göstergesi yeşil,
- duran bir pompanın göstergesi gri,
- alarm durumundaki bir cihazın göstergesi kırmızı

olarak gösterilebilir.

## 7. Alarm Sistemi

SCADA sistemlerinin önemli özelliklerinden biri normal olmayan çalışma durumlarını operatöre bildirmesidir.

Bu nedenle projede en az birkaç temel alarm koşulu oluşturulmalıdır.

Örneğin:

- tank seviyesi %90'dan büyükse **Yüksek Seviye Alarmı**,
- tank seviyesi %10'dan küçükse **Düşük Seviye Alarmı**,
- sıcaklık 85 °C'nin üzerindeyse **Yüksek Sıcaklık Alarmı**,
- basınç belirlenen sınırın üzerindeyse **Yüksek Basınç Alarmı**

oluşturulabilir.

Alarm durumunda;

- ilgili Label'ın rengi değişebilir,
- bir uyarı mesajı gösterilebilir,
- cihazın bulunduğu bölüm kırmızı renge dönüşebilir,
- ekranda bir alarm açıklaması gösterilebilir.

Alarm sistemi anlaşılır olmalı ve operatörün hangi büyüklüğün sınırı aştığını kolaylıkla görmesini sağlamalıdır.

## 8. Görsel Tasarım

SCADA ekranı yalnızca çalışan bir program olarak değil, aynı zamanda **kullanılabilir bir kullanıcı arayüzü** olarak tasarlanmalıdır.

Bu nedenle;

- bileşenler düzenli hizalanmalı,
- çok fazla ve uyumsuz renk kullanılmamalı,
- cihaz isimleri açık bir şekilde yazılmalı,
- ölçüm değerlerinin birimleri belirtilmeli,
- kontrol butonları anlaşılır isimlendirilmelidir.

Tank, kazan, pompa ve borular basit geometrik şekiller kullanılarak temsil edilebilir. Profesyonel bir grafik tasarım beklenmemektedir ancak hazırlanan ekranın bir endüstriyel kontrol panelini çağrıştırması beklenmektedir.

## 9. Programlama Gereksinimleri

Projede arayüzde bulunan bileşenlerin C# kodları ile kontrol edilmesi gerekmektedir.

Kod içerisinde uygun olduğu yerlerde;

- değişkenler,
- `if / else` yapıları,
- metotlar,
- Timer olayları,
- Button Click olayları,
- Random sınıfı,
- kullanıcıdan veri alma,
- değer kontrolü,
- bileşen özelliklerinin kod içerisinden değiştirilmesi

kullanılmalıdır.

Kodların mümkün olduğunca düzenli yazılması ve tekrar eden işlemlerin gerektiğinde metotlara ayrılması önerilmektedir.

Değişken ve bileşen isimlerinde;

`button1`, `label3`, `textBox2`

gibi anlamsız isimler yerine;

`btnPompaBaslat`,  
`lblSicaklik`,  
`progressTankSeviye`,  
`txtBasincLimiti`

gibi yaptığı işi açıklayan isimlerin kullanılması tercih edilmelidir.

## 10. Projenin Aşamaları

Proje iki temel aşamadan oluşmaktadır:

- Proje raporu
- Proje sunumu

## 11. Aşama 1 – Proje Raporu

Projede yapılanlarla ilgili ayrıntılı bir rapor hazırlanacaktır.

Rapor yalnızca projenin ekran görüntüsünü ve kaynak kodlarını içeren bir belge olmamalıdır.

Raporun, projeyi daha önce hiç hazırlamamış bir kişinin aynı uygulamayı yeniden geliştirebilmesini sağlayacak şekilde **adım adım hazırlanmış bir doküman** olması beklenmektedir.

Raporda kullanılan ekran görüntüleri, şekiller ve kod parçaları açıklamasız bırakılmamalıdır. Her görselin veya kod parçasının hangi amaçla kullanıldığı metin içerisinde açıklanmalıdır.

Rapor genel olarak aşağıdaki bölümlerden oluşmalıdır.

### 11.1. Kapak Sayfası

Raporun ilk sayfası kapak sayfası olmalıdır.

Kapak sayfasında en az aşağıdaki bilgiler bulunmalıdır:

- üniversite, fakülte ve bölüm bilgileri,
- dersin adı,
- **C# Windows Forms ile SCADA Arayüzü Tasarımı** proje başlığı,
- öğrencinin adı ve soyadı,
- öğrenci numarası,
- öğretim elemanının adı,
- tarih.

### 11.2. Projenin Tanıtımı

Bu bölümde hazırlanan proje genel olarak tanıtılmalıdır.

Aşağıdaki konulara yer verilmelidir:

- SCADA'nın kısa tanımı,
- projenin amacı,
- kurgulanan tesis veya sistem senaryosu,
- sistemde bulunan cihazlar,
- ölçülen veya simüle edilen büyüklükler,
- kullanıcı tarafından kontrol edilebilen elemanlar,
- programın genel olarak ne yaptığı.

Bu bölümü okuyan bir kişinin programı çalıştırmadan önce sistemin ne amaçla geliştirildiğini ve programın temel çalışma mantığını anlayabilmesi beklenmektedir.

### 11.3. Programın Genel Çalışma Yapısı

Hazırlanan programın çalışma mantığı genel olarak açıklanmalıdır.

Örneğin;

- program başladığında hangi işlemlerin gerçekleştirildiği,
- sensör değerlerinin nasıl üretildiği,
- verilerin hangi aralıklarla güncellendiği,
- pompa, vana, ısıtıcı vb. cihazların nasıl kontrol edildiği,
- ölçüm değerlerinin arayüzde nasıl gösterildiği,
- alarm koşullarının nasıl çalıştığı

açıklanmalıdır.

Programın yalnızca hangi bileşenlerden oluştuğu değil, **bileşenlerin birbirleriyle nasıl ilişkili olarak çalıştığı** da belirtilmelidir.

### 11.4. Kullanılan Bileşenlerin Eklenmesi

Arayüz oluşturulurken kullanılan önemli Windows Forms bileşenlerinin nasıl eklendiği ekran görüntüleriyle açıklanmalıdır.

Örneğin aşağıdaki işlemler gösterilebilir:

- bileşenin Toolbox içerisinden nasıl bulunduğu,
- Form üzerine nasıl eklendiği,
- `Name`, `Text`, `Size`, `Minimum`, `Maximum`, `Interval` gibi önemli Properties ayarlarının nasıl değiştirildiği,
- gerekli olayların nasıl oluşturulduğu.

Örneğin:

> Toolbox → Common Controls → ProgressBar seçildi.  
> ProgressBar Form üzerine sürüklendi.  
> Name özelliği `progressTankSeviye` olarak değiştirildi.  
> Minimum değeri 0, Maximum değeri 100 olarak ayarlandı.

şeklinde ekran görüntüleriyle adım adım açıklama yapılabilir.

Raporda kullanılan her küçük bileşen için ayrı ayrı aynı işlemlerin tekrarlanması gerekli değildir. Projenin geliştirilmesini ve kullanılan yöntemleri açıklayabilecek önemli bileşenlerin gösterilmesi yeterlidir.

### 11.5. Arayüz Tasarımının Oluşturulması

Tank, pompa, kazan, vana, boru, sensör veya diğer proses elemanlarının ekranda nasıl temsil edildiği açıklanmalıdır.

Arayüzün yalnızca son hali gösterilmemelidir. **Projenin geliştirme aşamalarını gösteren ekran görüntülerinin kullanılması gerekmektedir.**

Örneğin;

1. Formun ilk oluşturulduğu hali,
2. temel bileşenlerin eklendiği hali,
3. tank, pompa, vana veya diğer proses elemanlarının oluşturulması,
4. kontrol butonlarının eklenmesi,
5. ölçüm göstergelerinin eklenmesi,
6. alarm alanının oluşturulması,
7. tamamlanmış arayüz

gibi farklı geliştirme aşamalarına ait ekran görüntüleri kullanılabilir.

Ekran görüntülerinin altında kısa açıklamalar bulunmalıdır.

Örneğin:

> **Şekil 1.** Tank seviye göstergesinin ve kontrol butonlarının Form üzerine eklenmesi.

> **Şekil 2.** SCADA arayüzünün tamamlanmış görünümü.

Bu bölüm, yapılan tasarımın nasıl geliştirildiğini adım adım gösterecek şekilde hazırlanmalıdır.

### 11.6. Kodlama

Programın önemli kod parçaları raporda gösterilmeli ve kodların altında **ne yaptıkları açıklanmalıdır.**

Programdaki bütün kodların rapora kopyalanması gerekli değildir. Programın çalışmasını sağlayan önemli kod parçalarının verilmesi yeterlidir.

Örneğin yalnızca;

```csharp
temperature = random.Next(20, 101);
```

kodunu vermek yerine, bu satırın sıcaklık sensörünü simüle etmek amacıyla 20–100 °C arasında rastgele bir değer ürettiği açıklanmalıdır.

Raporda özellikle aşağıdaki kodların açıklanması önerilmektedir:

- değişkenlerin tanımlanması,
- Timer kullanımı,
- Random ile veri oluşturulması,
- butonların Click olayları,
- `if / else` koşulları,
- cihazların çalıştırılması veya durdurulması,
- ProgressBar ve Label değerlerinin güncellenmesi,
- renk ve durum bilgilerinin değiştirilmesi,
- alarm koşullarının oluşturulması,
- kullanılan önemli metotlar.

Kodların ekran görüntüsü olarak eklenmesi yerine mümkün olduğunca **metin/kod biçiminde** rapora eklenmesi tercih edilmelidir.

### 11.7. Timer ve Veri Simülasyonu

Bu bölümde;

- Timer bileşeninin neden kullanıldığı,
- Interval değerinin ne olduğu,
- Tick olayının nasıl oluşturulduğu,
- Tick içerisinde hangi işlemlerin yapıldığı,
- sensör verilerinin nasıl üretildiği,
- üretilen değerlerin arayüzde nasıl güncellendiği

açıklanmalıdır.

Eğer değerler yalnızca rastgele üretilmiyor ve sistemin durumuna göre değişiyorsa bu davranış da açıklanmalıdır.

Örneğin pompa çalışırken tank seviyesinin artması veya ısıtıcı çalışırken sıcaklığın yükselmesi gibi ilişkiler belirtilmelidir.

### 11.8. Sistem Kontrollerinin Açıklanması

Kullanıcının kontrol edebildiği cihazlar ve butonlar açıklanmalıdır.

Örneğin;

- pompa başlatma/durdurma,
- vana açma/kapatma,
- ısıtıcı açma/kapatma,
- sistemi başlatma/durdurma,
- alarm sıfırlama

işlemlerinin program içerisinde nasıl gerçekleştirildiği açıklanmalıdır.

Kullanılan önemli kod parçaları bu bölümde gösterilebilir.

### 11.9. Alarm Mekanizması

Alarm koşullarının nasıl oluşturulduğu ve alarm gerçekleştiğinde arayüzde hangi değişikliklerin meydana geldiği açıklanmalıdır.

Örneğin;

- hangi değerlerin alarm oluşturduğu,
- alarm sınırlarının nasıl belirlendiği,
- hangi `if / else` koşullarının kullanıldığı,
- alarm sırasında Label, Panel veya diğer bileşenlerin renginin nasıl değiştirildiği,
- alarm mesajının nasıl gösterildiği

açıklanabilir.

### 11.10. Programın Çalıştırılması ve Test Edilmesi

Programın farklı durumlarda nasıl davrandığı gösterilmelidir.

Örneğin;

- sistem ilk açıldığında,
- pompa çalıştırıldığında,
- vana açıldığında veya kapatıldığında,
- sıcaklık yükseldiğinde,
- tank dolduğunda,
- alarm oluştuğunda,
- alarm ortadan kalktığında

programın verdiği tepkiler ekran görüntüleriyle gösterilebilir.

Her ekran görüntüsünün altında ilgili durumun ne olduğunu açıklayan bir şekil açıklaması bulunmalıdır.

### 11.11. Programın Son Hali

Hazırlanan SCADA uygulamasının son hali bu bölümde gösterilmelidir.

Programın ana ekranının okunabilir bir ekran görüntüsü verilerek;

- görüntülenen sensörler,
- kontrol edilen cihazlar,
- kontrol butonları,
- göstergeler,
- alarm alanları

kısaca açıklanmalıdır.

### 11.12. Sonuç

Raporda proje sonunda;

- nelerin gerçekleştirildiği,
- programın hangi işlevleri yerine getirdiği,
- hangi C# konularının kullanıldığı,
- karşılaşılan temel problemler,
- bu problemlerin nasıl çözüldüğü,
- proje sonucunda elde edilen kazanımlar

kısaca değerlendirilmelidir.

## 12. Aşama 2 – Sunum

Hazırlanan program sınıfta çalıştırılarak sunulacaktır.

Sunum sırasında;

- sistemin hangi tesisi veya prosesi temsil ettiği,
- kullanılan cihazların ne işe yaradığı,
- sensör değerlerinin nasıl oluşturulduğu,
- Timer'ın nasıl çalıştığı,
- kullanılan butonların görevleri,
- alarm mekanizmasının nasıl oluşturulduğu,
- kullanılan önemli C# kodları

açıklanacaktır.

Sunum yalnızca programın çalıştırılıp gösterilmesinden oluşmamalıdır. Öğrencinin **programın nasıl geliştirildiğini ve yazdığı kodların ne yaptığını açıklayabilmesi** gerekmektedir.

Sunum sırasında öğrencilere kodlama ve arayüz tasarımıyla ilgili sorular sorulacaktır.

Öğrenci, projesinde bulunan herhangi bir kod parçasının ne amaçla kullanıldığını açıklayabilmelidir.

## 13. Yapay Zekâ Kullanımı

Projenin hazırlanması sırasında ChatGPT, DeepSeek, Gemini veya benzeri yapay zekâ araçları kullanılabilir.

Ancak öğrenciler, yapay zekâ araçlarının ürettiği kodların;

- ne amaçla yazıldığını,
- kullanılan değişkenlerin ne işe yaradığını,
- hangi olayın hangi kodu çalıştırdığını,
- kullanılan koşulların neyi kontrol ettiğini,
- kod üzerinde yapılacak temel değişikliklerin programın davranışını nasıl etkileyeceğini

açıklayabilmelidir.

Yapay zekâ tarafından üretilmiş olsa dahi öğrencinin açıklayamadığı kodların kullanılması uygun değildir.

## 14. Teslim Edilecek Dosyalar

Proje kapsamında **iki ayrı dosya** yüklenmelidir:

1. **Proje raporu**
2. **Visual Studio proje dosyalarının sıkıştırılmış hali**

### 14.1. Proje Raporu

Hazırlanan rapor tek bir dosya halinde teslim edilmelidir.

Rapor içerisinde;

- kapak sayfası,
- proje açıklamaları,
- geliştirme aşamalarına ait ekran görüntüleri,
- kullanılan önemli kod parçaları,
- programın çalışma mantığının açıklaması,
- test ekran görüntüleri,
- sonuç bölümü

bulunmalıdır.

Raporun düzenli, okunabilir ve bütün şekillerin açıklamalarının görülebilir olması gerekmektedir.

### 14.2. Visual Studio Projesi

Visual Studio ile oluşturulan projenin tamamı `.zip` veya `.rar` formatında sıkıştırılarak yüklenmelidir.

Sıkıştırılmış dosya içerisinde projenin tekrar Visual Studio ile açılabilmesini sağlayacak gerekli dosyalar bulunmalıdır.

Özellikle;

- `.sln` çözüm dosyası,
- proje dosyası,
- `.cs` kaynak kodları,
- Form dosyaları,
- kullanılan gerekli görseller ve diğer proje kaynakları

dosyada bulunmalıdır.

Yalnızca programın çalıştırılabilir `.exe` dosyasının teslim edilmesi yeterli değildir.

Dosya boyutunu azaltmak amacıyla ihtiyaç duyulmayan `bin`, `obj` ve `.vs` klasörleri sıkıştırılmış proje dosyasından çıkarılabilir. Ancak proje Visual Studio içerisinde açıldığında tekrar derlenebilir ve çalıştırılabilir durumda olmalıdır.

## 15. Dosya Boyutu ve Ekran Görüntüleri

Sisteme yüklenecek **her bir dosyanın maksimum boyutu 10 MB** olmalıdır.

Özellikle rapora çok sayıda yüksek çözünürlüklü ekran görüntüsü eklenmesi dosya boyutunun gereksiz şekilde büyümesine neden olabilir.

Rapor dosyasının boyutu 10 MB sınırını aşıyorsa;

- ekran görüntülerinin çözünürlükleri düşürülebilir,
- görseller kırpılarak yalnızca gerekli alanlar bırakılabilir,
- PNG yerine uygun durumlarda daha düşük dosya boyutuna sahip görsel biçimleri kullanılabilir,
- Word veya benzeri programların **resimleri sıkıştırma** özelliklerinden yararlanılabilir,
- gereksiz veya birbirinin aynı ekran görüntüleri kaldırılabilir.

Görsellerin dosya boyutu azaltılırken üzerlerindeki yazıların, kodların ve arayüz elemanlarının okunamayacak hale gelmemesine dikkat edilmelidir.

Visual Studio proje dosyasının boyutunu azaltmak için de derleme sırasında yeniden oluşturulabilen `bin`, `obj` ve `.vs` klasörleri sıkıştırılmadan önce kaldırılabilir.

## 16. Dosyaların Adlandırılması

Teslim edilen dosyaların kolaylıkla ayırt edilebilmesi için anlamlı şekilde adlandırılması önerilmektedir.

Örneğin:

```text
OgrenciNo_AdSoyad_SCADA_Rapor.pdf
OgrenciNo_AdSoyad_SCADA_Proje.zip
```

veya

```text
OgrenciNo_AdSoyad_SCADA_Proje.rar
```

şeklinde adlandırılabilir.

## 17. Teslim Öncesi Kontrol

Dosyalar yüklenmeden önce aşağıdaki hususlar kontrol edilmelidir:

- rapor dosyası açılıyor mu,
- rapordaki ekran görüntüleri okunabiliyor mu,
- raporda kullanılan şekillerin açıklamaları bulunuyor mu,
- önemli kod parçaları açıklanmış mı,
- programın ne yaptığı açıkça ifade edilmiş mi,
- Visual Studio proje dosyası `.zip` veya `.rar` olarak hazırlanmış mı,
- sıkıştırılmış proje içerisinde kaynak kodları bulunuyor mu,
- proje farklı bir klasöre çıkarıldığında Visual Studio ile açılabiliyor mu,
- proje derlenip çalıştırılabiliyor mu,
- her iki dosya da 10 MB dosya boyutu sınırına uygun mu,
- rapor ve proje dosyası olmak üzere toplam iki dosya yüklenmiş mi.

## 18. Genel Beklenti

Bu projede amaç profesyonel bir endüstriyel SCADA yazılımı geliştirmek değildir.

Temel amaç, gerçek bir endüstriyel otomasyon problemini örnek alarak **C# Windows Forms, görsel programlama ve temel programlama yapılarını birlikte kullanabilmektir.**

Proje tamamlandığında öğrencinin;

**“Bir endüstriyel sistemden gelen verileri nasıl ekranda gösterebilirim, bu değerleri nasıl güncelleyebilirim, bir cihazın durumunu nasıl görselleştirebilirim ve kullanıcıya basit kontrol imkânları nasıl sağlayabilirim?”**

sorularına uygulamalı olarak cevap verebilmesi beklenmektedir.