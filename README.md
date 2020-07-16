# C++Primer学习笔记
![233](https://github.com/tanfu2/CPP-Primer/blob/master/images/Hhh.jpg)
## 第Ⅰ部分 C++基础
### 2.2 变量
- 初始化不是赋值，初始化的含义是创建变量时赋予其一个初始值，而赋值的含义是把对象当前的值擦除，而以一个新值来替代
### 2.4 const限定符
- 指向常量的指针（point to const）
```C++
const int i= 0 ;
const int *j = &i;
```
- 常量指针（const point）
```C++
int i= 0 ;
int *const j = &i;
int u = 0;
const int *const v = &u;  //指向常量的常量指针
```
- constexpr和指针：在constexpr声明中如果定义了一个指针，限定符constexpr仅对指针有效，与指针所指的对象无关
```C++
const int *p = nullptr;     //p是指向常量的指针
constexpr int *q = nullptr; //q是指向常量的指针
```
### 2.5 处理类型
- 类型别名
```C++
typedef int integer;  //传统定义
using int = integer;  //C++11别名声明
```
- auto类型说明符
```C++
int i = 0, &r = i;
auto a = r;         //引用对象的类型作为auto的类型，所以a的类型是int

/*
auto一般会忽略顶层const，保留底层const
*/

const int ci = i, &cr = ci;
auto b = ci;    //int
auto c = cr;    //int
auto d = &i;    //int *
auto e = &ci;   //const int *

/*
如果希望推断出的auto类型是一个顶层const，需要明确指出
*/

const auto f = ci;    //const int
```
- decltype类型指示符
```C++
//decltype的表达式如果是加上了括号的变量，结果将是引用
int i = 0;
decltype((i)) d;  //错误:d是int&，必须初始化
decltype(i) e;    //正确:e是(未初始化的)int
```
