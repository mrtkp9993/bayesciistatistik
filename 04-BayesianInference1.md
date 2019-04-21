---
title: Adım Adım Bayesci Çıkarım 1 - Önsel Dağılımlar
---

[Frekanscı ve Bayesci İstatistiğin Karşılaştırılması](03-FrequentistVsBayesian.md) örneğinde görüleceği üzere Bayesci çıkarım 3 adımdan oluşur (Gelman ve diğerleri, 2013):

1. **Modelin olasılık dağılımları ile belirlenmesi**: Parametreler, veri ve olabilirlik için uygun dağılımlar seçilmelidir.
2. **Sonsal dağılımın hesaplanması**: Bayes teoremi ile sonsal dağılım hesaplanır.
3. **Modelin kontrol edilmesi**: Model veriye uyuyor mu, varsayımlarımız kabul edilebilir mi kontrol edilir.

İlk olarak önsel dağılımların nasıl seçileceğine bakalım.

Önsel dağılımlar içerdikleri bilgi seviyelerine göre 3 seviyede incelenebilir:

* **Bilgi içermeyen önsel dalığımlar (Noninformative prior distributions)**: Bir değişken hakkında çok az veya genel bir bilgi içerir, "Değişken pozitiftir", "Değişken belirli bir sayıdan daha küçüktür" gibi.
* **Tam bilgi içeren önsel dağılımlar (Highly Informative Prior Distributions)**: Bir parametre hakkındaki önbilgimizi içerir, örneğin, bir parametrenin ortalaması 8, standart sapması 3 olan bir normal dağılımdan geldiğini biliyorsak,önsel dağılım olarak ```N(8,3)``` seçebiliriz.
* **Az bilgi içeren önsel dağılımlar (Weakly Informative Prior Distributions)**: Parametrenin aldığı değerlerden daha geniş bir aralıkta değer almasına izin verir.

Bunların dışında sık karşılaşılan başka bir terimde **eşlenik dağılımlardır**. Bayesci çıkarım integral hesabı gerektirdiğinden ve analitik olarak çözümü bulunmayan integraller yüksek hesaplama gücü gerektirdiğinden, bilgisayarların yeterli işlem gücü olmadığı uzun yıllar boyunca eşlenik dağılımlar kullanılmıştır. Eşlenik dağılımların bir listesine [bu linkten](https://www.wikiwand.com/en/Conjugate_prior) ulaşılabilir. Örneğin, önsel dağılım olarak Beta dağılımı, olabilirlik olarak da Bernoulli seçildiğinde, sonsal dağılım da Beta dağılımı olmaktadır, yani sonsal dağılım herhangi bir nümerik hesaplama gerektirmeden analitik olarak bulunabilmektedir. 

# Kaynaklar

* https://github.com/fonnesbeck/bayes_tutorial_2019/blob/master/notebooks/2-Bayesian_Computation.ipynb
* https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations
* http://www.stat.columbia.edu/~gelman/research/published/p039-_o.pdf