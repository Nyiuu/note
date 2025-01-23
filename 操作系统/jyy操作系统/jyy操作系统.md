# ==0-绪论==
## ==01-操作系统概述==
- C + Python实现小功能——shell如何实现这些的？
- 模拟：一个CPU时钟周期可以包含：regs、csrs（Control and Status Registers（控制和状态寄存器））、memory                  *mini-rv32ima （一个github小项目，有空可以看看）*
- 一切都是状态机
	- 什么是状态机？——拥有严格数学定义的对象
- 历史小知识
	- 图灵的ENIAC是通过跳转真正的物理线路实现的跳转到下一条指令
	- 电子计算机：通过波的震动频率高低来实现0和1
	- bugs卡住继电器就没法改变电平了
	- 改进：通过磁铁磁性实现0和1——but I/O读写速度远低于CPU——改进
	- 高级语言和API诞生——but一行代码就得用一个卡片 return res;   （物理意义上的
	- 因为计算机太贵了，所以要排队用，因此要有一个operator（人）负责程序切换——操作系统的出现
	- 。。。
- How To Learn？
	- Just For Fun——我认同，但我能坚持干自己喜欢的事（悲
		- 看了Linus自传，发现这是Linus说的
## ==02-应用视角的操作系统==
- 程序
	- 需要补充的知识：
		- 直接gcc得到.out(即.o)文件？ —— `gcc a.c`[[csapp##1.2 程序被其他程序翻译成不同形式]]
		- file命令？——[[shell#file]]
		- objdump命令？——[[shell#objdump]]
		- --verbose？——即-v,详细模式每增加一个v,日志更详细
		- -Wl？——查看所有的链接选项 `gcc -Wl,opton1,opton2... `将参数（可以是路径）直接传递给链接器
		- ==end符号？==
		- -static？（静态链接选项，意味着所有依赖的库在编译期间会被直接嵌入到可执行文件中
		- ==gdb调试？==
		- RTFM？——reading the fucking manual（haha）
		- langchain？  ——意思是大语言模型IDE（很好奇是否是jyy自创的说法）——不是
		- SIGSEGV  ——SIGSEGV（Segmentation Violation）是一个常见的信号，表示程序试图访问非法的内存区域，通常是未分配的内存或已经释放的内存。它通常与Segmentation Fault（段错误） 相关，意味着程序发生了内存访问错误，导致操作系统终止该程序的运行。
		- 指令集？
		- syscall？——系统调用：程序从用户模式到内核模式的桥梁
	- 按照上一节的模拟程序，程序无法自己停下来、操作系统无法切断电源（指令集里没有）——特别的   指令：syscall：让操作系统接管程序
	- strace工具——查看syscall调用流程
	- 所有的窗口是程序调用窗口管理器绘制的 
	- 每一个栈桢都包含一个PC位
	- 编译器——状态机之间的转换器
	- 函数调用时需要留一个寄存器给栈
	- `gcc -O2 -c example.c` 将会生成：一个名为 `example.o` 的目标文件,使用 `-O2` 标志进行性能优化。
	- 编译器优化的“三板斧”
		- 函数内联
		- 常量传播
		- 死代码消除
	- 系统调用是不可优化的


-   everything is a state machine -> 看不懂的makefile也能像程序一样通过不断的trace简化它😆
- 