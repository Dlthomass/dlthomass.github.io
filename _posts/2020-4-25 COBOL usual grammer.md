COBOL语法简介ZZ (2013-09-12 16:29:38)转载▼
标签： 杂谈	分类： COBOL
一．COBOL程序的结构

1．部

IDENTIFICATION DIVISION 标识部

ENVIRONMENT DIVISION 环境部

DATA DIVISION 数据部

PROCEDURE DIVISION 过程部

2．节（SECTION）和段（PARAGRAPH）

（1）部-节-段

（2）标识部下面不设节，直接设段

（3）过程部可以设节，下面再设段，也可以直接设段

3．句子、语句和子句

每一段由若干句子（Sentence）组成，一个句子以句号加上一个以上的空格来结束。

句子由语句（Statement）组成。

语句中又可以包含若干子句（clause），每一个子句也有一个动词（但这个动词往往是可以省略的），它指定某一方面的特定功能。

二．COBOL源程序的书写格式

1．1-6列：标号区

2．第7列：续行标志区（“-”为续行，“*”为注解）

3．8-11列：A区（部头，节头，段头，层号01、77，文件描述符FD等）

4．12-72列：B区（正文）

5．73-80列：注释区

三．COBOL字符

数字0-9，大写字母A-Z，小写字母a-z，

专用字符15个{ + - * / = , . ; ‘ ( ) < > $ 空格 }

四．常量

1．数值常量

（1）小数点不能多于一个，而且不能出现在常数最右边。

（2）数值常量的长度不能超过18位数字。

（3）至少要有一个数字，不能有多于一个符号。

（4）数字间不能有空格，空格是分界符。

2．非数值常量

（1）用’’把字符串包起来

（2）假如要把’’放到非数值常量中，用QUOTE保留字，

如 MOVE QUOTE ‘CHINA’QUOTE TO A

（3）长度不应超过120个字符。

五．COBOL的数据关系

过程部初步

一．输入输出语句

1．ACCEPT（接收语句）：直接从中断键盘或系统指定的输入设备上输入少量的数据。

语法：ACCEPT 标识符 [FROM 助忆名]

2．READ（读语句）：从外部文件上读入数据输到程序中的数据项中。

语法：READ 文件名 RECORD [INTO 标识符][；AT END 执行语句]

3．WRITE（写语句）：将内存区中的数据输出到外部设备

语法：

WRITE 记录名 [FROM 标识符1][BEFORE ADVANCING 标识符2/整数 LINE/LINES]

AFTER 助忆名/PAEG

4．OPEN（打开语句）：程序若要读和写文件，先要把文件打开

语法：OPEN INPUT/OUPUT 文件名1[，文件名2……]

5．CLOSE（关闭语句）：关闭文件。

语法：CLOSE 文件名1[，文件名2……]

二．算术运算语句

1．ADD（加法语句）

举例：ADD A TO B A+BaB

ADD 15 TO C 15+CaC

ADD A，B TO C A+B+CaC

ADD 15，25 TO C 15+25+CaC

ADD A，B GIVING C A+B–C

ADD 15，25 GIVING T 15+25aT

ADD A，B TO C，D A+B+CaC,A+B+DaD

2．SUBTRACT（减法语句）

举例：SUBTRACT B FROM A A-BaA

SUBTRACT B，C FROM A A-B-CaA

SUBTRACT B，C FROM A，T A-B-CaA,T-B-CaT

SUBTRACT B，C FROM A GIVING X A-B-CaX

3．MULTIPLY（乘法语句）

举例：MULTIPLY A BY B A*BaB

MULTIPLY 0.5 BY B 0.5*BaB

MULTIPLY A BY B GIVING C A*BaC

MULTIPLY 1.5 BY 3 GIVING C,A 1.5*3aC,1.5*3aA

MULTIPLY A BY B,C A*BaB,A*CaC

4．DIVIDE（除法语句）

举例：DIVIDE A INTO B B/AaB

DIVIDE A INTO B GIVING C B/AaC

DIVIDE A BY B GIVING C A/BaC

5．COMPUTE（计算语句）

语法：COMPUTE 标识符1[，标识符2]……=算术表达式

举例：COMPUTE T = （A + B） * C / D

注意：（1）所以运算符两侧应留一空格

