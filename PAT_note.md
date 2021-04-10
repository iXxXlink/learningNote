

## 打卡记录表

|   日期    |                     题号                      |
| :-------: | :-------------------------------------------: |
| 2021.1.9  |                     1004                      |
| 2021.1.10 |                     1005                      |
| 2021.1.11 |                     1006                      |
| 2021.1.12 |                     1007                      |
| 2021.1.13 |                  1008，1009                   |
| 2021.1.14 |                     1010                      |
| 2021.1.15 |                1011，1012,1081                |
| 2021.1.16 |                   1082,1035                   |
| 2021.1.17 |                  1086，1015                   |
| 2021.1.18 |                     1019                      |
| 2021.1.19 |                     1020                      |
| 2021.1.20 |                1021,1023,1024                 |
| 2021.1.21 |           1027,1029,1031,1037,1038            |
| 2021.1.22 |                1040,1041,1043                 |
| 2021.1.23 |                   1044,1045                   |
| 2021.1.24 |              1048,1049,1051,1052              |
| 2021.1.25 |                1155,1154,1152                 |
| 2021.1.26 |         1151,1150,1149,1148,1147,1146         |
| 2021.1.27 |                1145,1144,1143                 |
| 2021.1.28 |      1142,1140,1138,1136,1135,1134,1133       |
| 2021.1.29 |        1132,1130,1129？,1128,1127,1126        |
| 2021.1.30 |         1125,1124,1122,1121,1120,1119         |
| 2021.1.31 |    1118,1117,1116,1115,1113,1112,1110,1109    |
| 2021.2.1  |           1108,1107,1106,1105?,1104           |
| 2021.2.2  |           1103,1102,1101,1100,1099            |
| 2021.2.3  |                1098,1097,1096                 |
| 2021.2.4  |           1094,1093,1092,1091,1090            |
| 2021.2.5  |                   1089,1085                   |
| 2021.2.6  |                1084,1083,1080                 |
| 2021.2.7  |           1079,1078,1077,1076,1074            |
| 2021.2.8  |              1073,1071,1070,1069              |
| 2021.2.9  |                   1068,1065                   |
| 2021.2.10 |         1064,1063,1062,1061,1059,1058         |
| 2021.2.11 |              1056,1055,1054,1053              |
| 2021.2.12 | 1047,1046,1042,1039,1036,1034,1033*,1032,1028 |
| 2021.2.13 |              1025,1022,1014,1013              |
| 2021.2.14 |              1003,1131\*,1111\*               |
| 2021.2.15 |             1087,\*1030,1018***,              |
| 2021.2.16 |                1153,1141,1137                 |
| 2021.2.17 |                     1075                      |
| 2021.2.18 |            1114、1066、1123、1139             |
| 2021.2.19 |                  1017、1088                   |
| 2021.2.20 |               1060、1095、1067                |
| 2021.2.21 |     1016、1026(至此PAT甲级测试题全部完成)     |
| 2021.3.13 |       参加PAT测试（助我好运吧，哈哈哈）       |



## 错误归纳

1. 循环边界错误
2. 使用索引错误
3. vector没有初始化大小就直接通过索引使用
4. 要谨防int溢出，如1049
5. 某个字符串可能出现空格，则需用getline（cin，s）；
6. 链表结点数不仅可能少于n个，甚至可能是0个
7. 检查for循环中变量是否写错：如比较的是k，但自增的是i
8. 判断相等时，容易少写一个=.（2）
9. 必须先看一遍英文题目，然后确认题意，再百度翻译一遍题目，比较与自己理解的差别，最后再根据题意做题
10. to_string（）中要确保不是字符型，因为字符型在该函数中会自动转为整型
11. 全局变量的vector要记得resize
12. 特殊情况：
    1. 输入个数为0或为1
13. 必须接收完所有的输入，不然如果某个测试用例没接收完全部数据就获得了答案，然后跳过接收后面的数据，这样会使得后一个测试用例的数据受到影响，所以不能随意if-else，或者break来跳过接收数据环节
14. 有时输出最后一行空行时，提交后会有某个测试点显示格式错误，所以可以不用输出最后一行空行
15. res+=x：少写了+号，这样的失误危害在于，虽然少写了东西，但是编译器检查不到错误，这样的错误较难发现
16. 必须注意结点的序号是从0还是1开始
17. 存储数据最好不要用char，应用string，因为char存储不了多位数
18. 仔细读题，例如1109中，输入给的是K总行数，而不是每行的个数
19. vector==初始化大小==和==push_back==一般只能使用1个（2者取其一）
20. 因为是纯英文题目，所以输出奇数和偶数时存在区别，如Is和are，可数名词有没有s之类的，必须和输出规则一一致
21. 1107，忘记对vt3排序，竟然还得了23分
22. 最小值的初值太小了，最大值的初值太大了
23. 一定先输入，再处理与数据长度相关的变量
24. 除了并查集，其他的无论多明显都不要考虑从叶子结点向上getfather，一律从上至下使用dfs，一定没问题！
25. 对于某些特殊的结点（根节点、空结点），输入数据中可能会用特殊的值替代，要防止这些特殊值进入正常处理中（例如代表根节点的-1，不能作为vector索引）
26. 运行时错误：vector使用了越界索引（负数或过大）
27. 不要依赖默认值，一定要手动赋初值
28. 对于实际应用题，要注意给出的数据可不可能是浮点数或负数
29. 整数和浮点数同时存在的运算式要注意其中==局部的整数与整数相除==导致的截断
30. 考虑前缀0（即固定位数）的题目，要注意一开始给的数据有没有前缀0
31. 通过对初始值循环转化，最终获得目标值的题目，必须考虑==初始值是否就是目标值==的题目
32. 字符数组开的一定要大，不然字符串缺少终止符‘\0’是不完整的，而且不需要担心转化为string时会出现多余的字符
33. reference to ‘******’ is ambiguous：对某某变量的引用不明确，意思是该变量名与引用库中的变量重名了，导致不知道该使用哪个，解决方法是将自定义变量换一个名字即可
34. 浮点数的四舍五入千万别画蛇添足加0.5,即使自定义测试出错了，提交也不会错
35. \#include<bits/stdc++.h> ：万能头文件
36. 对于精度很高（即小数位很多）的浮点数，不能用double存储，只能用string存储，并且该string不能使用stof转为浮点数判断该数是否是0。（对于上面这种用string存储的浮点数，因为不是用double存储，所以要十分小心==前缀0==）



## 常见英语单词

1. polynomials：多项式
2. exponents ：指数
3. coefficients：系数
4. **every seniority level** ：每一层
5. non-leaf nodes：非叶子结点
6. non-negative integer ：非负整数
7. accurate up to 1 decimal place：精确到小数点后一位
8. radix：进制，基数
9. respectively:各自的，分别的
10. priorities ：优先级
11. rank：排名、等级
12. rational numbers：有理数
13. chronological order：时间顺序
14. alphabetical order：字母顺序
15. Palindromic Number：回文数
16. level order traversal：层次遍历
17. postorder ：后序
18. inorder:中序；
19. preorder：前序
20. topological order：拓扑排序
21. hence ：因此
22. permutation：排列
23. symmetric ：对称的
24. Palindromic：回文的
25. vertices：顶点
26. ancestor ：祖先
27. descendants：后代
28. incompatible ：不相容的
29. ascending order：升序
30. descending order:降序
31. collisions：碰撞，冲突
32. Quadratic  probing：二次探测法
33. negative：负数
34. positive：正数
35. adjacent：相邻的
36. distinct ：不同的
37. corresponding ：对应的
38. properties:特点
39. A vertex cover of a graph is a set of vertices such that each edge of the graph ==is incident to== at least one vertex of the set.：图的点覆盖图是一个点集合，使得该图的每一条都至少和该点集中的一个==相关联==
40. be incident to：相关联
41. Z can ==be devided by== the ==product of A and B==：Z可以被A和B的乘积整除
42. be devided by：被整除、被分割
43. product：乘积
44. even：偶数的
45. odd：奇数的
46. syntax ：语法
47. infix expression：中缀表达式
48. parentheses：括号
49. precedence：优先级
50. If there is a tie：如果有一个平局
51. row、column、diagonal：行、列、对角线
52. halved：减半、对分
53. The result must ==be rounded to== the nearest integer that is no greater than the maximum length.：结果必须==四舍五入==到不大于最大长度的最接近整数。
54. segments ：段
55. piece：片、段
56. rope：绳子
57. chain ：链接
58. more than：大于，不能等于
59. partition：分割
60. disjoint：不相交
61. denote ：表示
62. stucked：卡住
63. invert ：翻转
64. absolute values：绝对值
65. separate list：单独链表
66. consecutive ：连续的
67. pedigree tree：谱系树
68. volume ：体积
69. regions ：区域
70. slice：切片
71. i.e：即
72. pixels ：像素
73. maximum resolution：最大分辨率
74. threshold ：阈值
75. constant：常数
76. Merge sort：归并排序
77. inventory ：清单、库存
78. Shuffling：洗牌
79. identical：完全一样的
80. one-way：单向
81. intersections：交叉点
82. candidate：候选人
83. followed by：紧接的是
84. if..,or…..：如果…，则…..
85. 



## 重要题型分类

1. 最短路径题目：1003、1111、1131、1087、1072、1030、1018
2. 排序：1012、==1016==、1025、==1026==、1028、1055、1062、1075、1080、1083、==1095==、1098、1101、1113、1137、1141、1153
3. 平衡二叉树（AVL）：==1066==，==1123==
4. 窗口排队：==1014==、1017
5. 树状数组（不要求）：1057



ASCII码表

1. ![image-20210117221358566](D:\Typora\note\PAT_note.assets\image-20210117221358566.png)

5. 输出换行：

   ``` c++
   cout<<endl;
   cout<<’\n’;
   cout<<"\n";
   ```

2. 输出空格

   ``` c++
   cout<<" "<<endl;
   ```

3. ``` c++
   //输入的是01，存进去的也只是1
   scanf("%d",&n);
   ```

4. 1004：

   ```c++
   //比较标准的输入方法
   //先只存入2个数，再在前2个数的基础上建立确定次数的循环进行输入。
   scanf("%d%d",&N,&M);
   for(int i=0;i<M;++i)
   {
       scanf("%d%d",&ID,&c);
       for(int j=0;j<c;++j)
       {
           scanf("%d",&child);
           tmp[child].father=ID;
           tmp[ID].children.push_back(child);
       }
   }
   ```

5. 1005：

   1. 所有输入的就是单纯的字符，是视作字符串还是整型自取决于自己用什么类型的变量存储
   2. 必须考虑特殊情况，如输入为空，如此题中的输入为0情况

