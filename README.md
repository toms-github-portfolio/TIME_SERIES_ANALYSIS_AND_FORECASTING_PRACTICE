# Time_Series_Analysis_And_Forecasting_Practice

# In a time series analysis
#install.packages("forecast")
library(forecast)
AirPassengers
     Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
1949 112 118 132 129 121 135 148 148 136 119 104 118
1950 115 126 141 135 125 149 170 170 158 133 114 140
1951 145 150 178 163 172 178 199 199 184 162 146 166
1952 171 180 193 181 183 218 230 242 209 191 172 194
1953 196 196 236 235 229 243 264 272 237 211 180 201
1954 204 188 235 227 234 264 302 293 259 229 203 229
1955 242 233 267 269 270 315 364 347 312 274 237 278
1956 284 277 317 313 318 374 413 405 355 306 271 306
1957 315 301 356 348 355 422 465 467 404 347 305 336
1958 340 318 362 348 363 435 491 505 404 359 310 337
1959 360 342 406 396 420 472 548 559 463 407 362 405
1960 417 391 419 461 472 535 622 606 508 461 390 432
#Time Series Decomposition
## the Ts() function will convert a numeric vector into an R time series object. The format is ts(vector, start =, end =, frequency = ) - where the start and end are the times of the first and last observation and frequency is the number of observations per unit time (1= annual, 4 = quarterly, 12 = monthly, etc)

#create a time series object
Air_passengers_TS <- ts(AirPassengers, frequency = 12)

#decompose the time series
Air_passengers_decomposition <- decompose(Air_passengers_TS)

#plot the decomposition
plot(AirPassengers)


#ARIMA Autoregressive Integrated Moving Averages

# Build the ARIMA model
arimaModel <- auto.arima(AirPassengers)

# Predict 12 months into the future
arimaForecast <- forecast(arimaModel, h = 12)
arimaForecast
 
 
Point Forecast
<dbl>
Lo 80
<dbl>
Hi 80
<dbl>
Lo 95
<dbl>
Hi 95
<dbl>
Jan 1961	445.6349	430.8903	460.3795	423.0851	468.1847
Feb 1961	420.3950	403.0907	437.6993	393.9304	446.8596
Mar 1961	449.1983	429.7726	468.6241	419.4892	478.9074
Apr 1961	491.8399	471.0270	512.6529	460.0092	523.6707
May 1961	503.3945	481.5559	525.2330	469.9953	536.7937
Jun 1961	566.8625	544.2637	589.4612	532.3007	601.4242
Jul 1961	654.2602	631.0820	677.4384	618.8122	689.7081
Aug 1961	638.5975	614.9704	662.2246	602.4630	674.7320
Sep 1961	540.8837	516.9028	564.8647	504.2081	577.5594
Oct 1961	494.1266	469.8624	518.3909	457.0177	531.2356
1-10 of 12 rows
Visualize the forecast
plot(arimaForecast)


Error detection

arimaForecast
 
 
Point Forecast
<dbl>
Lo 80
<dbl>
Hi 80
<dbl>
Lo 95
<dbl>
Hi 95
<dbl>
Jan 1961	445.6349	430.8903	460.3795	423.0851	468.1847
Feb 1961	420.3950	403.0907	437.6993	393.9304	446.8596
Mar 1961	449.1983	429.7726	468.6241	419.4892	478.9074
Apr 1961	491.8399	471.0270	512.6529	460.0092	523.6707
May 1961	503.3945	481.5559	525.2330	469.9953	536.7937
Jun 1961	566.8625	544.2637	589.4612	532.3007	601.4242
Jul 1961	654.2602	631.0820	677.4384	618.8122	689.7081
Aug 1961	638.5975	614.9704	662.2246	602.4630	674.7320
Sep 1961	540.8837	516.9028	564.8647	504.2081	577.5594
Oct 1961	494.1266	469.8624	518.3909	457.0177	531.2356
1-10 of 12 rows
#Exponential Smoothing (ETS) Forecasting

# Build the ETS model
etsModel <- ets(AirPassengers)

# Predict 12 months ahead
etsForecast <- forecast(etsModel, h=12)

