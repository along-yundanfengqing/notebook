#C语言上机复试
##程序设计基础
### 头文件
*   一个程序只要语法没有错误，编译就是正确的。
*   没有输入也没有输出，不必包含`<stdio.h>`头文件。

### 数据类型
1.  基本数据类型(字符、整型、浮点数)
    *   int类型在内存中字节数取决于编译系统。
    *   int类型所占的字节数不小于short型，不大于long类型。
    *   字符类型和整数类型，都有一个对应无符号类型表示不包含负数部分的值，导致正数表示范围会扩大。
    *   double类型比float类型精度要高，定义浮点类型建议使用double类型。

    Q：如何判断一个字符为汉字？
    
    A：使用连续两个负数来判断一个字符是否为汉字。

    T：英文字符用一个字节表示，最高位为0。两个连续字节表示一个汉字，每个字节最高位为1。有符号类型，最高位为1的字符转换为整数就是负数。
    
    


2.  

#C语言知识点
##结构体
###结构体声明
*   直接创建变量
   
```c
struct  {number-list} x ;   //创建名叫x的变量。
```
    
*   通过标签创建变量 

```c
struct SIMPLE {number-list};    //声明SIMPLE标签。
struct SIMPLE x;    //使用标签创建变量x。
```
        
*   通过类型创建变量  

```c       
typedef struct {number-list} SIMPLE;    //使用typedef创建SIMPLE类型。
SIMPLE x;   //使用类型创建变量。
```
        
###结构体自引用
*   **陷阱：**类型名直到声明的末尾才定义，所以在结构声明的内部尚未定义，因此创建类型名SELF_REF3失败。

```c  
typedef struct{
    SELF_REF3 *b
    int c;
}SELF_REF3;
```        

*   **解决方案：**定义一个结构标签来声明b。

```c
typedef struct SELF_REF3_TAG{
    struct SELF_REF3_TAG *b;
    int c;
}SELF_REF3;
```
        