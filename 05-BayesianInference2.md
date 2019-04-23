---
title: Adım Adım Bayesci Çıkarım 2 - Sonsal Dağılımın Hesaplanması
---

Bir çok modelde birden fazla parametre olacaktır. Dolayısıyla parametreler,  ![0501](imgs/05_01.svg) şeklinde bir vektör olacaktır. Bu durumda sonsal dağılım, ![0502](imgs/05_02.svg) çok değişkenli bir olasılık dağılımı olacaktır. Bu durumda, örneğin, ![0503](imgs/05_03.svg) parametresini tahmin etmek istediğimizde 

![0504](imgs/05_04.svg)

integralini hesaplamalıyız. Çoğu durumda bu integralin analitik olarak bir çözümü bulunamadığından nümerik yöntemlere başvurmalıyız.

## Monte Carlo İntegrasyonu

![0505](imgs/05_05.svg)

integralini hesaplamak istediğimizi düşünelim. Eğer ![0506](imgs/05_06.svg), polinom fonksiyon ya da trigonometrik fonksiyon gibi `kolay` bir fonksiyon ise, integralin kapalı form çözümünü bulmak kolaydır. Ancak ![0506](imgs/05_06.svg) daha komplike bir fonksiyon ise integralin kapalı form çözümü olmayabilir. Bu durumda integrali nümerik olarak hesaplayabilmek için çeşitli yöntemler bulunmaktadır. Monte Carlo integrasyonu bunlardan biridir.

İlk olarak

![0508](imgs/05_08.svg)

yazalım. Burada ![0509](imgs/05_09.svg) ve ![0510](imgs/05_10.svg)'dır. Burada ![0511](imgs/05_11.svg), ![0512](imgs/05_12.svg) aralığında düzgün dağılan bir olasılık yoğunluk fonksiyonudur. Bundan dolayı ![0514](imgs/05_14.svg) olmak üzere

![0513](imgs/05_13.svg)

olur. Eğer ![0515](imgs/05_15.svg) sayılarını üretirsek, Büyük Sayılar Kanunu nedeniyle

![0516](imgs/05_16.svg)

olur. Ayrıca ![0519](imgs/05_19.svg) ve ![0518](imgs/05_18.svg) olmak üzere standart hatayı

![0517](imgs/05_17.svg)

ile hesaplayabiliriz. Integralin ![0520](imgs/05_20.svg) güven aralığı ise ![0521](imgs/05_21.svg) ile hesaplanabilir.

Böylece en basit Monte Carlo integrasyonunu gördük. Importance sampling, Gibbs sampling, Hamiltonian Monte Carlo (HMC) gibi daha komplike ve modern yöntemler de mevcuttur. 

# Kaynaklar

* [Bayesian Inference Lecture Notes 14](http://www.stat.cmu.edu/~larry/=stat705/Lecture14.pdf)
* [Chapter 14 - Simulation](http://www.stat.cmu.edu/~larry/=stat700/MCMC.pdf)