（2）括号外侧应留空格，内侧可不要留空格

三．MOVE（传送语句）

语法：MOVE 标识符1/常量1 TO 标识符2[，标识符3]……

四．GOTO（转移语句）

语法：（1）GO TO 过程名

（2）GO TO 过程名1[，过程名2]……过程名n，DEPENDING ON 标识符

五．IF（条件语句）

1．关系运算符

 

COBOL关系运算符 意义

IS GREATER THAN

IS > THAN 大于

IS LESS THAN

IS < THAN 小于

IS EQUAL TO

IS = TO 等于

NOT GREATER THAN

NOT > 不大于

NOT LESS THAN

NOT < 不小于

NOT EQUAL TO

NOT = 不等于

2．IF语句的两种形式

（1）IF 条件 语句组

（2）IF 条件 语句组1 ELSE 语句组2

3．IF语句的一般格式

IF 语句组1/NEXT SENTENCE [ELSE 语句组2/NEXT SENTENCE]

六．STOP（停止语句）

语法：STOP RUN/常量

标识部和环境部

一．标识部

1．必写部分

IDENTIFICATION DIVISION

PROGRAM-ID. 程序名.

2．任选部分

[AUTHOR 作者姓名.]

[INSTALLATION. 计算机设置的场所.]

[DATE-WRITTEN. 源程序编写的日期.]

[DATE-COMPILED. 源程序编译的日期.]

[SECURITY. 保密程度.]

二．环境部

1．环境部的一般形式

ENVIRONMENT DIVISION. （环境部）

CONFIGURATION SECTION. （配置节）

SOURCE-COMPUTER. 源计算机名

OBJECT-COMPUTER. 目标计算机名

[SPECIAL-NAMES. 专用名描述项]

[INPUT-OUTPUT SECTION. （输入输出节）

FILE-CONTROL. {文件描述体}……

[I-O-CONTROL. 输入输出控制描述体]]

2．配置节（CONFIGURATION SECTION）

（1）源计算机段和目标计算机段的一般格式

SOURCE-COMPUTER.

OBJECT-COMPUTER.

[MEMORY SIZE IS 整数{WORDS/CHARACTERS/MODULES}]

（2）专用名段

格式：SPECIAL-NAMES.

[DECIMAL-POINT IS COMMA.]

[CURRENCY SIGN IS 非数值常量.]

[专用名 IS 助记名.]

3．输入输出节（分为输入输出控制段与文件控制段）

文件控制段

格式：INPUT-OUTPUT SECTION. （输入输出节）

FILE-CONTROL. （文件控制段）

SELECT 文件名 ASSIGN TO 外部文件名.

说明：SELECT的三种用法

（1）       在SELECT子句的“ASSIGN TO”的后面写上磁盘上实际的文件名。

（2）       在SELECT子句中只指出外部设备名。

（3）       在一些中、大型计算机系统，在SELECT子句中用该系统指定的逻辑名作为外部文件名，然后用作业控制语句将该逻辑名与实际的设备和文件相联系。

数据部（一）

一．概述

1．数据有两种：孤立的数据项，组合的数据项

2．数据的层次与层号

（1）数据的层次结构：记录a组合项a初等项

（2）层次的规定如下：

用来描述数据层次结构的层号从01开始，到49。记录的最高层次定为01号。

层号小的组合项包含层号大的数据项（组合项或初等项）。

一个层号为K的组合项包括它下面所有层号比它大的组合项和初等项，直到遇到层号小于K或等于K的层次为止。

3．数据部的结构

（1）文件节（FILE SECTION）

用来描述程序中用到的输入文件和输出文件及其记录中各数据项的属性。

（2）工作单元节（WORKING-STORAGE SECTION）

用来描述程序中用到的数据项。

（3）联接节（LINKAGE SECTION）

用来描述与调用程序间发生数据传递的数据项。

（4）报表节（REPORT SECTION）

为了完成报表编制功能，此节用来规定欲输出的报表的“体裁“，设计各报表栏的打印形式和方法等。

二．文件节

1．文件描述

格式：FD 文件名 LABEL {RECORD IS/RECORDS ARE} {STANDARD/OMITTED} [DATA {RECORD IS/RECORDS ARE} 数据名]

