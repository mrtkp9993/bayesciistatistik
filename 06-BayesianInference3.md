---
title: Adım Adım Bayesci Çıkarım 3 - Model için Tanı Testleri ve Modellerin Karşılaştırılması
---

## Tanı Testleri

Sonsal dağılımı hesapladıktan sonra MCMC algoritmalarının yapısı gereği bazı tanı testleri yapmamız gerekir:

*  MCMC ile ![0618](imgs/06_18.svg) tane örneklem çektiğimizi varsayalım, ![0623](imgs/06_23.svg). Örneklemimizi iki ayrı parçaya bölelim: ![0619](imgs/06_19.svg) ve ![0620](imgs/06_20.svg). Bu iki grubun ortalamalarını hesaplayalım:

![0621](imgs/06_21.svg)

![0622](imgs/06_22.svg) 

Bu iki ortalama birbirlerinden anlamlı derecede farklı ise, örneklemimiz problemlidir.

* MCMC algoritması birden çok zincir ile çalıştırılır ve farklı örneklemler elde edilir. Farklı zincirlerde aynı sonuçları elde etmemizi bekleriz. Bu nedenle zincirler arasında anlamlı fark olup olmadığını test ederiz.

* Yine ![0618](imgs/06_18.svg) tane örneklem çektiğimizi düşünelim ve aşağıdaki üç grafiği inceleyelim:

![0624](imgs/06_24.png)

İlk grafikte herhangi bir anomali görünmemektedir. 

İkinci grafikte, yaklaşık ilk 1500 örneklem, geri kalanlardan daha farklı görünmektedir. Büyük ihtimalle, başlangıç dağılımı, hedef dağılımdan oldukça farklıdır ancak zincir hedef dağılıma yakınsamayı başarmıştır.

Üçüncü grafikte ise, örneklemler arasında ciddi bir otokorelasyon bulunmaktadır. Büyük ihtimalle efektif örneklem büyüklüğü küçük olduğu için bu problem ile karşılaşılmıştır.

* Otokorelasyon ve kısmi otokorelasyon grafikleri incelenerek örneklemlerin otokorelasyon sorunu olup olmadığı kontrol edilmelidir.

* Gelman-Rubin istatistiği hesaplanıp ```1.1```'den küçük olup olmadığı kontrol edilmelidir.

* Sonsal dağılımın şekli kontrol edilmelidir.

## Bilgi Kriterleri

![0601](imgs/06_01.svg) olmak üzere T tane modeli karşılaştırmak istediğimizi düşünelim.

### Akaike Bilgi Kriteri (AIC)

Amaç, gerçek ![0603](imgs/06_03.svg) ve tahmin edilen ![0602](imgs/06_02.svg) arasındaki Kullback-Leibler ıraksamasını minimum yapmaktır:

![0607](imgs/06_07.svg)

Burada, ![0608](imgs/06_08.svg) bir sabit olduğundan,

![0609](imgs/06_09.svg)

ifadesini maksimize etmek yeterli olacaktır. Akaike'ye göre en iyi model, maksimum ![0610](imgs/06_10.svg) değerini verir. Monte Carlo integrasyonu ile ![0611](imgs/06_11.svg) integralini hesaplarsak,

![0612](imgs/06_12.svg)

Bu da bize ![0604](imgs/06_04.svg) tahmini için log-benzerlik ![0613](imgs/06_13.svg) değerini verir. Akaike, ![0614](imgs/06_14.svg) değerinin ![0615](imgs/06_15.svg) değerini modelin karmaşıklığına (![0606](imgs/06_06.svg): modeldeki parametre sayısı) bağlı olarak aşırı tahmin ettiğini göstermiştir:

![0616](imgs/06_16.svg)

ve aşağıdaki kriteri önermiştir:

![0617](imgs/06_17.svg)

Akaike bilgi kriteri, doğrusal regresyon, genelleştirilmiş doğrusal modeller, otoregresif modeller için uygun olsa da, derin sinir ağlar, mixture modeller için uygun değildir.

## Watanabe–Akaike information criterion

Akaike bilgi kriterinin singüler istatistiksel modeller için genelleştirilmiş halidir ve Akaike bilgi kriterinin Bayesci versiyonudur. 

# Kaynaklar
* [Model Checking and Selection](https://hciweb.iwr.uni-heidelberg.de/sites/default/files/profiles/mkandemi/files/lecture6_0.pdf)
* [WAIC Experiments](http://watanabe-www.math.dis.titech.ac.jp/users/swatanab/dicwaic.html)
* [A Widely Applicable Bayesian Information Criterion](http://www.jmlr.org/papers/volume14/watanabe13a/watanabe13a.pdf)
* [MCMC Diagnostics](https://www.statlect.com/fundamentals-of-statistics/Markov-Chain-Monte-Carlo-diagnostics)