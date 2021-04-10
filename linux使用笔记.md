# linux使用笔记

1. 安装软件：apt-get install xxx

2. 查看文件：cat 路径

3. vi操作：

   1. 进入插入模式：按i

   2. 退出：先按esc，再按  ==：== ，: w filename （输入 「w filename」将文章以指定的文件名filename保存）

      : wq (输入「wq」，存盘并退出vi)

      : q! (输入q!， 不存盘强制退出vi)

4. 当命令不存在时，添加环境变量：export PATH=$PATH:/usr/sbin

5. 使用root权限

   1. su
   2. sudo su -  root

6. apt原理：

   1. 镜像源站点目录：存放在**/etc/apt/source.list**，当我们要使用apt相关命令更新或下载时，实际上就是访问存在这个目录下的地址，然后更新数据或下载文件
   2. 更新软件列表：**apt-get update**命令会更新**/var/lib/apt/lists**软件列表，使其存储的软件信息和镜像源中最新信息一样（软件名称和版本）
   3. 下载某个软件：**apt-get install <软件名>**，首先会lists中软件列表扫描匹配输入的软件名，然后检查依赖项，找到支持该软件运行的依赖软件包，然后从镜像站点中下载所需要软件包，并解压，自动完成配置
   4. 卸载某个软件：**apt-get remove <软件名>**
   5. 完全卸载某软件，并删除配置：**apt-get --purge remove <软件名>**
   6. 下载软件包的源码：**apt-get source <源码包名>**
   7. 将系统中所有软件一次性升级到最新版本：**apt-get upgrade**
   8. 清除所有缓存文件：**apt-get clean**
   9. **apt autoremove**

7. linux 目录结构

   1. 文件系统的顶端是 / ，称为根目录，所有的文件都在根目录下

   2. /bin：放置单人维护模式下还能够被操作的指令

   3. /boot：开机会使用到的档案

   4. /dev：任何装置与周边设备都以档案的形态存于此目录

   5. /etc：系统主要的设定配置都放置在这个目录

   6. /home：系统预设的使用者家目录（homt directory）

   7. /lib：开机时会用到的函式库，以及在/bin或/sbin底下的指令会呼叫的函式库而已 

   8. /root：系统管理员(root)的家目录

   9. /sbin：里面包括了开机、修复、还原系统所需要的指令

   10. /srv：srv可以视为service的缩写，是一些网路服务启动之后，这些服务所需要取用的资料目录

   11. **/etc：**配置文件

       **/bin：**重要执行档

       **/dev：**所需要的设备文件

       **/lib：**执行档所需的函式库与核心所需的模块

       **/sbin：**重要的系统执行文件