etsForecast
 
 
Point Forecast
<dbl>
Lo 80
<dbl>
Hi 80
<dbl>
Lo 95
<dbl>
Hi 95
<dbl>
Jan 1961	441.8018	419.6256	463.9780	407.8863	475.7174
Feb 1961	434.1186	407.1668	461.0704	392.8994	475.3379
Mar 1961	496.6300	460.6291	532.6310	441.5714	551.6887
Apr 1961	483.2375	443.6210	522.8539	422.6493	543.8256
May 1961	483.9914	440.0236	527.9591	416.7484	551.2343
Jun 1961	551.0244	496.3368	605.7120	467.3869	634.6619
Jul 1961	613.1797	547.3865	678.9728	512.5577	713.8016
Aug 1961	609.3648	539.2447	679.4850	502.1253	716.6044
Sep 1961	530.5408	465.4872	595.5944	431.0500	630.0317
Oct 1961	463.0332	402.8496	523.2168	370.9904	555.0761
1-10 of 12 rows

# Visualize the forecast
plot(etsForecast)


TSA Example: https://www.datacamp.com/community/tutorials/time-series-r

install.packages("TSA")
Installing package into ‘/cloud/lib/x86_64-pc-linux-gnu-library/4.3’
(as ‘lib’ is unspecified)
trying URL 'http://rspm/default/__linux__/focal/latest/src/contrib/TSA_1.3.1.tar.gz'
Content type 'application/x-gzip' length 502593 bytes (490 KB)
==================================================
downloaded 490 KB

* installing *binary* package ‘TSA’ ...
* DONE (TSA)

The downloaded source packages are in
    ‘/tmp/RtmpG0TbA4/downloaded_packages’
library(TSA)
Registered S3 methods overwritten by 'TSA':
  method       from    
  fitted.Arima forecast
  plot.Arima   forecast

Attaching package: ‘TSA’

The following object is masked from ‘package:readr’:

    spec

The following objects are masked from ‘package:stats’:

    acf, arima

The following object is masked from ‘package:utils’:

    tar
# View data set
data("co2")
co2
        Jan    Feb    Mar    Apr    May    Jun    Jul    Aug    Sep    Oct    Nov
1994 363.05 364.18 364.87 364.47 364.32 362.13 356.72 350.88 350.69 356.06 360.09
1995 363.49 364.94 366.72 366.33 365.75 364.32 358.59 352.06 353.45 357.27 362.34
1996 366.93 366.71 367.63 368.15 369.14 367.33 361.53 356.11 354.51 360.12 363.85
1997 367.72 369.08 368.17 368.83 369.49 367.57 360.79 355.16 356.01 360.71 364.77
1998 369.40 370.12 370.88 370.53 371.56 369.28 364.50 357.46 360.54 364.04 368.74
1999 372.60 373.85 373.75 374.10 374.50 372.04 364.81 359.11 359.65 364.94 369.82
2000 373.23 375.13 374.83 375.42 376.18 374.01 366.54 360.78 361.77 367.51 370.58
2001 375.49 375.94 376.42 377.48 377.67 374.78 367.38 361.67 363.39 367.74 373.18
2002 376.68 377.42 378.27 378.73 379.01 375.95 370.78 364.07 365.36 370.25 374.04
2003 379.03 379.36 380.90 381.39 382.38 381.02 373.78 367.97 368.55 372.28 377.75
2004 382.44 382.36 381.58 383.21 383.58 382.59 374.58 368.69 368.55 373.39 378.49
        Dec
1994 363.27
1995 365.65
1996 365.52
1997 367.81
1998 371.58
1999 372.62
2000 373.37
2001 374.41
2002 377.99
2003 379.99
2004 381.62



# fitting
fit <- auto.arima(co2)

# Time series plot
plot(fc <- forecast(fit, h = 15))


# View data
data("boardings")

# fitting
fit2 <- auto.arima(boardings[,"log.price"])

# forecasting
plot(fc2 <- forecast(fit2, h = 15))


#Arima = autoregressive integrated moving averages
## arima is forecasting algorithms based on the assumption that previous values carry internet information and can be used to predict future values

