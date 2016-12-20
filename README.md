Day2_assingnment
# reading raw csv data file
Forest_Fires <- read.csv("D:/R DIR/R Training/Day 2/Forest Fires/forestfires.csv")
# To display structure of the data file
str(Forest_Fires)
# To display first 5 rows and variable names of the dat file
head(Forest_Fires)
# To display summary statistics 
summary(Forest_Fires)
# To display 

attach(Forest_Fires)
# 1. Compute the square of each data point in the X column and 
# store the result in a new column called "X_square"

Forest_Fires$X_square<-Forest_Fires$X*Forest_Fires$X
head(Forest_Fires)

#2.	Compute the sum, mean, median, standard deviation of the 
# following columns - a.	FMCC b.	DMC c.	DC

sum(Forest_Fires$FFMC)
mean(Forest_Fires$FFMC)
median(Forest_Fires$FFMC)
sd(Forest_Fires$FFMC)

sum(Forest_Fires$DMC)
mean(Forest_Fires$DMC)
median(Forest_Fires$DMC)
sd(Forest_Fires$DMC)

sum(Forest_Fires$DC)
mean(Forest_Fires$DC)
median(Forest_Fires$DC)
sd(Forest_Fires$DC)



# 3.	Create another column called "Month", which has full 
# values of month, i.e "aug" becomes "August", "sep" 
# becomes "September" and so on

Forest_Fires$Month1[Forest_Fires$month=="jan"]<-"January"
Forest_Fires$Month1[Forest_Fires$month=="feb"]<-"February"
Forest_Fires$Month1[Forest_Fires$month=="mar"]<-"March"
Forest_Fires$Month1[Forest_Fires$month=="apr"]<-"April"
Forest_Fires$Month1[Forest_Fires$month=="may"]<-"May"
Forest_Fires$Month1[Forest_Fires$month=="jun"]<-"June"
Forest_Fires$Month1[Forest_Fires$month=="jul"]<-"July"
Forest_Fires$Month1[Forest_Fires$month=="aug"]<-"August"
Forest_Fires$Month1[Forest_Fires$month=="sep"]<-"September"
Forest_Fires$Month1[Forest_Fires$month=="oct"]<-"October"
Forest_Fires$Month1[Forest_Fires$month=="nov"]<-"November"
Forest_Fires$Month1[Forest_Fires$month=="dec"]<-"December"

print(Forest_Fires$Month1)

#4.	Create another Column Day_Num where day will be 
#from 1 to 7 - 1 being Sunday, 2 being Monday, 
# 3 being Tuesday and so on

Forest_Fires$day_Num[Forest_Fires$day=="sun"]<-1
Forest_Fires$day_Num[Forest_Fires$day=="mon"]<-2
Forest_Fires$day_Num[Forest_Fires$day=="tue"]<-3
Forest_Fires$day_Num[Forest_Fires$day=="wed"]<-4
Forest_Fires$day_Num[Forest_Fires$day=="thu"]<-5
Forest_Fires$day_Num[Forest_Fires$day=="fri"]<-6
Forest_Fires$day_Num[Forest_Fires$day=="sat"]<-7

print(Forest_Fires$day_Num)

#5.	Find the correlation coefficient 
#(Theory: http://mathbits.com/MathBits/TISection/Statistics2/correlation.htm) 
#between X and Y [HINT: research and use cor() function]

cor(X,Y, method="pearson")



#### GROUPING AND PIVOTING
#install.packages("dplyr")

library(dplyr)

# filter(), arrange(), select(), mutate() and summarise()
#summarise(group_by(df, month), sum_rain=sum(rain),sum_wind=sum(wind),mean_rain=mean(rain),mean_wind=mean(wind),count=n())

#6.	Find the total rain,wind  for each month [HINT: dplyr]
#7.	Find the mean rain,wind  for each month [HINT: dplyr]
#8.	Find the number of records present for each month
#9.	Find the number of records for each month-day combo

summarise(group_by(Forest_Fires,month), sum_rain=sum(rain), sum_wind=sum(wind),count=n())
summarise(group_by(Forest_Fires,month), mean_rain=mean(rain), mean_wind=mean(wind),count=n())
summarise(group_by(Forest_Fires,month,day),count=n())

# month wise FFMC max values
summarise(group_by(Forest_Fires,month),max_FFMC=max(FFMC))

