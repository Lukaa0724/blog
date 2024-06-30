## WK Hw
- 一个指针不可以被多次`delete`，但是`nullptr`可以
- ![|405](images/Pasted%20image%2020240627183303.png)
- 在C++中，cin是预定义的对象
- 重载函数的时候，不需要考虑函数的返回值，只要函数名一样，传入的参数不一样，就可以重载
- Order of initialization in the initial list is the order of their declaration in the `class`.
- 友元函数，不是这个类的成员
- 设定缺省值，先设定右边，比如`f(int a, int b, int c = 1)`
- 类与类的友元关系 无法被**继承**
- One class can have more than one super classes.
- 构造函数不能为虚函数，析构函数不能被重载，没有参数，不知道使用哪一个，会有歧义
- 因为静态成员函数不能是虚函数，所以它们不能实现多态。
- class中的函数都是默认inline的 只在class里写的都是inline的
- 只有指针和引用才会实现动态绑定，不然都是静态了，不会调用虚函数，定义的什么类，调用什么函数
- ![|424](images/Pasted%20image%2020240627190322.png)
- 计算这个class的字节数，int+vptr的大小
- 派生类对象构造函数执行顺序：基类构造函数、对象成员构造函数、派生类本身的构造函数
- 静态成员函数不能使用`this`指针，其他的函数包括`virtual`函数等都可以使用`this`指针
- 若catch块采用异常类对象接收异常信息，则在抛出异常时将通过拷贝构造函数进行对象复制，异常处理完后才将两个异常对象进行析构，释放资源
- 下标运算符`[] ->`必须在类内些，不能写在类外重载
- The operator `::` can not be overloaded.
- 在类型转换符函数的定义中不需要声明返回类型 `double()`
- 模板函数的真正代码是在  源程序中调用函数时真正产生
- ![](images/Pasted%20image%2020240627192141.png)
- 定义了一个数组`int *p = new int[10]`，此时如果使用`delete p`，只会delete掉数组的第一个元素，内存泄漏
- ![|481](images/Pasted%20image%2020240628083215.png)
- 
## Old final
- 形如 `A a = b`其中b是一个已经定义好的class A，这里调用的是拷贝构造函数，而不是运载符重载
- default parameter其实是有指针类型决定的。A类型的指针对应着A类型的default parameter。A*=new B；中B仅仅决定分配的内存大小
- ![](images/Pasted%20image%2020240627203610.png)
- 就比如这道题目为 B  1
- manipulator are objects to be inserted or extracted into/from streams
- ![](images/Pasted%20image%2020240628080209.png)
- `throw;` 只有在catch子句中有效，把原本捕捉到的异常抛出，相当于把问题向上传递
- 
### 一些关于cast的问题
`static_cast`：用于基本数据类型的转换，基类的和派生类的转化，需要注意的是，派生类转化为基类安全，基类转化为派生类危险，同时注意不能转化`const,static`变量，不会进行类型检查，强制转化

`const_cast`，强制去掉`const`的常数特性，只能用于指针和引用
```cpp
const int a = 10; 
const int *p = &a; 
int *q; 
q = const_cast(p); 
*q = 20; 
cout << a << " " << *p << " " << *q << endl; 
cout << &a << " " << p << " " << q << endl;
```
输出结果为 10 20 20 三个地址相同

`reinterpret_cast` 运算符并不会改变括号中运算对象的值，而是对该对象从位 模式上进行重新解释，地址仍是一样的

`dynamic_cast`，在运行时进行类型检查，如果成功的，将返回指向类的指针或者引用，转换失败的话会返回NULL，转换时基类一定要有虚函数，这样转化才有意义，相比于`static_cast`，`dynamic_cast`的要求更高，更加不容易成功 **只有当基类指针或引用实际指向的是派生类对象时**

当且仅当某个数据类型能被隐式转换成为与该表达式相同类型时，`static_cast`才成立；换句话说，只要“大类型”相同，就能使用`static_cast`了，即使它在实际运行过程中可能是不安全的，因此父类和子类之间的上/下转换`static_cast`都能成立。但`dynamic_cast`则会在运行时进行检查，故上转换不一定能够成立。

- ![](images/Pasted%20image%2020240627210524.png)

### Exception 相关
![](images/Pasted%20image%2020240627212304.png)
`catch`的顺序
```cpp
#include <cstring>
#include <exception>
#include <vector>
#include <iostream>

using namespace std;

struct MyException : public exception {
    const char* what() const throw ()
    {
        return "C++ Exception";
    }
};
int main()
{
    try {
        throw MyException();
    } catch(MyException &s) {
        std::cout << "Catch the exception " << endl;
        std::cout << s.what() << endl;
    }
}
```
注意自定义类的`exception`如何书写
![](images/Pasted%20image%2020240628090405.png)


### 智能指针还得再看看