6. ``` c++
     #include<stack>
     #include<map>
     #include <iostream>
     using namespace std ;
   int main(){
         string N;
         int sum=0;
         stack<int> number;
         map<int,string>mp;
         mp[0]="zero";
         mp[1]="one";
         mp[2]="two";
         mp[3]="three";
         mp[4]="four";
         mp[5]="five";  
         mp[6]="six";
         mp[7]="seven";
         mp[8]="eight";
         mp[9]="nine";
         //输入的就是单纯的字符，是视作字符串还是整型自取决于自己用什么类型的变量存储
         cin>>N;
         for(int l=0;l<N.size();l++){
             sum+=N[l]-'0';
         }
         if(sum==0)//第二测试点。。
         {
             cout<<"zero"<<endl;
             return 0;
         }  
         while(sum){
             number.push(sum%10);
             sum/=10;
         }
         while(!number.empty()){
             int tmp=number.top();
             number.pop();
             if(!number.empty())
                 cout<<mp[tmp]<<" ";
             else
                 cout<<mp[tmp]<<endl;
         }
       return 0;
          }
   ```
   ```
   
   ```


​       
​       

   ```

11. 1006：

   12. 字符串string的可以直接用<、>进行字典序的比较

13. 1007：

    1. ``` c++
       #include <limits.h>
       int a=INT_MIN,b=INT_MAX;
   ```
   ```c++

    2. 题目要全部读完（必须），因为可以包含了对于特殊情况的处理方法，如： If all the *K* numbers are negative, then its maximum sum is defined to be 0, and you are supposed to output the first and the last numbers of the whole sequence.

14. 1009：

    1. 输出流控制小数点后的位数

       1. ``` c++
          #include <iomanip>
          //setiosflags(ios::fixed)说明控制小数点后的位数
          //setprecision(1)说明只保留1位小数点
          //注意：使用了一次setiosflags(ios::fixed)<<setprecision(1)，后面使用的所有cout都保留这个规定
          cout<<it->first<<setiosflags(ios::fixed)<<setprecision(1)<<it->second;
          //输出小数点后1位小数
          printf("%.1f",d);
          //输出12位宽度的数,右对齐
          printf("%12f",d);
          //输出12位宽度的数，左对齐
          printf("%-12f",d);
          //输出12位宽度的数,右对齐，位数不足左侧补0
          printf("%012f",d);
          //总而言之,小数点前面的数表示打印的数占多少位数，小数点后面的数表示要保留几位小数
   ```

15. 1010：

    1. 复杂的程序，最好使用多个函数模块化。优点是逻辑思路清晰，并且易于debug

    2. 当出现自乘时，要注意出现自增的情况，自增的特征就是正数相乘变负

    3. ``` c++
       #include <algorithm>
       //注意c和b的类型必须相同，c为long long，b为int也不行，需要进行强制类型转换
       int a=max(c,b);
       ```

    4. 

16. 1012

    1. ``` c++
       ，
       static bool cmp(int &a,int &b){
           return a>b;
       }
       //sort默认是升序，可以通过修改cmp函数参数，自定义排序方式
       sort(a.begin(),a.end(),cmp);
       ```

    2. ``` c++
       //结构体
       typedef struct{
           int id;
       }stu;
       ```

17. 四舍五入：C语言保留几位数字都是通过截断的方式，所以可以使用+0.5,(0的个数根据需求确定)的方式实现四舍五入。

18. 1081

    1. 对于long类型，scanf的格式必须是ld；

    2. ``` c++
       //求最大公因数
       long long gcd(long long x,long long y) {
           return y?gcd(y, x % y):x;
       }
       ```

19. 1015

    1. ``` c++
       //判断是否是素数
       bool isPrime(int n) {
           if (n == 0 || n == 1) return false;
           //如果是使用i*i<=n,则可能出现i*i溢出！！！！
           for (int i = 2; i <= sqrt(n); i++)
               if (n % i == 0) return false;
           return true;
       }
       ```
    
20. 1020

    1. 树中的每个元素都可以有一个隐藏的序号，根节点为1，左子树根节点为2*n，右子树根节点为2\*n+，然后根据此序号顺序遍历结点的结果就是层序遍历

21. 1021

    1. 图/树的关闭可尝试用二维数组存储，长度为结点的个数

    2. ``` c++
       //连通图个数求法
       int num(vector<vector<int>> &vt){
           int n=vt.size(),res=0;
           vector<bool> flag(n,false);
           queue<int> qu;
           for(int i=0;i<n;++i){
               //每个连通图
               if(!flag[i]){
                   res++;
                   flag[i]=true;
                   qu.push(i);
                   //缺少个！
                   while(!qu.empty()){
                       int now=qu.front();
                       qu.pop();
                       for(int k=0;k<vt[now].size();++k){
                           if(!flag[vt[now][k]]){
                               flag[vt[now][k]]=true;
                               qu.push(vt[now][k]);
                           }
                       }
                   }
                   
               }
           }
           return res;
       }
       ```

    3. 某图的结点数为n，若其是1个连通图，且边数为n-1，那必是树（连通无循环图）

    4. ==结点数为1的情况必须单独考虑==

    5. 并查集：对于无向图来说，并查集中任意2点都是可达的，也即使连通图

    6. ``` c++
       //结点个数n
       int n;
       vector<int> f(n);
       //初始化
       for(int i=0;i<n;i++){
       	f[i]=i;
       }
       for(int i=0;i<n-1;++i){
       	cin>>a>>b;
           make(a,b);
       }
       //添加一条边到图中
       void make(int a,int b){
       	//找到各自并查集的根节点
           a=getf(a);
           b=getf(b);
           //让a点的根节点指向b，完成2个并查集的合并
           if(a!=b){
        		f[a]=b;
               //n最终的结果是连通图的个数，n最开始表示的是总结点个数，因为n减少的值x表示有x个节点插入到某个连通图上，而对于某个连通图而言，除了其根节点，其他所有结点都是插入的，所以最终剩余的n-x，即未插入到其他图中，而自身就是根节点的点。
               n--；
           }
          
       }
       
       //寻找该点的根节点
       int getf(int a){
           //如果该结点是根节点则直接返回
           if(a==f[a])
               return a;
           else
               //递归到其父节点，继续寻找根节点，并且将获得根节点作为该结点的父节点（路径压缩）
         		return f[a]=getf(f[a]);
       }
       ```

    7. ``` c++
       //dfs，这种方法添加了一个参数：父节点，避免了重复递归，这样就省去了flag数组
       
       void dfs(int x,int father,int dep) {
           for (int i = 0; i < con[x].size(); ++i) {
               if (con[x][i] != father) {
                   dfs(con[x][i], x , dep + 1);
               }
           }
       }
       ```

    8. 找到一个树中距离最长的2个节点的方法（距离的计算方法不一定从父到子，可以从左孩子到父节点再到右孩子）（树的直径问题）

       1. 从任意一个节点开始使用dfs，找到以该结点P为根节点的最深的子节点Q(可能不止一个)（另一个结论是，最长线段的2个端点必定是叶子结点，即度为1的结点，因为端点如果有其他度，最长线段就能往其他方向继续延伸）

       2. 可以肯定结点Q必定是树的直径的一个端点，用反证法证明：假设AB是树的直径（当P在树的直径上时，Q自然是直径的端点，当P不在数的直径上时，有如下分析）

          1. 当AB与PQ相交时，因为QC>BC,所以ACQ大于AB，不符舍去

             ![image-20210120113656111](D:\Typora\note\PAT_note.assets\image-20210120113656111.png)

          2. 当AB与PQ不相交时：NQ>NM+MB,所以AMNQ>AB，不符舍去

             ![image-20210120113854867](D:\Typora\note\PAT_note.assets\image-20210120113854867.png)

          3. 综上AB不可能是树的直径，Q是树直径的一个端点

       3. 因为Q是直径的一个端点，所以从Q开始DFS找到的另一个最长点就是直径的另一个端点

22. 1024

    1. to_string()：c++内置函数，可以将int转为string类型

    2. 对于长整型，还是用string存储，安全普适

    3. ``` c++
       string a,tmp;
       int car;
       //在一个等式中不能同时进行整型、字符、字符串的加法,因为car+'0'无法被编译器识别是整型还是字符型，（字符和整型存储方式一样）
       a=car+'0'+a;
       //可以分开进行加法
       tmp=car+'0';
       a=tmp+a;
       //也可以强制类型转换
       a=(char)(car+'0')+a;
       //也不可以2个char类型直接相加得到string
       a='0'+'1';
       //需要分次相加
       a+='0';
       a+='1';
       ```

23. 1038

    1. ``` c++
       //启发：用于比较2个元素那个在前面更好时，不要局限于直接比较这2元素，可以通过比较2种先后排列间接获得元素的大小
       static bool cmp2(string &a,string &b){
           return a+b<b+a;
       }
       ```

    2. res.erase(0,n);（字符串删除从索引0开始的n个元素）

24. 1040

    1. ``` c++
       //cin只能获取从一个非空字符（空格、tab、换行）开始，到一个空字符结束的字符串
       cin>>s
       //getline能获得所有键入的字符（包括空格字符）
       getline(cin, s);
       ```

    2. ``` c++
       //启发：动态规划必须考虑的几个点:1、状态转移方程。2、转移边界，即状态转移的终点必须是初始化的值。3、求所有dp状态的流程算法，尤其是多维时，必须仔细思考如何求，求dp值的顺序是什么，例如此题，是按字符串长度顺序，即（b-a）的值遍历求dp，而不是简简单单先固定行或列坐标。求dp的顺序必须状态转移方程，思考状态转移方程中是从哪种状态转移到哪种状态，这2个状态本质的差异是什么。本题中本质差别就是字符串长度从x转移到了x-2.
       //动态规划，dp[a][b]表示从a到b的字符串是否是回文，转移方程为:当s[a]==s[b]时,dp[a][b]=dp[a+1][b-1]
       //转移边界为b-a=0,b-a=1，所以要先初始化字符串长度为1和2的dp值
       //然后按照字符串长度，依次求出所有长度为3、4...size长度字符串的dp值
       int main(){
           string s;
           getline(cin, s);
           int size=s.size(),max1=1;
           vector<vector<int>> dp(size,vector<int>(size,0));
           for(int i=0;i<size;++i)
               dp[i][i]=1;
           for(int i=0;i<size-1;++i)
               if(s[i]==s[i+1]){
                   dp[i][i+1]=1;
                   max1=2;
           }
                  
           for(int i=3;i<=size;++i){
               for(int k=0;k<size-i+1;++k)
                   if(s[k]==s[k+i-1]){
                       dp[k][k+i-1]=dp[k+1][k+i-2];                
                       if(dp[k][k+i-1])
                           max1=i;
                   }
           }
           cout<<max1<<endl;
           return 0;
       }
       ```

    3. ``` c++
       //中心扩展
       #include <iostream>
       #include <vector>
       #include <algorithm>
       using namespace std ;
       
       //中心扩展法
       int main(){
           string s;
           getline(cin, s);
           int size=s.size(),max1=0;
           
           //以单个字符为中心
           for(int i=0;i<size;++i){
               int tmp=1;
               for(int k=1;(i-k)>=0&&(i+k)<size&&s[i-k]==s[i+k];k++,tmp+=2);
               max1=max(tmp,max1);
           }
           
           //以连续2个相同字符为中心
           for(int i=0;i<size-1;++i){
               if(s[i]!=s[i+1])
                   continue;
               int tmp=2;
               for(int k=1;(i-k)>=0&&(i+1+k)<size&&s[i-k]==s[i+k+1];k++,tmp+=2);
               max1=max(tmp,max1);
           }
           
           cout<<max1<<endl;
           return 0;
       }
       ```

