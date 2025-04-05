
size_t strlen(const char* s);                占位符%zu

int strcmp(const char* s1, const char* s2 );            ——注意是比较字符串，不是字符

char* strcat(char* dest, const char* src);               ——src连接到dest尾部返回值：成功：返回dest字符串的首地址  / 失败：NULL

scanf()在输入数据时  读到空格(space)，制表符(\t)，换行符(\n)会停止！


sizeof（计算字符串内存大小） 和 strlen（[计算字符串长度](https://so.csdn.net/so/search?q=%E8%AE%A1%E7%AE%97%E5%AD%97%E7%AC%A6%E4%B8%B2%E9%95%BF%E5%BA%A6&spm=1001.2101.3001.7020)）  **返回类型： %zd**

puts只能输出字符串，不能是字符，并且不换行

fgets(str, sizeof(str), stdin);   

char ch = getchar(); // 读取一个字符 
putchar(ch); // 输出该字符

---

### **1. 输入输出函数**

这些函数主要用于从键盘读取输入或者向屏幕输出数据，定义在 `stdio.h` 中。

#### 常用函数：

- **`printf`**：格式化输出
    
    ```c
    printf("Hello, %s! You are %d years old.\n", "Alice", 25);
    ```
    
- **`scanf`**：格式化输入
    
    ```c
    int age;
    scanf("%d", &age); // 读取一个整数
    printf("You entered: %d\n", age);
    ```
    
- **`gets` (已废弃)** 和 **`fgets`**：读取字符串
    
    ```c
    char str[50];
    fgets(str, sizeof(str), stdin); // 从输入中读取一行字符串
    printf("You entered: %s", str);
    ```
    
- **`putchar`** 和 **`getchar`**：读取/写入单个字符
    
    ```c
    char ch = getchar(); // 读取一个字符
    putchar(ch);         // 输出该字符
    ```
    

---

### **2. 字符串处理函数**

这些函数定义在 `string.h` 中，用于处理字符串操作。

#### 常用函数：

- **`strlen`**：计算字符串长度
    
    ```c
    char str[] = "Hello, world!";
    printf("Length: %zu\n", strlen(str));
    ```
    
- **`strcpy` 和 `strncpy`**：复制字符串
    
    ```c
    char dest[20];
    strcpy(dest, "Hello");
    printf("%s\n", dest); // 输出 "Hello"
    ```
    
- **`strcat` 和 `strncat`**：拼接字符串
    
    ```c
    char str1[20] = "Hello";
    strcat(str1, ", world!");
    printf("%s\n", str1); // 输出 "Hello, world!"
    ```
    
- **`strcmp`**：比较两个字符串
    
    ```c
    if (strcmp("apple", "banana") < 0) {
        printf("apple comes before banana\n");
    }
    ```
    
- **`strchr`**：查找字符第一次出现的位置
    
    ```c
    char *pos = strchr("Hello, world!", 'w');
    printf("Character found at: %s\n", pos);
    ```
    
- **`strstr`**：查找子字符串
    
    ```c
    char *found = strstr("Hello, world!", "world");
    printf("Substring found: %s\n", found);
    ```
    

---

### **3. 数学函数**

数学函数定义在 `math.h` 中，处理常见的数学运算。

#### 常用函数：

- **`pow`**：计算幂次
    
    ```c
    printf("2^3 = %.2f\n", pow(2, 3)); // 输出 "2^3 = 8.00"
    ```
    
- **`sqrt`**：计算平方根
    
    ```c
    printf("sqrt(16) = %.2f\n", sqrt(16)); // 输出 "sqrt(16) = 4.00"
    ```
    
- **`sin`, `cos`, `tan`**：三角函数（弧度制）
    
    ```c
    printf("sin(pi/2) = %.2f\n", sin(3.14159 / 2));
    ```
    
- **`ceil` 和 `floor`**：向上/向下取整
    
    ```c
    printf("ceil(3.2) = %.2f, floor(3.7) = %.2f\n", ceil(3.2), floor(3.7));
    ```
    
- **`fabs`**：计算绝对值
    
    ```c
    printf("fabs(-3.14) = %.2f\n", fabs(-3.14));
    ```
    

---

### **4. 动态内存管理函数**

动态内存函数定义在 `stdlib.h` 中，用于申请和释放内存。

#### 常用函数：

- **`malloc`**：分配内存
    
    ```c
    int *arr = (int *)malloc(5 * sizeof(int)); // 分配5个整数大小的内存
    ```
    
- **`calloc`**：分配并初始化内存
    
    ```c
    int *arr = (int *)calloc(5, sizeof(int)); // 分配5个整数大小并初始化为0
    ```
    
- **`realloc`**：调整已分配内存大小
    
    ```c
    arr = (int *)realloc(arr, 10 * sizeof(int)); // 扩展到10个整数大小
    ```
    
- **`free`**：释放内存
    
    ```c
    free(arr);
    ```
    

---

### **5. 时间和日期处理函数**

时间和日期函数定义在 `time.h` 中，用于获取和操作时间。

#### 常用函数：

- **`time`**：获取当前时间
    
    ```c
    time_t t = time(NULL);
    printf("Current time: %s", ctime(&t));
    ```
    
- **`clock`**：获取程序运行时间
    
    ```c
    clock_t start = clock();
    // 一些耗时操作
    clock_t end = clock();
    printf("Execution time: %.2f seconds\n", (double)(end - start) / CLOCKS_PER_SEC);
    ```
    

---

### **6. 随机数生成函数**

随机数生成函数定义在 `stdlib.h` 中。

#### 常用函数：

- **`rand`**：生成随机数
    
    ```c
    printf("Random number: %d\n", rand());
    ```
    
- **`srand`**：设置随机数种子
    
    ```c
    srand(time(NULL)); // 使用当前时间作为种子
    printf("Random number: %d\n", rand());
    ```
    

---

### **7. 文件操作函数**

文件操作函数定义在 `stdio.h` 中，用于文件的读写。

#### 常用函数：

- **`fopen` 和 `fclose`**：打开和关闭文件
    
    ```c
    FILE *file = fopen("example.txt", "r");
    if (file) {
        fclose(file);
    }
    ```
    
- **`fgets` 和 `fputs`**：读写文件中的字符串
    
    ```c
    char line[100];
    fgets(line, sizeof(line), file); // 从文件读取一行
    ```
    
- **`fread` 和 `fwrite`**：读写文件中的数据
    
    ```c
    int buffer[10];
    fread(buffer, sizeof(int), 10, file);
    ```
    
- **`fprintf` 和 `fscanf`**：格式化读写文件
    
    ```c
    fprintf(file, "Hello, %s!\n", "world");
    ```
    

--- 

### **1. 字符分类函数**

这些函数用来判断某个字符是否属于某种特定的类别，返回值为 **非零值** 表示 **真**，**0** 表示 **假**。

| **函数**         | **描述**               | **示例**                    |
| -------------- | -------------------- | ------------------------- |
| **`isalnum`**  | 判断字符是否为字母或数字         | `isalnum('A')` -> 非零值（真）  |
| **`isalpha`**  | 判断字符是否为字母            | `isalpha('a')` -> 非零值（真）  |
| **`isdigit`**  | 判断字符是否为数字            | `isdigit('5')` -> 非零值（真）  |
| **`isxdigit`** | 判断字符是否为十六进制数字        | `isxdigit('F')` -> 非零值（真） |
| **`islower`**  | 判断字符是否为小写字母          | `islower('b')` -> 非零值（真）  |
| **`isupper`**  | 判断字符是否为大写字母          | `isupper('C')` -> 非零值（真）  |
| **`isspace`**  | 判断字符是否为空白字符（如空格、换行等） | `isspace('\n')` -> 非零值（真） |
| **`ispunct`**  | 判断字符是否为标点符号          | `ispunct('!')` -> 非零值（真）  |
| **`isprint`**  | 判断字符是否为可打印字符（包括空格）   | `isprint(' ')` -> 非零值（真）  |
| **`iscntrl`**  | 判断字符是否为控制字符（如回车、ESC） | `iscntrl('\n')` -> 非零值（真） |

---

### **2. 字符转换函数**

这些函数用于改变字符的大小写或格式。

| **函数**        | **描述**     | **示例**                  |
| ------------- | ---------- | ----------------------- |
| **`tolower`** | 将字符转换为小写字母 | `tolower('A')` -> `'a'` |
| **`toupper`** | 将字符转换为大写字母 | `toupper('b')` -> `'B'` |

