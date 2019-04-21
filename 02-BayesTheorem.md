---
title: Bayes Teoremi
---

![0201](imgs/02_01.svg), ![0202](imgs/02_02.svg) örneklem uzayında ![0203](imgs/02_03.svg) tane olay olsun (![0204](imgs/02_04.svg) ve her ![0205](imgs/02_05.svg) için ![0206](imgs/02_06.svg)) ve ![0207](imgs/02_07.svg) olmak üzere ![0208](imgs/02_08.svg) aynı örneklem uzayında bir olay olsun. O halde,

![0209](imgs/02_09.svg)

dir. Yani, eğer her bir ![0210](imgs/02_10.svg) olayının olasılığını ve ![0211](imgs/02_11.svg) koşullu olasılığını biliyorsak ![0212](imgs/02_12.svg) olasılıklarını hesaplayabiliriz.

Bayes teoremini şu şekilde de yazabiliriz:

_H_ hipotez ve _D_ veri olmak üzere:

![0214](imgs/02_14.svg)

Burada:

* ![0215](imgs/02_15.svg), veriyi görmeden önce hipotezimizin doğru olma olasılığı (**prior, önsel olasılık**),
* ![0218](imgs/02_18.svg), hipotez doğru ise veriyi gözlemleme olasılığımız (**likelihood, olabilirlik**),
* ![0216](imgs/02_16.svg), tüm hipotezler gözönüne alındığında verinin olasılığı (**evidence**),
* ![0217](imgs/02_17.svg), veri gözlemlendikten sonra hipotezin doğru olma olasılığıdır (**posterior, sonsal olasılık**).

Paydadaki ifade sabit bir sayıdır ancak çoğu zaman doğrudan hesaplanamaz. Bu nedenle paydayı gözardı edersek,

![0219](imgs/02_19.svg).

Yani,

![0220](imgs/02_20.svg)

yazabiliriz.

**Örnek 1.** Bir tıbbi testin %1 yalancı pozitif oranına (birey sağlıklı iken hasta sonucu verme) ve %1 yalancı negatif oranına (birey hasta iken sağlıklı sonucu verme) sahip olduğunu varsayalım. Hastalığın karşılaşılma oranı da 0.002 olsun. Rasgele seçilen bir bireyde test pozitif sonuç verdiyse, bireyin gerçekten hasta olma olasılığı nedir?

Hipotezimizi ve verimizi aşağıdaki gibi tanımlayalım:

* Hipotez: _H: "Birey hastadır."_
* Veri: _D: "Test sonucu pozitiftir."_ 

Böylece, 

![0213](imgs/02_13.svg)

bulunur.

# Kaynaklar

- [Bayes' theorem - Wikiwand](https://www.wikiwand.com/en/Bayes%27_theorem)
- [Introduction to Bayesian Analysis, Arto Luoma](https://www.sis.uta.fi/tilasto/paattely2/BayesianAnalysis.pdf)
- [Comparison of frequentist and Bayesian inference](https://ocw.mit.edu/courses/mathematics/18-05-introduction-to-probability-and-statistics-spring-2014/readings/MIT18_05S14_Reading20.pdf)
- [Bayesian Basics](https://m-clark.github.io/bayesian-basics/a-hands-on-example.html)
