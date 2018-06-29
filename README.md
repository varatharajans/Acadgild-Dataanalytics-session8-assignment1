# Acadgild-Dataanalytics-session8-assignment1

Session8 Assignment 1
varatharajan
June 21, 2018

1. Use the package RcmdrPlugin.IPSUR. 
data (RcmdrTestDrive) 
   and perform the below operations: 
a. Calculate the average salary by gender and smoking status. 
b. Which gender has the highest mean salary? 
c. Report the highest mean salary. 
d. Compare the spreads for the genders by calculating the standard deviation of salary by gender.

library(RcmdrPlugin.IPSUR)
library(TeachingDemos)
library(Hmisc)
## Loading required package: lattice
## Loading required package: survival
## Loading required package: Formula
## Loading required package: ggplot2
## 
## Attaching package: 'Hmisc'
## The following objects are masked from 'package:TeachingDemos':
## 
##     cnvrt.coords, subplot
## The following object is masked from 'package:RcmdrPlugin.IPSUR':
## 
##     stripChart
## The following objects are masked from 'package:base':
## 
##     format.pval, units
data("RcmdrTestDrive")
attach(RcmdrTestDrive)
names(RcmdrTestDrive)
## [1] "order"     "smoking"   "gender"    "race"      "before"    "after"    
## [7] "salary"    "reduction" "parking"
summary(RcmdrTestDrive)
##      order             smoking       gender            race   
##  Min.   :  1.00   Nonsmoker:136   Female:70   AfricanAmer:46  
##  1st Qu.: 42.75   Smoker   : 32   Male  :98   Asian      :13  
##  Median : 84.50                               Caucasian  :73  
##  Mean   : 84.50                               Hispanic   :34  
##  3rd Qu.:126.25                               Other      : 2  
##  Max.   :168.00                                               
##      before          after           salary         reduction      
##  Min.   :71.30   Min.   :66.60   Min.   : 377.2   Min.   :   3.00  
##  1st Qu.:73.10   1st Qu.:72.50   1st Qu.: 621.1   1st Qu.:  78.75  
##  Median :73.90   Median :73.70   Median : 710.1   Median : 139.50  
##  Mean   :73.97   Mean   :73.27   Mean   : 724.5   Mean   : 223.63  
##  3rd Qu.:74.80   3rd Qu.:74.60   3rd Qu.: 808.6   3rd Qu.: 335.50  
##  Max.   :76.30   Max.   :76.40   Max.   :1156.2   Max.   :1632.00  
##     parking     
##  Min.   :1.000  
##  1st Qu.:1.000  
##  Median :1.000  
##  Mean   :1.952  
##  3rd Qu.:2.000  
##  Max.   :8.000
Smoking status---
There are 136 non-smokers and 32 smokers