2．记录描述

记录描述体由01层号开头，后跟记录名。

如果记录下面不再分项，即记录本身就是一个初等项，则这种描述体最简单。

三．字型子句（PIC子句）

1．数值型数据的描述

（1）“9”描述符：表示在该位置上可以放入一个0-9之间的数字

举例：02 X PIC 9999.

02 Y PIC 9(5).

（2）“V”描述符：支持在数值型数据结构中隐含的小数点位置

举例：03 M PIC 999V999.

（3）“P”描述符：对低位上有若干个零的数，可以用该描述符。

举例：01 A PIC 9P(9). 表示10的9次方

01 B PIC PPPP99. 表示0.000023

（4）“S”描述符：如果想在数据项中放入一个带符号的数，可以用该描述符。对于类似PIC S99的数据项，系统在内存中该数据项的最后一个字节中，放入一个标记，表示此数为负。

二．字母型数据的描述

“A”描述符：这种类型的数据项中只能放字母或空格

三．字符型数据的描述

（1）字符型数据的规定

概念：由任意的COBOL字符组成的数据，称字符型数据。

说明：I.字符型数据可以用X描述符来描述，也可以用9和A描述符来描述。

II.字母型数据可以用A来描述，也可以用X。

III.字符型数据中可以放数字。

四．编辑型描述符

1．插入小数点“.”，用“.”描述符。

2．插入逗号“，”作分位号，用“，”描述符。

3．插入零，用“0”描述符。

4．插入空格，用“B”描述符。

5．插入正负号，用“+”或“-”描述符。

6．插入“$”

（1）加到数字前。

（2）在数字前加正负号和$。

7．浮动插入正负号和“$”

8．取消高位零，用“Z”和“*”描述符。

9．插入“DB“和“CR”字符：此两个描述符只能用作固定插入，而且只作最后一个描述符号。当数值为正时，此两次留两个空格；为负时，在编辑型数据项中最后两个字节中置DB或CR。五．PIC子句小结

1．格式：PICTURE/PIC IS 描述字符串

2．每一种类型数据可以使用的描述字符如下：

 

数据类型 在PIC子句中允许使用的描述字符

数值数据项 9 V S P

字母数据项 A

字符数据项 9 A X

编辑数值数据项 9 P V . , B Z + - $ * 0 CR DB

编辑字符数据项 A X 9 B 0

3．描述字符的含义

 

描述字符 含义

9 表示一个数字的位置

A 表示一个字母的位置

X 表示一个字符的位置

V 表示隐含小数点的位置

S 表示数值数据带符号

P 表示十进制比例换算，即指明落在数据域外的十进制小数点位置

$ 插入货币号位置

. 插入小数点位置

, 插入逗号的位置

+ 一律加符号

- 对负数加负号，对正数前留一空格

Z 取消高位零，以代空格

* 取消高位零，代以*

B 插入空格的位置

0 插入零的位置

DB（借方） 数据为负时，在数据后面出现DB，数据为正时，数据后空两格

CR（贷方） 数据为负时，在数据后面出现CR，数据为正时，数据后空两格

四．工作单元节（WORKING-STORAGE SECTION）

1．工作单元节的作用

程序中用的数据项分两部分：一部分是属于输入或输出文件的，另一部分是非输入或输出的数据。

在工作单元节中描述的数据项也有两种形式：一种是孤立的数据项，它们是初等项。

一种是组合项。COBOL规定，孤立的数据项的描述体以层号77开头，组合项描述体以01到49之间的一个数作层号。在次序上常先写77层，再写01-49层。

2．赋初值子句（VALUE子句）

举例：77 A PIC 99 VALUE IS 0.

77 T PIC X(9) VALUE ‘fogshadow’.

说明：只有对工作单元节中的数据项可以赋初值。

过程部之二

一．传送语句（MOVE语句）的较高技巧

1．各种类型数据间的传送

（1）同类型数据间的传送

（2）编辑传送。

注意：传送的方向必须是由数值型数据传送给编辑型数据，而不能由编辑型数据传送给数值型数据。

（3）不同类型数据间的传送规则。

说明：Y为允许传送，N为不允许，Z为在某些情况下是正确的

 

横接收项

竖发送项 数值型 数值编辑型 字母型 字符型 字符编辑型 组合项

