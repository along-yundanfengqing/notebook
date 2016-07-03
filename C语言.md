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
        