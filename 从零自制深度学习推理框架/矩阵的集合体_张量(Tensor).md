- 对象
	- 三维_shapes
		- 通道数_channels
		- 行数_rows
		- 列数_cols
	- data_ 数据本身存储的数据空间


- 为了方便,我们的张量类将在叠加而成的三维矩阵`arma::fcube`的基础上提供扩充和封装，以使其更适用于我们的推理框架项目
- 简要介绍用到的arma库->Armadillo 是一个高效的 C++ 线性代数库，专注于矩阵运算和科学计算。它以易用性和高性能著称，提供了类似于 MATLAB 的语法接口，同时底层调用高度优化的线性代数库（如 LAPACK、BLAS 或 Intel MKL）。Armadillo 广泛应用于机器学习、信号处理、统计建模等领域。
- 为什么不直接把data_给用户->不方便用户调用
- 排序方式
	- 行主序->内存增长方向先行后列(pytorch)
	- 列主序->内存增长方向先列后行(armadillo)
- 方法
	- 创建张量(构造函数)
		- 一维:只有列
		- 二维
		- 三维
	- 返回张量的维度信息
		- row()
		- cols()
		- channels()->这个项目里有关通道数相关的命名挺乱的
		- size()
		- slice(uint32_t channel)返回矩阵
		- at(uint32_t channel, uint32_t row, uint32_t col)获得张量数据
	-  处理	
		- Fill()张量的填充
		- reshape()变形
		- Transform()依次处理张量信息
		- flatten()平铺, reshape()的特殊形式
		- padding(),按要求向周围填充
	- 辅助函数
		- empty()
		- raw_shapes()返回张量的shape
		- values()判断是行主序还是列主序
	
