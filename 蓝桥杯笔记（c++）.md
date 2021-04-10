## Code Blocks使用笔记

1. 调节编译器
   1. settings->compiler
   2. 选择同目录下的==MinGW==文件
   3. <img src="D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223122924705.png" alt="image-20210223122924705" style="zoom:150%;" />
   
2. 调节debugger
   1. Setting->debugger
   2. 选择MinGW/bin/gdb.exe
   3. ![image-20210223123147799](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223123147799.png)
   
3. 调整字体及风格
   1. settings->Editor
   2. 字体：Consolas，字形：斜体，大小：11
   3. ![image-20210223124203700](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223124203700.png)
   
4. 启动修改后的文件，必须选择 run and build，只选择run只是运行未修改前的exe文件。
   
   1. ![image-20210223125859862](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223125859862.png)
   
5. 自动补全
   1. 自动补全调节至1
   2. ![image-20210223125910394](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223125910394.png)
   
6. 关闭语法纠错
   1. plugins->manage plugins
   2. ![image-20210223131908329](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210223131908329.png)
   
7. 读取文件

   1. ``` c++
      int main(){
          //注意：txt文件每行的末尾有个换行符，需要用getchar（）吸收掉
          freopen("in.txt","r", stdin);
      
          fclose(stdin);
          return 0;
      }
      ```

8. 高亮变量最小字符选择

   1. 调整mininum 至1
   2. ![image-20210224053008258](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210224053008258.png)

9. 创建工程（单个文件可以运行，但不能调试，所以需要工程）

   1. File->new->project

   2. 选择console application

   3. 关闭工程（如果不关闭，则不能再次运行工程之外的文件）

      1. file->close project

   4. 快速启动已有工程：（用于快速运行单文件和debug）

      1. file->recent project

   5. ![image-20210224074302896](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210224074302896.png)

   6. ![image-20210224074706381](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210224074706381.png)

      

10. debug流程

    1. 打断点
    2. 单行调试：F7，进入函数当行调试：shift+F7
    3. 查看变量，点击watchs
    4. ![image-20210224115939282](D:\Typora\note\蓝桥杯笔记（c++）.assets\image-20210224115939282.png)

11. 



