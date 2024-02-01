---
title: "基础的小算法"
seoTitle: "基础算法"
seoDescription: "基础算法"
datePublished: Tue Jan 30 2024 13:09:37 GMT+0000 (Coordinated Universal Time)
cuid: cls0dl8pm00070ajsfapb3up0
slug: 5z656ga566x5rov77yi5q2j5zyo56ev57sv77yj
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706775171544/0689fb79-e670-4730-9a8a-5fbccaafa1d6.jpeg

---

* 1.前缀和
    
* 2.差分
    

---

### 前缀和（s\[i\]）

作用：用O(1)的时间求出\[L,R\]范围内的和，缩短多次求和时间

分一维和二维

**1.主要是记住公式，先把<mark>S[i]</mark>求出来(注意s\[0\]=0)**

一维：S\[i\]=S\[i-1\]+a\[i\]

二维：S\[ i\]\[ j\]=S\[i-1\]\[ j\]+S\[ i\]\[j-1\]-S\[i-1\]\[j-1\]+a\[ i\]\[ j\]

**2.\[L,R\]范围内快速求和**

一维：ans=S\[R\]-S\[L-1\]

**3.\[x1,y1\]到\[x2,y2\]所有元素和**

二维：ans=S\[x2,y2\]-S\[x1-1\]\[y2\]-S\[x2,y1-1\]+S\[x1-1,y1-1\]

---

### 差分

作用：用O(1)时间对范围内全部元素加上c

**1.同样需要记住公式，求出b\[i\]**

一维：b\[i\]=a\[n\]-a\[n-1\]

**2.一维的数组\[L,R\]区间增加c的操作**

b\[ L\]+=c; b\[R+1\]-=c;

**3.对于二维矩阵的b\[i\]构造和增加c**

b\[i\]构造可以理解为初始全0矩阵插入a\[i\]\[j\]

```cpp
void insert(int x1, int y1, int x2, int y2, int c)//加c的操作
{
    b[x1][y1] += c;
    b[x2 + 1][y1] -= c;
    b[x1][y2 + 1] -= c;
    b[x2 + 1][y2 + 1] += c;//补回来
}
for (int i = 1; i <= n; i ++ )
    for (int j = 1; j <= m; j ++ )
        insert(i, j, i, j, a[i][j]);//将a[i][j]的值增加到b中
```

---