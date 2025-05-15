
# Proje 

## Proje ile ilgili genel açıklamalar

Projenin ilerleyen aşamalarında, yapmış olduğunuz çalışmayı benzer çalışmalarla kıyaslamanız, modelinizin üstün ve zayıf yönlerini ortaya koymanız ve performansı iyileştirmek amacıyla yaptığınız deneme ve iyileştirme adımlarını detaylı şekilde açıklamanız beklenmektedir. Bu süreçte kullanılan farklı yöntemlerin karşılaştırılması, yapılan parametre değişikliklerinin etkisi ve elde edilen sonuçların yorumlanması da gerekecektir. Yapılan çalışma neticesinde tam anlamı ile bir çalışmanın makalesi yazılmış olacaktır. İleride  yapılacak çalışmaları merak ediyorsanız araştırmalarınızı buna göre yapabilirsiniz.


## 4. adım

**Önemli Not: Daha önce göndermiş olduğunuz dokümanlarda ciddi anlamda eksik ve yanlışlar mevcut. Bundan dolayı çalışmanızı özenli bir şekilde yapmanız gerekiyor.**

Dokümanın güncel halini 26 Mayıs 2025 saat 08:00 son saat olmak üzere Turnitine yükleyiniz. Bu tarihten sonra yüklenen dokümanlar %50 olarak değerlendirilecektir.

4\. Adım Sonuçlar ve Tartışma bölümüdür. Daha önce hazırladığınız dokümana bu başlığı ekleyerek devam edin. Ayrıca daha önce hazırladığınız bölümlerde gerekiyorsa değişiklikler de yapabilirsiniz. Bu bölümde neler olması ve bu bölümün nasıl yazılması gerektiğini araştırdığını makaleleri okuyarak anlamanız gerekiyor.

Bu alt bölümde, modelinizi test ettikten sonra elde ettiğiniz performans ölçümlerini açıkça tablo ve grafiklerle vermeniz gerekmektedir.

Yazımda dikkat edilecekler:

- Tablo kullanarak doğruluk, hata oranı vb. metrikleri verin.
- (Varsa) Eğitim ve doğrulama kaybı  grafiklerini ekleyin.

Aşağıdaki gibi cümleler eklemeniz gerekebilir:

    Modelimiz %92 doğruluk oranına ulaşmıştır. Eğitim verisi üzerinde doğruluk %95 iken, test verisindeki doğruluk %92 olarak ölçülmüştür. Bu durum modelin aşırı öğrenme (overfitting) eğiliminde olmadığını göstermektedir.

- Literatürde incelediğiniz çalışmalarla kendi sonuçlarınızı karşılaştırın.

    Aşağıdaki Tablo 1’de benzer çalışmada kullanılan farklı algoritmaların karşılaştırması verilmiştir:
    ...

    Modelimizin doğruluk oranı literatürdeki benzer çalışmalara kıyasla yüksek bulunmuştur. Örneğin [12] numaralı çalışmada aynı veri seti üzerinde %89 doğruluk elde edilmiştir. Bizim modelimiz, LSTM mimarisi ve uyguladığımız önişleme adımları sayesinde %92 doğruluğa ulaşmıştır.

    Bununla birlikte, model bazı sınıflarda diğerlerine göre daha düşük başarı göstermiştir. Özellikle az örnek içeren sınıflarda F1-skorunun düşmesi, veri setinin dengesiz yapısından kaynaklanıyor olabilir.


Çalışmanızın hangi yönlerden sınırlı kaldığını belirtin.

    Veri setimiz sınırlı sayıda örnek içerdiğinden dolayı modelin genellenebilirliği tam olarak test edilememiştir. Ayrıca model sadece tek bir tür veri (örneğin metin) üzerinde test edilmiştir. Farklı türde veri üzerinde test edilmesi, modelin daha kapsamlı şekilde değerlendirilmesini sağlayacaktır.


- Bu kısımda, elde ettiğiniz sonuçları yorumlayarak neden bu sonuçları aldığınızı açıklayın.

- Yüksek veya düşük performansın nedenlerini düşünün.

- Veri setindeki dengesizlik, eksiklik, gürültü gibi faktörlerin etkisi olabilir mi?


Turnitin benzerlik kontrolü yapılmaktadır. Bundan dolayı metinleri kendi cümlelerinizle yazın, başka çalışmalardan doğrudan alıntı yapmayın.

Bu bölüm için aşağıdaki gibi bir şablon kullanabilirsiniz:

<pre>
4. Sonuçlar ve Tartışma

4.1. Deney Sonuçları

[Elde edilen metrikler tablo ve grafiklerle verilmelidir.]

4.2. Sonuçların Yorumlanması

[Elde edilen sonuçlar değerlendirilip, literatürle karşılaştırılmalı, yorum yapılmalı.]

4.3. Kısıtlamalar

[Çalışmanın sınırlı yönleri açıklanmalıdır.]

</pre>



## 3. adım

Bu adıma geçmeden önce 1. ve 2. adımların eksiksiz tamamlanmış olması zorunludur.
Bu kısmın başlığı "Materyal ve Yöntem"dir.

