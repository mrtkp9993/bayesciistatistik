---
title: Örnek Modeller
---

## t-Testi

### Bağımlı örneklem t-Testi

```y``` son gözlemler ve ilk gözlemler arasındaki farklar olmak üzere,

![0702](imgs/07_02.svg)

Örnek [veriseti](https://dasl.datadescription.com/datafile/freshman-15/), Stan modeli ve R kodu:

```stan
data {
  int<lower=0> N;
  vector[N] diff;
}

transformed data {
  real meanDiff;
  real sdDiff;
  real unifLo;
  real unifHi;
  real normalSigma;
  real expLambda;
  
  meanDiff = mean(diff);
  sdDiff = sd(diff);
  unifLo = sdDiff / 1000;
  unifHi = sdDiff * 1000;
  normalSigma = sdDiff * 100;
  expLambda = 1 / 29.0;
}

parameters {
  real<lower=0> nuMinusOne;
  real mu;
  real<lower=0> sigma;
}

transformed parameters {
  real<lower=0> nu;
  nu = nuMinusOne + 1;
}

model {
  sigma ~ uniform(unifLo, unifHi);
  mu ~ normal(meanDiff, normalSigma);
  nuMinusOne ~ exponential(expLambda);
  diff ~ student_t(nu, mu, sigma);
}
```

```r
library(readr)
library(rstan)
# https://dasl.datadescription.com/datafile/freshman-15/
freshman_15 <- read_delim("freshman-15.txt", 
                          "\t", escape_double = FALSE, trim_ws = TRUE)

data.list <- list(N=length(freshman_15$Initial.Weight),
                  diff=freshman_15$Terminal.Weight-freshman_15$Initial.Weight)
str(data.list)

fit <- stan(file = "Untitled.stan", data = data.list, iter = 1000, chains = 4)
print(fit)
plot(fit)

check_hmc_diagnostics(fit)
summary(fit)
traceplot(fit)
stan_diag(fit)
```

## Lojistik Regresyon

_i_ öznitelik sayısı olmak üzere,

![0701](imgs/07_01.svg)

Örnek [veriseti](https://archive.ics.uci.edu/ml/datasets/Vertebral+Column), [Stan](https://mc-stan.org/) modeli ve R kodu:

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

```r
library(rstan)

rstan_options(auto_write = TRUE)
options(mc.cores = parallel::detectCores())

standardize = function (x) {
  for(i in 1:length(colnames(x))) {
    if(class(x[,i]) == "numeric" || class(x[,i]) == "integer") {
      x[,i] <- as.vector(scale(x[,i])) 
    }
  }
  x
}

data <- read.table("column_2C.dat")

names(data)[1] <- "pelvic_incidence"
names(data)[2] <- "pelvic_tilt"
names(data)[3] <- "lumbar_lordosis_angle"
names(data)[4] <- "sacral_slope"
names(data)[5] <- "pelvic_radius"
names(data)[6] <- "grade_of_spondylolisthesis"
names(data)[7] <- "class"

data <- standardize(data)

data$class <- as.numeric(data$class)
data$class[data$class == 1] <- 1 ## abnormal
data$class[data$class == 2] <- 0 ## normal

str(data)
summary(data)

data.list <- list(N=nrow(data),
                  class_=data$class,
                  pi_=data$pelvic_incidence,
                  pt=data$pelvic_tilt,
                  lla=data$lumbar_lordosis_angle,
                  ss=data$sacral_slope,
                  pr=data$pelvic_radius,
                  grd=data$grade_of_spondylolisthesis)

str(data.list)


fit <- stan(file = "Untitled.stan", data = data.list, iter = 1000, chains = 4)

print(fit)
plot(fit)

check_hmc_diagnostics(fit)
summary(fit)
traceplot(fit)
stan_diag(fit)
```
Daha fazla örnek model için bu [link](https://github.com/mrtkp9993/Statistical-Modeling-Examples)'e bakılabilir.

# Kaynaklar
* [Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)
* [Doing Bayesian Data Analysis](https://www.elsevier.com/books/doing-bayesian-data-analysis/kruschke/978-0-12-405888-0)