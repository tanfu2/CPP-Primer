# C++Primer学习笔记
![233](https://github.com/tanfu2/CPP-Primer/blob/master/images/Hhh.jpg)
## 第Ⅰ部分 C++基础
### 2 变量和基本类型
#### 2.2 变量
- 初始化不是赋值，初始化的含义是创建变量时赋予其一个初始值，而赋值的含义是把对象当前的值擦除，而以一个新值来替代
#### 2.4 const限定符
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
#### 2.5 处理类型
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
### 3 字符串、向量和数组
#### 3.1 命名空间的using声明
- 头文件不应包含using声明  
&emsp;&emsp;头文件的内容会拷贝到所有引用它的文件中去，如果头文件里有某个using声明，那么每个使用了这个头文件的文件就会有这个声明，可能会产生始料未及的名字冲突。
#### 3.3 标准库类型vector
- 范围for语句体内不应该改变遍历序列的大小
- vector对象（以及string对象）的下标运算符可用于访问已存在的元素，而不能用于添加元素
- 凡是使用了迭代器的循环体。都不要向迭代器所属的容器添加元素
#### 3.4 迭代器
- 如果容器为空，则begin和end返回的事同一个迭代器，都是尾后迭代器(off-the-end iterator)
#### 3.5 数组
- 理解复杂的数组声明
```C++
int *ptrs[10];      // ptrs是含有10个整型指针的数组
int &refs[10];      // 错误：不存在引用的数组
int (*Parray)[10];  // Parray指向一个含有10个整数的数组
int (&arrRef)[10];  // arrRef引用一个含有10个整数的数组

/*
  要想理解数组声明的含义，最好的方法是从数组名字开始按照由内向外的顺序阅读
*/
```
- 类型别名简化多维数组的指针
```C++
int ia[3][4] = {0};
using int_array = int[4];

for(int_array *p = ia; p != ia + 3; ++p)
{
  for(int *q = *p; q != *p + 4; ++q)
  {
    std::cout<<*q<<' ';
  }
}
```
### 4 表达式
#### 4.5 递增和递减运算符
- 除非必须，否则不用递增递减运算符的后置版本
#### 4.8 位运算符
- 位运算符(左结合律)
|运算符|功能|用法|
|:----:|:----:|:----:|
|~|位求反|~expr|
|<<|左移|expr1 << expr2|
|>>|右移|expr1 >> expr2|
|&|位与|expr1 & expr2|
|^|位异或|expr1 ^ expr2|
|&#124;|位或|expr1 &#124; expr2|
- 关于符号位如何处理没有明确的规定，所以强烈建议仅将位运算符用于处理无符号类型
### 5 语句
#### 5.3 条件语句
- 在switch的最后一个标签最好加上break，如果后续增加新的case分支，就不用补充前面的break语句
- 即使不准备再default标签下做任何工作，定义一个default标签也是有用的。其目的在于告诉程序的读者，我们已经考虑到了默认的情况，只是目前什么也不做
#### 5.5 跳转语句
- 不要使用goto语句，因为它使得程序既难理解又难修改
### 6 函数
#### 6.
