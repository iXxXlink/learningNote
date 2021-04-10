## 	第一章 计算机系统漫游

1. hello.c程序转为可执行文件的过程（编译系统过程）：

   1. 预处理阶段：预处理器将所有宏定义进行替换，且在文本中直接代替。#include<stdio>，类似include的头文件，也会在其系统中找到stdio文件，并将该文件中的内存之间复制粘贴到C程序文本中。预处理过后,文件依然是一个文本（通过acsii码将字节映射为字符），通常以.i作为文件扩展名
   2. 编译阶段：编译器将hello.i文本翻译为汇编语言程序，依然是文本，但是用汇编语言描述的,通常以.s作为文件扩展名
   3. 汇编阶段：汇编器将汇编程序文件翻译为机器语言指令,该文件不再是文本文件而是二进制文件（即只有二进制码没有字符）,通过以***.o***作为文件扩展名
   4. 链接阶段：类似于print的在标准库中的函数,同样以.o的预编译目标文件形式存在，链接器就负责将该目标文件与hello.c生成的目标稳进连接，最终获得hello文件,改文件为可执行目标文件（可以加载到存储器，由系统负责执行）
   5. ![image-20201216144137480](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201216144137480.png)

2. hello执行文件在硬件中的执行过程

   1. 在shell中键入**./hello**时，键盘通过io总线向寄存器逐一传输字符,然后再将这些字符存入主存中。

      <img src="C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201216155208014.png" alt="image-20201216155208014" style="zoom:50%;" />

   2. 再敲回车时,shell使得cpu执行一系列指令,将磁盘中的hello目标文件的代码和数据（数据即“hello,world”）传入主存中。（通过DMA，从磁盘到主存的数据拷贝可以不通过处理器，而直接从磁盘传输到主存）

      <img src="C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201216155228930.png" alt="image-20201216155228930" style="zoom:50%;" />

   3. CPU开始执行hello目标文件中机器指令，将主存中存储的数据(hello,world)拷贝到寄存器中，再从寄存器通过io总线拷贝到显示屏设备中，最终显示在屏幕上。

      <img src="C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201216155241817.png" alt="image-20201216155241817" style="zoom:50%;" />

3. 任何时刻，系统中都只有一个进程正在运行。当操作系统决定进程切换时，首先进行上限文切换（即保存当前进程的上下文、恢复新进程的上下文）（上下文：包括pc、寄存器值、和主存值），然后将控制权转移给新进程。

4. 执行hello程序时，操作系统的工作流程

   1. 一开始只有shell进程在运行
   2. 在命令行上输入后,shell进程使用==系统调用==函数，将控制权交给操作系统
   3. 操作系统保存shell进程的上下文，并创建hello进程及其上下文，然后操作系统将控制权交给hello进程
   4. hello进程结束后，控制权交给操作系统
   5. 操作系统恢复shell进程的上下文，并将控制权再次交给shell进程
   6. ![image-20201217014541678](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217014541678.png)

5. 文件：IO设备的抽象

6. 虚拟存储器：主存和磁盘的抽象

7. 进程：处理器、主存和IO设备的抽象

8. ![image-20201217020242352](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217020242352.png)



## 第二章  信息的表示和处理

1. 机器级程序将存储器视作一个虚拟存储器（virtual memory），（==而非区分内存和磁盘==），虚拟存储器的每一个==字节==都有一个数字标识，称为它的地址。

2. 为什么使用16进制：计算机中数据都是用2进制表示，但是2进制写起来太繁琐了，而16进制写起来简单，并且能够方便的转换为2进制（16进制1位代表二进制4位）

3. 字长的作用：字长是一次性处理事务的固定长度，用于指明整数和指针数据的大小，即虚拟地址都是用1个字表示的，所以字长决定了能够寻址的虚拟地址的大小。n位字长，就决定了程序只能使用2的n次方字节的空间。（地址范围为：0~$2^n-1$）

