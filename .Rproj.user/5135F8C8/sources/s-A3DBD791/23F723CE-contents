# ggplot2 visualizations of bicycle data in Stavanger Kommune 2016-2020
# loading library packages
library(ggplot2)
library(tidyverse)
library(Hmisc)
library(car)

# merge dataset
dataset <-
  list.files(pattern = "*.csv") %>%
  map_df(~read_csv(., col_types = cols(Station_id = col_double())))

# scatter plots
ggplot(data = dataset, 
       mapping = aes(x = Date,
                     y = Count)) +
  geom_point()

ggplot(data = dataset, 
       mapping = aes(x = Average_Temperature,
                     y = Count)) +
  geom_point()

ggplot(data = dataset, 
       mapping = aes(x = Average_Speed,
                     y = Count)) +
  geom_point()

ggplot(data = dataset, 
       mapping = aes(x = Average_Temperature,
                     y = Average_Speed)) +
  geom_point()

# BAR
ggplot(dataset, aes(Date, Count)) +
  geom_bar(stat = "summary", fun.y = "average")

# histogram
ggplot(data = dataset, 
       mapping = aes(Date)) +
  geom_histogram() + labs(x = "Date", y = "Average_Speed")

ggplot(data = dataset, 
       mapping = aes(Average_Temperature)) +
  geom_histogram() + labs(x = "Average_Temperature", y = "Count")

ggplot(data = dataset, 
       mapping = aes(Count)) +
  geom_histogram() + labs(x = "Count", y = "Average_Speed")

ggplot(data = dataset, 
       mapping = aes(Average_Temperature)) +
  geom_histogram() + labs(x = "Average_Temperature", y = "Average_Speed")


# Qplot
qplot(sample = dataset$Count) + labs(x = "theoretical", y = "Count")
qplot(sample = dataset$Average_Temperature) + labs(x = "theoretical", y = "Average_Temperature")
qplot(sample = dataset$Average_Speed) + labs(x = "theoretical", y = "Average_Speed")

# Correlation
cor.test(dataset$Count, dataset$Average_Temperature, method = "spearman", exact = F)
cor.test(dataset$Count, dataset$Average_Speed, method = "spearman", exact = F)
cor.test(dataset$Average_Speed, dataset$Average_Temperature, method = "spearman", exact = F)

# Correlation matrix
CorrMatrix <- as.matrix(dataset[,c("Count", "Average_Temperature", "Average_Speed")])
rcorr(CorrMatrix)
 