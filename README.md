# Introduction

This is my work from the Google Code-In

# Required

- R
- RStudio

# Code Description

```
# Task 2

library(dplyr)

# Reading E Commerce Data
e_commerce= read.csv("https://raw.githubusercontent.com/FahroziFahrozi/Google-Code-In-Task/master/Task%20Dataset.csv", header = TRUE)

# How many observation and variables are in the data set?
nrow (e_commerce)
#1593

ncol(e_commerce)
#45

# Which city had the most visitors and how many? Among Australia cities.
subset_Australia=subset(e_commerce, e_commerce$country=="Australia")
subset_Australia%>%
  group_by(city)%>%
  summarise(behavNumVisits= sum(behavNumVisits)) %>% arrange(desc(behavNumVisits))
# "Brisbane"                    10

# Draw a horizontal box plot for the number of site visits.
boxplot(e_commerce$behavNumVisits, horizontal=TRUE)

# Solve the previous problem for the city with the most visitors, using the which.max function.
citywithmostvisitors=e_commerce%>%
  group_by(city)%>%
  summarise(behavNumVisits= sum(behavNumVisits))

maxcity = which.max(citywithmostvisitors$behavNumVisits)
citywithmostvisitors [maxcity,]
# Lakewood            104

# What is the mean-median difference for number of site visits?
meanx = mean(e_commerce$behavNumVisits)
medianx = median(e_commerce$behavNumVisits)
meanx-medianx
# 0.7715003

# What is the mean-median difference for site visits, after excluding the person who had the most visits?
max_index=which.max(e_commerce$behavNumVisits)
e_commerce_exclude=e_commerce[-c(max_index),]
meanx_exclude = mean(e_commerce_exclude$behavNumVisits)
medianx_exclude = median(e_commerce_exclude$behavNumVisits)
meanx_exclude-medianx_exclude
# 0.7091709
```
# Screen Cast
![Record](http://g.recordit.co/BRuaL5MZVm.gif)

# Authors

- Mridul
