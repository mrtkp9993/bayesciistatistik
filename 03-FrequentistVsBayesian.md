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


1. Frekanscı yaklaşım

   İşaretin konumu için bir tahmin yapmamız gerekir. İşaretin konumunu Alice'in lehine sonuçlanan atış sayısı ![0301](imgs/03_01.svg) ile belirlersek, ![0301](imgs/03_01.svg) parametresinin maksimum olabilirlik tahmini

![0302](imgs/03_02.svg)

   olur. Bunu ve binom dağılımını kullanırsak (Binom dağılımı, başarı olasılığı p, başarısızlık olasılığı 1-p olmak üzere, N denemede n tane başarı elde etme olasılığını verir),

![0303](imgs/03_03.svg)

   olarak bulunur. Yani Bob'un bu oyunda kazanma olasılığı %5'dir.

2. Bayesci yaklaşım

# Kaynaklar

* https://github.com/mrtkp9993/Bayesian-Inference
* https://www.youtube.com/watch?v=KhAUfqhLakw
* http://mathworld.wolfram.com/BinomialDistribution.html