25. 1043

    1. 思路：先假设它是正常的BST，根据其先序序列直接求后序序列，然后如果后序序列的个数小于n，则再假设其为镜像BST，再求其后序序列，如果后序序列的个数小于n，则说明不是BST。

    2. 根据先序序列判断是否是BST的方法：分治判断，当前根节点是否符合BST，即：序列=根节点+小于根节点的连续序列+大于等于根节点的连续序列。然后分治判断左孩子在左子树中、右孩子在右子树中是否符合BST性质

    3. 根据中序序列判断是否是BST：递增即是

    4. 根据一棵树判断是否是BST：求中序序列，其递增即是

    5. ``` c++
       #include <iostream>
       #include <vector>
       #include <algorithm>
       
       using namespace std ;
       
       vector<int> post,pre;
       //getpost根据flag的值，将输入视为BST还是镜像BST
       int flag=0;
       //判断BST树，并根据BST的先序序列求后序序列
       void getpost(int l,int r){
           int root=pre[l],a,b;
           
           if(flag==0)
           {
               //a最终为r+1或者是第一个大于等于root的索引
               //a==r+1时，说明没有右子树
               //a!=r+1时，a为右子树第一个索引
               for(a=l+1;a<=r&&pre[a]<root;a++);
               
               //b最终为l或者是最后一个小于root的索引
               //b==l时，没有左子树
               //b!=l时，b为左子树最后一个索引
           	for(b=r;b>l&&pre[b]>=root;b--);
           }
           else
           {
               //a最终是r+1或是第一个小于root的索引
               //a==r+1时，说明没有右子树
               //a!=r+1时，a为右子树第一个索引
               for(a=l+1;a<=r&&pre[a]>=root;a++);
           	//b最终是l或是最后一个大于等于root的索引
               //b==l时，没有左子树
               //b!=l时，b为左子树最后一个索引
               for(b=r;b>l&&pre[b]<root;b--);
           }
           
           ///****/因为b右侧的所有数都符合右子树特性，a左侧所有数都符合左子树特性，所以如果a==b+1，说明对于该根节点符合BST树的性质，即（根节点、小于根节点的连续序列、大于等于根节点的连续序列）,如果a!=b+1，这说明当前判断序列不是一颗BST树
           if(a-b!=1)
               return;
           
           if(b>=l+1)
               getpost(l+1,b);
           if(r>=a)
               getpost(a,r);
           post.push_back(root);
       }
       
       
       int main(){
           int n;
           cin>>n;
           pre.resize(n);
           for(int i=0;i<n;++i){
               cin>>pre[i];
           }
           getpost(0,n-1);
           
           if(post.size()!=n){
               flag=1;
               post.clear();
               getpost(0,n-1);
           }
           
           if(post.size()!=n){
               cout<<"NO"<<endl;
               return 0;
           }
           cout<<"YES"<<endl;
           for(int i=0;i<n;++i){
               if(i==0)
                   cout<<post[i];
               else
                   cout<<" "<<post[i];
           }
           cout<<endl;
       
           
           return 0;
       }
       ```

    6. 按照BST先序序列插入创建BST能够还原出BST（后序序列则不行）

26. 1044

    1. 还是需要使用printf和scanf，因为cin和cout太慢了，例如该题必须使用printf，否则会超时。

    2. 滑动窗口法：遍历前缀和向量的每一个元素i，然后j递增找到第一个j，使得i-j小于等于target，然后判断此时的i和j是否满足题意。

    3. 滑动窗口适用的原因：由于前缀和数组是递增数组，

    4. ```c++
       #include <vector>
       #include <limits.h>
       #include <cstdio>
       using namespace std ;
       
       int main(){
           int n,m,tmp,flag=0,min=INT_MAX,j=0;
           vector<int> minl,minr;
           scanf("%d%d",&n,&m);
           vector<int> presum(n+1,0);
           //滑动窗口法
           for(int i=1;i<=n;++i){
               scanf("%d",&tmp);
               presum[i]=presum[i-1]+tmp;        
               for(;presum[i]-presum[j]>m;j++);
               if(presum[i]-presum[j]==m){
                   printf("%d-%d\n",j+1,i);
                   flag=1;
               }
               if(!flag&&j!=0){
                   if(presum[i]-presum[j-1]<min){
                       min=presum[i]-presum[j-1];
                       minl.clear();
                       minr.clear();
                       minl.push_back(j);
                       minr.push_back(i);
                   }
                   else if(presum[i]-presum[j-1]==min){
                       minl.push_back(j);
                       minr.push_back(i);
                   }
               }
           }
           if(!flag){
               for(int i=0;i<minl.size();++i){
                   printf("%d-%d\n",minl[i],minr[i]);
               }
           }
           
       
           return 0;
       }
       
       ```

    5. ``` c++
       //二分法
       #include <iostream>
       #include <vector>
       using namespace std;
       vector<int> sum, resultArr;
       int n, m;
       
       void Func(int i, int &j, int &tempsum) {
           int left = i, right = n;
           while(left <= right) {
               int mid=left+(right-left)/2;
               if(sum[mid]>=m+sum[i])
                   right=mid-1;
               else
                   left=mid+1;
           }
           j = left;
           tempsum = sum[j] - sum[i];
       }
       
       int main() {
           scanf("%d%d", &n, &m);
           sum.resize(n+1);
           for(int i = 1; i <= n; i++) {
               scanf("%d", &sum[i]);
               sum[i] += sum[i-1];
           }
           int minans = sum[n],flag=0;
           for(int i = 0; i < n; i++) {
               int j, tempsum;
               Func(i, j, tempsum);
               if(tempsum==m){
                   if(flag==0){
                       flag=1;
                       resultArr.clear();                
                   }
                   resultArr.push_back(i+1);
                   resultArr.push_back(j);            
               }
               //虽然你func中求的是大于等于m的结果，但因为可能不存在大于等于的结果，所以此处必须加上判断
               else if(tempsum>m&&flag==0){
                   if(tempsum<minans){
                       minans=tempsum;
                       resultArr.clear();
                       resultArr.push_back(i+1);
                       resultArr.push_back(j);
                   }
                   else if(tempsum==minans){
                       resultArr.push_back(i+1);
                       resultArr.push_back(j);
                   }
               }
       
           }
           
           for(int i=0;i<resultArr.size();i+=2){
               printf("%d-%d\n",resultArr[i],resultArr[i+1]);
           }
       
           return 0;
       }
       
       ```
    
27. 1050：从字符串a中删去字符串b中所有字符

    1. 创建bool flag[256]数组，因为ASCII字符最多256个，然后遍历b中每一个字符，将其在数组对应位置的索引设置为true。然后遍历字符串a，只输出flag为false的字符
    2. 其本质就是通过将字符串b映射到flag数组上，而实现高效地、只通过char索引访问就能知道该字符是否在字符串b中（set同样可以实现，并且根具有普适性）

28. 1052

    1. 结果的链表中的结点数可能少于n个，并且还有可能是0个

29. 1155

    1. 完全二叉树（不一定是满二叉树）可以用vector存储，设root索引是x，则左孩子索引是2x，右孩子是2x+1

    2. ``` c++
       //判断堆
       int isMin=1,isMax=1;
        for (int i = 2; i <= n; i++) {
            	//如果孩子结点小于父节点，那一定不是小堆
               if (a[i]<a[i/2]) isMin = 0;
            	//如果孩子结点大于父节点，那一定不是大堆
               if (a[i]>a[i/2]) isMax = 0;
       }
       if (isMin == 1)
           printf("Min Heap");
       else 
           printf("%s", isMax == 1 ? "Max Heap" : "Not Heap");
       ```

    3. ``` c++
       #include <iostream>
       #include <cstdio>
       #include <algorithm>
       #include <vector>
       
       using namespace std ;
       vector<int>vt;
       int n;
       void helper(vector<int>&tmp,int root){
           
           tmp.push_back(vt[root]);
          if(root*2+1<=n)
               helper(tmp,root*2+1);
           if(root*2<=n)
               helper(tmp,root*2);
           else{
               for(int i=0;i<tmp.size();++i){
                   if(i==0)
                       cout<<tmp[i];
                   else
                       cout<<" "<<tmp[i];
               }
               cout<<endl;
           }
           tmp.pop_back();
       }
       int main(){
           cin>>n;
           vt.resize(n+1);
           for(int i=1;i<n+1;++i){
               cin>>vt[i];
           }
           vector<int>tmp,flag(n+1,0);
           helper(tmp,1);
           int i;
           //max heap
           for(i=1;i<n+1;++i){
               if(2*i<=n&&vt[i]<vt[2*i])
                   break;
               if((2*i+1)<=n&&vt[i]<vt[2*i+1])
                   break;
           }
           if(i==n+1){
               cout<<"Max Heap"<<endl;
               return 0;
           }
           //min heap
           for(i=1;i<n+1;++i){
               if(2*i<=n&&vt[i]>vt[2*i])
                   break;
               if((2*i+1)<=n&&vt[i]>vt[2*i+1])
                   break;
           }
           if(i==n+1){
               cout<<"Min Heap"<<endl;
               return 0;
           }
           
           cout<<"Not Heap"<<endl;
           return 0;
       }
       ```

30. 1152

    1. s.substr(i,k)：获取子串，从s的i索引开始的长度为k的子字符串
    2. string转为int：int n=stoi(s)；（stoi，string to int的缩写）
    3. int转为string：string s=to_string(n);

31. 1150

    1. simple cycle：该环经历了图中的每一个结点，并且有且只有首位结点是相同的，其他节点只经过一次的环

32. 1148

    1. int:能够保存+8，（即使前面有一个加号也可以用int保存）

    2. ``` c++
       #include <cmath>
       //绝对值
       int a=abs(-1);
       ```

33. 1147

    1. 判断堆

       1. ``` c++
          //Min Heap
              for(i=2;i<=n;i++){
                  if(vt[i]<vt[i/2])
                      break;
              }
              if(i==n+1){
                  printf("Min Heap\n");
                  return;
              }
          ```

    2. ==完全二叉树==的==层次遍历==转其他遍历（先、中、后）（堆是完全二叉树）

       1. ``` c++
          void helper2(int x){
              if(2*x<=n)
                  helper2(2*x);
              if(2*x+1<=n)
                  helper2(2*x+1);
              //cout的位置决定了遍历方式
              cout<<vt[x];
          }
          ```

