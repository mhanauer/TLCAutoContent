---
title: "TLC Measurement Example"
output: ''
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Library the packages that you need
```{r}
library(foreign)
library(nnet)
library(ggplot2)
library(prettyR)
library(nlme)
library(prettyR)
library(descr)
library(Amelia)
library(mitools)
library(BaylorEdPsych)
library(lavaan)
library(MissMech)
library(devtools)
install_github("iqss-research/VA-package")
install_github("iqss-research/ReadMeV1")
library(ReadMe)
```
Get the open ended items that you want to analyze.  Just pilot with stress one Stressa_1.
Need to source the csv to text files 
```{r}
autoContentTLC = Stressa_1
write.csv(autoContentTLC, "autoContentTLC.csv", row.names=FALSE)
autoContentTLC = read.csv("autoContentTLC.csv", na.strings = " ")
autoContentTLC = data.frame(Stressa_1 = na.omit(Stressa_1))
autoContentTLC
autoContentTLC$id = 1:dim(autoContentTLC)[1]
attach(autoContentTLC)
autoContentTLC = data.frame(id, Stressa_1)
setwd("C:/Users/Matthew.Hanauer/Desktop/autoContentTLC")
write.csv(autoContentTLC, "autoContentTLC.csv", row.names = FALSE)
```
Now we need to take the text and put into csv files
```{r}
source_url("https://gist.github.com/benmarwick/9266072/raw/csv2txts.R")
csv2txt("C:/Users/Matthew.Hanauer/Desktop/autoContentTLC", labels = 1)

```
Now create the filename
```{r}
x = 1
filename = data.frame(t(sample(x, dim(autoContentTLC)[1], replace = TRUE)))
filename
names(filename) <- paste0( "C:/Users/Matthew.Hanauer/Desktop/autoContentTLC/",1:ncol(filename), ".txt")
filename = t(filename)
filename = melt(filename)
filename$Var2 = NULL
filename$value = NULL
colnames(filename) = c("filename")
filename
```
Need to create the truth and training sets




