# 计算机的微分方式
- 符号微分--人把公式化简之后再交给计算机去算
- 数值微分--人工设定一个很小的delta x
- 自动微分--链式法则+基本运算+表达式追踪
# 自动微分模式
- 前向
	- ![[Pasted image 20250719030818.png]]
	- ![[Pasted image 20250719031055.png]]
	- 这样以后其实只得到了x1的导数，因此还需要反向传播
- 后向
	- ![[Pasted image 20250719031216.png]] 
	- ![[Pasted image 20250719031343.png]]
	- 适用于输出结果只有一个
- 雅可比矩阵
	- ![[Pasted image 20250719032427.png]]
	- ![[Pasted image 20250719032552.png]]
	- ![[Pasted image 20250719032733.png]]
	- ![[Pasted image 20250719032848.png]]
	- 显然神经网络更适合反向传播


# 具体实现方式
- ![[Pasted image 20250719040401.png]]
	- ![[Pasted image 20250719040718.png]]
	- ![[Pasted image 20250719040936.png]]
		- ![[Pasted image 20250719041212.png]]
	- ![[Pasted image 20250719041338.png]]
		- ![[Pasted image 20250719041455.png]]
	- 