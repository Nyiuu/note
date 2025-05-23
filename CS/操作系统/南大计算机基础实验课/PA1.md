==Q==:如果没有寄存器, 计算机还可以工作吗? 如果可以, 这会对硬件提供的编程模型有什么影响呢?
==A==:我的回答是:可以,但速度会变慢
After asking AI:
### 对编程模型的影响

1. **内存直接操作**：
    - 编程将变得更加复杂，因为开发者需要直接管理内存，所有的数据和指令都必须从内存中读取和写入，这会增加编程的难度和出错的风险。 
2. **指令集架构变化**：
    - 当前基于寄存器的指令集（如x86、ARM）将不再适用，可能需要转向堆栈机或其他架构，这些架构不使用传统寄存器，而是依靠堆栈来存储数据。   
3. **编译器和编程语言的影响**：
    - 编译器将无法再为变量分配寄存器，所有变量必须存储在内存中，这会显著增加内存访问次数，从而影响性能。编程语言的实现和优化策略也将需要调整。
4. **计算机体系结构的重新设计**：
    - 缺乏寄存器将迫使重新设计数据路径和控制逻辑，可能需要更复杂的机制来补偿速度的损失，如更高效的内存管理或全新的架构设计。

CPU怎么知道现在执行到哪一条指令呢->
程序计数器-EIP(Extended Instruction Pointer)/ PC(Program Counter)通常叫第二个

从此以后, 计算机就只需要做一件事情:
```
while (1) {
  从PC指示的存储器位置取出指令;
  执行指令;
  更新PC;
}
```
TRM->turing machine

### 计算机是状态机
既然计算机是一个数组逻辑电路, 那么我们可以把计算机划分成两部分, 一部分由所有时序逻辑部件(存储器, 计数器, 寄存器)构成, 另一部分则是剩余的组合逻辑部件(如加法器等). 这样以后, 我们就可以从状态机模型的视角来理解计算机的工作过程了: 在每个时钟周期到来的时候, 计算机根据当前时序逻辑部件的状态, 在组合逻辑部件的作用下, 计算出并转移到下一时钟周期的新状态.

### 程序是状态机

现在我们就可以通过状态机的视角来解释"程序在计算机上运行"的本质了: 给定一个程序, 把它放到计算机的内存中, 就相当于在状态数量为`N`的状态转移图中指定了一个初始状态, 程序运行的过程就是从这个初始状态开始, 每执行完一条指令, 就会进行一次确定的状态转移. 也就是说, 程序也可以看成一个状态机! 这个状态机是大状态机(状态数量为`N`)的子集.

我们应以两个互补的视角看代码
- 代码:静态,描述精简,掌控大局
- 状态机:动态,描述复杂,理解局部

### NEMU的代码框架
```
nemu
├── configs                    # 预先提供的一些配置文件
├── include                    # 存放全局使用的头文件
│   ├── common.h               # 公用的头文件
│   ├── config                 # 配置系统生成的头文件, 用于维护配置选项更新的时间戳
│   ├── cpu
│   │   ├── cpu.h
│   │   ├── decode.h           # 译码相关
│   │   ├── difftest.h
│   │   └── ifetch.h           # 取指相关
│   ├── debug.h                # 一些方便调试用的宏
│   ├── device                 # 设备相关
│   ├── difftest-def.h
│   ├── generated
│   │   └── autoconf.h         # 配置系统生成的头文件, 用于根据配置信息定义相关的宏
│   ├── isa.h                  # ISA相关
│   ├── macro.h                # 一些方便的宏定义
│   ├── memory                 # 访问内存相关
│   └── utils.h
├── Kconfig                    # 配置信息管理的规则
├── Makefile                   # Makefile构建脚本
├── README.md
├── resource                   # 一些辅助资源
├── scripts                    # Makefile构建脚本
│   ├── build.mk
│   ├── config.mk
│   ├── git.mk                 # git版本控制相关
│   └── native.mk
├── src                        # 源文件
│   ├── cpu
│   │   └── cpu-exec.c         # 指令执行的主循环
│   ├── device                 # 设备相关
│   ├── engine
│   │   └── interpreter        # 解释器的实现
│   ├── filelist.mk
│   ├── isa                    # ISA相关的实现
│   │   ├── mips32
│   │   ├── riscv32
│   │   ├── riscv64
│   │   └── x86
│   ├── memory                 # 内存访问的实现
│   ├── monitor
│   │   ├── monitor.c
│   │   └── sdb                # 简易调试器
│   │       ├── expr.c         # 表达式求值的实现
│   │       ├── sdb.c          # 简易调试器的命令处理
│   │       └── watchpoint.c   # 监视点的实现
│   ├── nemu-main.c            # 你知道的...
│   └── utils                  # 一些公共的功能
│       ├── log.c              # 日志文件相关
│       ├── rand.c
│       ├── state.c
│       └── timer.c
└── tools                      # 一些工具
    ├── fixdep                 # 依赖修复, 配合配置系统进行使用
    ├── gen-expr
    ├── kconfig                # 配置系统
    ├── kvm-diff
    ├── qemu-diff
    └── spike-diff
```