#Arima models are applied in the cases where the data shows evidence of non stationary data 
##It allows us to forecatse or predict future outcomes based on a historical time series. It is based on the statistical concept of serial correlation where past data points influence future data points.
gas_prod_input <- as.data.frame(read.csv("gas_prod.csv"))
gas_prod_input
Month
<int>
Gas_prod
<dbl>
1	384.2611
2	380.1073
3	392.9674
4	402.1147
5	393.5196
6	384.9178
7	387.0473
8	395.2735
9	387.5905
10	365.1166
...
1-10 of 240 rows

#create a time series object
gas_prod <- ts(gas_prod_input[,2])
gas_prod
Time Series:
Start = 1 
End = 240 
Frequency = 1 
  [1] 384.2611 380.1073 392.9674 402.1147 393.5196 384.9178 387.0473 395.2735
  [9] 387.5905 365.1166 381.2301 385.3283 384.5220 376.9251 389.6017 398.5708
 [17] 381.3281 383.9691 377.4357 390.1675 367.8366 359.8777 370.1539 376.5482
 [25] 373.6261 376.4238 384.3008 393.8535 368.1156 372.9807 368.8520 371.8966
 [33] 349.3898 348.8001 351.5719 368.5909 361.8514 363.4106 380.7292 388.7903
 [41] 365.0580 368.1457 363.4552 364.5328 349.3743 346.7684 345.4838 366.8078
 [49] 358.0384 354.8464 370.9050 371.2289 362.4159 362.7829 362.6374 354.7984
 [57] 344.7691 349.8382 348.9582 367.1169 357.4586 356.2123 368.7638 366.4915
 [65] 361.5556 360.7517 371.7317 357.4217 345.2024 344.7793 351.5371 364.4690
 [73] 365.5526 354.1007 367.7785 371.4241 362.1323 362.4000 369.9742 361.8811
 [81] 343.3916 342.4114 350.3186 361.2015 353.7961 349.4083 377.3817 365.1934
 [89] 365.5990 364.2395 367.2532 366.5127 341.0385 345.5748 343.9211 352.9116
 [97] 354.6275 353.5596 380.7902 359.7584 366.0491 369.1072 360.5079 366.5216
[105] 341.2924 354.9480 343.4257 359.0446 362.2595 362.0339 378.7503 370.5111
[113] 373.1233 377.2825 367.3448 382.8817 354.8925 367.5603 362.0913 367.1718
[121] 366.7558 368.3599 391.9210 371.5101 380.0478 379.1329 373.5286 382.9236
[129] 362.2642 371.5335 362.2826 373.7731 374.5527 370.6616 394.6760 382.9170
[137] 380.9585 387.5343 379.7269 381.9066 368.1905 372.3537 369.7750 379.1830
[145] 374.7539 379.5710 396.1087 394.2388 383.7402 389.3859 381.8750 380.3991
[153] 375.3605 385.6053 382.3354 390.2775 374.1852 384.6754 399.8546 401.1613
[161] 392.4891 388.0526 390.8398 392.5266 384.0206 397.0242 389.7558 401.3772
[169] 385.6510 394.4542 413.1976 412.7181 402.7693 395.8044 401.7768 397.6990
[177] 392.1938 401.7197 395.6571 400.9156 383.0953 390.5547 413.5578 411.5326
[185] 399.3026 399.3511 414.2567 403.2949 398.5850 401.3869 391.8897 414.0845
[193] 393.2940 392.7363 414.0253 404.0706 397.4976 391.9574 411.3324 394.1259
[201] 387.4905 397.9629 381.6492 404.7980 391.0838 382.6579 408.3820 400.7036
[209] 402.0134 389.9063 395.4429 389.0535 385.7513 394.4641 381.9485 403.2101
[217] 395.7453 377.4446 397.5944 399.7648 398.9752 395.1845 397.3971 392.9125
[225] 381.6154 387.9312 385.1374 401.6251 401.0117 382.4033 401.9923 414.1446
[233] 406.3315 404.6103 405.5817 395.3791 395.3310 396.5201 391.4281 400.0000
#examine the time series
plot(gas_prod, xlab = "Time (months)",
     ylab = "Gasoline production (millions of barrels)")



