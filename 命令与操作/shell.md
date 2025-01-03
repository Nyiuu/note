# file
- file 选项名 文件名
- 作用：检测文件类型
-  常用选项

| 选项            | 说明                      |
| ------------- | ----------------------- |
| `-i`          | 输出文件的 MIME 类型。          |
| `-b`          | 去掉文件名，仅显示文件类型。          |
| `-f <文件>`     | 从文件中读取文件列表，然后检测这些文件的类型。 |
| `-h`          | 检测符号链接本身的类型，而不是其目标的类型。  |
| `--extension` | 根据文件名的扩展名推断文件类型（不总是准确）。 |
| `-z`          | 检测压缩文件的内容类型。            |
| `--version`   | 显示 `file` 命令的版本信息。      |
# objdump
- objdump 选项 文件
- 作用：检查和分析二进制文件
-  常用选项总结

| 选项                  | 说明                |
| ------------------- | ----------------- |
| `-d`                | 反汇编所有可执行段。        |
| `-h`                | 显示文件的段头信息。        |
| `-x`                | 显示文件的所有头部信息。      |
| `-t`                | 显示文件的符号表。         |
| `-g`                | 显示调试信息（如果存在）。     |
| `-r`                | 显示重定位条目。          |
| `-T`                | 显示动态符号表（动态链接库）。   |
| `-s`                | 显示二进制内容（以十六进制形式）。 |
| `--disassemble=函数名` | 仅反汇编指定函数。         |
