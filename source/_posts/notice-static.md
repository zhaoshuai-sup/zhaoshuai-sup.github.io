---
title: static 的注意事项
date: 2020-01-06 16:19:15
tags: c++
---
# 全局静态变量
## 代码
### head.h
```c++
#include <stdio.h>
static int a = 0;
int x();
int x2();
int x3();
int xx();
```

### c1.cpp
```c++
int x()
{
    printf("%x\n", &a);
    a += 1;
    return a;
}
```
### c2.cpp
```c++
int x2()
{
    printf("%x\n", &a);
    a += 2;
    return a;
}

int x3()
{
    printf("%x\n", &a);
    a += 3;
    return a;
}

int xx()
{
    x();
    printf("%x\n", &a);
    return a;
}
```

### main.cpp
```c++ 

#include "t1.h"

int main()
{
    printf("%x\n", &a);
    cout << a << endl;
    cout << x() << endl;
    printf("%x\n", &a);
    cout << a << endl;
    cout << x2() << endl;
    printf("%x\n", &a);
    cout << a << endl;
    cout << x3() << endl;
    printf("%x\n", &a);
    cout << a << endl;
    cout << xx() << endl;
    printf("%x\n", &a);
    cout << a << endl;
    cout << x() << endl;
}
```

```shell
g++ main.cpp c1.cpp c2.cpp
./a.out
```

### result
```c++
602198
0
6021a0
1
602198
0
60219c
2
602198
0
60219c
5
602198
0
6021a0
60219c
5
602198
0
6021a0
3
```

## 结论

1. 每个源文件都生成了自己的静态变量a
2. 重名的东西最好用命名空间分包管理
3. 通过调用同一个命名空间的函数来访问对应空间的值是避免bug的好规范
