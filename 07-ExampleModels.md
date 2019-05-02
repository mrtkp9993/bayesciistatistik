---
title: Örnek Modeller
---

## Lojistik Regresyon

_i_ öznitelik sayısı olmak üzere,

![0701](imgs/07_01.svg)

Örnek [Stan](https://mc-stan.org/) modeli:

```stan
data {
  int<lower=0> N;
  int<lower=0,upper=1> class_[N];
  vector[N] pi_;
  vector[N] pt;
  vector[N] lla;
  vector[N] ss;
  vector[N] pr;
  vector[N] grd;
}

parameters {
  real nu;
  real s;
  real a;
  real b_pi;
  real b_pt;
  real b_lla;
  real b_ss;
  real b_pr;
  real b_grd;
}

model {
  nu ~ gamma(2,0.1);
  s ~ normal(0, 10);
  a ~ student_t(nu,0,s);
  b_pi ~ student_t(nu,0,s);
  b_pt ~ student_t(nu,0,s);
  b_lla ~ student_t(nu,0,s);
  b_ss ~ student_t(nu,0,s);
  b_pr ~ student_t(nu,0,s);
  b_grd ~ student_t(nu,0,s);
  class_ ~ bernoulli_logit(inv_logit(a + b_pi * pi_ + b_pt * pt + b_lla * lla + b_ss * ss + b_pr * pr + b_grd * grd));
}
```

# Kaynaklar
* [Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)