print(RcmdrTestDrive)
##     order   smoking gender        race before after  salary reduction
## 1       1 Nonsmoker Female   Caucasian   72.6  75.2  618.65         9
## 2       2 Nonsmoker   Male AfricanAmer   75.3  73.2  544.56        62
## 3       3 Nonsmoker Female   Caucasian   75.5  74.5  550.24        19
## 4       4 Nonsmoker Female   Caucasian   71.3  74.6  616.16        30
## 5       5 Nonsmoker Female    Hispanic   74.3  73.8  543.39       105
## 6       6 Nonsmoker   Male   Caucasian   73.0  73.6  692.09        43
## 7       7    Smoker   Male    Hispanic   72.4  70.7  800.48       229
## 8       8 Nonsmoker   Male    Hispanic   73.6  74.0  703.79        40
## 9       9 Nonsmoker Female   Caucasian   73.7  75.9  540.06       101
## 10     10 Nonsmoker Female    Hispanic   74.6  74.8  522.28       440
## 11     11 Nonsmoker Female AfricanAmer   75.8  73.1  377.17       213
## 12     12 Nonsmoker Female   Caucasian   75.3  72.1  525.96       474
## 13     13 Nonsmoker Female   Caucasian   75.0  72.5  548.88       144
## 14     14 Nonsmoker   Male       Asian   72.8  72.7  537.70       179
## 15     15 Nonsmoker   Male       Asian   74.4  75.7  500.20        63
## 16     16 Nonsmoker Female    Hispanic   72.9  73.1  597.73       570
## 17     17 Nonsmoker Female    Hispanic   72.3  74.0  578.95       437
## 18     18 Nonsmoker   Male   Caucasian   74.0  74.6  690.06        62
## 19     19 Nonsmoker   Male   Caucasian   73.1  72.8  748.98       437
## 20     20 Nonsmoker   Male AfricanAmer   74.0  76.1  811.71        60
## 21     21 Nonsmoker   Male       Other   73.6  74.5  660.58       255
## 22     22 Nonsmoker   Male    Hispanic   73.4  75.0  586.29       133
## 23     23 Nonsmoker   Male AfricanAmer   73.9  74.0  387.59        88
## 24     24 Nonsmoker   Male   Caucasian   73.0  73.9  524.54       116
## 25     25 Nonsmoker Female    Hispanic   74.2  75.7  536.87        48
## 26     26 Nonsmoker   Male   Caucasian   73.6  75.4  503.64       365
## 27     27    Smoker   Male AfricanAmer   74.6  68.1  496.09        73
## 28     28 Nonsmoker   Male AfricanAmer   74.5  72.6  701.91       306
## 29     29 Nonsmoker Female   Caucasian   72.6  73.2  595.70       497
## 30     30 Nonsmoker   Male       Asian   72.6  74.1  759.30        32
## 31     31 Nonsmoker Female    Hispanic   72.1  73.7  717.91       497
## 32     32 Nonsmoker   Male       Asian   73.2  73.5  808.63        21
## 33     33    Smoker   Male   Caucasian   73.2  70.0  682.60       291
## 34     34 Nonsmoker   Male       Asian   74.3  75.2  623.09        83
## 35     35    Smoker   Male AfricanAmer   74.0  68.7  550.28        55
## 36     36 Nonsmoker   Male AfricanAmer   75.5  72.9  646.25       100
## 37     37 Nonsmoker Female AfricanAmer   75.4  72.6  635.43       439
## 38     38 Nonsmoker   Male   Caucasian   75.5  72.5  437.19       419
## 39     39 Nonsmoker Female   Caucasian   74.4  73.6  619.29        23
## 40     40 Nonsmoker   Male   Caucasian   73.7  75.0  593.68        71
## 41     41 Nonsmoker   Male AfricanAmer   75.8  73.1  546.26       109
## 42     42 Nonsmoker Female   Caucasian   74.3  72.2  704.83        98
## 43     43 Nonsmoker   Male   Caucasian   74.7  73.1  764.15        78
## 44     44 Nonsmoker Female   Caucasian   74.9  72.0  859.67       257
## 45     45 Nonsmoker Female AfricanAmer   75.3  76.2  724.25       487
## 46     46 Nonsmoker   Male AfricanAmer   75.6  75.0  631.62       213
## 47     47 Nonsmoker Female    Hispanic   72.7  73.4  478.39       383
## 48     48 Nonsmoker Female   Caucasian   75.6  74.9  652.79       116
## 49     49 Nonsmoker   Male   Caucasian   73.8  71.9  545.66      1632
## 50     50 Nonsmoker   Male   Caucasian   74.7  75.8  515.95       151
## 51     51 Nonsmoker   Male AfricanAmer   75.4  74.8  612.27       152
## 52     52 Nonsmoker Female    Hispanic   74.3  73.8  633.12       390
## 53     53 Nonsmoker   Male AfricanAmer   75.0  73.2  671.35        64
## 54     54 Nonsmoker Female AfricanAmer   75.3  73.8  643.83        85
## 55     55 Nonsmoker   Male    Hispanic   74.8  73.6  794.66        71
## 56     56    Smoker Female       Asian   73.2  70.6  888.00        37
## 57     57 Nonsmoker Female   Caucasian   74.0  75.8  602.94        89
## 58     58    Smoker   Male   Caucasian   75.5  74.3  716.78       172
## 59     59 Nonsmoker   Male   Caucasian   75.3  72.8  606.12         3
## 60     60 Nonsmoker   Male AfricanAmer   73.9  73.7  704.90       247
## 61     61 Nonsmoker   Male   Caucasian   71.7  72.5  620.32       127
## 62     62 Nonsmoker   Male   Caucasian   73.6  74.7  515.92       337
## 63     63 Nonsmoker Female AfricanAmer   72.1  73.7  655.72       123
## 64     64 Nonsmoker Female    Hispanic   72.7  73.1  619.44       205
## 65     65 Nonsmoker Female   Caucasian   74.5  71.9  640.48        61
## 66     66    Smoker   Male   Caucasian   73.2  72.8  844.32       119
## 67     67 Nonsmoker Female   Caucasian   73.3  74.9  918.03       165
## 68     68 Nonsmoker Female       Asian   74.2  75.1  933.49       480
## 69     69 Nonsmoker Female    Hispanic   74.7  74.2  699.63        39
## 70     70 Nonsmoker Female   Caucasian   74.4  74.2  593.27       434
## 71     71    Smoker   Male   Caucasian   74.5  69.7  634.24       147
## 72     72    Smoker Female   Caucasian   73.0  69.3  686.98       270
## 73     73 Nonsmoker Female    Hispanic   73.5  72.5  618.68       384
## 74     74    Smoker Female    Hispanic   72.3  70.6  631.20        87
## 75     75 Nonsmoker Female   Caucasian   75.7  73.8  608.88       291
## 76     76    Smoker Female    Hispanic   75.6  69.1  686.28        31
## 77     77    Smoker Female AfricanAmer   75.4  70.0  715.44       549
## 78     78 Nonsmoker   Male    Hispanic   73.4  74.8  754.66       172
## 79     79 Nonsmoker   Male AfricanAmer   72.9  74.6  865.89       251
## 80     80 Nonsmoker Female   Caucasian   72.3  74.0  890.88       335
## 81     81    Smoker   Male AfricanAmer   74.4  70.7  777.91       319
## 82     82    Smoker   Male   Caucasian   72.8  70.5  680.56       519
## 83     83 Nonsmoker   Male   Caucasian   75.1  73.5  594.61        94
## 84     84 Nonsmoker   Male AfricanAmer   73.2  75.1  651.73        15
## 85     85    Smoker   Male   Caucasian   74.0  71.3  601.11       397
## 86     86 Nonsmoker Female       Asian   73.8  72.9  626.71        95
## 87     87 Nonsmoker Female   Caucasian   73.5  74.8  643.80       551
## 88     88    Smoker   Male    Hispanic   72.2  66.6  724.52        89
## 89     89 Nonsmoker Female AfricanAmer   74.4  75.3  745.57       121
## 90     90    Smoker   Male   Caucasian   75.2  72.5  842.05       319
## 91     91 Nonsmoker   Male AfricanAmer   73.6  74.2  880.47       424
## 92     92 Nonsmoker Female   Caucasian   73.1  72.6 1016.21        79
## 93     93 Nonsmoker   Male AfricanAmer   73.9  73.3  726.13       372
## 94     94 Nonsmoker   Male   Caucasian   74.9  74.4  780.21       195
## 95     95 Nonsmoker Female   Caucasian   72.5  75.0  704.08       324
## 96     96 Nonsmoker Female       Other   75.0  73.4  785.89       532
## 97     97 Nonsmoker   Male AfricanAmer   73.8  75.2  662.98        91
## 98     98 Nonsmoker   Male   Caucasian   73.6  75.2  621.30        32
## 99     99    Smoker   Male       Asian   74.8  71.3  521.17        94
## 100   100 Nonsmoker Female   Caucasian   73.8  74.3  714.58        95
## 101   101 Nonsmoker   Male   Caucasian   75.8  74.6  728.94        99
## 102   102    Smoker   Male   Caucasian   75.5  71.1  812.26       275
## 103   103    Smoker   Male   Caucasian   72.4  71.7  924.78       203
## 104   104 Nonsmoker Female AfricanAmer   73.6  74.3 1001.31       131
## 105   105 Nonsmoker   Male    Hispanic   73.3  74.3  724.99       116
## 106   106 Nonsmoker   Male    Hispanic   72.9  73.3  822.35        66
## 107   107 Nonsmoker   Male    Hispanic   75.7  73.1  653.58       574
## 108   108 Nonsmoker Female       Asian   72.6  73.3  642.28        87
## 109   109 Nonsmoker   Male AfricanAmer   73.8  73.6  730.12       149
## 110   110    Smoker Female AfricanAmer   72.8  70.6  708.30       538
## 111   111 Nonsmoker   Male   Caucasian   73.9  71.9  629.17       419
## 112   112 Nonsmoker   Male   Caucasian   73.2  75.1  790.33        33
## 113   113 Nonsmoker   Male AfricanAmer   75.5  73.8  788.05       213
## 114   114 Nonsmoker Female   Caucasian   72.4  74.5  849.25        44
## 115   115 Nonsmoker   Male AfricanAmer   72.8  74.5 1036.06       814
## 116   116 Nonsmoker   Male    Hispanic   74.8  75.2 1149.92       131
## 117   117    Smoker   Male   Caucasian   75.6  72.4  854.31       100
## 118   118 Nonsmoker Female   Caucasian   74.1  74.2  768.94       688
## 119   119    Smoker   Male   Caucasian   75.3  69.6  666.74        83
## 120   120 Nonsmoker Female    Hispanic   75.1  73.2  639.72       185
## 121   121    Smoker   Male AfricanAmer   74.1  70.3  744.38        60
## 122   122 Nonsmoker Female   Caucasian   74.6  74.1  584.08         6
## 123   123 Nonsmoker   Male   Caucasian   74.1  72.5  712.00        60
## 124   124 Nonsmoker Female AfricanAmer   73.9  72.7  789.76       282
## 125   125    Smoker   Male    Hispanic   73.0  67.3  719.06        31
## 126   126 Nonsmoker   Male AfricanAmer   75.3  73.8  903.34        82
## 127   127 Nonsmoker   Male   Caucasian   73.5  75.3 1044.98        65
## 128   128 Nonsmoker   Male       Asian   72.3  74.8 1027.36        26
## 129   129 Nonsmoker Female AfricanAmer   73.5  73.7  855.36       117
## 130   130 Nonsmoker   Male   Caucasian   72.9  76.2  796.51       205
## 131   131    Smoker   Male   Caucasian   72.6  70.3  771.74        99
## 132   132 Nonsmoker   Male   Caucasian   76.3  74.2  780.27       401
## 133   133 Nonsmoker   Male AfricanAmer   73.0  75.2  808.65         8
## 134   134 Nonsmoker Female   Caucasian   74.7  74.7  632.05       469
## 135   135    Smoker Female    Hispanic   74.5  67.5  681.58       116
## 136   136 Nonsmoker   Male   Caucasian   71.4  74.6  823.38       298
## 137   137 Nonsmoker   Male    Hispanic   74.4  73.9  754.55       115
## 138   138 Nonsmoker   Male       Asian   72.1  73.1  938.47       721
## 139   139 Nonsmoker   Male   Caucasian   73.1  76.4 1072.65       135
## 140   140 Nonsmoker   Male AfricanAmer   73.7  73.3 1021.69       202
## 141   141 Nonsmoker Female   Caucasian   73.0  73.3  785.75       642
## 142   142 Nonsmoker Female    Hispanic   73.8  74.4  882.78        95
## 143   143 Nonsmoker Female   Caucasian   73.6  72.0  762.43       262
## 144   144 Nonsmoker   Male    Hispanic   73.1  74.2  863.78       564
## 145   145 Nonsmoker   Male   Caucasian   73.4  73.9  745.97       258
## 146   146 Nonsmoker Female    Hispanic   74.0  72.4  809.26        41
## 147   147 Nonsmoker Female AfricanAmer   75.8  72.9  668.26        77
## 148   148    Smoker Female       Asian   74.2  67.8  780.61       429
## 149   149 Nonsmoker Female AfricanAmer   75.4  73.3  749.43       557
## 150   150 Nonsmoker   Male   Caucasian   75.1  72.9  889.55        89
## 151   151 Nonsmoker Female   Caucasian   74.6  74.9 1025.09        59
## 152   152    Smoker   Male   Caucasian   75.5  69.8 1156.16       370
## 153   153 Nonsmoker   Male AfricanAmer   74.9  74.3  777.93       202
## 154   154 Nonsmoker   Male AfricanAmer   73.6  74.3  835.96       111
## 155   155 Nonsmoker Female   Caucasian   74.5  72.6  668.69       598
## 156   156 Nonsmoker Female   Caucasian   75.7  74.6  870.52        55
## 157   157 Nonsmoker   Male AfricanAmer   72.6  73.8  827.18       750
## 158   158    Smoker   Male   Caucasian   74.1  70.8  689.23        83
## 159   159 Nonsmoker Female AfricanAmer   73.6  74.2  662.17       257
## 160   160    Smoker Female   Caucasian   75.0  70.3  820.52       303
## 161   161 Nonsmoker Female AfricanAmer   73.1  74.8  780.51        79
## 162   162 Nonsmoker   Male    Hispanic   73.6  74.3  980.09       156
## 163   163 Nonsmoker   Male AfricanAmer   73.6  75.1 1084.21       166
## 164   164    Smoker   Male    Hispanic   73.5  72.1 1073.50         9
## 165   165 Nonsmoker   Male AfricanAmer   73.7  72.5  908.11       409
## 166   166 Nonsmoker   Male    Hispanic   73.1  73.4  793.42       424
## 167   167 Nonsmoker   Male    Hispanic   74.5  74.9  804.78       205
## 168   168 Nonsmoker   Male AfricanAmer   73.7  74.1  790.82        47
##     parking
## 1         2
## 2         1
## 3         4
## 4         1
## 5         1
## 6         1
## 7         5
## 8         1
## 9         2
## 10        1
## 11        1
## 12        2
## 13        1
## 14        2
## 15        3
## 16        1
## 17        4
## 18        2
## 19        2
## 20        1
## 21        1
## 22        4
## 23        1
## 24        1
## 25        3
## 26        1
## 27        1
## 28        5
## 29        1
## 30        1
## 31        1
## 32        2
## 33        1
## 34        1
## 35        2
## 36        8
## 37        4
## 38        1
## 39        2
## 40        1
## 41        4
## 42        1
## 43        1
## 44        3
## 45        1
## 46        3
## 47        1
## 48        1
## 49        2
## 50        1
## 51        3
## 52        2
## 53        1
## 54        1
## 55        2
## 56        1
## 57        2
## 58        1
## 59        1
## 60        5
## 61        2
## 62        1
## 63        1
## 64        4
## 65        1
## 66        2
## 67        2
## 68        6
## 69        3
## 70        4
## 71        1
## 72        2
## 73        1
## 74        1
## 75        3
## 76        2
## 77        1
## 78        2
## 79        1
## 80        6
## 81        1
## 82        1
## 83        2
## 84        1
## 85        5
## 86        2
## 87        2
## 88        1
## 89        2
## 90        1
## 91        3
## 92        2
## 93        5
## 94        1
## 95        1
## 96        3
## 97        2
## 98        1
## 99        2
## 100       3
## 101       5
## 102       1
## 103       1
## 104       3
## 105       2
## 106       1
## 107       1
## 108       1
## 109       1
## 110       1
## 111       2
## 112       1
## 113       1
## 114       1
## 115       1
## 116       2
## 117       4
## 118       4
## 119       1
## 120       1
## 121       2
## 122       1
## 123       2
## 124       1
## 125       1
## 126       2
## 127       1
## 128       2
## 129       1
## 130       1
## 131       3
## 132       1
## 133       2
## 134       4
## 135       4
## 136       4
## 137       2
## 138       1
## 139       1
## 140       1
## 141       1
## 142       1
## 143       2
## 144       1
## 145       3
## 146       1
## 147       3
## 148       2
## 149       1
## 150       1
## 151       1
## 152       1
## 153       2
## 154       2
## 155       3
## 156       1
## 157       1
## 158       2
## 159       1
## 160       1
## 161       2
## 162       4
## 163       6
## 164       1
## 165       3
## 166       2
## 167       1
## 168       2