整数 非整数

数值型 整数 Y Y Y Y Y Y Y

非整数 Y Y Y N N N Y

数值编辑型 N N N N Y Y Y

字母型 N N N Y Y Y Y

字符型 Z Z Z Z Y Y Y

编辑字符型 N N N N Y Y Y

数值常量 Y Y Y N N N Y

非数值常量 N N N Y Y Y Y

ZERO Y Y Y N Y Y Y

SPACE N N N Y Y Y Y

组合项 Z Z Z Z Y Y Y

2．组合项的传送

（1）发送项和接收项都是组合项，而且其结构和描述均相同，则可看作将各初等项一一对应传送。

（2）如发送项与接收项长度相同，但数据结构形式不同，则将发送项的内容原样不变地自左而右顺序地传送到接收项。

3．对应传送（带CORRESPONDING子句的MOVE语句）

（1）数据名的受限与受限名的传送

数据名和限定符之间用OF或IN 来连接。

举例：MOVe A1 OF A OF SUM TO T1.

（2）用CORRESPONDING子句的传送——对应传送（同名传送）

作用：把一个组合项中若干项传送给另一组合项中同名的项。

格式：MOVE CORRESPONDING/CORR 标识符1 TO 标识符2

二．算术运算语句的较高技巧

1．四舍五入处理（ROUNDED子句）

作用：按照数据项的描述要求对多余位截断，然后对被截断的后一位数进行四舍五入处理。

举例：ADD A，B TO C ROUNDED

 

A+B+C值 C描述 有无ROUNDED C内容

186.7851 999 有187

186.7851 999V9 有 186.8

186.7851 999V99 有 186.79

186.7851 999V999 有 186.785

如果计算结果有多个，则应该分别说明哪一个接收项要进行舍入处理，ROUNDED应写在有关的接收项（结果数据项）的数据名后面，如

ADD A,B,C TO D,E,F ROUNDED,G ROUNDED,H

2．长度溢出处理

当计算结果的整数部分的长度如果比结果数据项描述所规定的整数部分长，则发生长度溢出，结果的高位部分被截断。

ON SIZE ERROR子句提供“溢出”处理。即当发生溢出错误的时候，按程序设计者事先指定的操作处理。

举例：MULTIPLY A BY B GIVING C

ON SIZE ERROR DISPLAY‘SIZE ERROR‘ STOP RUN.

3．对应项间的运算（带CORRESPONDING子句的算术运算语句）

格式：ADD CORRESPONDING/CORR 标识符1 TO 标识符2 [ROUNDED]

[;ON SIZE ERROR 强制语句]

SUBTRACT CORRESPONDING/CORR 标识符1 TO 标识符2 [ROUNDED]

[;ON SIZE ERROR 强制语句]

4．除法语句中的余数子句（REMAINDER子句）

举例：DIVIDE 1.5 INTO 7 GIVING C REMAINDER D.

三．IF语句的高级技巧

1．IF语句的嵌套

举例：（注意IF与ELSE的一一配对）

IF A=B

MOVE B TO T

IF A=C

MOVE C TO R

IF X

 

SUBTRACT X FROM Y

IF N=M

IF P=Q

DISPLAY P,Q

ELSE NEXT SENTENCE

ELSE NEXT SENTENCE

ELSE NEXT SENTENCE

ELSE NEXT SENTENCE

ELSE NEXT SENTENCE

2．关系表达式条件

以下为关系条件的比较方式，其中，Y表示作为数值型比较，N表示作为非数值型（即字符型比较），Z表示不能比较。

 

横-客体

竖-主体 数值型 数值常量 非数值常量 字母型 字符型 组合项

数值型 Y Y N N N N

数值常量 Y Z Z N N N

非数值常量 N Z Z N N

字母型 N N N N N N

字符型 N N N N N N

组合项 N N N N N N

3．符号条件

格式：数据名/数值表达式 IS [NOT] POSITIVE/NEGATIVE/ZERO

举例：（1）IF X IS POSITIVE 与 IF X>0 等价

（2）IF X IS NEGATIVE 与 IF X<0 等价

（3）IF X IS ZERO 与 IF X=0 等价

4．类型条件

格式：标识符 IS [NOT] NUMERIC/ALPHABETIC

