# C# Windows Forms ile SCADA Arayüzü Tasarımı  
## Proje Yönergesi

### 1. SCADA Nedir?

SCADA (*Supervisory Control and Data Acquisition – Gözetleyici Kontrol ve Veri Toplama*), endüstriyel tesislerde bulunan cihazların, sensörlerin ve makinelerin izlenmesi ve gerektiğinde kontrol edilmesi amacıyla kullanılan sistemlerin genel adıdır.

Bir SCADA sistemi aracılığıyla operatör;

- sıcaklık, basınç, seviye, debi gibi ölçüm değerlerini izleyebilir,
- pompa, motor, vana ve ısıtıcı gibi ekipmanların çalışma durumlarını görebilir,
- belirli cihazları çalıştırabilir veya durdurabilir,
- kritik durumları ve alarmları takip edebilir,
- tesisin genel çalışma durumunu grafiksel bir arayüz üzerinden gözlemleyebilir.

Gerçek SCADA sistemlerinde bilgiler PLC, sensör, mikrodenetleyici veya diğer endüstriyel cihazlardan alınmaktadır. Bu projede gerçek bir endüstriyel cihaz kullanılmayacaktır. Bunun yerine C# programı içerisinde **Timer, Random ve benzeri programlama yapıları kullanılarak gerçek sensörlerden veri geliyormuş gibi bir simülasyon oluşturulacaktır.**

Bu nedenle hazırlanacak çalışma, gerçek bir SCADA sisteminin basitleştirilmiş bir **operatör arayüzü (HMI – Human Machine Interface)** olarak düşünülebilir.

---

# 2. Projenin Amacı

Bu projenin temel amacı, öğrencilerin C# Windows Forms ortamında öğrendikleri;

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

Çalışmada yalnızca programın çalışması yeterli değildir. Hazırlanan arayüzün aynı zamanda **düzenli, anlaşılır, görsel olarak uygun ve bir operatör tarafından kolay kullanılabilir** olması beklenmektedir.

---

# 3. Uygulama Senaryosu

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

---

# 4. Arayüz Tasarımı

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
- isteğe bağlı olarak **Chart:** belirli bir sensör değerinin zaman içerisindeki değişiminin gösterilmesi.

Her bileşenin yalnızca ekranda bulunması yeterli değildir. Mümkün olduğunca sistemin işleyişinde bir görevi bulunmalıdır.

---

# 5. Simülasyonun Oluşturulması

Gerçek sensörler kullanılmayacağından sistem verileri program içerisinde üretilecektir.

Örneğin bir Timer nesnesi kullanılarak her 500 ms veya 1000 ms'de bir sensör değerleri güncellenebilir.

Rastgele değer üretmek için C# içerisindeki `Random` sınıfından yararlanılabilir.

Ancak değerlerin tamamen anlamsız ve birbirinden bağımsız şekilde değişmesi yerine mümkün olduğunca gerçek bir sistem davranışı oluşturulması önerilmektedir.

Örneğin:

- pompa çalışıyorsa tank seviyesi yavaşça artabilir,
- çıkış vanası açıksa tank seviyesi azalabilir,
- ısıtıcı çalışıyorsa sıcaklık artabilir,
- ısıtıcı kapatıldığında sıcaklık yavaşça azalabilir,
- tank seviyesi yükseldikçe belirli ölçüde basınç artabilir.

Böylece yalnızca ekrana rastgele sayı yazdıran bir program yerine **sistem davranışını taklit eden küçük bir simülasyon** oluşturulmuş olacaktır.

---

# 6. Sistem Kontrolleri

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

---

# 7. Alarm Sistemi

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

---

# 8. Görsel Tasarım

SCADA ekranı yalnızca çalışan bir program olarak değil, aynı zamanda **kullanılabilir bir kullanıcı arayüzü** olarak tasarlanmalıdır.

Bu nedenle;

- bileşenler düzenli hizalanmalı,
- çok fazla ve uyumsuz renk kullanılmamalı,
- cihaz isimleri açık bir şekilde yazılmalı,
- ölçüm değerlerinin birimleri belirtilmeli (`°C`, `bar`, `%` vb.),
- kontrol butonları anlaşılır isimlendirilmelidir,
- ekran gereksiz bilgilerle doldurulmamalıdır.

Örneğin uygulama ekranı;

**Proses Görünümü**,  
**Anlık Değerler**,  
**Cihaz Kontrolleri**,  
**Alarm Durumu**

gibi bölümlere ayrılabilir.

Tank, kazan, pompa ve borular basit geometrik şekiller kullanılarak temsil edilebilir. Profesyonel bir grafik tasarım beklenmemektedir; ancak hazırlanan ekranın bir endüstriyel kontrol panelini çağrıştırması beklenmektedir.

