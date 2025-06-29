- `void foo() noexcept{...}` noexcept表明不会抛出异常
- 智能指针unique_ptr `std==unique_ptr<T> ptr = std==make_unique<T>()`
- 常量表达式constexpr,使编译器能在编译时将表达式直接优化并植入到程序运行
```C++
int len = 10;
// char arr_3 [ len ];  非 法(某些编译器)
constexpr int len_2_constexpr = 1 + 2 + 3;
char arr_4 [ len_2_constexpr ]; // 合 法
```
- 从 C++14 开始，constexpr 函数可以在内部使用局部变量、循环和分支等简单语句，但C++11不可以
- C++17实现:将临时变量放到if语句中
```C++
if ( const std :: vector<int> :: iterator itr = std :: find ( vecor<int>.begin () , vec.end () , 3)
	;
```
- C++11开始,将初始化列表的概念绑定到了类型上,使类\数组\类以统一的方式进行初始化
```C++
std::vector<int> vec;
for ( std :: initializer_list<int> :: iterator it = list.begin() ; it != list.end () ; ++it ) {
	 vec.push_back(*it) ;
 }
```
- C++17结构化绑定
```C++
[[include]]<iostream>
[[include]]<tuple>

std==tuple<int, double, std==string> f() {
return std::make_tuple(1, 2.2, "abc");
}

int main()
{
auto [x, y, z] = f();

std==cout << x << "," << y << "," << z << std==endl;
return 0;
}
```
- auto不能用于函数传参(显然) \ 推导数组类型 \ 
- decltype `decltype(expression)` 是查询类型的表达式, 解决了auto只能推导类型的缺陷
- C++11引入尾返回类型
```C++
template<tpename T, typename U>
auto add(T x, U y) -> decltype(x+y){
	return x + y;
}
```
- 从 C++14 开始是可以利用auto直接让普通函数具备返回值推导           `auto add(T x, T y) {return x+y;}`
- decltype(auto) 是 C++14 开始提供的一个略微复杂的用法,主要用于对转发函数或封装的返回类型进行推导
- C++17 引入`if constexpr()` ,能够让代码在编译的时候就能通过穿入参数的不同进行分支判断,
- C++11 引入了基于范围的迭代写法 `for ( auto element : vec )`
- 模板的哲学在于将一切能够在编译期处理的问题丢到编译期进行处理，仅在运行时处理那些最核心的动 态服务，进而大幅优化运行期的性能
- C++11 引入了外部模板，扩充了原来的强制编译器在特定位置实例化模板的语法，使我们能 够显式的通知编译器何时进行模板的实例化,缩短编译时间
```C++
template class std::vector<bool>;// 强 行 实 例 化
extern template class std::vector<int>;// 不 在 该 当 前 编 译 文 件 中 实 例 化 模 板
```
- 类型与模板的关联:模板是用来产生类型的(类型的产生基于模板的需求?
- C++11引入类型别名模板`using TrueDarkMagic = MagicType < std:: vector<T>, std::string >;` 
- C++11指定模板的默认参数
```C++
template<tpename T = int, typename U = int>
auto add(T x, U y) -> decltype(x+y){
	return x + y;
}
```
- 变长参数模板,在 C++11 之前，无论是类模板 还是函数模板，都只能按其指定的样子，接受一组固定数量的模板参数；而 C++11 加入了新的表示方 法，允许任意个数、任意类别的模板参数，同时也不需要在定义时将参数的个数固定:`template < typename Require , typename ... Args > class Magic ;` ,为编写变长参数函数提供了便捷的手段
- 对变长模板的参数解包
 计算个数
```C++
void magic ( Ts ... args ) {
std==cout << sizeof ...( args ) << std==endl;
}
```
解包参数:法一:递归   法二:C++17引入的变参模板展开(还记得if constexpr吗)
```C++
templcate<typename T0, typename... T>
void printf(T0 to, T... t){
	std==cout << to << std==endl;
	if cosntexpr (sizeof...(t) > 0) 
		printf(t...)
}
```
- C++17引入:非类型模板参数推导,并能使用auto推导
- C++11 引入了委托构造的概念，这使得构造函数可以在同一个类中一个构造函数调用另一个构造函 数，从而达到简化代码的目的
- 在传统 C++ 中，构造函数如果需要继承是需要将参数一一传递的，这将导致效率低下。C++11 利 用关键字 using 引入了继承构造函数的概念
```C++
class Subclass : public Base {  
public :  
using Base :: Base ; 
};
```
- C++11引入override(明确一个函数是重写基类的派生类,并且编译器会检查基类是否有该函数) 和 final(防止派生类重写该函数) 这两个关键字
- C++11显示禁用或使用默认函数
```C++
Magic () = default ; // 显 式 声 明 使 用 编 译 器 生 成 的 构 造
Magic & operator =( const Magic &) = delete ; // 显 式 声 明 拒 绝 编 译 器 生 成 构 造
```
- C++11引入枚举类,实现了类型安全`enum class new_enum` 
- Lambda表达式
```C++
[捕获列表](参数列表) mutable (可选) 异常属性 -> 返回类型 {
//函数体
}
```
- 捕获列表的几种类型
	1. 值捕获 与参数传值类似，值捕获的前提是变量可以拷贝，不同之处则在于，被捕获的变量在 lambda 表达式被创建时拷贝，而非调用时才拷贝,也就是说捕获变量后若变量改变,捕获的变量的值并不会变
	2.  引用捕获 因为是保存的引用,所以变量改变值会发生改变
	3. 隐式捕获
		- `[]`空捕获列表
		- `[name1, name2,...]`捕获一系列变量
		- `[&]` 引用捕获, 让编译器自行推导捕获列表
		- `[=]` 值捕获, 让编译器执行推导引用列表
	4. 表达式捕获 之前的只能捕获右值,不能捕获左值,而这个方式可以捕获左值 类似`v1 = f()` ,将表达式赋值给变量,由编译器自行推断
- 泛型Lambda : auto 关键字不能够用在参数表里，这是因为这样的写法会与模板的功能产生冲突,但Lambda 表达式并不是普通函数，所以 Lambda 表达式并不能够模板化,**but** C++14 开始，Lambda 函数的形式参数可以使用 auto 关键字来产生意义上的泛型
- 函数对象包装器 funcational以后就可以f(n)这样调用了(和scheme中的define定义函数的方式很像)
```cpp
using foo = void(*)(int);
void std::functional(foo f);

//
int foo(int para){return para};
std::functional <int(int)> f = foo;
```
- 参数绑定
```cpp
int foo(int a, int b, int c)
{;}
int main(){
auto bindfoo = std==bind(foo, std==placeholders::_1, 1, 2);
bindfoo(1);
//这里用std==placeholders==_1对第一个参数进行占位
}
```

- 右值引用 
	- 将亡值 (xvalue, expiring value)，是 C++11 为了引入右值引用而提出的概念（因此在传统 C++ 中，纯右值和右值是同一个概念），也就是即将被销毁、却能够被移动的值。
	- 需要拿到一个将亡值，就需要用到右值引用的申明：T &&
	- C++11 提供了 std::move 这个方法将左值参数无条件的转换为右值，有了它我们就能够方便的获得 一个右值临时对象
- 移动语义
```cpp
A ( A && a ) : pointer ( a . pointer ) {
a. pointer = nullptr ;
}	

//...

v . push_back ( std :: move ( str ) ) ;  //减少拷贝出现的开销 
```
- 完美转发:无论模板参数是什么类型的引用，当且仅当实参类型为右引用时，模板参数才能被推导为 右引用类型
	- 使用std::forward
- 线性容器 std::array,对象大小固定,