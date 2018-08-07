### 1.认识二进制

```
二进制由0和1组成
```

### 2.二进制转十进制

```
# 将十进制的n转为二进制的m
import math
n = int(input())
print("十进制:",n)
strnum = ""
while n>0:
    strnum += str(math.floor(n%2))
    n = math.floor(n/2)
print("二进制:",strnum[::-1])
```

### 3.二进制之间的与\(&\)或\(\|\)运算

```

```



