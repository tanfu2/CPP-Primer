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
```