4. 基本数据类型所占的字节数（32机和64位机）

   1. 相同的：char 1字节，short int 2字节，int 4字节，float 4字节，double 8字节
   2. 不同的：long int、char* 都是相应机器的==全字长==（指针大小一般都为全字长，因为指针就虚拟地址）
   3. ![image-20201217082047493](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217082047493.png)

5. 大小端的判断：首先所有数据储存在存储器中都是从低地址到高地址，小端即先存放数据的低有效位，再存放高有效位；而大端是先在低地址存放数据的高有效位，再存放低有效位

6. 反汇编器：将可执行文件转为汇编指令

7. show_bytes函数的作用：从该数据存储的地址最低位开始，逐个字节读取存储在虚拟存储器上的值，直至读取完该数据

   1. ![image-20201217191625972](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217191625972.png)

8. 字符串在系统中存储与字节顺序无关：因为一个字符的ascii码都是一个字节，即每个字符都可看作是独立的1个字节的数据，按顺序排列（字节顺序只与一个完整的数据有关），所以文本数据比二进制数据有更强的平台独立性

9. 字符串以null（0x00）结尾

10. 二进制代码是不兼容的：在机器眼中，程序就是一系列二进制代码，但这些二进制代码不能在不同机器或操作系统间移植

    1. 机器类型不同：不同的机器使用不同的机器指令和不同的编码方式
    2. 操作系统不同：程序不只有代码，还有数据，不同操作系统数据编码规则不同，还有文件格式、系统API（代码调用的系统api不同）不同

11. 在C语言中，直接使用~ | & ^进行数据间的运算时，实际是对其二进制表达式进行运算（运算过程时将原数据类型转为二进制，进行二进制运算，再转为原数据类型）

12. ~0将生成全为1的掩码：长度为字长

13. 算数右移：==在一个字节内==，最高为X，则右移后的左侧空余处，全补上X（如果1个数占2个字节，则2个字节补的数不一定相同）

    1. 大多数机器和编译器都使用算数右移
    2. ![image-20201217220709277](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217220709277.png)

14. 移位的优先级低于算术运算符

15. 补码（two’s complement）的定义:这里对补码最高位的解释非常有趣，且深刻

    1. ![image-20201217235045481](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201217235045481.png)’

16. 无符号数、有符号数、补码的一些特性

    1. 在符号数中，最小值的绝对值=最大值的绝对值+1
    2. 相同位数，最大的无符号数值等于最大有符号数值\*2+1
    3. ![image-20201218105040951](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218105040951.png)

17. 有符号数的其他表示法

    1. 反码（one’s complement）:与补码的区别仅为，最高位的权是$-(2^{w-1}-1)$而非$-2^{w-1}$.
       1. +0:全0表示
       2. -0：全1表示
       3. ![image-20201218113137578](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218113137578.png)
    2. 原码（Sign-Magnitude）:最高位只表示符号，其它位用于确定绝对值
       1. +0：全0表示
       2. -0:10000表示
       3. ![image-20201218113508676](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218113508676.png)
    3. 反码和原码都极少使用，几乎所有机器使用补码。

18. C语言中的强制类型转换：例如无符号数转换到有符号数（U2T），==实际储存在虚拟内存空间中的二进制序列不改变==，改变的只是这段二进制序列的编码方式，无符号的编码方式是直接转为对于的10进制数，而有符号数的编码方式是补码。所以，U2T(53191)=-12345,T2U(-12345)=53191

    1. 且有一个性质：一个数的无符号表示+补码表示=$2^w$
    2. T2U公式（补码转无符号）：
       1. ![image-20201218212646954](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218212646954.png)
    3. U2T公式（无符号转补码）：
       1. ![image-20201218215335562](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218215335562.png)

19. 有无符号的数打印输出时：

    1. %u：数据的二进制序列（无论数据类型有无符号）按照无符号数方式输出
    2. %d：数据的二进制序列（无论数据类型有无符号）按照补码方式打印
    3. ![image-20201218222854697](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218222854697.png)