#check for conditions of a stationary time series
plot(diff (gas_prod))
abline(a = 0, b = 0)


# examine ACF and PACF of differenced series
acf(diff(gas_prod), xaxp = c(0, 48, 4), lag.max=48, main="")


pacf(diff(gas_prod), xaxp = c(0, 48, 4), lag.max=48, main="")



# fit a (0,1,0)x(1,0,0)12 ARIMA model
arima_1 <- arima (gas_prod,
                  order=c(0,1,0),
                  seasonal = list(order=c(1,0,0),period=12))
arima_1

Call:
arima(x = gas_prod, order = c(0, 1, 0), seasonal = list(order = c(1, 0, 0), 
    period = 12))

Coefficients:
        sar1
      0.8335
s.e.  0.0324

sigma^2 estimated as 37.29:  log likelihood = -778.69,  aic = 1559.38
# it may be necessary to calculate AICc and BIC
# http://stats.stackexchange.com/questions/76761/extract-bic-and-aicc-from-arima-object
AIC(arima_1,k = log(length(gas_prod)))   #BIC
[1] 1568.34
# examine ACF and PACF of the (0,1,0)x(1,0,0)12 residuals
acf(arima_1$residuals, xaxp = c(0, 48, 4), lag.max=48, main="")


pacf(arima_1$residuals, xaxp = c(0, 48, 4), lag.max=48, main="")



# fit a (0,1,1)x(1,0,0)12 ARIMA model
arima_2 <- arima (gas_prod,
                  order=c(0,1,1),
                  seasonal = list(order=c(1,0,0),period=12))
arima_2

Call:
arima(x = gas_prod, order = c(0, 1, 1), seasonal = list(order = c(1, 0, 0), 
    period = 12))

Coefficients:
          ma1    sar1
      -0.7065  0.8566
s.e.   0.0526  0.0298

sigma^2 estimated as 25.24:  log likelihood = -733.22,  aic = 1470.43
# it may be necessary to calculate AICc and BIC
# http://stats.stackexchange.com/questions/76761/extract-bic-and-aicc-from-arima-object
AIC(arima_2,k = log(length(gas_prod)))   #BIC
[1] 1482.874
# examine ACF and PACF of the (0,1,1)x(1,0,0)12 residuals
acf(arima_2$residuals, xaxp = c(0, 48, 4), lag.max=48, main="")


pacf(arima_2$residuals, xaxp = c(0, 48,4), lag.max=48, main="")



# Normality and Constant Variance

plot(arima_2$residuals, ylab = "Residuals")
abline(a=0, b=0)



hist(arima_2$residuals, xlab="Residuals", xlim=c(-20,20))



qqnorm(arima_2$residuals, main="")
qqline(arima_2$residuals)


# Forecasting

#predict the next 12 months
arima_2.predict <- predict(arima_2,n.ahead=12)
matrix(c(arima_2.predict$pred-1.96*arima_2.predict$se,
         arima_2.predict$pred,
         arima_2.predict$pred+1.96*arima_2.predict$se), 12,3,
       dimnames=list( c(241:252) ,c("LB","Pred","UB")) )
          LB     Pred       UB
241 394.9689 404.8167 414.6645
242 378.6142 388.8773 399.1404
243 394.9943 405.6566 416.3189
244 405.0188 416.0658 427.1128
245 397.9545 409.3733 420.7922
246 396.1202 407.8991 419.6780
247 396.6028 408.7311 420.8594
248 387.5241 399.9920 412.4598
249 387.1523 399.9507 412.7492
250 387.8486 400.9693 414.0900
251 383.1724 396.6076 410.0428
252 390.2075 403.9500 417.6926
plot(gas_prod, xlim=c(145,252),
     xlab = "Time (months)",
     ylab = "Gasoline production (millions of barrels)",
     ylim=c(360,440))
lines(arima_2.predict$pred)
lines(arima_2.predict$pred+1.96*arima_2.predict$se, col=4, lty=2)
lines(arima_2.predict$pred-1.96*arima_2.predict$se, col=4, lty=2)