34. 1146

    1. 存储有向图的方法：

       1. 邻接矩阵：固定(n+1)*(n+1)的大小，优点是实现简单清晰，缺点是不适合稀疏图，稀疏矩阵会产生巨大浪费

          1. ``` c++
             vector<vector<int>>G(n+1,vector<int>(n+1,-1));
             //表示从A到B边的大小
             G[A][B]
             ```

             

       2. 邻接表：大小不固定，适合稀疏图

          1. ``` c++
             //与上面的区别是vector大小不固定
             vector<vector<int>>G(n+1,vector<int>);
             ```

    2. 实现拓扑排序：

       1. 重点：创建一个入度表，记录每个绩点的入度，
       2. 每次遍历选择某个入度为0的点作为当前排序点
       3. 然后遍历该点的所有出点，将出点的度减1，在进行第步2操作

35. 1145

    1. 哈希解决冲突之平方探测法：即产生冲突时，顺序检测H(key)+1\*1、H(key)-1\*1，H(key)+2\*2、H(key)-2\*2……….H(key)+i\*i

       1. 可以证明：如果某个元素在i遍历[0，Tsize)的范围都找不到位置，可以确认该元素找不到位置(只需要检测size+1次？)

       2. ``` c++
          int detect(int x){
              int res=0;
              //注意点1：i的范围必须为0到size，左右都闭
              for(int i=0;i<=size;++i){
                  res++;
                  //注意点2：不仅是检测到值相同返回，为0（即为赋值时）也需要返回
                  if(table[(x+i*i)%size]==x||table[(x+i*i)%size]==0)
                      break;
              }
              return res;
          }
          ```

36. 1143

    1. 1151也是一道找LCA，区别是1151是普通二叉树，但给了中序和先序2个遍历序列，但是该题只给了一个，所以不能在常数时间复杂度下获得左右孩子索引，所以该题不能像1151一样分治解决，直接遍历每一个结点，检测其是否是所寻找的LCA即可

37. 1142

    1. 所有的以return 结尾的if-else都可以转为等价三目运算式
    2. 可以在程序的不同位置插入 return 0,观察何时报错以确定代码错误位置
    3. 在考场上思考了许久也没发现有巧妙解法时，就用==暴力解决==

38. 1136

    1. 使用printf输出string

       1. ``` c++
          //错误事例
          	string str="hello";
          	//注意：%s输出的是char*类型，而不是string类型
          	printf("%s",str);
          
          //正确事例
          	string str="hello";
          	printf("%s",str.c_str());    // 调用c_str()函数
          
          ```

    2. 自带的翻转字符串函数

       1. ``` c++
          reverse(s.begin(), s.end());
          ```

    3. 字符串加法：

       1. ``` c++
          string addfs(string a,string b){
              string tmps;
              if(a.size()<b.size()){
                  tmps=a;
                  a=b;
                  b=tmps;
              }
              int an=a.size()-1,bn=b.size()-1,car=0,tmp;
              for(;bn>=0;bn--,an--){
                  tmp=car+a[an]-'0'+b[bn]-'0';
                  car=tmp/10;
                  a[an]=tmp%10+'0';
              }
              for(;an>=0;an--){
                  tmp=car+a[an]-'0';
                  car=tmp/10;
                  a[an]=tmp%10+'0';
              }
              if(car){
                 string res="1";
                  res=res+a;
                  return res;
              }
              else{
                  return a;
              }
          }
          ```

39. 1135

    1. 经典错误：f1、f2必须先赋初值true，不然如果左子树不存在，那么f1默认为false与事实不符

       1. ``` c++
          bool f1=true,f2=true;
          if(root>0)
              num++;
          if(l+1<=i-1)
              f1=helper(l+1,i-1,num);
          if(i<=r)
              f2=helper(i,r,num);
          return f1&&f2;
          ```

    2. 可以根据BST的==先序遍历==建树

    3. 想不出较好方法时，可以考虑建树

       1. ``` c++
          struct node {
              int val;
              struct node *left, *right;
          };
          //将v元素添加入BST中，并返回根节点地址
          node* build(node *root, int v) {
              if(root == NULL) {
                  root = new node();
                  root->val = v;
                  root->left = root->right = NULL;
              } else if(v <= root->val)
                  root->left = build(root->left, v);
              else
                  root->right = build(root->right, v);
              return root;
          }
          ```

40. 1134

    1. 判断一个点集是否包括了每一条边的至少一个顶点。
       1. 法一：遍历所有边，判断每一边的2个顶点是否至少有1个在点集中。（遍历边，判断点）
       2. 法二：遍历点集，标记出其中每个点参与的所有边，然后判断是否是所有边都被标记了。（遍历点，判断边）

41. 1133

    1. vector的合并

       1. ``` c++
          //将vec1插入到vec3末尾
          vec3.insert(vec3.end(),vec1.begin(),vec1.end());
          ```

    2. ``` c++
       //定义结构体变量
       typedef struct{
           int add,val,next;
       }node;
       //直接通过结构体名就定义了一个node变量，
       node tmp;
       //通过new创建变量，返回的是变量指针！！
       node* tmp2=new node();
       ```

    3. 哈希映射时：如果原值的范围较小，可以直降用vector的索引映射；范围较大就只能用map了

    4. 哈希映射的意义：在于（通过某个索引）在O（1）时间内找到特定元素（或多个元素）

42. 1132

    1. 基本类型范围

       1. ![image-20210129054956856](D:\Typora\note\PAT_note.assets\image-20210129054956856.png)

    2. 浮点错误：通常出现除以0或==模0==的情况

    3. 除法、模运算要考虑除0、模0的情况

    4. ``` c++
       a=s.substr(i,n)//s从i索引开始的长度为n的子字符串
       ```

43. 1129

    1. map中value为某个结构体时，即使某个key还未定义，但可以引用其value的成员变量，（成员变量需要为基本类型，初值为0）

    2. 结构体构造函数和重载符号（方便set自动排序）

       1. ``` c++
          struct node {
              int value, cnt;
              //自定义构造函数，方便find时定义一个变量
              node(int a, int b):value(a), cnt(b){}
              //重载小于号<，使得能在set内部就按照次数降序排序，次数相同则按照索引升序排序
              bool operator < (const node &a) const {
                  return (cnt != a.cnt) ? cnt > a.cnt : value < a.value;
              }
          };
          ```

    3. set之查找结构体和set增加、删除元素

       1. ``` c++
          //如果set中元素是结构体，则find查询时，查询依据是每个成员变量的值。且最好使用构造函数，方便定义一个值
          auto it = s.find(node(num, book[num]));
          ```

    4. erase（it），注意：参数必须是迭代器

       1. ```  c++
          //set删除元素
          if (it != st.end()) 
              st.erase(it);
          ```

44. 1121

    1. 遍历set集合

       1. ``` c++
          for(auto it=st.begin();it!=st.end();it++)
              //it迭代器可以看作是地址，所以使用*就可获得目标值
          cout<<*it<<endl;
          ```

    2. 格式错误：常见于最后输出了一行空行

45. 1120

    1. 遍历map

       1. ``` c++
          for(auto it=mp.begin();it!=mp.end();it++)
              //map通过引用first表示key值，通过second表示val值
              cout<<it->first<<it->second;
          ```

46. 1119：根据前序和后序遍历序列判断该树是否可以被唯一分辨，如果不可以，也要输出多种情况中的一种

    1. 理解：根据前序和后序之所以不能唯一判别，是因为当某个结点只有一颗子树时，无法分辨该子树时左子树还是右子树。所以只有每个结点都有0或2个子树时才能唯一判别。

    2. 当先序中的LC与后序中的RC相等时，即只有一颗子树，此时无法唯一判别该子树时左子树还是右子树，可以将除了R之外的所有点视作左子树或右子树

    3. L：表示左子树结点，R：表示右子树结点![image-20210130193640252](D:\Typora\note\PAT_note.assets\image-20210130193640252.png)

    4. ``` c++
       #include <iostream>
       #include <vector>
       
       using namespace std;
       int flag=0;
       vector<int>pre,post,in;
       void helper(int preL,int preR,int postL,int postR){
           //当一颗子树也没时
           if(preL==preR){
               in.push_back(pre[preL]);
               return;
           }
           
           int tmp=pre[preL+1],i;
           for(i=postL;i<postR&&post[i]!=tmp;++i);
           
           //当某棵子树为空时，无法判断剩余的那颗是左子树还是右子树，情况有多种，假设此为左子树
           if(i==postR-1){
               flag=1;
               helper(preL+1,preR,postL,postR-1);
               in.push_back(pre[preL]);
               
           }else{
               int nol=i-postL+1;
               //left
               helper(preL+1,preL+nol,postL,i);
               in.push_back(pre[preL]);
               //right
               helper(preL+nol+1,preR,i+1,postR-1);
           }
       }
       int main(){
           int n;
           cin>>n;
           pre.resize(n);
           post.resize(n);
           for(int i=0;i<n;++i)
               cin>>pre[i];
           for(int i=0;i<n;++i)
               cin>>post[i];
           helper(0,n-1,0,n-1);
           if(flag)
               cout<<"No"<<endl;
           else
               cout<<"Yes"<<endl;
           for(int i=0;i<in.size();i++){
               if(i==0)
                   cout<<in[i];
               else
                   cout<<" "<<in[i];
           }
           cout<<endl;
           return 0;
       }
       ```

47. 1118

    1. 并查集获得根节点只能使用getfather（）函数，不要使用father数组

48. 1117

    1. more than:一定是大于，而不能等于

    2. ``` c++
       //使用greater<int>(),更方便地从大到小排序
       sort(vt.begin(),vt.end(),greater<int>());
       ```

49. 1115

    1. ``` c++
       //C++中，结构体创建不需要用typedef,之后不管是定义变量还是指针还是new，都不需要加struct！
       struct node{
           int val;
           node* left;
           node* right;
       };
       ```

    2. 良好的编程习惯：将未初始化的指针设置为nullptr

50. 1110

    1. 判断某棵树是否是完全二叉树的一种方法：设x为该树中的最大索引值（根节点索引值为1，左孩子为根节点的2倍，右孩子索引为根节点的2倍加1），n为结点个数，必有n<=x，当且仅当，该树为完全二叉树时，才有n==x。

    2. 

       1. ``` c++
          #include <iostream>
          using namespace std;
          struct node{
              int l, r;
          }a[100];
          int maxn = -1, ans;
          void dfs(int root, int index) {
              //此处十分重要
              if(index > maxn) {
                  maxn = index;
                  ans = root;
              }
              if(a[root].l != -1) dfs(a[root].l, index * 2);
              if(a[root].r != -1) dfs(a[root].r, index * 2 + 1);
          }
          int main() {
              int n, root = 0, have[100] = {0};
              cin >> n;
              for (int i = 0; i < n; i++) {
                  string l, r;
                  cin >> l >> r;
                  if (l == "-") {
                      a[i].l = -1;
                  } else {
                      a[i].l = stoi(l);
                      have[stoi(l)] = 1;
                  }
                  if (r == "-") {
                      a[i].r = -1;
                  } else {
                      a[i].r = stoi(r);
                      have[stoi(r)] = 1;
                  }
              }
              while (have[root] != 0) root++;
              dfs(root, 1);
              if (maxn == n)
                  cout << "YES " << ans;
              else
                  cout << "NO " << root;
              return 0;
          }
          ```