---

# 9. Programlama Gereksinimleri

Projede yalnızca Designer kullanılarak görsel bir ekran oluşturulması yeterli değildir. Arayüzde bulunan bileşenlerin C# kodları ile kontrol edilmesi gerekmektedir.

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

---

# 10. Projenin Aşamaları

Proje iki temel aşamadan oluşmaktadır:

## Aşama 1 – Programlama ve Sunum

Öğrenciler öncelikle C# Windows Forms kullanarak SCADA arayüzünü geliştirecektir.

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

Sunum yalnızca programın çalıştırılıp gösterilmesinden oluşmamalıdır. Öğrencinin **programın nasıl geliştirildiğini ve yazdığı kodların ne yaptığını açıklayabilmesi** beklenmektedir.

Sunum sırasında öğrencilere kodlama ve arayüz tasarımıyla ilgili sorular sorulabilir.

Örneğin;

- Timer neden kullanıldı?
- Timer'ın Interval değeri ne işe yarıyor?
- Random sınıfı hangi amaçla kullanıldı?
- Bu Button'ın Click olayında hangi işlemler gerçekleştiriliyor?
- Bu `if` koşulu kaldırılırsa ne olur?
- ProgressBar değeri hangi değişkenden geliyor?
- Alarm hangi koşul gerçekleştiğinde aktif oluyor?
- Pompa kapatıldığında sistemin davranışı nasıl değişiyor?

gibi sorular yöneltilebilir.

---

# 11. Yapay Zekâ Kullanımı

Projenin hazırlanması sırasında ChatGPT, Copilot, Gemini veya benzeri yapay zekâ araçlarının kullanılmasına izin verilmektedir.

Yapay zekâ;

- örnek kod oluşturmak,
- hata mesajlarını açıklamak,
- kodu düzenlemek,
- arayüz tasarımı konusunda fikir almak,
- kullanılabilecek C# bileşenlerini araştırmak

amacıyla kullanılabilir.

Ancak **yapay zekâ tarafından üretilen kodun doğrudan kopyalanması, kodun ne yaptığının bilinmemesi durumunda yeterli kabul edilmeyecektir.**

Öğrenci projesindeki kodların;

- ne amaçla yazıldığını,
- kullanılan değişkenlerin ne işe yaradığını,
- hangi olayın hangi kodu çalıştırdığını,
- kullanılan koşulların neyi kontrol ettiğini

açıklayabilmelidir.

Sunum sırasında projede bulunan herhangi bir kod parçası hakkında soru sorulabilir.

Yapay zekâ bir **yardımcı araç** olarak kullanılmalıdır; öğrencinin programlama bilgisi yerine geçmemelidir.

---

# 12. Aşama 2 – Proje Raporu

Projenin ikinci aşamasında ayrıntılı bir rapor hazırlanacaktır.

Rapor yalnızca projenin ekran görüntüsünü ve kaynak kodlarını içeren bir belge olmamalıdır.

Raporun, projeyi daha önce hiç hazırlamamış bir kişinin aynı uygulamayı yeniden geliştirebilmesini sağlayacak şekilde **adım adım hazırlanmış bir tutorial/eğitim dokümanı** olması beklenmektedir.

Raporda aşağıdaki konulara yer verilmelidir.

### 12.1. Projenin Tanıtımı

- SCADA'nın kısa tanımı,
- seçilen tesis veya proses,
- sistemde bulunan cihazlar,
- projenin amacı.

### 12.2. Yeni Projenin Oluşturulması

Visual Studio içerisinde;

- hangi proje türünün seçildiği,
- Windows Forms projesinin nasıl oluşturulduğu,
- Form ekranına nasıl ulaşıldığı

ekran görüntüleriyle açıklanmalıdır.

### 12.3. Kullanılan Bileşenlerin Eklenmesi

Her önemli bileşenin;

- Toolbox içerisinden nasıl bulunduğu,
- Form üzerine nasıl eklendiği,
- önemli Properties ayarlarının nasıl değiştirildiği

açıklanmalıdır.

Örneğin:

> Toolbox → Common Controls → ProgressBar seçildi.  
> ProgressBar Form üzerine sürüklendi.  
> Name özelliği `progressTankSeviye` olarak değiştirildi.  
> Minimum değeri 0, Maximum değeri 100 olarak ayarlandı.

şeklinde adım adım açıklama yapılabilir.

### 12.4. Arayüz Tasarımının Oluşturulması

Tank, pompa, kazan, vana veya diğer proses elemanlarının ekranda nasıl temsil edildiği açıklanmalıdır.