20. 有无符号数的运算

    1. 进行运算时（>、<），一个运算数是有无符号数（无符号数末尾须用u表明），C语言会隐式地将另一个运算数从有符号数转为无符号数（无符号first）
    2. 提示：2147483648=0x8000 0000
    3. ![image-20201218225103571](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218225103571.png)

21. 有无符号数的符号扩展（扩展都只指从位数小的数转为位数大的数）

    1. 某数从16位扩展到32位无符号数时，只需在前面16位加上16个0
    2. 某数从16位扩展到32位有符号数时，只需在前面16位加上16个1
    3. ![image-20201218232440793](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218232440793.png)
    4. ![image-20201218232447293](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201218232447293.png)

22. 有无符号转换和扩展转换的相对顺序：先扩展大小，再转换符号

    1. 一个short类型（2bytes）的数据sx=-12345，转为无符号int(4bytes)时，sx先通过+1扩展到32位，再换位无符号数

23. ![image-20201219053858218](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219053858218.png)

24. 截断（高位转为低位）：32位uint转为16位的short时，是直接将高位去掉，只保留低16位数值（有符号数，同样是截断，只保留低16位，然后第16位作为符号位）

    1. 截断的意义：将溢出范围的数据（无论有符号还是补码）按照下面的加法溢出处理方法，转为w位范围内的数据。很有趣，只需要保留低w位就能实现范围的规范。（就像群一样，截断后的结果仍是群中同余的那个结果）

