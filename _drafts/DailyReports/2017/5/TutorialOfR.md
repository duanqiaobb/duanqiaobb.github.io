- [输入](#org3b89e2e)
  - [赋值](#orged1c3a4)

<div style="color:#369">R语言教程</div>


<a id="org3b89e2e"></a>

# 输入


<a id="orged1c3a4"></a>

## 赋值

```R
bubba <- c(3,5,7,9)
```

    3
    5
    7
    9

-   通过下标访问

```R
bubba <- c(3,5,7,9)
bubba[0]
bubba[1]
bubba[2]
bubba[3]
bubba[4]
```

    numeric(0)
    [1] 3
    [1] 5
    [1] 7
    [1] 9

<div style="color:#369">读取CSV文件</div>

```R
heisenberg<-read.csv(file="./data/files/simple.csv", head=TRUE,sep=",")
heisenberg
summary(heisenberg)
```

      trial mass velocity
    1     A 10.0       12
    2     A 11.0       14
    3     B  5.0        8
    4     B  6.0       10
    5     A 10.5       13
    6     B  7.0       11
     trial      mass          velocity    
     A:3   Min.   : 5.00   Min.   : 8.00  
     B:3   1st Qu.: 6.25   1st Qu.:10.25  
           Median : 8.50   Median :11.50  
           Mean   : 8.25   Mean   :11.33  
           3rd Qu.:10.38   3rd Qu.:12.75  
           Max.   :11.00   Max.   :14.00