a.	Calculate the average salary by gender and smoking status.
b.	Which gender has the highest mean salar?
c.	Report the highest mean salary?



x<-tapply(salary,list(gender=gender),mean)
x
## gender
##   Female     Male 
## 698.0911 743.3915 (Average salary by gender)
by(salary,gender,mean,na.rm=TRUE)
## gender: Female
## [1] 698.0911
## -------------------------------------------------------- 
## gender: Male
## [1] 743.3915
x[which(x==max(x))]
##     Male 
## 743.3915          
(Male gender has the highest mean salary and the salary is 743.3915)     
Smoking status---
There are 136 non-smokers and 32 smokers

d. Compare the spreads for the genders by calculating the standard deviation of salary by gender.

y<-tapply(salary,list(gender=gender),sd)
y
## gender
##   Female     Male 
## 130.7053 158.5423
Item Compare the spreads for the genders by calculating the standard deviation of \emph{salary} by \emph{gender}. Which gender has the biggest standard deviation?
For these data, the the largest standard deviation is approximately
Sexpr{round(y[which(y==max(y))],2)} which was attained by the Sexpr{names(y)[which(y==max(y))]}gender.
\item Make boxplots of \emph{salary} by \emph{gender}. How does the boxplot
compare to your answers to (1) and (3)?