其中，NUMERIC表示数值类型，ALPHABETIC表示字母类型。

5．条件名条件

作用：用来代替一系列繁杂的IF-ELSE语句。

格式：88 条件名 VALUE IS/ARE 常量1[THROUGH/THRU 常量2]

[常量3[[THROUGH/THRU 常量4]]……

举例：首先在数据部说明

77 X (条件变量) PIC 9(6).

88 X1 VALUE 0 THRU 99.

88 X2 VALUE 100 THRU 999.

88 X3 VALUE 1000 THRU 4999.

88 X4 VALUE 5000 THRU 100000.

经过上面的说明后，可以在过程部中直接使用条件名条件。

IF X1 MOVE 0.03 TO R. (在0<=X<100时，R=0.03)

IF X2 MOVE 0.04 TO R. (在100<=X<1000时，R=0.04)

IF X3 MOVE 0.05 TO R. (在1000<=X<5000时，R=0.05)

IF X4 MOVE 0.06 TO R. (在5000<=X<=100000时，R=0.06)

6．复合条件

逻辑运算符有：AND、OR、NOT

运算次序是：NOTaANDaOR

五．字符串连接语句（STRING语句）

六．字符串分解语句（UNSTRING语句）

七．检测语句（INSPECT语句）

八．转换语句（TRANSFORM语句）

过程部之三

—执行语句（PERFORM语句）

一．执行语句的作用 类似于子程序

二．执行语句的最基本形式

格式：PERFORM 过程名1[THROUGH/THRU 过程名2]

三．执行语句的使用规则

1．PERFORM语句的嵌套

2．在PERFORM语句所执行的语句序列中，可以含有转移语句，可以使流程转到语句序列之外，但一般应该转回到此语句序列，以便能最后能执行此语句序列的最后一个句子。

四．使用PERFORM语句实现循环

格式：PERFORM 过程名1[THROUGH/THRU 过程名2] 整数/标识符 TIMES

说明：1.标识符应为整数数据项

2如果此标识符的值在执行语句序列中有变化，不会影响执行次数。即以它开始时候的值来决定执行的次数。

五．执行语句的较复杂的形式

1．格式：PERFORM 过程名1[THROUGH /THRU 过程名2 ] UNTIL 条件

作用：反复执行指定的语句序列，直到给定的条件满足为止。

2．格式：

PERFORM 过程1[THROUGH/THRU 过程名2]

VARYING 标识符1 FROM 常数1/标识符2 BY 常数2/标识符3 UNTIL 条件

举例：PERFORM T1 THRU T2 VARYING X FROM A

BY B UNTIL X>5

其作用是执行T1到T2语句序列，X是“循环变量”，是整型数据项。A为初值，B为步长，它们都是整数或整数数据项。

六．执行语句的多重循环形式

格式：PERFORM 过程名1 [THROUGH/THRU] 过程名2

[VARYING 参数1 FROM 初值1 BY 步长1 UNTIL 条件1]

[AFTER 参数2 FROM 初值2 BY 步长2 UNTIL 条件2]

[AFTER 参数3 FROM 初值3 BY 步长3 UNTIL 条件3]

说明：1。最后面的循环体先执行。

2．COBOL允许用到三重循环。

七．出口语句（EXIT语句）

作用：提供一个段名，被PERFORM调用的语句序列由此公共汇集点，返回到PERFORM的下一个语句去。

举例：PERFORM A THRU B

……

A. IF X>Y GO TO B

MOVE X TO T.

B.        EXIT.

八．修改语句（ALTER语句）

格式：ALTER 过程名1 TO [PROCEED TO] 过程名2

[，过程名3 TO [PROCEED TO] 过程名4]……

作用：用来改变GO TO的转向点。该语句使以过程名1，过程名3，……命名的各段中的GO TO语句的转向点分别被修改为过程名2，过程名4……。注意，过程名1，过程名3……各段只能由一条GO TO语句单独组成。

数据部之二

-数据部的较高技巧

一．数据在计算机内的表示形式

1．字符数据在内存中的存储形式

（1）ACSII

（2）EBCDIC

2．数值型数据在内存中的存储形式

（1）外部十进制（或称扩张十进制）形式

（2）外部浮点数形式

（3）内部十进制（又称缩合十进制）形式

（4）定点二进制形式

（5）内部浮点形式

二．用法子句（USAGE子句）

作用：可以使程序设计者自由选择数据在内存中的存放形式。

格式：[USAGE IS] DISPLAY/COMPUTATIONAL/COMP

说明：1。DISPLAY表示是“显示型的用法”，表示此数据项适于显示，打印。

2．COMPUTATIONAL=COMP，表示是“计算型的用法”，适于计算。

3．如省略USAGE子句，则隐含表示为用DISPLAY形式。

三．符号子句（SIGN子句）

作用：用来指定数值型数据描述体中运算符号的状态和位置。

格式：[SIGN IS] LEADING/TRAILING [SEPARATE CHARACTER]

说明：1。没有SIGN子句时，数值的符号是存放在数据项最后一个字节中的。

2．用SIGN子句可以指定符号在数值的前部还是后部（LEADING/TRAILING）。

3．指定符号单独占一个字节，用“SEPARATE”可选项，内存中增加一个字节。

4．SIGN子句只能用于PIC字符串中含有“S”的数值型数据描述体中。

5．使用SIGN子句的数据项的用法应该是USAGE DISPLAY（显式的或隐含的）。

举例：02 A PIC S9(3) USAGE DISPLAY SIGN IS LEADING.

四．重定义子句（REDEFINES子句）

作用：不同的数据项可以共用内存中的同一段空间。例如已给数据项A分配了一段内存空间，在经过某一段的过程后，A已经不再使用了，但它仍占着内存这部分空间，为了节约内存，可以将另一数据项B也分配在A所占的这段内存空间。

格式：层号 数据名1 REDEFINES 数据名2

举例：02 A PIC X(5).

02 B REDEFINES A PIC 9(5).

说明：

1。数据名2 与数据名1的层号必须相同。

2．用REDEFINES子句的描述体应该紧跟在被重新定义的数据项的描述之后，中间不能插入其它项的描述说明。

3．可以多次重定义，但必须紧跟出现，而且要求使用最初定义的数据名。

4．REDEFINES子句不能用于文件节的01层中。

5．用REDEFINES子句可以改变数据结构，但数据名1、2的长度应该相等。

6．REDEFINES子句应在其它子句之前。

7．重定义子句所在的数据描述体中不能使用初值子句赋初值。.

五．重命名子句（RENAMES子句）

作用：在不改变数据项的长度的前提下，重新定义数据区的名称和数据结构的形式（包括初等项的类型和长度）。可以把原来已经定义的某些数据项重新组合成一个新项，并以一个新名字来代表它。但用重命名子句不能改变原来各初等项的类型、长度等属性。

格式：66 数据名1 RENAMES 数据名2 [THRU 数据名3]

说明：只能用于工作单元节中，不能用于文件节中

六．遇零置空子句（BLANK子句）

作用：当数据项的值为零时，使它的内容改变为空白（空格）。这个子句只能用于数值型或编辑型的初等项。

举例：03 A PIC 9999 BLANK WHEN ZERO.

七．对齐子句（JUSTIFIED子句）

作用：字符或字母型数据传送的时候是按标准的对齐方式，即“左对齐”，若想改为“右对齐”，可以用JUSTIFIED子句。

格式：JUSTIFIED/JUST RIGHT

举例：77 B PIC X（5） JUSTIFIED RIGHT

八．同步安置子句（SYNCHRONIZED子句）

作用：一个机器字一般定为4个字节，从内存中取数据的时候是以机器字为单位的，而数据存放则是按字节连续存放的，这里面就存在一个边界对齐的矛盾，会影响目标程序运行时间。用同步安置子句可以指定数据项在内存中如何按自然边界来安置。

格式：SYNCHRONIZED/SYNC LEFT/RIGHT

说明：1。用SYNC LEFT时，左对齐，右边补零或空格。

2．用SYNC RIGHT时，右对齐，左边补零或空格。

举例：01 A.

02       A1 PIC 9(3) SYNC LEFT VALUE 82.

03       A2 PIC X(3) SYNC RIGHT VALUE ‘ABC’

九．复写语句（COPY语句）

作用：把“源程序库”中的某些记录描述和数据描述插入到自己的源程序中。

格式：COPY 库名 [REPLACING 标识符1/常量1/字1 BY 标识符2/常量2/字2]

子程序

一．概述

举例：编一个打印一行“*”符号的子程序

1． 主程序（只写与调用子程序有关的部分）

IDENTIFICATION DIVISION. （标识部）

PROGRAM-ID. A. （程序名为A）

ENVIRONMENT DIVISION. （环境部）

……

DATA DIVISION. （数据部）

……

PROCEDURE DIVISION. （过程部）

……

CALL B. （调用子程序B）

……

2． 子程序

IDENTIFICATION DIVISION.

PROGRAM-ID. B.

ENVIRONMENT DIVISION.

DATA DIVISION.

WORKING-STORAGE SECTION.

77       X PIC X(80).

PROCEDURE DIVISION.

MOVE ALL’*’ TO X.

DISPLAY X.

EXIT PROGRAM.

可以看到程序A和程序B分别是两个程序，各有自己的程序名，都有四大部分。

二．调用程序与被调用程序间的数据联系

格式：调用语句

CALL 子程序名 USING 数据名1 [，数据名2]……]

