# Data-Rep
Project 
---
title: "Data replaiction"
author: "Janna M"
date: "3/30/2021"
output:
  html_document: default
  pdf_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Including Plots

You can also embed plots, for example:

```{r pressure, echo=FALSE}
plot(pressure)
```
The data files were separated. In the original code they were apart of one txt file.
I decided to load the separate files. 

For this reason i had to assign sex and bind_rows to combine them 
The rest of the code allowed me to generate a file.

I do not understand how 26 rows are missing. 

Some of the data is missing , therefore i did not accomplish the task of generating  graph just like theirs. 

In the future attaching the original data files would be helpful. However the code is sufficient enough to attempt to replicate this anaysis using my own data. 

```{r}
FemaleBeetle <- read.table("C://Documents and Settings/JSG-BS05V2/Desktop/Class/Beetle_data_exploratory.txt/femaledata.txt")

MaleBeetle <- read.table("C://Documents and Settings/JSG-BS05V2/Desktop/Class/Beetle_data_exploratory.txt/maledata.txt")
FemaleBeetle$Sex <- "female"
MaleBeetle$Sex <- "male"
library(dplyr)

Beetle<- bind_rows(FemaleBeetle,MaleBeetle)
# dowloding this data set was diffulut and i was having troble locting it
library(ggplot2)

library(scales)

p1 <- ggplot(data = Beetle, aes(x = Elytra, y = lnProt, shape = Sex,
colour = Sex))
p1 <- p1 + geom_point() + scale_shape_manual(values = c(16, 17)) +
scale_color_manual(values = c("darkred", "steelblue")) +
theme_bw()
p1 <- p1 + xlab("Elytra (mm)") + ylab("Pronotum length (mm)")
p1
```