Bu adımda, proje çalışmanız için uygun veri setinin temin edilmesi, ön işleme adımlarının gerçekleştirilmesi, ardından probleminize yönelik modelin geliştirilmesi, programın yazılması ve denemelerin yapılması gerekmektedir.  Dolayısıyla model mimarisinin bu aşamada anlatılması gerekmektedir. Yaptığını işlemleri ve modelinizi anlatmak için resim ve şekiller, gerekiyorsa algoritma sözde kod veya akış diyagramı kullanılmalıdır. 
- Kullanılan veri seti ayrıntılı açıklanmalıdır. Veri seti üzerinde yapılan işlemler anlatılmaldır.
- Kullandığınız programlama dili, kütüphaneler vs. belirtilmelidir.
- Kullandığınız modeli ayrıntılı anlatmanız gerekmektedir. Gerekiyorsa çizim eklemelisiniz.

Daha önce hazırladığınız Literatür Taraması dokümanında yeni bir başlık açarak  3. adımı tamamlayınız.

Dokümanın güncel halini 11 Mayıs 2025 saat 10:00 son saat olmak üzere Turnitine yükleyiniz. Bu tarihten sonra yüklenen dokümanlar %50 olarak değerlendirilecektir.




## 2. Adım

2\. adımdaki çalışmayı yapabilmenin ön şartı 1. adımın tamamlanmış olmasıdır.

Projenin bu adımında Literatür Taraması yapılması gerekmetedir. Literatür taramasında yapacağınız proje ile ilgili "daha önce yapılan benzer çalışmalar nelerdir" sorusuna cevap vermeniz gerekiyor. En az 10 ile 15 çalışmayı araştırıp, çalışmalarda hangi veri seti kullanılmış, hangi yöntem kullanılmış ve başarı miktarı ne olmuş gibi bilgilerin tespit edilmesi ve bunların giriş gelisme sonuc yazımına uygun olacak şekilde ifade edilmesi gerekmetedir.  İlgili çalışmaları araştırmak için

- <https://tez.yok.gov.tr/UlusalTezMerkezi/>
- <https://dergipark.org.tr/tr/>
- <https://scholar.google.com/>
- <https://ieeexplore.ieee.org/Xplore/home.jsp>
- <https://www.sciencedirect.com/>
- <https://link.springer.com/>

gibi siteleri kullanabilirsiniz.

Kullandığınız kaynakları ieee referans stili ile göstermelisiniz. Lütfen kaynak gösterimi ne demektir nasıl yapılır araştırın. Kaynak yönetimi için [Zotero](https://www.zotero.org/) programını kullanabilirsiniz. Veya manuel olarak da kaynak ekleyebilirsiniz. Anlamadığınız bir şey olursa sorabilirsiniz. IEEE kaynak stili için aşağıdaki dokümanı inceleyiniz.

[IEEE Referencing Style Sheet ](files/ieee-style-guide.pdf)

Çalışmalarını grup halinde yapanlar tek bir doküman göndersinler.

Aşağıdaki şablonu kullanın.

[Literatür şablonu](files/rapor_sablon_v1.docx)

Literatür taraması makalelerde ayrı bir bölümde de verilmiş olabilir veya Giriş kısmında da  verilebilir. Özellikle kaynak olarak kullanacağınız dokümanlarda "Literatür Taraması" nasıl yapılmış inceleyin. Örnek olarak aşağıdaki makaleleri de inceleyebilirsiniz.

- [Örnek makale 1](files/ornek_makale1.pdf)
- [Örnek makale 2](files/ornek_makale2.pdf)



Hazırlamış olduğunuz dokümanı Turnitin sitesine yüklemeniz gerekiyor.
Siteye kayıt olduktan sonra   
- Sınıf numarası: 48325932
- Kayıt Anahtarı: isubu_eem272    
bilgileri ile sınıfa ulaşıp ödevinizi yükleyebilirsiniz.

Literatür taraması demek, bir makaleyi okumanız ve o çalışmada yapılanları kendi ifadelerinizle yazmanız demektir. Yoksa kopyala/yapıştır yapmanız anlamına gelmez. Turnitin sistemi kopyala/yapıştır yapılan metinleri göstermektedir. Ayrıca yapay zeka ile üretilen yazıları da göstermektedir. Turnitin sisteminden alınan raporlar çalışmanızın notlandırılmasında kullanılacaktır. Bundan dolayı çalışmanızı özenli bir şekilde yapın lütfen.

Bu çalışmanın tüm proje notuna katkısı %20'dir.

Son tarih 2 Mayıs 2025 08:00. Bu tarihten sonra yüklenen ödevler %50 değerlendirmesine tabi olacaktır.

Herhangi bir sorunuz olursa e-posta ile de ulaşabilirsiniz.



## 1. Adım

Projenin kabul edilmesi ve kabul edilen proje üzerine görüşme yapılarak projede yapılacakların netleştirilmesi gerekmektedir.  Bu adımı tamamlamamış olanlar Ana sayfadaki linki kullanarak proje önerisi formunu doldurabilirler.

