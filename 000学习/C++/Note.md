- 动态变量不能直接访问，要用指针(动态变量就是在堆上创建的变量)
- scorePtr = new int创建一个int类型的动态变量，并让scorePtr指向它
- 函数指针的缺点（C中将函数当作参数传递的唯一方法）
	- 无法持有自己的状态
	- 无法再次经过修饰并使用
- 仿函数：重载括号以使用看起来像函数的东西
- `placement new` ——自定义分配内存，减少动态内存分配的开销
- `size_t `无符号整数类型
- `ptrdiff_t`有符号整数类型，用于计算差值
- `static_cast`类型转换运算符
- `operator new` 不初始化内存    new调用对象的构造函数初始化对象
- `::operator + 运算符` ->调用全局作用域函数 
- `inline + 返回类型 + 函数名（参数列表）{ 函数体}`-> 请求编译器将函数嵌入到每个调用它的位置，通常用于小函数或频繁调用的函数（如标准库中的）以提高执行效率
- 习惯用`auto`呀
- lambda可以用在任何需要函数指针的地方
	- `[](){...}`
	- `[]`内是捕获的外部变量,为什么要这样呢?->因为我们的匿名函数内部也许需要一些外部的变量
	- `[]`内常用`&` ,`=`, 一个是捕获所有的引用,一个是值
- 函数是存储在内存中的,函数名实际上是指向这个地址的指针名
- 类中定义的成员隐含访问权限是私有
- 类的静态成员和成员函数不通过对象也能访问
- `bool x = 5`时`x == true`,因此在转换为`int`类型时,依然会变为`1`
- `const`常量不能被修改,因此在定义时要初始化,但直接`const double *t`这样是可行的,因为const只是代表不能修改指向的值,但是我们可以不用立马确定指向啥
- 不能直接在类内部对非静态成员进行初始化
- 没有unsigned float
- 对于 `a && b`,只要`a`为假,就不会再求值`b`
- 模板只有在我们实际调用它时才会创建,因此如果只定义了未调用甚至不能在编译时发现它的错误 
- 模板类要把定义放在头文件中
- `vector <T> (s.begin(), s.end(), swap(s))` 可以释放向量容器多余的空间
-  `dequee` 在向两端插入元素的时候原来的迭代器会失效
- `cin` 和 `getline`不要混用，因为`getline`会读cin剩下来的换行符
- `close(0/1/2)` 关掉标准输入/输出/错误输出
- 在C++中，`explicit`关键字用于修饰构造函数或转换函数，以防止隐式类型转换和复制初始化。当你在构造函数前使用`explicit`时，它告诉编译器不要使用该构造函数进行隐式类型转换。
- 
```cpp
bool is_value_node_ = false;  // 拷贝初始化
bool is_value_node_{false};   // 直接初始化（推荐）
```
- wstring
	- 是 C++ 标准库中用于处理宽字符字符串，使得程序能够处理多种语言的文本
	- 关键点：
	- L 前缀: 在宽字符串字面量前必须加上 L，例如 L"你好"。单个宽字符则用 L'你'。
	- 宽字符 I/O: 使用 std::wcin 进行输入，std::wcout 进行输出。为了正确显示非 ASCII 字符，通常需要配置本地化设置（std::locale）。控制台/终端本身也需要支持相应的字符编码。