被调用程序中过程部部头的一般格式为

PROCEDURE DIVISION [USING 数据名1[，数据名2]……]

说明：1。两部分相对应的参数个数、长度必须相等。

2．参数是在内存中建立关联，类似于C++中的传递引用参数。

三．子程序的结构

1．标识部

说明子程序的名字，以供调用。

2．环境部

3．数据部

（1）文件节（FILE SECTION）

（2）工作单元节（WORKING-STORAGE SECTION）

（3）联接节（LINKAGE SECTION）：如果子程序过程部部头的USING子句中有数据名，则此数据名应在此节中加以说明。

4．过程部

过程部的部头：PROCEDURE DIVISION USING 数据名1，数据名2，……

过程部中应该包括一个程序出口语句：EXIT PROGRAM.

表的建立与查找

一．表的概念

COBOL语言中的表（TABLE）类似于其他高级语言中的数组（ARRAY）。

表中，序号称为下标，相对地址称为位标，下标和位标称为“出现号”。

二．表的建立（OCCURS子句）

格式：OCCURS 整数 TIMES

举例：01 PRODUCT-RECORD.

03     RODUCT OCCURS 20 TIMES.

04 QUANTITY-OF-PRODUCTION PIC 9(6).

04 QANTITY-OF-SALES PIC 9(6).

