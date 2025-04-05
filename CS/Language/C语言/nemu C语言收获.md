c 写头文件一定要记得防重定义条件编译
---
 结构体数组
```C
struct {
const char *name;
const char *description;
int (*handler) (char *);
} cmd_table [] = {
{{...}, {...} , ...
};
```

---
为函数参数添加一个bool类型便于验证是否成功使用函数
```C
int cmd_w(char *args){
if(args == NULL){
Log("Usage: w EXPR ");
return 0;
}
bool success;
set_wp(args, &success);
if(!success){
Log("Invalid expression: %s ", args);
}
return 0;
}
```
---
readline()
```C
#include <stdio.h>
#include <readline/readline.h>
#include <readline/history.h>
int main() {
    char *input;
    // 读取用户输入
    input = readline("Enter a string: ");
    // 打印输入的内容
    printf("You entered: %s\n", input);
    // 释放内存
    free(input);
    return 0;
}
```
---
strtok
```
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Hello,World,This,is,C";
    char *token;

    // 第一次调用，传入原始字符串
    token = strtok(str, ",");

    // 继续调用，直到返回 NULL
    while (token != NULL) {
        printf("Token: %s\n", token);
        token = strtok(NULL, ",");//`token = strtok(NULL, ",");` 是 `strtok` 函数的一种特殊用法，用于继续分割同一个字符串
    }

    return 0;
}
```
---
涉及指针一定记得检验NULL

---
几个有关字符串操作的函数strcmp strcat strncp
