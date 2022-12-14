# 1.python垃圾回收机制？
python的垃圾回收的话主要是通过引用计数为主，标记-清除和分代收集为辅;

python每创建一个对象都会加入一个环状双向链表，每个对象中都有一个引用计数器，用来标记对象被引用的次数，当值被多次引用时，不会开辟内存，而是引用计数器加1；当不在需要这个对象时，对象的引用计数变为0，会被垃圾回收；

其中标记清除和分类回收主要是针对可能存在循环引用的一些特殊对象的；


# 2.浅谈c++和Python的赋值操作符"="的区别?
c++的赋值操作总是默认执行拷贝；
对于一般的非指针变量执行深度拷贝，即拷贝的对象于原对象地址不共享；

```c++
//深拷贝
int a = 5;
int b = a;

```
对于指针类型的变量，赋值执行的是浅拷贝，地址共享；
```c++
//浅拷贝
int a = 8;
int *p;
p = &a;

//深拷贝
int a = 8;
int *p = new int;
*p = a;
```

c++如果要避免拷贝的话，可以用&符号，比如auto& a = b;


python的赋值操作对于可变对象的赋值使用的是引用，地址共享；
对于不可变对象的赋值采用的是深拷贝；


python的可变对象有 list,dict等；
不可变对象有 int ,float, tuple, string等；

思考：python的赋值操作对于可变对象默认采用引用赋值，主要原因在于节省时间和空间开销；
引用计数器记录一个对象被引用的次数，直到引用次数为0时销毁对象；

# 3.深拷贝和浅拷贝的区别

浓缩一句话：新旧对象的地址相不相同；