04 QANTITY-OF-HAND PIC 9(6).

说明：1。OCCURS子句不能出现在77层，因为77层是独立的数据项。

2．OCCURS子句不能用于01层。

3．只有当OCCURS所说明的数据是初等项时，才能在该数据项的描述中使用PIC子句。

4．不能用VALUE子句对表赋初值，不能同时用OCCURS子句和VALUE子句来描述同一数据项。

三．可变长表

格式：OCCURS 整数1 TO 整数2 TIMES DEPENDING ON 数据名1

说明：根据数据名1的值来确定数据项重复的次数。

四．表元素的引用

格式：表名（下标）

说明：1。如果B是一个表，不直接引用表名B而不加下标。

2．如果表元素是组合项，则引用它下属的项（可以是初等项或组合项），也必须用下标指明它是属于哪一个表元素的。

3．如果表元素是组合项，可以用它对下属的数据项进行限定。

4．下标只能是整常数或具有整型值的数据名。

5．下标不能是带下标的数据名，即不能是表元素。

五．给表元素赋初值

1．对包括所有表元素的整个表赋给一个初值，这时可以对表的描述体上面一层的数据项赋一个初值即可。

例1：01 TABLE VALUE IS ZERO.

03     OCCURS 20 PIC 9(3).

例2：01 T VALUE ‘ABCDEFHIJ’.

02       Q OCCURS 3 PIC X(3).

这样，Q（1），Q（2），Q（3）的内容分别是ABC，DEF，HIJ。

2．联合使用OCCURS子句和REDEFINES子句来给各个表元素赋值。

（1）先在工作单元节中定义一个组合项，它占的内存的大小和需赋值的表一样，在该组合项中定义若干个数据项，数据项的描述和表的元素相同。

