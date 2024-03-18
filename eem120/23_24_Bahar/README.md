# EEM-120 Algoritma ve Programlama II Dersi

<!-- ### [Duyurular](#duyurular) |  [Laboratuvar](#Laboratuvar) |  [Dersler](#dersler) | [Kaynaklar](#kaynaklar) |  [Programlar](#programlar)

### Duyurular
- Online dersin son saatinde lab çalışması yapılacaktır. Lab çalışması yapmak isteyenlerin ekran paylaşımı yapabilmek için Adobe Connect programını kurması gerekmektedir.

### Laboratuvar


- Lab 1 çalışması için [tıklayınız](./lab/01.md).
- Lab 2 çalışması için [tıklayınız](./lab/02.md).
- Lab 3 çalışması için [tıklayınız](./lab/03.md).
- Lab 4 çalışması için [tıklayınız](./lab/04.md). -->

 


### Dersler

- [Konu 1](./dersler/01.md): Özyineli (Recursive) fonksiyonlar
- [Konu 2](./dersler/02.md): Local, static ve global değişkenler
- [Konu 3](./dersler/03.md): İşaretçiler
- [Konu 4](./dersler/04.md): İşaretçi aritmetiği
- [Konu 5](./dersler/05.md): Karakter dizileri

<!-- 
-  [Konu 3](./dersler/02.md): String (karakter dizisi)
- [Konu 4](./dersler/03.md): Struct (yapılar)
- [Konu 5](./dersler/04.md): Bit düzey (bitwise) operatörler
- [Konu 6](./dersler/05.md): Dosya okuma ve dosyaya yazma işlemleri
- [Konu 7](./dersler/06.md): Dinamik Bellek Tahsisi
- [Konu 8](./dersler/07.md): Makrolar -->



### Ödev/Lab çalışmaları

- Çalışma 4:




- Çalışma 3:

`int sicaklik[7][24]` dizisine 7 gün her saatin sıcaklık bilgisi girilmiştir.

Tüm sıcaklıkları işaretçi ve döngü kullanarak ekrana yazdırın.

Tüm sıcaklıkları satırlar günü sütunlar saati gösterecek şekilde işaretçi kullanarak ekrana yazdırın.

Kullanıcıdan gün ve saat bilgisini isteyerek sıcaklık bilgisini ekrana yazdırın. (1 boyutlu işaretçi kullanın.)

En yüksek sıcaklık olan gün ve saat bilgisi için 
`void en_yuksek(int *p, int boyut, int *gun, int *saat)`
fonksiyonunu yazın, programda kullanın.

Aşağıdaki kodlamadan devam edebilirsiniz.

```C
#include <stdio.h>
#include <stdlib.h>
int main() {
  int sicaklik[7][24],i,j;
  srand(100);  
  for(i = 0; i < 7; i++){
    for(j = 0; j < 24; j++) {
      sicaklik[i][j] = rand() % 40;
    }
  }
  return 0;
}
```

- Çalışma 2: İki ürünün satışlarını kontrol etmek için `satis1` ve `satis2` fonksiyonlari yazılacaktır. Bu fonksiyonlara satış adedi ve satış miktarı parametre olarak girilecektir. Bu fonksiyonlardan  satis 1 fonksiyonu çağırıldı ise ürün 1'in satis2 fonksiyonu çağırıldı ise ve ürün 2'nin toplam satış adetleri ve toplam satış sonrası elde edilen gelir ekrana yazdırılacaktır. Bu işlemler için `statik` değişkenler kullanınız. Ayrıca yine her bir fonksiyon çağırıldığında toplam satış adedi ve toplam gelir yazıdırılacaktır. Bu işlem için ise `global` değişkenler kullanınız.


- Çalışma 1: Ekrana n defa merhaba yazdıran `void yazdir(int n)` fonksiyonunu döngü kullanmadan tasarlayınız. Ana programda çağırarak programı çalıştırınız.

<!-- 
### Kaynaklar -->

<!-- #### Kitaplar -->
<!-- Hiperkitap ve Turcademy sitelerine üniversitemiz üye olduğundan bu sitedeki kitaplara ücretsiz ulaşabilirsiniz.   
Kampus dışı erişim ayarları için [tıklayınız](https://bidb.isparta.edu.tr/tr/servisler/kampus-disi-erisim-6932s.html).
- [Her yönüyle C,  Tevfik Kızılören](https://www.hiperkitap.com/her-yonuyle-c)
- [Algoritma Tasarlama Ve C İle Temel Bilgisayar Programlama, Atakan Abuşoğlu](https://www.turcademy.com/tr/kitap/algoritma-tasarlama-ve-c-ile-temel-bilgisayar-programlama-9786053279099)
- [C İle Programlama, Deitel ve Deitel](https://www.turcademy.com/tr/kitap/c-ile-programlama-9786053556237) -->


<!-- #### İnternet -->


### Programlar
- [Dev-C++ (Orwell)](https://sourceforge.net/projects/orwelldevcpp/)





