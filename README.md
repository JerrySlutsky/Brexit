# Data from an Economist poll on how opinions of Brexit have changed from 2016-2018

brexit <- readr::read_csv("https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2019/2019-04-16/brexit.csv")
brexit
as.data.frame(brexit$date)
brexit$date <- format(strptime(brexit$date,"%d/%m/%y"),"%m/%Y")

summ <- brexit %>% 
  gather(key=decision,value=response
         , percent_responding_right:percent_responding_wrong) %>% # One y variable

# Stacked barplot with multiple groups
ggplot(data=summ, aes(x=summ$date, y=summ$response, fill=summ$decision)) +
  geom_bar(stat="identity", position = "stack")

![Brexit figure](https://user-images.githubusercontent.com/48695787/56917559-ca621480-6a89-11e9-8db4-b89d69a4e88c.png)
