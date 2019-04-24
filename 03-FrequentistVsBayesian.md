---
title: Frekanscı ve Bayesci İstatistiğin Karşılaştırılması
---

Hangi istatistiksel yaklaşım olduğundan bağımsız olarak, herhangi bir istatistiksel çıkarım paradigması aşağıdaki şeylerle ilgilenir:

1. Öğrenmek veya test etmekle ilgilendiğimiz bazı _bilinmeyen çokluklar_ (quantity). Bunlar **parametre** olarak adlandırılır.

2. Gözlemlediğimiz ve bilgi içermesini ümit ettiğimiz bazı **veriler**.

3. Veriler ve parametreler arasında ilişki kurmamıza yardım edecek **modeller**.

Frekansçı bakış açısına göre:

* **Veriler** rasgeledir, çünkü veriler stokastik süreçlerin (random processes) bir sonucudur.
* **Model parametreleri** sabit (fixed) kabul edilir. Bir parametrenin gerçek değeri bir bilinmeyen ve sabittir.

Bayesci bakış açısına göre:

* **Veriler** sabittir. Veriler rasgele olsalar bile, bir kez gözlemlendikten sonra değişmezler.
* **Model parametreleri** rasgele olmayabilirler, ancak Bayesciler parametre değerlerindeki belirsizlikleri tanımlamak için olasılık dağılımlarını kullanırlar, ve bu nedenle parametreler rasgele olarak değerlendirilir.

**Örnek 1.** Bayesci bilardo oyunu olarak da bilinen oyun aşağıdaki gibi tanımlanır:

> Alice ve Bob bir odaya girerler. Perdenin arkasında göremedikleri bir bilardo masası vardır. Arkadaşları Carol masaya bir top atar ve nereye indiğini işaretler. Daha sonra Carol masaya toplar atmaya başlar ve, eğer bir top işaretli noktanın soluna düşerse Alice 1 puan alır, sağına düşerse Bob 1 puan alır. Carol'un yansız olduğunu varsayalım. 6 puana ilk ulaşan kişi oyunu kazanır.

İşaretin konumu, sonraki atışların sonucunu belirleme de önemli bir unsurdur. Eğer ilk atış sağa doğru düşerse, sonraki atışlar Alice'in lehine olacaktır. Tersine, ilk atış sola doğru düşerse, sonraki atışlar Bob'un lehine olacaktır.

> Bir oyunda, 8 atıştan sonra, Alice 5 ve Bob 3 puana sahip olsun. Bu oyunu Bob'un kazanma şansı nedir?

*Çözüm*

Bob'un 3 kere üst üste kazanma şansını hesaplayacağız.


* Frekanscı yaklaşım

  İşaretin konumu için bir tahmin yapmamız gerekir. İşaretin konumunu Alice'in lehine sonuçlanan atış sayısı ![0301](imgs/03_01.svg) ile belirlersek, ![0301](imgs/03_01.svg) parametresinin maksimum olabilirlik tahmini

![0302](imgs/03_02.svg)

  olur. Bunu ve binom dağılımını kullanırsak (Binom dağılımı, başarı olasılığı p, başarısızlık olasılığı 1-p olmak üzere, N denemede n tane başarı elde etme olasılığını verir),

![0303](imgs/03_03.svg)

  olarak bulunur. Yani Bob'un bu oyunda kazanma olasılığı %5'dir.

* Bayesci yaklaşım

  İlk olarak bazı tanımlamalar yapalım:

  * ![0304](imgs/03_04.svg): Bob kazanır,
  * ![0305](imgs/03_05.svg): Gözlemlenen veri, ![0306](imgs/03_06.svg),
  * ![0307](imgs/03_07.svg): Topun Alice'in tarafına düşme olasılığı

  ![0308](imgs/03_08.svg) olasılığını hesaplamak istiyoruz; yani, Alice 5, Bob 3 puana sahipken Bob'un oyunu kazanma olasılığını hesaplamak istiyoruz.

  Bu değeri hesaplamak için, ilk olarak ifadeyi koşullu olasılık tanımı ile:

  ![0310](imgs/03_10.svg) 

  şeklinde yazalım. Bayes teoremini kullanarak ![0311](imgs/03_11.svg) ifadesini yeniden yazalım:

  ![0312](imgs/03_12.svg)

  Son olarak ![0322](imgs/03_22.svg) ifadesini genişletelim:

  ![0313](imgs/03_13.svg)

  Buradaki terimleri tek tek inceleyelim:

  * ![0314](imgs/03_14.svg): Bu terim, frekanscı yaklaşımda kullandığımız olabilirlik ile aynıdır. Yani, işaretin konumu p, Alice 5 ve Bob 3 puana sahip olmak üzere, ![0315](imgs/03_15.svg) dir.
  * ![0316](imgs/03_16.svg): Bir p olasılığı için, 8 denemede 5 pozitif sonuç elde etme olasılığı nedir? Binom dağılımını kullanırsak: ![0317](imgs/03_17.svg).
  * ![0318](imgs/03_18.svg): p olasılığına ait önbilgimiz. Problem tanımından (Carol yansız), p değerinin ```[0,1]``` aralığından eşit olasılıkla geldiğini varsayabiliriz, yani ![0319](imgs/03_19.svg) olur.

  Bu değerleri yerine koyarsak,

  ![0320](imgs/03_20.svg)

  bulunur. Yukarıdaki integraller Beta fonksiyonunun özel bir halidir:

  ![0321](imgs/03_21.svg)

  Beta fonksiyonları hesaplanırsa sonuç ```0.09``` olarak bulunur. 

Frekansı ve Bayesci yaklaşımlar farklı sonuç verdi. Hangisinin doğru olduğuna nasıl karar vereceğiz?

Monte Carlo simülasyonundan daha sonra detaylı olarak bahsedeceğim. Basitçe açıklamak gerekirse; yüksek sayıda rasgele oyun üretip, kaç tanesinde Bob'un kazanacağını sayacağız. 

Simülasyon için yazılmış Python kodu kaynaklar kısmındaki 4. linkte bulunabilir. Simülasyon sonucuna bakarsak Bob'un kazanma olasılığının ```0.09``` olduğunu gözüyoruz. 

Örneğimizde frekanscı yaklaşım yanlış sonuç verdi, ancak bu frekanscı yaklaşımın yanlış olduğu anlamına gelmemektedir. Bu tip problemlerle uğraşmak için çeşitli frekanscı yöntemler mevcuttur, ancak Bayesci yaklaşım - Bayesci yaklaşımın daha zor olduğu düşünüldüğü halde - basit bir model ile daha doğru sonuç vermektedir.  

# Kaynaklar

* [Bayesci Çıkarıma Giriş](https://github.com/mrtkp9993/Bayesian-Inference)
* [Frequentism and Bayesianism: What's the Big Deal?](https://www.youtube.com/watch?v=KhAUfqhLakw)
* [Binomial Dist.](http://mathworld.wolfram.com/BinomialDistribution.html)
* [Frequentism and Bayesianism](http://jakevdp.github.io/blog/2014/06/06/frequentism-and-bayesianism-2-when-results-differ/)
* [STATISTICAL ERRORS - P values, the ‘gold standard’ of statistical validity, are not as reliable as many scientists assume.](https://www.nature.com/polopoly_fs/1.14700!/menu/main/topColumns/topLeftColumn/pdf/506150a.pdf)