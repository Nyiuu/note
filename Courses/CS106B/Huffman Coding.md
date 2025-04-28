- https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1224/resources/huffman.html
- 应用：压缩
- 思想：根据字符使用频率决定编码序列长短，节省空间
- 霍夫曼编码的一个重要特性是_前缀属性_ ：任何字符的编码都不是其他字符的前缀（例如，如果 `h` 的编码为 `01` ，则其他任何字符的编码都不会以 `01` 开头，也不会有任何字符被编码为 `0` ）。有了这种保证，解码过程中确定边界时就不会出现歧义
- 构建最优编码树
	1. 根据出现次数获取每个字符权重
	2. 根据权重为每个字符创建一棵树，获得一片森林
	3. 将权重最小的的两棵树合并，新树的权重等于二者之和
	4. 新树添加回森林
	5. 重复步骤3-4，直到森林里只有一棵树
	- 开始
	- ![begin](https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1224/resources/img/huffman/forest1.png)
	- 结束
	- ![end](https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1224/resources/img/huffman/forest6.png)
- 解码
	- 典型的策略是将编码数据与所用编码的附加信息打包在一起。这些信息是树的“扁平化”版本，通过遍历编码树并记录树结构以及每个字符的位置来创建。为了解码文件，扁平化的表示会被重新扩展以生成原始编码树的副本，然后用于解码位序列。