Hazırlanan arayüzün farklı geliştirme aşamalarına ait ekran görüntülerinin kullanılması önerilmektedir.

### 12.5. Kodlama

Programın önemli kod parçaları raporda gösterilmeli ve kodların altında **ne yaptıkları açıklanmalıdır.**

Örneğin yalnızca;

```csharp
temperature = random.Next(20, 101);
```

kodunu vermek yerine bu satırın sıcaklık sensörünü simüle etmek amacıyla 20–100 °C arasında rastgele bir değer ürettiği açıklanmalıdır.

### 12.6. Timer Kullanımı

- Timer bileşeninin neden kullanıldığı,
- Interval değerinin ne olduğu,
- Tick olayının nasıl oluşturulduğu,
- Tick içerisinde hangi işlemlerin yapıldığı

açıklanmalıdır.

### 12.7. Alarm Mekanizması

Alarm koşullarının nasıl oluşturulduğu ve alarm gerçekleştiğinde arayüzde hangi değişikliklerin meydana geldiği açıklanmalıdır.

### 12.8. Programın Çalıştırılması ve Test Edilmesi

Programın farklı durumlarda nasıl davrandığı gösterilmelidir.

Örneğin;

- sistem ilk açıldığında,
- pompa çalıştırıldığında,
- sıcaklık yükseldiğinde,
- tank dolduğunda,
- alarm oluştuğunda

ekran görüntüleri alınarak açıklanabilir.

### 12.9. Sonuç

Raporda proje sonunda;

- nelerin gerçekleştirildiği,
- hangi C# konularının kullanıldığı,
- karşılaşılan temel problemler,
- bu problemlerin nasıl çözüldüğü

kısaca değerlendirilmelidir.

---

# 13. Beklenen Minimum Özellikler

Hazırlanan projede en az aşağıdaki özelliklerin bulunması beklenmektedir:

- Bir endüstriyel tesis/proses senaryosu,
- birden fazla sensör değerinin görüntülenmesi,
- Timer kullanılarak değerlerin periyodik güncellenmesi,
- Random veya benzeri yöntemlerle veri simülasyonu,
- en az bir cihazın kullanıcı tarafından kontrol edilebilmesi,
- ProgressBar veya benzeri görsel bir gösterge,
- Button, Label ve giriş bileşenlerinin kullanılması,
- cihaz durumunun görsel olarak ifade edilmesi,
- en az bir alarm mekanizması,
- düzenli ve anlaşılır bir kullanıcı arayüzü.

Bunlara ek olarak isteyen öğrenciler;

- grafik çizimi,
- alarm geçmişi,
- manuel/otomatik çalışma modu,
- set değeri değiştirme,
- sensör değerlerini dosyaya kaydetme,
- çalışma süresini gösterme

gibi ek özellikler geliştirebilirler.

Ancak ek özellik sayısından daha önemli olan, **eklenen özelliklerin doğru çalışması ve öğrencinin nasıl çalıştıklarını açıklayabilmesidir.**

---

# 14. Projede Dikkat Edilecek Hususlar

Projede değerlendirme yapılırken özellikle;

- programın doğru çalışması,
- C# kodlarının anlaşılması,
- kullanılan bileşenlerin amaca uygun olması,
- arayüzün düzeni ve kullanılabilirliği,
- sistem davranışının anlamlı olması,
- alarm ve kontrol mekanizmalarının çalışması,
- kodların düzenli olması,
- sunum sırasında öğrencinin projeye hâkimiyeti,
- raporun ayrıntılı ve öğretici hazırlanması

dikkate alınacaktır.

Aynı kodların veya aynı arayüzlerin küçük değişikliklerle farklı öğrenciler tarafından teslim edilmesi uygun değildir. Her öğrencinin veya grubun kendi senaryosunu, tasarımını ve program yapısını oluşturması beklenmektedir.

---

# 15. Genel Beklenti

Bu projede amaç profesyonel bir endüstriyel SCADA yazılımı geliştirmek değildir.

Temel amaç, gerçek bir endüstriyel otomasyon problemini örnek alarak **C# Windows Forms, görsel programlama ve temel programlama yapılarını birlikte kullanabilmektir.**

Proje tamamlandığında öğrencinin;

**“Bir endüstriyel sistemden gelen verileri nasıl ekranda gösterebilirim, bu değerleri nasıl güncelleyebilirim, bir cihazın durumunu nasıl görselleştirebilirim ve kullanıcıya basit kontrol imkânları nasıl sağlayabilirim?”**

sorularına uygulamalı olarak cevap verebilmesi beklenmektedir.