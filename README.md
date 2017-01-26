# R-pachong
library(stringr)
library(rvest)
slogan <- NULL
type <-NULL
salary <-NULL
time <-NULL
lable <-NULL
position <-NULL
location <-NULL
for(i in 1:10){
 url1 <- "https://www.lagou.com/zhaopin/chanpinjingli1/"
 url2 <-"/?filterOption=3"
 num <-as.character(i)
 url<-str_c(url1,num,url2)
 web <-read_html(url,encoding="UTF-8")
slogan <- c(slogan ,web%>%html_nodes("div.li_b_r")%>%html_text())
type <-c(type,web%>%html_nodes("div.industry")%>%html_text())
salary <-c(salary,web%>%html_nodes("span.money")%>%html_text())
time <-c(time,web%>%html_nodes("span.format-time")%>%html_text())
lable <-c(lable,web%>%html_nodes("div.list_item_bot")%>%html_text())
position<-c(position,web%>%html_nodes("h2.position_link")%>%html_text())
location <-c(location,web%>%html_nodes("em.add")%>%html_text())
}