8. 相对路径和绝对路径

   1. 假设现在在/home目录下，需要进入/var/log目录
   2. 绝对路径：cd /var/log
   3. 相对路径：../var/log
   4. 0个点：/ 表示根目录（即绝对路径）
   5. 1个点 **.**：./表示当前目录，也可以用**./**表示（也可以省略不写）
   6. 2个点**..**：../表示上一层目录，也可以用**../**表示

9. 打开终端：Ctrl+Alt+T

10. 使用文本编辑器打开文件：gedit +文件路径

11. 文件相关指令

    1. 删除文件夹：rm -rf /var/log/httpd/access（将会删除/var/log/httpd/access目录以及其下所有文件、文件夹，其中r表示向下递归该节点下所有文件，f表示直接删除不做提示）
    2. 删除文件：rm -f /var/log/httpd/access.log
    3. 创建目录：mkdir dir1
    4. 创建文件：vi test.c（创建并打开一个文件test.c）
    5. 重命名文件：
    6. 移动文件：
    7. 复制文件：
    8. 

12. GCC使用指令

    1. 编译c语言文件生成可执行文件obname：gcc -o obname clanguage.c -g
    2. 运行可执行文件：./obname

13. GDB指令

14. 关机

    1. ==shutdown -h now==关闭系统（这种会调用init 0，但更安全）
    2. init 0 关闭系统
    3. reboot 重启
    4. telinit 0 关闭系统
    5. shutdown -h hours:minutes & 按预定时间关闭系统 
    6. shutdown -c 取消按预定时间关闭系统 
    7. shutdown -r now 重启
    8. logout 注销 

15. 显示当前的绝对路径：pwd

16. 显示当先所有进程：top

    使用格式：

    top [-] [d] [p] [q] [c] [C] [S] [s] [n]


    参数说明：
    
    d：指定每两次屏幕信息刷新之间的时间间隔。当然用户可以使用s交互命令来改变之。
    
    p:通过指定监控进程ID来仅仅监控某个进程的状态。
    
    q:该选项将使top没有任何延迟的进行刷新。如果调用程序有超级用户权限，那么top将以尽可能高的优先级运行。
    
    S：指定累计模式。
    
    s：使top命令在安全模式中运行。这将去除交互命令所带来的潜在危险。
    
    i：使top不显示任何闲置或者僵死进程。
    
    c:显示整个命令行而不只是显示命令名。

17. 必杀某个进程：kill -9 pid （9表示Kill(can't be caught or ignored) (POSIX)）

18. 查看某个端口上进程的信息：lsof -i:8000

19. fork函数：

    1. 为什么调用fork生成的子进程共享父进程一样的变量：我认为是因为子进程必然与父进程有某些联系，所以父进程需要向子进程传递一些参数，但是由于在不同情况下，传递的参数的个数与类型各不相同，所以为了方便，就统一将父进程所有变量都给子进程，这样就避免了繁琐的传递参数过程

    2. 一次调用，两次返回：在父进程中返回子进程的pid，在子进程中返回0（子进程可以通过getppid获得父进程pid）

    3. 使用具体过程：在父进程中调用fork（），然后父进程复制一个副本为子进程（程序代码完全一次），然后fork函数返回相应返回值给这2个进程，之后这2个进程同时执行接下来的代码

    4. 为了使父进程和子进程执行不同任务：只需要对fork的返回值进行判断，然后给不同进程分配不同任务

       1. ``` c
          connfd=accept();//创建tcp连接的套接字
          if((pid=Fork())==0){//下方为子进程需要执行的任务
          	close(listenfd);//关闭监听套接字
              doit(connfd);//对该特定的已连接tcp连接完成业务需求
              close(connfd);//关闭该tcp连接
              exit(0); //结束子进程，即子进程不需要继续运行了
          }
          close(connfd)//关闭tcp连接
          ```

    5. close（）：创建套接字时会给套接字积分+1，每用一次fork（）共享一次套接字，也会给套接字的积分+1;每close（）一次套接字，积分-1，当某个套接字积分为0时，该套接字会彻底释放，所以并发服务器中出现了多次close()套接字的情况

20. fork用于多进程的缺陷：

    1. fork是昂贵的，因为父进程中的所有描述符都会被复制进子进程
    2. 从子进程返回信息给父进程是困难的
    3. 解决方案：使用多线程模型

21. 多线程模型：

    1. 优点：创建线程比进程块10-100倍

    2. 缺点：一个进程中所有线程共享相同内存和大部分变量，所以存在同步问题

    3. 编译方式：gcc -o test test.c -lpthread

    4. 相关函数

       1. 创建：pthread_create(&tid,NULL,fun,(void*)arg):意义是创建一个线程，，该线程执行fun函数，参数为arg，其线程id存储于tid中。注意：此处传递的参数是arg值而不是指针，因为由于并发特性，该变量地址可能被下一个连接请求覆盖，所以将参数的值强转为（void *）类型进行传递。

          1. 更好的解决方式：对于每一个线程，使用malloc申请一个内存空间用于存储已连接描述符。就不需要强转了，而只需要直接传递变量地址，只不过在线程中使用完后，需要free。

             ![image-20201019212833334](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201019212833334.png)

       2. 退出：pthread_exit(void **status),pthread_cancel(tid)。一般使用thread_exit(0)结束线程

       3. pthread_join(tid,status):==等待==tid的线程结束，然后将该线程的返回值存入status中

       4. pthread_self():返回进程id

       5. 线程可分为：

          1. 可汇合的（joinable）：当该线程结束时，其id和退出状态会保留，直到另一个线程对其使用pthread_join（）。
          2. 脱离的（detached）：当该线程终止时，该线程所有资源都会释放
          3. 可汇合状态是线程的默认状态，如果需要将线程转为脱离状态，则使用pthread_detach(tid)

22. 多线程模型的缺点：虽然多线程对多进程有一些性能上的改善，但未解决根本问题，所以提出如下多路io模型的解决方案

23. 多路IO模型：

    1. 一般io的特点：
       1. 单路：只等待一个fd的可读或可写（即可输出或可输入）
       2. 阻塞：阻塞直到fd可读或可写
       3. 同步：read和write必须一次性全部完成（中途不能去做其他任务，异步和同步的区别就是正在读或写的过程中能否中断去做其他事）
    2. 相反io的特点：
       1. 多路：可以同时等待多个fd的读或写
       2. 非阻塞：fg无法进行读或写时立即返回。（即如果没有输入是，不继续等待输入，而是继续执行程序）
       3. 异步：读或写的过程没有结束，CPU也可以转向去做其他事情
    3. select函数
       1. select（maxfd1，read，write，NULL,timeout），maxfd1为最大描述符加1，read是需要等待输出的描述符集合，write是需要输入的描述符集合，NULL不需要管，timeout超时时间一般也不要管，设置为NULL。执行select之后会进入阻塞状态，直到read或write中的描述符就绪后，就返回已就绪描述符的个数
       2. 以上的read、write、rest都是fd_set数据类型，
       3. FD_SET(sockfd,&rset)：rest等价于一个数组，开启rest中的一位，然后将sockfd描述符放入该数组中
       4. FD_ISSET(sockfd，&rset)，检验rset中sockfd是否就绪，如果就绪则返回1
    4. 使用select的多路复用IO的优点：可以同时等待多个文件描述符，而这些文件描述符只有有一个就绪，select函数就可以返回。

24. 网络地址相关函数：

    1. inet_ntoa（）：将网络地址转为点分十进制的字符串格式
    2. inet_addr（）：将点分十进制字符串转为长整型的网络地址格式

25. linux套接字编程流程：

    1. TCP：
       1. sockfd=socket(AF_INET,SOCK_STREAM,0)创建服务器端套接字
          1. AF_INET：协议族，表示使用TCP/IP协议
          2. SOCK_STREAM:表示SOCKET类型，此为字节流，是TCP协议；使用SOCK_DGRAM表示是UDP协议，使用SOCK_RAW表示原始套接字
          3. 第三个参数：协议类型（网络层？），为0时表示套接字可以接收内核传递的任何IP数据包。
       2. bind（sockfd,(struct sockaddr*)&server_addr,sizeof(struct sockaddr)）,绑定服务器端套接字网络信息
       3. listen（sockfd，BACKLOG）:是套接字处于监听状态
       4. connect=accept（sockfd，（struct sockaddr*）&client,&len）,使套接字处于阻塞，并等待客户端建立TCP连接。
    2. UDP:

26. 原始套接字的创建：

    1. 创建原始套接字：sockfd=socket(AF_INET,SOCK_RAW,protocol)：protocol是形如IPPROTO_xxx的某个常值

    2. 开启套接字的IP_HDRINCL选项：

       ``` c
       const int on=1;
       setsockopt(sockfd,IPPROTO_IP，IP_HDRINCL,&on,sizeof(on));
       ```

    3. bind（）设置源IP地址（在IP_HDRINCL未开启时）

    4. connect（）：设置目标地址，也较少见

27. 原始套接字的输出：

    1. 普通输出使用sendto、sendmsg并指定IP地址，或者在连接后使用write、writev、send
    2. 如果开启了IP_HDRINCL，则起始IP是首部的第一个字节，输出函数写出的数据量必须包括IP首部的大小。

28. 使用tcpdump抓包：

    1. tcpdump -any i:抓取网卡所有的包
    2. tcpdump host 124.1.1.1：host表示源ip，dst host表示目标ip
    3. tcpdump -i any tcp and dst host 192.168.2.2 and dst port 80:使用and连接多个条件筛选需要抓取的包
    4. tcpdump -i eth0 udp port 12345:eht0可替换为其他网卡，或者any为所有网卡；udp也可替换为其他协议例如tcp。
    
29. win：arp -a查看arp表

30. pipline:|管道,A|B,A的输出作为B的输入

31. grep:拮取

    1. grep -[niv]  ‘string’ filename:指令作用是在filename文件中筛选出含string字符串的==行==，然后输出，注意grep以行为最小单位处理。（n表示显示行数，i表示忽略大小写，v表示取反，即输出不含string的行）
    2. 正则表达式：可以在‘string’中使用正则表达式来代表所需的字符串
       1. [ab]：中括号[ab]只表示=1个==元素，但这个元素可以是括号内的任意一个元素
       2. \[a-b1-9\]:横杠-表示按照ascii码顺序，从a到b的所有字符，再加上从1到9的所有字符
       3. \[\^a-b\]:在中括号内的\^表示取反，即\[\]内表示的元素不能是a-b
       4. \^:\^abc，在中括号外的\^表示起始符，即行的开头必须是abc
       5. abc$:表示该行必须以abc结尾
       6. .:一个点```.```表示任意一个字符
       7. a\*:表示0个或无数个a字符，注意\*和其前一个字符是一体的，共同表达的意思就是0或无数个a字符
       8. a\\{2,6\\}，a\\{2,\\}:注意在正则表达式中使用大括号{}必须加上转移符号\，且和前面一个字符合为一体，共同表达的意思是前面这个字符可以出现2到6次（逗号后没有数字表示到无穷大即无数个）

