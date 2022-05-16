# hello-world
My first project

SECOND

# 二、gdb
1.gdb是GNU开源组织发布的一个强大的Unix/Linux下的程序调试工具，通过shell操作，可以实现各类IDE（程序开发环境）类似的调试功
能。[gdb官方手册](https://www.sourceware.org/gdb/)

2.程序猿的代码总会有各种各样的错误，这些错误基本可以分为两类：
```cpp
1.语法错误：编译器会报错，解决比较方便
2.逻辑错误：此时就需要调试代码
注：虽然我们有各种各样的IDE，但是对于从事 Linux C/C++ 开发的程序猿来说，大多数都需要熟悉gdb调试工具。尤其当不具备IDE的环境时（嵌入式
系统等资源限制的场景），gdb以其占用资源少、开源免费和方便实用的优势被广泛使用，当然有IDE的话还是就根据个人习惯来吧。
```
3.gdb主要有以下的作用
```cpp
1.启动程序，程序猿可以自定义地运行程序
2.让被调试的程序在指定的断点处停住，便于分析
3.当程序被停住时，可以检查此时程序中所发生的事
4.动态地改变程序的执行环境
```
4.使用例子
```cpp
源代码：main.cpp
#include <iostream>
using namespace std;
int main()
{
	int a[]={1,2,3,4};
	cout<<"hello world1"<<endl;
	cout<<"hello world2"<<endl;
	cout<<"hello world3"<<endl;
	cout<<"hello world4"<<endl;
}

（1）使用g++ -g main.cpp -o main编译程序，执行gdb main进入gdb
（2）在gdb中使用(gdb) list（缩写l）可以查看代码（查看的是当目录的main.cpp文件
（3）在gdb中使用(gdb) break（缩写b）命令来设置断点，设置断点的方法包括:
1.break "function"   //在函数那设置断点，如break functionname
2.break "linenum"    //在main.cpp文件里设置断点，如果break 5
3.break "filename":"linenum"  //在其他源码文件设置断点
4.break "filename":"function" //在其他源码文件设置断点
（4）在gdb中使用(gdb) run（缩写r）运行程序，程序在断点之前就会停下来，断点的那一行不运行。
（5）在gdb中使用(gdb) next（缩写n）/step（缩写s）进行单步调试。其中：
1.next ：类似于step over，不会进入函数的内部
2.step：类似于step into，会进入函数的内部
（6）在gdb中使用(gdb) continue（缩写c，fg命令同continue命令）可以恢复程序的运行直到程序结束或到达下一个断点
（7）在gdb中使用(gdb) print（缩写c）查看当前程序的运行数据：print a
（8）在gdb中使用(gdb) watch来观察某个表达式的值是否有变化了，若有变化，马上停住程序
（9）在gdb中使用(gdb) quit来退出gdb调试模式
（10）查看汇编代码：disassemble /m

补充：
（gdb）break+num：在第num行设置断点,简写b
（gdb）info breakpoints：查看当前设置的所有断点
（gdb）delete breakpoints num：删除第num个断点,简写d
（gdb）enable breakpoints：启用断点
（gdb）disable breakpoints：禁用断点
（gdb）run argv[1] argv[2]：调试时命令行传参
```
