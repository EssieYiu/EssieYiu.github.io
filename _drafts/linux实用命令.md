# linux 实用命令

### grep

#### egrep

```bash
egrep [command line options] <pattern> [path]
```

例如：

```bash
egrep -i 'picoCTF' *
egrep 'mellon' text.txt
```

##### 正则表达式

一些常见的基本正则表达式如下

- **.** （点）单个字符
- **?** 它前面的字符仅匹配0次或1次
- ***** 它前面的字符匹配次数大于等于0
- **+** 它前面的字符匹配次数大于等于1
- **{n}** 它前面的字符匹配次数为n次
- **{n,m}** 它前面的字符匹配次数大于等于n且小于等于m
- **[agd]** 出现的字符是中括号里面的其中之一
- **[^agd]** 出现的字符不能是中括号里面的其中之一
- **[c-f]** 中间的杠表示一个范围，在这里是c到f之间的字符
- **()** 允许我们将几个字符分成一组
- **|** 逻辑或运算
- **^** 匹配字串的开头
- **$** 匹配字串的末尾

### strings 

在对象文件或二进制文件中查找可打印的字符串。字符串是4个或更多可打印字符的任意序列，以换行符或空字符结束。strings命令对识别随机对象文件很有用。

```bash
-a --all 扫描整个文件
-f -print-file-name 在显示字符串前先显示文件名
-n –bytes=[number]：找到并且输出所有NUL终止符序列
- ：设置显示的最少的字符数，默认是4个字符
-t --radix={o,d,x} ：输出字符的位置，基于八进制，十进制或者十六进制
-o ：类似--radix=o
-T --target= ：指定二进制文件格式
-e --encoding={s,S,b,l,B,L} ：选择字符大小和排列顺序:s = 7-bit, S = 8-bit, {b,l} = 16-bit, {B,L} = 32-bit
@ ：读取中选项
```

配合grep使用

```bash
strings -a filename | grep pico
```

### pipe 管道

### 重定向

command > file将输出重定向到file

command < file 将输入重定向到file

command >> file 将输出以追加的方式重定向到file

n > file 将文件描述符为n的文件重定向到file文件

n < file 将文件描述符为n的文件以追加的方式重定向到file

n >& m 将输出文件n和m合并

n <& m 将输入文件n和m合并

<< tag 将开始标记tag和结束标记tag之间的内容作为输入

文件描述符

- 0（STDIN标准输入）
- 1（STDOUT标准输出）
- 2（STDERR标准错误输出）

例如

```bash
user@shell:/$ ./in-out-err 1> ~/out 2> ~/err
```

### cat

用于连接文件并打印到标准输出设备上

**-n 或 --number**：由 1 开始对所有输出的行数编号。

**-b 或 --number-nonblank**：和 -n 相似，只不过对于空白行不编号。

**-s 或 --squeeze-blank**：当遇到有连续两行以上的空白行，就代换为一行的空白行。

**-v 或 --show-nonprinting**：使用 ^ 和 M- 符号，除了 LFD 和 TAB 之外。

**-E 或 --show-ends** : 在每行结束处显示 $。

**-T 或 --show-tabs**: 将 TAB 字符显示为 ^I。

**-A, --show-all**：等价于 -vET。

**-e：**等价于"-vE"选项；

**-t：**等价于"-vT"选项；

### wc

用于计算字数

-c 或 --bytes 或 --chars 只显示bytes数

-l 或 --lines 只显示行数

-w 或 --words只显示字数

### env

显示所有的环境变量

## gdb使用

#### disas反汇编

```bash
gdb-peda$ disas main
```

#### break断点设置

```bash
gdb-peda$ break 3
gdb-pead$ break *0x00000000004008df
gdb-peda$ break *main
gdb-peda$ break *(main+132)
```

#### 格式化输出

```bash
gdb-peda$ printf "%s", (char*)flag_buf
```