（2）然后对这些数据项分别用VALUE子句赋以初值，由于在这些数据项的描述中没有出现OCCURS子句，因此用VALUE赋初值是合法的（VALUE子句和OCCURS子句不能同时用来描述一个数据项）。这些值就是要赋给表元素的初值。

（3）把这个组合项重定义为一个表。

六．用位标法(cursor)引用表元素

1．位标的概念：位标的值表示表元素在该表中的相对位置（以字节数表示）。

2． 位标名的指定方法：在数据部中定义一个表时所用的OCCURS子句中要加上“INDEXED BY 位标名”短语来指定。

说明：（1）由于位标是专门用于引用表元素的特殊数据项，它不能用来进行算术运算。

（2）一维表或多维表的每一维按需要可以指定若干个位标名，引用时这些位标名只能在该维内使用。

（3）有时需要把位标的值转存到另一个数据项中，但由于位标是特殊类型的数据项，因此，需要另外定义一种特殊的数据项叫位标数据项，用来专门存储位标的值。位标数据项在数据部中定义。描述位标数据项用USAGE子句。例如：77 K USAGE IS INDEX.

七．SET（设置）语句

1．作用：将一表元素的相对地址放到指定的位标去。

如： SET I TO 10.

表示将位标I置位到第10个元素的第一个字节的相对地址上去。

2．格式一

SET 标识符1[，标识符2]…… TO 标识符3/位标3/整数

位标1[，位标2]……

规则列表（设SET A TO B）

 

横-发送项B

竖-接收项A 整数 数值初等项 位标名 位标数据项

数值初等项 不合法 不合法 将位标代表的序号传送 不合法

位标名 将整数（序号）化成相对地址传送 同左 （1）如果两个位标名指向同一个表，则转换成另一表的相对地址再传送，即将发送项代表的表元素顺序号减1，乘以接收项相关表元素的长度，再传送 简单传送

位标数据项 不合法 不合法 简单传送 简单传送

3． 格式二

SET 位标1 [，位标2]…… UP/DOWN BY 标识符/整数

作用：给位标增减一个量。

八．表的检索

1．用于顺序检索的SEARCH语句

格式：SEARCH 表名[VARYING 位标名1/标识符2][AT END 强制语句1]

WHEN 条件1 强制语句2/NEXT SENTENCE

[WHEN 条件2 强制语句3/NEXT SENTENCE]……

举例：SET N TO 1.

SEARCH WORKER-TABLE

AT END DISPLAY‘CANNOT FIND NAME’

WHEN NAME（N）=‘ZHANG SHENG’

DISPLAY NAME（N），PAY（N）.

……

SEARCH语句是这样执行的：从指定的表元素开始，检查是否满足WHEN后面指定的条件。如不满足，就使N增值，自动执行一个SET N UP BY 1。使N指向下一个元素的地址，如果查到某一个元素满足指定的条件时，查表工作立即停止，执行WHEN字句中条件后面的语句。

2．用于有序表的SEARCH语句（折半法检索）

（1）说明升（降）序的一般格式为：

ASCENDING/DESCENDING KEY IS 数据名1[，数据名2]……

ASCENDING/DESCENDING KEY IS 数据名3[，数据名4……]……

举例：02 BOOK-TABLE OCCURS 100

ASCENDING KEY IS NAME

DESCENDING KEY IS COD

INDEX BY N.

（2）SEARCH语句的一般格式（之二）

SEARCH ALL 表名[；AT END 强制语句1]

WHEN 条件 强制语句2/NEXT SENTENCE

举例：SEARCH ALL BOOK-TABLE

AT END DISPLAY’CANNOT FIND NAME’

WHEN NAME(N) = ‘COMPUTER DESIGN’

DISPLAY NAME (N),NUM (N).

九．用PERFORM语句对表进行检索

最多可以处理三重循环

PERFORM 过程名1[THRU 过程名2]

VARYING 位标名1/下标名1 FROM 位标名2/常量1/标识符1 BY 常量2/标识符2 UNTIL 条件1

AFTER 位标名3/下标名2 FROM 位标名4/常量3/标识符3 BY 常量4/标识符4 UNTIL 条件2

AFTER 位标名5/下标名4 FROM 位标名6/常量5/标识符5 BY 常量6/标识符6 UNTIL 条件3