方法->看不懂Makefile的时候,可以用make -nB查看make做了什么,由此来推断Makefile中的规则(现在的我还是倾向于问AI😢)

匿名联合体:
匿名联合体没有名称，其成员可以直接访问，而无需通过联合体变量。匿名联合体通常用于结构体中
```C
#include <stdio.h>

struct MyStruct {
    int type;
    union {
        int i;
        float f;
        char str[20];
    };  // 匿名联合体
};

int main() {
    struct MyStruct s;
    s.type = 1;
    s.i = 10;  // 直接访问匿名联合体的成员
    printf("s.i = %d\n", s.i);  // 输出: s.i = 10

    s.type = 2;
    s.f = 3.14;  // 直接访问匿名联合体的成员
    printf("s.f = %f\n", s.f);  // 输出: s.f = 3.140000

    return 0;
}
```

### ==必做题:实现x86的寄存器结构体==(不知道如何切换为x86,无法验证正确性,但学到了很多东西)
需要干的事:
1. 创建x86_CPU_state类型的变量cpu ✔
2. 将实际的寄存器架构与变量绑定 ---难点:
 - 怎么绑定?---给的枚举类型如何绑定给结构体中的变量->枚举的变量作为索引
 - ~~如何批量修改寄存器的值?--数组+遍历(注意用memcpy会有无法对齐的问题)~~->不需要初始化
3. 怎么让_16是_32的低16位...->匿名联合体

---
`do { ... } while (0)`在多行宏定义中非常有用
在宏定义中使用 `do { ... } while (0)` 是一种常见的编程技巧，**并不是多此一举**。它的作用是解决宏定义在展开时可能导致的语法问题，尤其是在宏被用作语句时。以下是对其作用的详细分析：

###  **为什么需要 `do { ... } while (0)`**

#### **问题背景**
- 宏定义是简单的文本替换，编译器在预处理阶段会将宏展开为代码。
- 如果宏定义中包含多条语句，直接使用 `{ ... }` 可能会导致语法错误或逻辑错误。

#### **示例：没有 `do { ... } while (0)` 的问题**
假设有以下宏定义：
```c
#define FOO(x) \
  { \
    printf("x = %d\n", x); \
    x++; \
  }
```

在以下代码中使用：
```c
if (cond)
  FOO(x);
else
  printf("cond is false\n");
```

宏展开后：
```c
if (cond)
  { \
    printf("x = %d\n", x); \
    x++; \
  };
else
  printf("cond is false\n");
```

- **问题**：
  - 宏展开后，`if` 语句后面多了一个分号 `;`，导致 `else` 无法与 `if` 匹配，编译错误。

---

### 2. **`do { ... } while (0)` 的作用**

#### **解决方案**
使用 `do { ... } while (0)` 可以解决上述问题：
```c
#define FOO(x) \
  do { \
    printf("x = %d\n", x); \
    x++; \
  } while (0)
```

在以下代码中使用：
```c
if (cond)
  FOO(x);
else
  printf("cond is false\n");
```

宏展开后：
```c
if (cond)
  do { \
    printf("x = %d\n", x); \
    x++; \
  } while (0);
else
  printf("cond is false\n");
```


### ==必做题:优美地退出==

为了测试大家是否已经理解框架代码, 我们给大家设置一个练习: 如果在运行NEMU之后直接键入`q`退出, 你会发现终端输出了一些错误信息. 请分析这个错误信息是什么原因造成的, 然后尝试在NEMU中修复它.

问题:make run->q->给出错误信息:
`make: *** [/home/nyiuu/workplace/ics2024/nemu/scripts/native.mk:38：run] 错误 1`
回到报错附近的代码:

```shell
NEMU_EXEC := $(BINARY) $(ARGS) $(IMG)

run-env: $(BINARY) $(DIFF_REF_SO)

run: run-env
$(call git_commit, "run NEMU")
$(NEMU_EXEC)

gdb: run-env
$(call git_commit, "gdb NEMU")
gdb -s $(BINARY) --args $(NEMU_EXEC)
```

以下是问完AI后本人对代码的理解:
- 变量NEMU_EXEC->运行,它继承了BINARY->可执行文件 && ARGS->命令行参数 && IMG->nemu运行的镜像文件
- $()->表示文件的路径
- ==最重要的部分==:问题出在哪儿
	- 首先看一下怎样会报错:直接输入q退出->报错 --- 按输入其他指令后再输入q->不报错
	- 说明在执行其他命令之前我们的nemu处于一种特殊的状态
	- 说明执行其他命令前nemu没有进入一个稳定的状态,并因为gdb的终止终止了nemu进程,而nemu可能~~未完成初始化或清理任务~~
	- 遇到的问题是在 NEMU 运行时直接输入 `q` 退出时报错，而输入其他指令后再输入 `q` 则不会报错。这表明问题可能与 NEMU 的运行时状态或资源管理有关，而不是初始化逻辑。
- 经过多次无意义的问题以后总结出来的高效利用AI完成本题的流程
	- 问AI : main函数里哪一个函数最有可能与报错相关
	- 进入可能影响的函数
	- 回到第一步