25. 整数运算

    1. 无符号加法

       1. 无符号加法的运算符$a+^u_wb$，x与y两无符号数相加，只保留低w位，并将结果视作无符号数
       2. ![image-20201219061006468](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219061006468.png)
       3. 判断是否发生溢出：发生溢出当且仅当res<x，或res<y

    2. 无符号数求反：如果无符号数x+y在w位的范围内，和为0，就称y是x的反

       1. 对于x等于UMIN时，其反为UMIN，其他无符号数的反是与$-2^w$的和
       2. ![image-20201219145103075](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219145103075.png)

    3. 补码加法

       1. 补码加法运算符  $a+^t_wb$：表示2个有符号数相加，只保留低w位，并将结果视作有符号数
       2. 正溢出的实质：2正数之和大于w位补码能表示的TMAX，即原为0的符号位由于低位的进位变成了1。因为低w-1位不变，而第w位为1，等价于在原值上加$-2^w$
       3. 负溢出的实质：2负数之和小于w位补码能表示的TMIN，即原为1的符号位由于向前进位变成了0。因为低w-1位不变，而第w位为由0变为1，等价于在原值上加$2^w$
       4. ![image-20201219061956580](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219061956580.png)
       5. ![image-20201219142128900](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219142128900.png)
       6. 值得注意：有符号加法和无符号加法在位级上的操作是一样的，所以==位级上的结果相同==，所以有符号加法，等价于先将2有符号操作数x，y转为无符号数，进行无符号数加法，再将结果转为有符号数
       7. 有符号数加法实质，可以看作无符号一样，每位相加进位（==注意：符号位一样相加！==），然后最高位作为新的符号位（溢出的话最高位1作为符号位，没溢出的话原最高位作为符号位）
       8. ![image-20201219062419118](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219062419118.png)
       9. 溢出的检验：
          1. 正溢出：当且仅当，x>0,y>0,x+y<0时
          2. 负溢出：当且仅当，x<0,y<0,x+y>0时

    4. 补码的的非：即求其值在w位范围内的负元（即x与y的和在w位范围内为0，所以y就是x的非）

       1. 当x等于TMIN时，其非为TMIN，其他数的非即为其相反数。（因为补码的正负数存在不对对称性，所以要特殊考虑TMIN）

       2. ![image-20201219145408469](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219145408469.png)

       3. 补码非在位级上的意义：

          1. 每位求补（求补：即0变1,1变0），再加1

             ![image-20201219150440057](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219150440057.png)

          2. 另一种解释：找到最低位的1，将其左边所有数字求补

             ![image-20201219150418580](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219150418580.png)

          3. 值得注意：无符号数的反和补码的非计算在位级上的==操作方式一样==。都是以上2种

    5. 无符号乘法：

       1. w位的无符号数x,y相乘，其结果只保留低w为
       2. ![image-20201219151200381](D:\Typora\image-20201219151200381.png)

    6. 补码乘法：w位的有符号数x,y相乘，结果只保留低w位，并将其结果视作补码表示

       1. ![image-20201219152234293](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219152234293.png)
       2. 值得注意：对于相同w位二进制序列的无符号与补码的乘法，或许完成的位级可能不同，但截断后的结果位级是一样的
          1. ![image-20201219153535254](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219153535254.png)

    7. 乘以常数：

       1. 加法、减法、位级运算、移位只需要1个时钟周期，整数乘法需要10多个时钟周期。所以尝试用移位和加法的组合实现整数乘法
       2. 乘以2的k幂，向右移k位
          1. ![image-20201219161502685](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201219161502685.png)
          2. 无论无符号还是补码，无论有无溢出：直接右移k位就是乘以$2^k$的结果。（因为，先假设没有位数限制，右移k位的结果对于无符合和补码都适用，然后截取低w位，因为截断的性质，将溢出的数据规范在范围内）
       3. 乘以其他常数n，将n转为2的幂之和（就是转为2进制形式），然后分别对于每一个2的幂因子使用移位获得结果，将所有移位结果相加得到最终结果。
          1. 例如，当n=14时，因为14=$2^3+2^2+2^1$，所以$x*14=(x<<3)+(x<<2)+(x<<1)$

    8. 除以2的幂：

       1. 在机器中，除法比乘法更慢，要30多个时间周期

       2. 整数除法的定义:x/y，y>0

          1. 当x<0时，结果为x/y向上取整
          2. 当x>0时，结果为x/y向下取整
          3. 其实就等价于先都视为正数，向下取整，再加上符号

       3. 无符号除以2的幂

          1. ==逻辑右移==k位即为除以$2^k$
          2. ![image-20201220045301050](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220045301050.png)

       4. 补码除以2的幂

          1. ==算数右移==k位，只表示x/y向下取整（当x<0时，需要向上取整，与此方法不符，故此方法不能直接用）

          2. 补码除法：移位前在x上加一个偏置值

          3. ![image-20201220050332691](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220050332691.png)

             1. 原理：向上取整的转换公式![image-20201220050442440](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220050442440.png)

          4. 机器中计算除以2的幂的公式

             ![image-20201220050736006](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220050736006.png)

26. 浮点数

    1. 二进制小数

       1. 二进制小数表达的意义

       ![image-20201220052204300](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220052204300.png)

       1. 性质：小数点左移1位，表示除以2，右移1位表示乘以2
       2. 缺点：只能精确表示形如$x*2^k$的数，其他数只能被近似表示

    2. IEEE浮点数

       1. IEEE浮点标准：
       
          ![image-20201220054203965](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220054203965.png)
       
       2. 浮点数位级表示：S+E+M
       
          ![image-20201220054352373](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220054352373.png)
       
       3. 单精度浮点数（float）：S1位，E8位，M23位，共32位
       
          ![image-20201220054837622](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220054837622.png)
       
       4. 双进度浮点数（double）:S1位，E11位，M52位，共64位
       
          ![image-20201220054759245](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220054759245.png)
       
          1. 根据阶码有3种情况
       
             1. 非全0非全1：是规格化的数据
             2. 全0：非规格化
             3. 全1：无穷大或NaN
       
             ![image-20201220065252530](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201220065252530.png)
       
       5. 1
       
       6. 1

27.  