51. 1109

    1. 对于从中间开始，左右交替输出的题（或逆向的，最左右交替输出），可以考虑先确定中间点，然后先输出一个方向，自增为2，再输出另一个方向，自增为2，循环退出的条件都相同（都是小于该行的总个数）

       1. ``` c++
          ans[m / 2] = stu[t].name;
          // 左边一列
          //先获得最中间的索引
          int j = m / 2 - 1;
          //注意：2个循环退出条件都是小于m,自增只是2
          for(int i = t + 1; i < t + m; i = i + 2)
              ans[j--] = stu[i].name;
          // 右边一列
          j = m / 2 + 1;
          for(int i = t + 2; i < t + m; i = i + 2)
              ans[j++] = stu[i].name;
          ```
    
    
    
52. 1108

    1. 整型、[浮点型和字符串的相互转换](https://www.cnblogs.com/onycea/p/5400681.html)

       1. ``` c++
          //整型和浮点型转为字符串
          string s=to_string(x);
          ```

       2. ``` c++
          //字符串转整型
          string s;
          //stoi直接用string就行，不需要c_str()转为字符数组
          int a=stoi(s);
          //atoi要转为，使用c_str()转为字符数组
          int b=atoi(s.c_str());
          ```

       3. ``` c++
          //字符串转双浮点型
          //string使用stof，char*使用atof（s表示string字符串，a表示array字符数组，f表示float浮点型）
          double t1=stof(s),t2=atof(s.c_str());
          ```

    2. 读取和输出格式化字符串数据（==这种方法十分适合于判断输入字符串的合法性==）

       1. 保留小数的规则时四舍六入五成双

       2. ``` c++
          //这种方法十分适合于判断输入字符串的合法性
          char a[50], b[50];
          double temp;
          //从标准输入流（键盘）输入的字符串存入a字符串数组中
          scanf("%s", a);
          //将a数组作为输入流，以%lf的格式输入到变量temp中
          //（%lf表示双精度，%f表示单精度）
          sscanf(a, "%lf", &temp);
          //在将temp作为输出流，将temp以%.2f的格式输出到b中,
          sprintf(b, "%.2f",temp);
          //注意：sscanf的输入和sprintf的输出都必须是字符串数组
          //二者的区别在于：sscanf输入和格式不同时是选择不再输入，返回EOF,而sprintf输出和格式不同时直接报错
          ```

       3. ![image-20210201144513375](D:\Typora\note\PAT_note.assets\image-20210201144513375.png)

    3. 获得字符串的大小

       1. ``` c++
          //string类型
          string a;
          a.size();
          //字符串数组类型
          #include <cstring>//使用strlen()必须引用cstring
          char b[20];
          strlen(b);
          ```

53. 1107

    1. 并查集的极简写法

       1. ``` c++
          vector<int>father;
          int getf(int x){
              return father[x]=(x==father[x]?x:getf(father[x]));
          }
          void insert(int x,int y){
              father[getf(x)]=getf(y);
          }
          ```

    2. 如果输入的测试用例有特殊的格式，可以在scanf的格式中也设置特殊格式，就可以只提取所需的数据

       1. ``` c++
          scanf("%d:", &t);
          ```

54. 1106

    1. ==能用dfs就用dfs==，无他，绝不超时
    2. printf（）输出格式指定位数后会自动四舍五入，不需要人为的加0.5（对于浮点数实际上是：四舍六入，五的话使得最后一位有效位是偶数）（有其他情况就是浮点数不够精确，有误差，但是PAT中题目都不需要加0.5）

55. 1104

    1. 该题思路比较清晰，每个数在总和中出现的次数是：子序列左端点的个数*子序列右端点的个数。但由于double类型数据与大数直接相乘会产生精度上的误差问题，使得测试点2无法通过。所以使用现将double类型的tmp变量\*1000（貌似只有输入的小数只精确到小数点后3位），转为long long类型，再正常进行整型的乘法，最后输出时结果res除以1000.0,以浮点型输出

56. 1103

    1. 一直认为很难，所以很抗拒写，但是一旦强迫自己一定要写，当手指接触到键盘，然后一步一步的完成每一个模块，最终一次ac，才发现，原来这么简单，其实很多道题，很多事物也是同样的道理。还真是那句烂大街的话语最具概括力，世上无难事，只怕有心人。
    2. dfs yyds！！！
    3. dp思路：dp\[i\][j\]的值为1和0，分别表示以i为最大索引，j的sum总和，是否存在分割法（1表示存在，0表示不存在），状态转移方程式**dp\[i\]\[j\]=dp\[i\]\[j-vt\[i\]\]  ||  dp\[i-1\]\[j\]**。边界情况时=0

57. 1100

    1. getline是遇到一个回车停止，cin和scanf都是遇到空格就停止，所以该题中使用cin获得了n后，需要用getchar()吸收掉缓冲区中的的换行符，再使用getline获得一行数据。

58. 1098

    1. 堆排序实质：将序列放入完全二叉树中，并且初始化使得父节点的值大于孩子结点（大堆的性质），然后取出根节点的值（一定为当前序列最大值）与最大叶子结点交换（该叶子结点视作已排序结点，不参与后序操作），然后从根节点开始调整，使得整颗完全二叉树再次满足大堆的性质。

    2. [堆排序步骤](https://www.cnblogs.com/chengxiao/p/6129630.html)

       1. 前提准备阶段：将整个vector视作完全二叉树（实际的堆结构就是完全二叉树），所以索引为X的左孩子是2X+1(因为根节点是0不是1)，右孩子是2X+2，索引==最大的非叶子结点==是==Y=SIZE/2-1==(SIZE为vector的长度)，
       2. 初始化阶段：（使无序序列转换为堆）
          1. ==adjust（Y）调整函数==：如果索引P的值小于其孩子结点的值,则交换索引Y的值和最大孩子的值，并且对交换过的那个孩子结点继续使用adjust函数（这样的目的是保证每个父节点都大于孩子结点）
          2. 从Y开始向左边遍历：对当前结点使用adjust（）函数
       3. 排序阶段（每次获得当前未排序序列的最大值，放入已排序序列中）
          1. 将根节点即索引为0的结点值与索引为SIZE-1的结点值交换，并且SIZE=SIZE-1（即将该根节点值加入已排序序列中，未排序序列长度减1）
          2. 然后对交换过的根结点使用adjust（）函数。再跳转到步骤1(当SIZE==1时排序结束)

59. 1097:脑残题目，不同的绝对值的多余项不是放在不同链表中，而是放在同一条链表中

    1. ![image-20210203182755312](D:\Typora\note\PAT_note.assets\image-20210203182755312.png)
    2. 链表的头结点必须初始化为-1,不然默认值为0，当链表为空，如果真存在地址为0的点，那原本为空的链表就会输出其他值

60. 1096

    1. 判断素数不要再使用i*i<N，可能出现溢出，要使用i<sqrt(n）

    2. 和因素有关的的题目，可以考虑特判素数

    3. 一个数的因素不只是小于等于sqrt(n)，除了自身以外还至多有n/2

    4. 对于这种求某种连续序列的题目，不需要存储所有数据，==只需要存储起点和长度即可==！！

       1. ``` c++
          #include <iostream>
          #include <cmath>
          using namespace std;
          long int num, temp;
          int main(){
              cin >> num;
              int first = 0, len = 0, maxn = sqrt(num) + 1;
              for (int i = 2; i <= maxn; i++) {
                  int j; 
                  temp = 1;
                  for (j = i; j <= maxn; j++) {
                      temp *= j;
                      if (num % temp != 0) break;
                  }
                  if (j - i > len) {
                      len = j - i;
                      first = i;
                  }
              }
              if (first == 0) {
                  cout << 1 << endl << num;
              } else {
                  cout << len << endl;
                  for (int i = 0; i < len; i++) {
                      cout << first + i;
                      if (i != len - 1) cout << '*';
                  }
              }
              return 0;
          }
          ```

61. 1091:此题是三维空间

    1. dfs递归层数太多可能会导致爆栈，显示段错误，用bfs解决

    2. ``` c++
       //结构体的构造函数
       struct node{
           int x,y,z;
          //注意没有分号
           node(int a, int b, int c) :x(a), y(b), z(c){}
       };
       //使用node构造函数，node（）
       qu.push(node(a,b,c-1));
       ```

62. 1090

    1. 除了并查集，其他的无论多明显都不要考虑从叶子结点向上getfather，一律从上至下使用dfs，一定没问题！
    2. 对于某些特殊的结点（根节点、空结点），输入数据中可能会用特殊的值替代，要防止这些特殊值进入正常处理中（例如代表根节点的-1，不能作为vector索引）
    3. 如果给出提升率或降低率k，使用时注意要先除以100再加上1才能作为幂：pow（（1+k/100）,n）;
    4. 函数的参数不要写反
    5. 运行时错误：vector使用了越界索引（负数或过大）

63. 1089

    1. vector可以直接用=判断是否相等

64. 1084

    1. 将转为大写字符（单个字符）

       1. ``` c++
          #include <cctype>
          s2[i] = toupper(s2[i]);
          ```

65. 1083

    1. 不要依赖默认值，一定要手动赋初值

66. 1077

    1. 这种思路比较好

    2. ``` c++
       #include <iostream>
       #include <algorithm>
       using namespace std;
       int main() {
           int n;
           scanf("%d\n", &n);
           string ans;
           for(int i = 0; i < n; i++) {
               string s;
               getline(cin, s);
               int lens = s.length();
               reverse(s.begin(), s.end());
               if(i == 0) {
                   ans = s;
                   continue;
               } else {
                   int lenans = ans.length();
                   if(lens < lenans) swap(ans, s);
                   int minlen = min(lens, lenans);
                   for(int j = 0; j < minlen; j++) {
                       if(ans[j] != s[j]) {
                           ans = ans.substr(0, j);
                           break;
                       }
                   }
               }
           }
           reverse(ans.begin(), ans.end());
           if (ans.length() == 0) ans = "nai";
           cout << ans;
           return 0;
       }
       ```

67. 1076

    1. BFS+裁剪=YYDS！
    
68. 1073

    1. 字符串多种增减修改

    2. ``` c++
       //1、提取子字符串
       //第二个参数缺省，表示截取索引后面剩余所有字符
       s2=s.substr(i+1);
       
       //2、删除从索引2开始的长度为1的字符串
       s1.erase(2,1);
       
       //3、在s1字符串的索引为2处，插入字符串“.”
       s1.insert(2,"0.");
       ```

69. 1071

    1. [判断某个字符是否是数字或字母及大小写字母转换](https://www.cnblogs.com/r1-12king/p/13161762.html)

    2. ``` c++
       #include <cctype>
       //判断一个字符是否是字母
       isalpha('a');
       //判断一个字符是否是字母或数字
       isalnum('a');
       ```

70. 1070

    1. 对于实际应用题，要注意给出的数据可不可能是浮点数或负数
    2. 整数和浮点数同时存在的运算式要注意其中局部的整数与整数相除导致的截断

71. 1069

    1. string也能使用sort进行字符排序

    2. [string和字符数组相互转换](https://www.cnblogs.com/fnlingnzb-learner/p/6369234.html)

       1. ``` c++
          char a[5];
          string s;
          //字符数组转为string，直接用等号
          //tip：字符数组开的一定要大，不然字符串缺少终止符‘\0’是不完整的；
          //而且不需要担心转化为string时会出现多余的字符
          s=a
          //string转为字符数组，使用strcpy,将string的c_str()复制
          strcpy(a,s.c_str());
          ```

    3. 考虑前缀0（即固定位数）的题目，要注意一开始给的数据有没有前缀0

    4. 通过对初始值循环转化，最终获得目标值的题目，必须考虑初始值是否就是目标值的题目

    5. 字符数组开的一定要大，不然字符串缺少终止符‘\0’是不完整的，而且不需要担心转化为string时会出现多余的字符

72. 1065

    1. ==正溢出的结果一定小于0,负溢出大于等于0==
    2. 对于longlong一定要用scanf进行输入，且格式为%ll

73. 1064

    1. 完全二叉树前、中、后序的遍历序列的递归边界都是如下的，注意root表示完全二叉树中结点的序列

       1. ``` c++
          if(root>=n)
              return;
          ```

    2. 完全二叉树的层序遍历序列就是按照完全二叉树中结点的序列顺序输出。

    3. 该题中给出完全二叉搜索树的结点序列，求其层次序列

       1. 将结点排序的到in[n]
       2. 中序遍历==结点序号==（非结点值），当前结点序号root对应的结点值就是：vt[root]=in[now++]
       3. 因为vt的索引对应的就是结点序号，所以vt顺序输出即是层次序列

74. 1063

    1. 2个set合并

       1. ``` c++
          a.insert(b.begin(),b.end());
          ```

75. 1062

    1. ``` c++
       //sort的cmp有多种规则时，建议使用if(a!=b)的判断形势
       bool cmp(per &a,per &b){
           if(a.lev!=b.lev)
               return a.lev>b.lev;
           else if(a.tel+a.vir!=b.tel+b.vir)
               return (a.tel+a.vir)>(b.tel+b.vir);
           else if(a.vir!=b.vir)
               return a.vir>b.vir;
           else
               return a.id<b.id;
       }
       ```

76. 1057

    1. vector、string、deque的迭代器是有加减法的；而map、set、multimap、multiset、list的迭代器是没有加减法的。他们仅支持++itr、–itr这些操作。
    2. ++it返回的是引用，it++返回的是临时对象。所以++it更好
    3. sort排序范围是左闭右开！！！

77. 1056

    1. ![image-20210211221157014](D:\Typora\note\PAT_note.assets\image-20210211221157014.png)
    2. 一开始理解错了题意：The third line gives the initial playing order which is a permutation of 0,⋯,N-1。这句话的意思是第三行的数据是初始比赛==排序==，该顺序是0..N-1的一种排列。注意：0..N-1是老鼠的序号，所以第一组比赛成员是6 0 8号老鼠。而我一开始的错误理解是该行数据对应的比赛顺序。
    3. 即正确的理解是：索引是比赛顺序，值是老鼠序号
    4. 我的错误理解是：索引是老鼠序号，值是比赛顺序
    5. 理解的关键在于0..N-1表示的是老鼠的序号

78. 1053

    1. 对vector<vector<int>>的自定义排序（按字典序递减）

       1. ``` c++
          bool cmp(vector<int>&a,vector<int>&b){
              int size=min(a.size(),b.size());
              for(int i=0;i<size;++i)
                  if(a[i]!=b[i])
                      return a[i]>b[i];
              return a.size()>b.size();
          }
          ```

79. 1046

    1. 前缀和是一种计算连续元素之和的好方法，计算连续的元素之和如果出现超时，一般要想到前缀和

    2. 在不确定a,b 两个元素相对大小，进而不好实施具体操作是，可以使用swap交换，即保证了a一定小于等于b

       1. ``` c++
          if(a>=b)
              swap(a,b);
          ```

80. 1034

    1. A "Gang" is a cluster of more than 2 persons who are related to each other.
    2. 意思是Gang中人数必须大于2，且related to each other与其他人有关系，
    3. 注意：其意思并不是一个Gang任意2人都打过电话，所以只要没说任意2点都相联都可认为联系关系具有传递性
    4. 如果是求任意2人都打过电话的集合，该问题即是求该无向图中所有极大完全子图，是完全NP问题，现可用[Bron-Kerbosch算法](https://blog.csdn.net/fjsd155/article/details/105018185)

81. 1033

    1. 该题的贪心算法十分经典，是经典题，一开始想到了动态规划的想法，但是因为参数都是浮点数，无法规划。。

82. 1025

    1. 用同向双指针解决相同排名、相同字符等问题是否清晰简单。

       1. ``` c++
          for(a=0;a<n;a=b){
             for(b=a;b<n&&tmp[a].grades==tmp[b].grades;++b)
                  tmp[b].locRank=nowRank;            
              	nowRank+=b-a;            
          }
          ```
    
    2. vector合并
    
       1. ```c++
          //如vector、string的属性顺序数据结构，insert时一定要有起点位置（set就不需要）
          all.insert(all.end(),tmp.begin(),tmp.end());
          ```
    
83. 1022

    1. map<string,set>、map<string,vector>都是非常好的实现1对多的数据结构

    2. map可以和set一样查找某个值是否是其中一个键值

       1. ``` c++
          if(mp.find(str) != mp.end());
          ```

84. 1014

    1. 对使用数组对矩阵赋值（即给出一个顺序数组，对依次对每行每列进行赋值）的题目，最好不要使用行数与列数的表达式来代替数组的索引，设置一个index变量作为数组的索引，每次处理完，使index自增。（优点是能更好地处理数组大小与矩阵大小不一样时的问题）

    2. 对于多个队伍排队的时间问题可以设置一个队列的结构体
    
       1. ``` c++
          struct line{
              //poptime表示当前队首出队的时间，endtime表示队尾结束排队的时间
              //pocetime存储的是当前队伍中每个人在收银台处理的时间
              int poptime,endtime;
              queue<int>pocetime;
          };
          ```
    
    3. 处理类似的HH:MM的时间格式问题时，可以设置起始时间为0，然后其他所有时刻都用以==最小时间单位==为单位的==纯数字==表示，最后打印结果是，才将==纯数字==转为了HH:MM的格式
    
       1. ``` c++
          //如此题中，起始时间为8:00，最小时间单位为分钟
          hour=8+leavetime[tmp-1]/60;
          min=leavetime[tmp-1]%60;
          printf("%02d:%02d\n",hour,min);
          ```
    
85. 1013

    1. 问题：在图中加上n条变，使得整个图相连。就是求出整个图的连通分量（dfs易得）为X，将这X个连通分量合成1个连通图，只需要X-1条边即可。
    2. 并且如果需要假设某个点不存在（相应边也不再），不需要在G数组中将对应边去除，只需要将其在flag数组中设置为已访问即可

86. 1003

    1. 迪杰斯塔拉算法

       1. 思想：从A->B的一条最短路径，假如C是AB中的一个结点，那么A->C也是最短路径。

          1. 初始化时将原点u放入N'（已确定的最短路径的结点集合）中，然后把u作为最小代价路径中的前置节点，计算达到其他所有节点的代价值（不可达记为$\infty$）
          2. 然后将计算拥有最小代价值路径的终点x放入N'中，然后将x作为前置节点，路径前一部分是u到x的路径，然后计算达到其他所有节点（不包括N’）的代价，不可达记作$\infty$
          3. 循环2过程。

       2. ``` c++
          void djstl(vector<vector<int>>&G,int root){
              //dis[i]表示目前为止从root到i的最短路径长度；flag表示到该点的最短路径有没有找到
          	vector<int>dis(n,9999999),flag(n,0);
              //root表示前缀结点
              int mindis=9999999,minno=0;
              dis[root]=0;
              flag[root]=1;
              //遍历n次即可找完从root到所有结点的最短路径
              for(int j=0;j<n;++j){    
                  //更新最短路径
                  for(int i=0;i<n;++i){
                      if(G[root][i]==-1||flag[i]==1)
                          continue;
                      dis[i]=min(dis[i],dis[root]+G[root][i]);          
                  }
                  //寻找本次dis中最短路径
                  for(int i=0;i<n;++i){
                      if(flag[i]==0&&dis[i]<mindis){
                          mindis=dis[i];
                          minno=i;
                      }
                  }
                  //本次dis中最短路径的终点的最短路径已找到，该终点作为下一次遍历的前缀结点
                  root=minno;
                  flag[root]=1;       
              }
          }
          ```

87. 1131

    1. 解决在图中2点间最短路径的问题有3种解法
       1. 迪杰斯特拉：不知道如何存储中间结点值(使用pre数组存储，再使用dfs)，适合需要求出某个点到其他所有点的最短距离问题
       2. dfs：容易递归太深导致内存超限
       3. bfs：只能解决==无权图==最短路径问题（即图中每条边长度相等）
    
88. 1111

    1. dfs都是最后一个测试点超时。。。。。。。。
    2. 对于多个相似函数的使用（主题一样，细节有偏差），必须小心对待其中每一个函数、变量名字的区别，不然很可能出现这次，在dfs2函数中调用dfs函数的错误

89. 1087

    1. 使用迪杰斯特拉时，同时存储完整的不同的最短路径

       1. ``` c++
          //pre[i]保存的是从起点到第i个节点最短路径的前一个节点值（因为可能有多条最短路径，所以前一个节点也可能有多个）
          //使用pre[n]的方法：将pre[n]看成一棵树，终点节点是该树的根节点，从根节点开始使用dfs，寻找起始结点
          vector<vector<int>> pre(n);
          if(dis[u] + e[u][v] < dis[v]) {
              dis[v] = dis[u] + e[u][v];
              //清空pre[v]，并将u加入
              pre[v].clear();
              pre[v].push_back(u);
          } 
          else if(dis[v] == dis[u] + e[u][v]) {
              //添加u
              pre[v].push_back(u);
          }
          ```

90. 1072：

    1. 草，本来早就做出来了

    2. 不能将int类型数据在printf（）中隐式转化从而保留多少位小数。必须先显式转化为double再打印，不然会出现错误数据

       1. ``` c++
          int x=2;
          //这样是错误的
          printf("%.2f",x);
          //必须显式转化
          printf("%.2f",(double)x);
          ```

       2. 

    3. 浮点数的四舍五入千万别画蛇添足加0.5,即使自定义测试出错了，提交也不会错

    4. A gas station has to be built at such a location that ==the minimum distance between the station and any of the residential housing is as far away as possible==. However it must guarantee that all the houses are in its service range.

       Now given the map of the city and several candidate locations for the gas station, you are supposed to give the best recommendation. If there are more than one solution, output the one with the==smallest average distance== to all the houses. If such a solution is still not unique, output the one with the ==smallest index number.==

    5. 上面这句题意中隐藏了条件，十分阴险：第一条件是加油站到居民楼最短距离要最大，第二条件是加油站到所有居民楼的平均距离最短，第三条件是索引最小

    6. 由此可见，读题必须慎之又慎，题目的三部分：前言，输入说明，输出说明，都是十分重要，三者中任何一者都是无比重要，不可或缺。

    7. 对vector进行整体赋值之fill函数

       1. ``` c++
          #include <algorithm>
          //vt整体赋值为1
          fill(vt.begin(),vt.end(),1);
          ```

91. 1081

    1. 这题的flag数组出现了2个问题

       1. djstl中更新了最短路径结点时，未对该结点的flag赋值为1

       2. dfs中的flag2数组，我竟然在dfs函数上面使用下面这种方式初始化，还竟然以为在进行dfs()之前已经对n进行了赋值，全局变量是main函数运行之前就确定的，而运行之前n是未知的，所以绝对不能用这种方式初始化，所以记住：==全局变量中不能出现n==

          1. ``` c++
             vector<int>flag2(n+1,0);
             void dfs(){
             ;}
             ```

    2. djstl+dfs：要谨记，由djstl获得的pre二维数组，对pre进行dfs，dfs起点是原来的终点，dfs终点是原来的起点

    3. 这题的num_to和num_back比较复杂，后面结点的多余无法解决前面结点的缺少，仅仅从终点到起点的反向过程中是无法获得真实的num_to和num_back，而由pre数组的性质，dfs求出的结点的过程时逆向的，所以需要在first==last时，对tmpv进行反向模拟：即模拟真实情况时从起点到终点num_to和num_back的变化情况，然后才能进行结果的判断

92. 1153

    1. 原本第3个测试点超时，但将cout改为printf后就过了，所以，输出一定要用printf。

    2. 使用构造函数初始化结构体

       1. ``` c++
          ans.push_back({it.first, it.second});
          ```

    3. 对结构体排序的题目，如果按多种需求排序，如对特类元素，不需要什么简便方法，逐个搜索匹配。

93. 1141

    1. 所有变量最好都要初始化，不要认为默认为0，容易引起错误，尤其是结构体中的变量（因为字节对齐），可以在定义结构体模板时，在其中直接初始化

       1. ``` c++
          struct school{
              string name;
              int num=0,weight;
              double wt=0,wa=0,wb=0;
          };
          ```

    2. Score=ScoreB/1.5 + ScoreA + ScoreT*1.5，该题最后一个测试点是受double精度影响的，下面是最大程度保证精度的技巧

       1. 虽然==最终的打印的是整型==，但==中间过程量不能用int保存！！！！==，中间的任何一个score都用double存储
       2. 每次输入一个score并不直接就乘1.5或除1.5，而是==先分类累加存储==，最后计算最终结果时，==再整体乘1.5和除1.5==。这样做的依据是使得被除数足够大，整体除保留的精度更多

94. 1137

    1. 题目真TM阴险，注意这个if是在一个句子的末尾，而不是开头，所以if表示的情况对应的结果在前面！！！
    2. <img src="D:\Typora\note\PAT_note.assets\image-20210216143446535.png" alt="image-20210216143446535" style="zoom: 200%;" />
    3. 草，这题中的double转为int没有四舍五入，所以还是要加0.5！！（所以加不加0.5看情况而定，没有绝对的）
    4. 这题的$G$是final grade，$G_{final}$是final exam scores，所以要注意题目中的final指的是期末考试成绩还是最终成绩

95. 1075

    1. 结构体中的vector不能初始化！！

96. 1066

    1. AVL树是模板题，有固定的的答题套路

    2. 无论左旋、右旋、还是左右旋、右左旋，其本质都是输入一个root结点，通过一系列操作，返回另一个root结点（原root孩子结点）

       1. 左旋是返回原root结点的右孩子
       2. 右旋是返回原root结点的左孩子
       3. 左右旋是：先让root的左孩子左旋，再让root右旋

    3. 使用哪种旋法取决于树形

       1. LL：新插入结点在root左子树的左子树上
          1. 解决方法：对root右旋
          2. ![image-20210218090416351](D:\Typora\note\PAT_note.assets\image-20210218090416351.png)
       2. LR：新节点在root左子树的右子树上
          1. 解决方法：对root左孩子左旋，再对root右旋
          2. ![image-20210218090408043](D:\Typora\note\PAT_note.assets\image-20210218090408043.png)
       3. RR：新节点在ROOT右子树的右子树上
          1. 解决方法：对root左旋
          2. ![image-20210218090355566](D:\Typora\note\PAT_note.assets\image-20210218090355566.png)
       4. RL：新节点在root的右子树的左子树上
          1. 对root右孩子右旋，再对root左旋
          2. ![image-20210218090318986](D:\Typora\note\PAT_note.assets\image-20210218090318986.png)

    4. AVL树答题模板

       1. ``` c++
          #include <bits/stdc++.h>
          using namespace std;
          //结点的数据结构
          struct node{
              node* left=nullptr;
              node* right=nullptr;
              int val;
          };
          //查询结点高度
          int getH(node *root){
              if(root==nullptr)
                  return 1;
              return max(getH(root->left),getH(root->right))+1;
          }
          //左旋，对于RR型树
          node* lrotate(node* root){
              node*tmp=root->right;
              root->right=tmp->left;
              tmp->left=root;
              return tmp;
          }
          //右旋，对于LL型树
          node* rrotate(node* root){
              node* tmp=root->left;
              root->left=tmp->right;
              tmp->right=root;
              return tmp;
          }
          //右旋再左旋，对于RL型树
          node* rlrotate(node* root){
              root->right=rrotate(root->right);
              return lrotate(root);
          }
          //左旋再右旋，对于LR型树
          node* lrrotate(node* root){
              root->left=lrotate(root->left);
              return rrotate(root);
          }
          //结点插入函数（最主要的函数）
          node* insert(int val,node* root){
              if(root==nullptr){
                  node* tmp=new node();
                  tmp->val=val;
                  root=tmp;
              }
              else if(val<root->val){
                  root->left=insert(val,root->left);
                  //进入这段条件语句的一定是祖父结点，即root就是祖父结点，也就是深度最大的失衡结点
                  if(getH(root->left)-getH(root->right)==2){
                      //树形为LL,
                      if(val<root->left->val)
                          root=rrotate(root);         
                      //树形为LR
                      else
                          root=lrrotate(root);          
                  }
              }
              else{
                  root->right=insert(val,root->right);
                  if(getH(root->right)-getH(root->left)==2){
                      //树形为RR
                      if(val>root->right->val)
                          root=lrotate(root);
                      //树形为RL
                      else
                          root=rlrotate(root);
                  }
              }
              return root;
          }
          
          ```

       2. 

97. 1123

    1. AVL模板题
    2. 完全二叉树等价条件是：如果某个结点不同时拥有2个孩子结点，那么序号在它后面的全部结点都是叶子结点。

98. 1088

    1. ``` c++
       //最大公因数
       long long gcd(long long a,long long b){
           return b?gcd(b, a % b):a;
       }
       ```

    2. 运行时错误：就是数组越界（数组开小了、索引越界）

99. 1060

    1. 对于精度很高（即小数位很多）的浮点数，不能用double存储，只能用string存储，并且该string不能使用stof转为浮点数判断该数是否是0。（对于上面这种用string存储的浮点数，因为不是用double存储，所以要十分小心==前缀0==）

    2. erase是直接对原字符串进行操作，所以可以不用返回

    3. ``` c++
       /*#include <bits/stdc++.h>
       using namespace std;
       int resn,n;
       double func(double s){
           if(s==0){
               resn=0;
               return s;
           }
           double tmp=s;
           int num=0;
           if(tmp>=1){
               for(num=0;tmp>=1;++num)
                   tmp/=10;
               resn=num;
               return tmp;
           }
           else{
               for(num=0;tmp<1;++num)
                   tmp*=10;
               resn=-1*(num-1);
               return tmp/10;
           }
       }
       int main(){
           int na,nb;
           //double还是不太行，精度还是不够，能够保持的小数位数有限
           double a,b;
           string sa,resa="0.",sb,resb="0.";
           scanf("%d %lf %lf",&n,&a,&b);
           a=func(a);
           na=resn;
           sa=to_string(a);
           for(int i=0,j=2;i<n;++i,++j){
               if(j<sa.size())
                   resa+=sa[j];
               else
                   resa+="0";
           }
           b=func(b);
           nb=resn;
           sb=to_string(b);
           for(int i=0,j=2;i<n;++i,++j){
               if(j<sb.size())
                   resb+=sb[j];
               else
                   resb+="0";
           }
           if(resa==resb&&na==nb){
               printf("YES %s*10^%d\n",resa.c_str(),na);
           }
           else{
               printf("NO %s*10^%d %s*10^%d\n",resa.c_str(),na,resb.c_str(),nb);
           }
           return 0;
       }*/
       #include <bits/stdc++.h>
       using namespace std;
       int resn;
       string func(string s){   
           int n,size=s.size();
           for(n=0;n<size&&(s[n]=='0'||s[n]=='.');++n);
           if(n==size){
               resn=0;
               return "0";
           }
           //小数，整数都可能出现前缀0
           for(n=0;n<size&&s[n]=='0';++n);
           if(s[n]=='.'){
               s.erase(0,n-1);
           }
           else{
               s.erase(0,n);
           }
           //寻找小数点
           for(n=0;n<size&&s[n]!='.';++n);
           //整数也可能存储前缀0
           //无小数点，纯整数
           if(n==size){
               resn=s.size();
               s="0."+s;
           }
           //小数
           else{
               //小数点在索引1
               if(n==1){
                   if(s[0]=='0'){
                       int m;
                       for(m=2;m<s.size()&&s[m]=='0';++m);
                       resn=-1*(m-2);
                       s.erase(0,m);
                       s="0."+s;
                   }
                   else{
                       resn=1;
                       //测试点2：写成了s.erase(1,0);
                       s.erase(1,1);
                       s="0."+s;
                   }
               }
               else{
                   resn=n;
                   s.erase(n,1);
                   s="0."+s;
               }
           }
           return s;
       }
       int main(){
           int n,na,nb;
           string a,b,resa="0.",resb="0.";
           cin>>n>>a>>b;   
           a=func(a);
           na=resn;
           for(int i=0,j=2;i<n;++i,++j){
               if(j<a.size())
                   resa+=a[j];
               else
                   resa+="0";
           }
           
           b=func(b);
           nb=resn;
           for(int i=0,j=2;i<n;++i,++j){
               if(j<b.size())
                   resb+=b[j];
               else
                   resb+="0";
           }
           if(resa==resb&&na==nb){
               printf("YES %s*10^%d\n",resa.c_str(),na);
           }
           else{
               printf("NO %s*10^%d %s*10^%d\n",resa.c_str(),na,resb.c_str(),nb);
           }
       }
       ```

100. 1095

     1. 时间hh:mm:ss，一律转为以最小单位为单位的int类型数据

101. 1067

102. 1016

     1. 此题==最重要的思路==是：2个时刻之间极其复杂的计费方式（不同小时内的话费不同，并且还可能跨天），可以通过分别计算从00:00:00到2个时刻的费用，二者费用之差即所求话费！！！（原理是：较大时刻的费用包括了较小时刻的费用，所以二者之差就是较大时刻的费用减去了前面公共的费用部分，结果就是所求的2时刻之间的费用！）

103. 1026






## 二刷笔记

### 数学问题

1. 1015

   1. ``` c++
      //函数作用：将十进制数a转为b进制，再反转，再求出其十进制
      //进制转换的本质
      int reverseInN(int a,int b){
          int res=0;
          while(a){
              res*=b;
              //a%b逐渐获得b进制的从低到高各个位上的数字
              res+=a%b;
              a/=b;
          }
          return res;
      }
      ```

2. 1002

   1. 浮点数也直接用==判断是否为0，别tm用什么<10e-16

   2. 反向遍历，使用rbegin()，和rend()（前面加一个r即可）

      1. ``` c++
             for(auto it=mp.rbegin();it!=mp.rend();++it){
                 if(it->second==0)
                     continue;
                 printf(" %d %.1f",it->first,it->second);
             }
         ```

3. 1044

   1. 思考窗口移动中同向和异向的区别（一般为有序数组）
      1. 2个指针指向的元素==和==为定值：使用异向
      2. 2个指针指向的元素==差==为定值：使用同向


### 动态规划

1. 1007：很有意思，不能用2重循环

### 双指针

1. 1085
2. 1089

### 图

1. 遍历
   1. DFS
      1. 1021
      2. 1034
   2. BFS
      1. 要时刻警惕初始化是否完全
         1. ==flag[root]是否赋值为1==
         2. 计数变量num是否赋值为1
         3. 还有其他各种各样的初值！
2. 最短路径
   1. ==1131==：太难了
   2. 1111

### 树

1. 1151

2. 遍历问题

   1. 后+中->层次：1020，即转为（先、中）序遍历，并附带深度即可
      1. ==一种很重要的方法==：将==二叉树==存储在数组中：根节点索引为x，则左孩子索引为2x+1，右孩子为2x+2。将数组顺序输出就是该树的层次序列！(==注意==：如果该树不是完全二叉树，则可能出现很多空闲元素，这种情况时，可以使用map代替数组)
   2. 先+中->后：1138，拥有先（后）和中序序列，就可以通过dfs进行模拟遍历过程
   3. 先+后->中：1119，先序和后序无法得出唯一中序的原因：==当root只有1棵子树数，无法知道该子树是左子树还是右子树==
      1. 当先序中的LC与后序中的RC相等时，即只有一颗子树，此时无法唯一判别该子树时左子树还是右子树，可以将除了R之外的所有点视作左子树或右子树
      2. L：表示左子树结点，R：表示右子树结点（==此图中很重要的细节，通过先序获得左孩子值（在root右侧1位），然后在后序序列中找到左孩子就可以获得左子树的个数==）![image-20210130193640252](D:\Typora\note\PAT_note.assets\image-20210130193640252.png)
   4. 二叉树的拓扑结构->该二叉树的反转树的层次、中序遍历序列：1102
      1. 反转树的定义：交换每个节点的左子树和右子树
      2. 对于层次遍历：即从左往右输出改为从右往左输出（还有一种方式是模拟遍历时先递归右子树再递归左子树）
      3. 对于先、中、后遍历：交换左右子树递归的顺序即可，即先对右子树递归，再对左子树递归

3. ==由遍历序列判断是否能获得该树全部拓扑信息的等价条件==：是能否==唯一==区分出root、左子树和右子树。如果能唯一区分，就能获得该树的所有遍历序列。

4. 给出一个树的方式：

   1. 给出该树的遍历序列（前、中、后、层次）

   2. 按顺序给出每个节点的孩子结点的索引

      1. 如![image-20210311013232226](D:\Typora\note\PAT_note.assets\image-20210311013232226.png)

      2. 此时需要创建node结构体存储结点，并使用vector<node>存储整个树

         1. ``` c++
            struct{
                int val,left,right;
            };
            ```

   3. 给出该树（一般是二叉搜索树等特殊树）结点的==插入顺序==

      1. 此时必须使用结构体真实模拟创建该树，用指针表示结点之间的关系，并写出插入函数

      2. ``` c++
         struct node{
             int val;
             node* left=nullptr;
             node* right=nullptr;
         };
         //插入结点函数
         node* insert(node* root,int val){
             if(root==nullptr){
                 root=new node();
                 root->val=val;
             }
             else if(val<=root->val)
                 //注意此处是将返回值给root->left
                 root->left=insert(root->left,val);
             else
                 root->right=insert(root->right,val);
             return root;
         }
         
         int main(){
             int n,tmp1;
             cin>>n;
             node* root=nullptr;
             for(int i=0;i<n;++i){
                 cin>>tmp1;
                 root=insert(root,tmp1);
             }
         }
         ```

      3. 

      

5. 完全二叉树：

   1. 树的拓扑结构->判断是否是完全二叉树：1110
      1. 遍历该树，将该二叉树的存储到vector中（按左孩子是root*2+1索引的方式存储），然后根据完全二叉树的性质：==在vector中一定顺序存储0-n-1中==，如果有结点的索引大于等于n，则不是完全二叉树

6. 二叉搜索树：

   1. 前序序列->判断是否是二叉搜索树并得出后序序列：1043
      1. 判断二叉搜索树：对于所有树的序列，如果排列顺序是==root–>所有小于root的结点（左子树）–>所有大于等于root的结点（右子树）==，通过递归所有结点可判断该结点作为root是否满足二叉搜索的性质，如果所有结点都满足，即使二叉搜索树，有任何一个节点不满足即不是
      2. 通过二叉搜索树的前序序列获得后序序列：由遍历序列判断是否能获得该树全部信息的等价条件是能否区分出root、左子树和右子树。而因为此树是二叉搜索树，满足==root–>所有小于root的结点（左子树）–>所有大于等于root的结点（右子树）==的性质，所以很容易通过模拟遍历的方式获得后序序列
   2. 树的拓扑结构和所有结点值->由此组成的二叉搜索数的层次序列：1099
      1. 因为是拓扑结构，所以使用结构体node和vector存储整颗数
      2. 因为是二叉搜索树，所以值的递增排序即使中序序列
      3. 通过模拟中序遍历过程，逐步输出中序序列即可获得当前节点的正确值
   3. 给出结点的==插入顺序==->获得该二叉树的层次序列
      1. 

7. 完全二叉搜索树

   1. 给出一组序列->获得由该序列组成的完全二叉搜索树的层次遍历序列:==1064==,即创建CBT

      1. 因为是二叉搜索树，所以其==结点递增序列==就是==中序遍历序列==。

      2. 因为是完全二叉树，所有将整颗数存储进vector中，左孩子索引是root*2+1。

      3. 然后可以模拟中序遍历过程，将逐渐将中序序列中的值加入到vector对应的索引中

         1. 为什么要模拟中序遍历过程？

            1. 答：因为我们只有中序遍历序列，而我们想做的事是将每个元素放到vector中对应索引中，由完全二叉树性质，==我们知道当前节点的索引是什么，但是不知道值是多少==，最好的方式就是按照中序序列依次获得元素的值，要想如此，只能模拟中序遍历过程，然后逐步输出元素值

         2. ``` c++
            void inT(int index){
                if(index>=n)
                    return;
                inT(index*2+1);
                pre[index]=in[now++];
                inT(index*2+2);
            }
            ```

      4. 最后，对于存储在vector中的完全二叉树，将vector按顺序输出即是层次遍历序列

8. 平衡二叉树（avl）

   1. 模板题：

      1. ``` c++
         #include <bits/stdc++.h>
         using namespace std;
         //结点的数据结构
         struct node{
             node* left=nullptr;
             node* right=nullptr;
             int val;
         };
         //查询结点高度
         int getH(node *root){
             if(root==nullptr)
                 return 1;
             return max(getH(root->left),getH(root->right))+1;
         }
         //左旋，对于RR型树
         node* lrotate(node* root){
             node*tmp=root->right;
             root->right=tmp->left;
             tmp->left=root;
             return tmp;
         }
         //右旋，对于LL型树
         node* rrotate(node* root){
             node* tmp=root->left;
             root->left=tmp->right;
             tmp->right=root;
             return tmp;
         }
         //右旋再左旋，对于RL型树
         node* rlrotate(node* root){
             root->right=rrotate(root->right);
             return lrotate(root);
         }
         //左旋再右旋，对于LR型树
         node* lrrotate(node* root){
             root->left=lrotate(root->left);
             return rrotate(root);
         }
         //结点插入函数（最主要的函数）
         node* insert(int val,node* root){
             if(root==nullptr){
                 node* tmp=new node();
                 tmp->val=val;
                 root=tmp;
             }
             else if(val<root->val){
                 root->left=insert(val,root->left);
                 //进入这段条件语句的一定是祖父结点，即root就是祖父结点，也就是深度最大的失衡结点
                 if(getH(root->left)-getH(root->right)==2){
                     //树形为LL,
                     if(val<root->left->val)
                         root=rrotate(root);         
                     //树形为LR
                     else
                         root=lrrotate(root);          
                 }
             }
             else{
                 root->right=insert(val,root->right);
                 if(getH(root->right)-getH(root->left)==2){
                     //树形为RR
                     if(val>root->right->val)
                         root=lrotate(root);
                     //树形为RL
                     else
                         root=rlrotate(root);
                 }
             }
             return root;
         }
         ```

9. 堆

   1. 完全二叉树的层次序列->是否是堆并输出后序序列
      1. ==完全二叉树的重要性质==：按层序序列存储于vector中，左孩子索引是2*root+1,所以完全二叉树只需要层次序列就能获得整颗树的完整信息，模拟遍历过程即可获得后序序列
      2. 堆的性质：全部结点都大于等于或者小于等于孩子结点

### 并查集

1. 模板题

   1. ``` c++
      vector<int>father;
      int getf(int x){
          return father[x]=(x==father[x]?x:getf(father[x]));
      }
      void insert(int x,int y){
          father[getf(x)]=getf(y);
      }
      ```

   2. 



































