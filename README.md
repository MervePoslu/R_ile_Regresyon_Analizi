# R_ile_Regresyon_Analizi
data<-read.table("C:/Users/User/Desktop/veri.txt")
View(veri)
names(veri)
names(veri)<-c("y","x1","x2","x3","x4")
attach(veri)
x4<-as.factor(x4)
qqnorm(y)
qqline(y)
install.packages("nortest")
library(nortest)
lillie.test(y)
qqnorm(lny)
lny<-log(y)
qqnorm(lny)
qqline(lny)
lillie.test(lny)
datayeni<-cbind(x1,x2,x3,x4,lny)
pairs(datayeni)
Etkin değer olup olmadığı incelendiğinde 
library(zoo) #index fonksiyonu için paket

cooksd <- cooks.distance(sonuc)

plot(cooksd, pch="*", cex=2, main="Influential Obs by Cooks distance")
s2 <- (t(residuals) %*% residuals)/(nrow(Y)-nrow(betahat))  
Var_betahat <- s2[1,1]*solve(t(X)%*%X)  

abline(h = if (length(data$lny)>50) 4/length(data$lny) else 4/(length(data$lny)-(length(data)-1)-1) , col="red")
sonuc<-lm(lny~x1+x2+x3+x4)
predict(sonuc)
summary(sonuc)
inf<-ls.diag(sonuc)
inf()
confint(sonuc)
cor(datayeni)
influence.measures(sonuc)
summary(influence.measures(sonuc))
lavera
