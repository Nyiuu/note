- 使用缓冲流而不是使用buffer的原因，读取时的便利
-   流有几种bits state
	- G--good
	- B--Bad
	- EOF--到达末尾
	- F--Fail，指针会回到开头
- 缓冲流之所以叫缓冲，是因为在到达'endl'之前，流都进入了缓存，如果每次I/O都刷新缓冲区让程序速度变慢
- `std::endl` 是一个用于输出流的操纵符（manipulator），它主要完成两个操作：
	1. 插入换行符 `'\n'`   
	2. 强制刷新输出缓冲区
- 仅插入换行符，不强制刷新缓冲区。
- 有些时候类型太长了可以取别名(但是个人感觉大项目这样不利于理解源码)
- 