The graph is shown below
\begin{center}
<<echo = FALSE, fig=true, height = 4.5, width = 6>>=boxplot(salary~gender, xlab="salary", ylab="gender", main="", notch=FALSE, varwidth=TRUE, horizontal=TRUE, data=RcmdrTestDrive)@\par\end{center}

Answers will vary. There should be some remarks that the center of
the box is farther to the right for the \Sexpr{names(x)[which(x==max(x))]}
gender, and some recognition that the box is wider for the \Sexpr{names(y)[which(y==max(y))]}gender.\end{enumerate} 


table(race)
## race
## AfricanAmer       Asian   Caucasian    Hispanic       Other 
##          46          13          73          34           2
race
##   [1] Caucasian   AfricanAmer Caucasian   Caucasian   Hispanic   
##   [6] Caucasian   Hispanic    Hispanic    Caucasian   Hispanic   
##  [11] AfricanAmer Caucasian   Caucasian   Asian       Asian      
##  [16] Hispanic    Hispanic    Caucasian   Caucasian   AfricanAmer
##  [21] Other       Hispanic    AfricanAmer Caucasian   Hispanic   
##  [26] Caucasian   AfricanAmer AfricanAmer Caucasian   Asian      
##  [31] Hispanic    Asian       Caucasian   Asian       AfricanAmer
##  [36] AfricanAmer AfricanAmer Caucasian   Caucasian   Caucasian  
##  [41] AfricanAmer Caucasian   Caucasian   Caucasian   AfricanAmer
##  [46] AfricanAmer Hispanic    Caucasian   Caucasian   Caucasian  
##  [51] AfricanAmer Hispanic    AfricanAmer AfricanAmer Hispanic   
##  [56] Asian       Caucasian   Caucasian   Caucasian   AfricanAmer
##  [61] Caucasian   Caucasian   AfricanAmer Hispanic    Caucasian  
##  [66] Caucasian   Caucasian   Asian       Hispanic    Caucasian  
##  [71] Caucasian   Caucasian   Hispanic    Hispanic    Caucasian  
##  [76] Hispanic    AfricanAmer Hispanic    AfricanAmer Caucasian  
##  [81] AfricanAmer Caucasian   Caucasian   AfricanAmer Caucasian  
##  [86] Asian       Caucasian   Hispanic    AfricanAmer Caucasian  
##  [91] AfricanAmer Caucasian   AfricanAmer Caucasian   Caucasian  
##  [96] Other       AfricanAmer Caucasian   Asian       Caucasian  
## [101] Caucasian   Caucasian   Caucasian   AfricanAmer Hispanic   
## [106] Hispanic    Hispanic    Asian       AfricanAmer AfricanAmer
## [111] Caucasian   Caucasian   AfricanAmer Caucasian   AfricanAmer
## [116] Hispanic    Caucasian   Caucasian   Caucasian   Hispanic   
## [121] AfricanAmer Caucasian   Caucasian   AfricanAmer Hispanic   
## [126] AfricanAmer Caucasian   Asian       AfricanAmer Caucasian  
## [131] Caucasian   Caucasian   AfricanAmer Caucasian   Hispanic   
## [136] Caucasian   Hispanic    Asian       Caucasian   AfricanAmer
## [141] Caucasian   Hispanic    Caucasian   Hispanic    Caucasian  
## [146] Hispanic    AfricanAmer Asian       AfricanAmer Caucasian  
## [151] Caucasian   Caucasian   AfricanAmer AfricanAmer Caucasian  
## [156] Caucasian   AfricanAmer Caucasian   AfricanAmer Caucasian  
## [161] AfricanAmer Hispanic    AfricanAmer Hispanic    AfricanAmer
## [166] Hispanic    Hispanic    AfricanAmer
## Levels: AfricanAmer Asian Caucasian Hispanic Other
x<-tapply(salary,list(gender=gender),mean)
x
## gender
##   Female     Male 
## 698.0911 743.3915

