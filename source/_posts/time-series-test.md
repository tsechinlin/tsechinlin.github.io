---
title: Time Series Plot
date: 2019-11-12 00:37:38
tags:
---

用于测试插入图片。

<!--more-->

```R
library(astsa)
library(tidyverse)
library(gridExtra)
library(reshape2)
```

## Time Series Plot

**Basic Plot**

``` r
# data
df.chicken <- data.frame(chicken, time = time(chicken))
```

``` r
ggplot(df.chicken) +
  geom_line(aes(time, chicken)) +
  scale_x_continuous() +
  scale_y_continuous() +
  theme_minimal()
```

![](unnamed-chunk-4-1.svg)<!-- -->

``` r
ggplot(df.chicken, aes(time, chicken)) + 
  geom_area(color = "#00AFBB", fill = "#00AFBB", alpha = 0.5) +
  scale_x_continuous() +
  scale_y_continuous() +
  theme_minimal()
```

![](unnamed-chunk-5-1.svg)<!-- -->

**Multiple Series Plot**

``` r
# data
df.economics <- economics %>%
  select(date, psavert, uempmed) %>% 
  gather(key = "variable", value = "value", -date)
```

``` r
ggplot(df.economics, aes(x = date, y = value)) + 
  geom_line(aes(color = variable), size = 1) +
  scale_color_manual(values = c("#00AFBB", "#E7B800")) +
  theme_bw()
```

![](unnamed-chunk-7-1.svg)<!-- -->

``` r
ggplot(df.economics, aes(x = date, y = value)) + 
  geom_area(aes(color = variable, fill = variable), alpha = 0.5, position = position_dodge(0.8)) +
  scale_color_manual(values = c("#00AFBB", "#E7B800")) +
  scale_fill_manual(values = c("#00AFBB", "#E7B800")) +
  theme_minimal()
```

![](unnamed-chunk-8-1.svg)<!-- -->

## Autocorrelation Plot

``` r
# -------------------------------------------------------------
# ts: time series
# lag.max: maximum of lag
# conf.level: level of the confidence interval for the variance
# -------------------------------------------------------------
gg.acf <- function(ts, lag.max = 24, conf.level = 0.95) {
  list.acf <- acf(as.numeric(ts), lag.max = lag.max, 
                  type = "correlation", plot = FALSE)
  N <- as.numeric(list.acf$n.used)
  df <- with(list.acf, data.frame(lag, acf))
  plot.acf <- ggplot(data = df, aes(x = lag, y = acf)) +
    geom_area(aes(x = lag, y = qnorm((1+conf.level)/2)/sqrt(N)), fill = "#B9CFE7") +
    geom_area(aes(x = lag, y = -qnorm((1+conf.level)/2)/sqrt(N)), fill = "#B9CFE7") +
    geom_col(fill = "#4373B6", width = 0.7) +
    geom_hline(yintercept = 0, color = "black", size = 0.3) +
    scale_x_continuous(breaks = seq(0, max(df$lag), 6)) +
    ggtitle("ACF") +
    theme_minimal()
  return(plot.acf)
}
```

``` r
gg.acf(diff(gtemp), lag.max = 48)
```

![](unnamed-chunk-10-1.svg)<!-- -->

## Multipile Autocorrelation Plot

``` r
# -------------------------------------------------------------
# ts.list: list of serval time series
# lag.max: maximum of lag
# conf.level: level of the confidence interval for the variance
# -------------------------------------------------------------
gg.acf.facet <- function(ts.list, lag.max = 24, conf.level = 0.95) {
  list.acf <- lapply(ts.list, function(ts) {
    acf(as.numeric(ts), lag.max = lag.max, 
        type = "correlation", plot = FALSE)
  })
  N <- as.numeric(list.acf[[1]]$n.used)
  df <- data.frame(sapply(list.acf, function(l) {l$acf}), list.acf[[1]]$lag)
  colnames(df) <- c(names(ts.list), "lag")
  df.melt <- melt(df, id = "lag")
  plot.acf <- ggplot(data = df.melt, aes(x = lag, y = value)) +
    geom_area(aes(x = lag, y = qnorm((1+conf.level)/2)/sqrt(N)), fill = "#B9CFE7") +
    geom_area(aes(x = lag, y = -qnorm((1+conf.level)/2)/sqrt(N)), fill = "#B9CFE7") +
    geom_col(fill = "#4373B6", width = 0.7) +
    geom_hline(yintercept = 0, color = "black", size = 0.3) +
    scale_x_continuous(breaks = seq(0, max(df$lag), 6)) +
    facet_grid(variable ~ .) +
    ggtitle("ACF") +
    theme_bw()
  return(plot.acf)
}
```

``` r
df.gtemp <- list(gtemp = gtemp, 
                 first.diff = diff(gtemp))
gg.acf.facet(df.gtemp)
```

![](unnamed-chunk-12-1.svg)<!-- -->
