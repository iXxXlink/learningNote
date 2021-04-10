## C/C++的一点随笔

1. 如何调试：

   1. 进入调试：F5
   2. 设置断点：能直接执行断点行之前的所有行，==不执行断点行==
   3. 继续（continue）：F5，执行断点行和之后连续的所有非断点行，最后再断点行处暂停
   4. 单步跳过（step over）：F10，不管断点，只执行一个语句（不进入函数内部，直接运行完整个函数）
   5. 单步调试（step in）：F11，不管断点，只执行一个语句（运行函数，会进入函数内部，然后逐步调试）
   6. 单步跳出（step out）：shift+F11，在子函数中直接运行完剩余部分，然后返回上一级函数
   7. 可以在左侧监控处添加变量或表达式实时查看变化，或者在下方调试控制台输入所需了解的表达式

2. 输入多次2个整型

   ``` c
   while(scanf("%d%d",&t1,&t2)!=EOF){
   }
   ```

3. 字符串整体赋值：strcpy（des,src）

4. 字符串部分赋值：strncpy（dest，src,n）：将src的前n个字符拷贝到dest，因为不会自动在dest末尾加0，所以需要手动添加

5. 字符串拼接：strcat

6. gets可以接受空格，遇到回车结束输入，回车不会留在缓冲区;而scanf遇到空格、回车、tab都会认为输入接受，所以不能接受空格，回车、空格会留在缓存区（可在输入后一行加一个getchar（）取出缓存区中字符）。但都会在字符串末尾加一个\0

7. string.h

   1. strcmp（str1,str2）：如果str1小于str2，返回值小于0；str1等于str2,返回值等于0

   2. strcat(str1,str2)：将str2拼接到str1后面。会删去str1、str2末尾的'\0'，然后将str2拼接到str1后面，再在最后加上‘\0’。注意：如果str1、str2末尾需要有‘\0’，且str1数组大小需要足以包括所有元素和‘\0’

   3. strlen（array）：读取数组的元素个数，直至读到‘\0’为止（结尾一定要有‘\0’，不然会一直读下去），但返回的元素个数不包括‘\0’

   4. strcpy（str1,str2）：将str2地址开始直到‘\0’的字符串（注意：包括‘\0’）复制到str1开始的地址空间

   5. 打印printf("%s",str)；打印字符串%s，也以‘\0’作为结束符，否则就会打印越界，直至遇到结束符'\0'

   6. 动态分配多维数组

         1. ``` c++
            int **p,m,n;//m为行数,n为列数	
            p = (int **)malloc(sizeof(int *) *m);
            for (i = 0; i < m; i++)
                p[i] = (int *)malloc(sizeof(int) * n);
            ```


1. ==二分查找变种总结==：在顺序序列中查找key，序列中可能有0个或多个key

   1. （最重要的图！）![image-20210123090900329](D:\Typora\note\算法笔记c++.assets\image-20210123090900329.png)

   2. 模板特点：

      1. 不变处
         1. 循环条件是left<=right（必须有等号）
         2. 每次分割区间都是，mid-1或mid+1
      2. 改变处
         1. ==循环中A【mid】与key的比较有无等号==
         2. ==最终返回的是left还是right（二者一定不等）==

   3. 模板

      1. ``` c++
         //二分查找
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         	//下列6种情况只会改变该模板中的2处：1、等于的情况归在哪。2、返回left还是right
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] > key) 
                     right = mid - 1;
                 } else if (arr[mid] < key) {
                     left = mid + 1;
                 } else {
                     return mid;
                 }
             }
             return -1;
         }
         ```

      2. 

   4. [博客原文](https://www.cnblogs.com/gongpixin/p/6761389.html)

      

   5. 查找第一个大于等于key的元素

      1. ``` c++
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] >= key) {
                     right = mid - 1;
                 } else if (arr[mid] < key) {
                     left = mid + 1;
                 } 
             }
             return left;
         }
         ```

         

   6. 查找最后一个小于key的值

      1. ``` c++
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] >= key) {
                     right = mid - 1;
                 } else if (arr[mid] < key) {
                     left = mid + 1;
                 } 
             }
             return right;
         }
         ```

   7. 查找第一个key

      1. ``` c++
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] >= key) {
                     right = mid - 1;
                 } else if (arr[mid] < key) {
                     left = mid + 1;
                 } 
             }
             if(left<len&&arr[left]==key)
             	return left;
             else
                 return -1;
         }
         ```

   8. 查找最后一个小于等于key的元素

      1. ``` c++
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] > key) {
                     right = mid - 1;
                 } else if (arr[mid] <= key) {
                     left = mid + 1;
                 } 
             }
             return right;
         }
         ```

   9. 查找第一个大于key的元素

      1. ``` c++
         int binarySearch(int arr[], int len, int key)
         {
             int left = 0;
             int right = len - 1;
             int mid;
         
             while (left <= right) {
                 mid = (left + right) / 2;
                 if (arr[mid] > key) {
                     right = mid - 1;
                 } else if (arr[mid] <= key) {
                     left = mid + 1;
                 } 
             }
             return left;
         }
         ```

   10. 查找最后一个key

      11. ``` c++
          int binarySearch(int arr[], int len, int key)
          {
              int left = 0;
              int right = len - 1;
              int mid;
          
              while (left <= right) {
                  mid = (left + right) / 2;
                  if (arr[mid] > key) {
                      right = mid - 1;
                  } else if (arr[mid] <= key) {
                      left = mid + 1;
                  } 
              }
              if(right>=0&&arr[right]==key)
              	return right;
              else
                  return -1;
          }
          ```

   12. ==做题流程==

       1. 判断返回对象：根据上图判断返回的是left还是right
       2. 判断等于情况属于谁：判断相等时的情况与小于时情况相同还是和大于时情况相同
       3. 判断目标是否存在：明确找与key相等的元素时，最后一定还要判断是否为key，并且要避免访问不存在空间

   






## 基础算法

### 排序

1. 选择排序：每次从待排序的序列【i,n】中搜索最小元素，另其与待排序列的第一个元素即A[i]交换（循环n次）

2. 插入排序：有序序列为[1,i-1]，无序序列为[i,n],将i移动到[1,i-1]中的恰当位置，使得[1,i]依然保持有序（从A[2]开始循环，循环n-1次）

3. 归并排序：将待排序列【1，n】看作n个长度为1的有序序列，然后相邻2个序列合并为新的1个有序序列，不断循环合并，直到只剩下1个有序序列

   1. ``` c++
      //将2个递增数组合并
      void merge(int *A,int L1,int R1,int L2,int R2){
      	int i=L1,j = L2;
          //i 指向A[L1]，j指向A[L2]
          int temp [maxn], index = 0; //temp 临时存放合并后的数组， index为其下标
          while(i<=R1&&j<=R2) {
          if(A[i] <= A[j]) { // 如果A[i]<=A[j]
          temp[index++] = A[i++]; //将 A[i]加入序列temp
          } else {
          //如果 A[i]>A[j]
          temp[index++]二A[j++]; / /将A[j]加入序列temp
          ]
          while(i<= Rl) temp[index++] = A[i++]; //将[L1, R1] 的剩余元素加入序列temp
          while(j <= R2) temp [index++] = A[j++]; //将 [L2，R2] 的剩余元素加入序列temp
          for(i= 0; i < index; i++) {
          A[L1 + i]- temp[i];放//将合并后的序列赋值回数组A
      
      }
      
      //对1个无序数组使用归并排序
      void mergesort(int* A,int L,int R){
          //递归边界
          if(L==R)
              return;
      	int mid=(R-L)/2;
          mergesort(A,L,mid);
          mergesort(A,mid+1,R);
          merge(A,L,mid,mid+1,R); 
      }
      ```

4. 快速排序：

   1. 整体思路就是：使用递归实现快排，每次以当前序列（【left，right】）的第一个元素为枢纽，将其排到其正确的位置pos，然后再对【left，pos-1】和【pos+1，right】递归使用快排函数
   2. 函数1：对于待排序列【1,M】，将A【1】调整至A【1】左边的元素都小于等于A【1】,右侧的元素都大于A【1】.
      1. 用tmp存储A【1】,left指针等于1，right指针等于M
      2. ==从right开始==，如果A【right】大于tmp，right–；如果A【right】小于等于tmp，则A【left】=A【right】，然后转到3
      3. 如果A【left】小于等于tmp，left++；否则，A【right】=A【left】，然后跳转到2
      4. 如果left\==right，则A【left】=tmp，==并返回left==
      5. ![image-20210226173450947](D:\Typora\note\算法笔记c++.assets\image-20210226173450947.png)
   3. ==函数2==：将待排序列【1，N】排序
      1. 对当前待排序列使用函数1，获得已经排序元素索引pos
      2. 然后对【1，pos-1】和【pos+1，N】再使用函数2
      3. ![image-20210226173500077](D:\Typora\note\算法笔记c++.assets\image-20210226173500077.png)

### 散列

1. 散列：将所有元素（结构体、字符串）转为一定范围内的整数（一个元素只能对应一个整数）
2. 直接定址法（最常见的散列应用）：对于==不过大==（10^5以下）的==int型==数据，可将输入的数作为vector的下标，而这些数的特征（个数等）存储在数组对应的元素中。
3. 除留余数法：![image-20200923235735598](D:\Typora\note\算法笔记c++.assets\image-20200923235735598.png)（作用是将很大的数转为小于mod的整数，一般==mod为且与表长相等==，且为==素数==）
4. 冲突解决方法：
   1. 线性探测法：如果有一个数的的哈希值已被占用，则其位置顺延下一个。（逐步加1）
   2. 平方探测法：其位置按1，-1,4，-4……+k\^2,-k\^2的方式顺延。**(k<Tsize)**
      1. 可以证明：如果k在**[0,TSIZE)**范围内依然没找到位置，那么当K>=Tize时，也找不到位置。
      2. 插入和查找时循环的范围是==k<Tsize==
   3. 链地址法：把哈希值相同的key值连接成一条单链表
5. 字符串hash：即使用一种哈希函数，使某一字符串能用唯一一个整数代表
   1. 思路：假设只有26个字母（更多字符类似），每个字母都用26进制对应的数字代替，所组成的长度与字符串长度相同的26进制数再转为10进制数，该10进制数就能唯一标识该字符串。（虽然该10进制数可能很大，但字符串问题转换为了大整数映射为小整数问题！）
   2. 原理：![image-20200924001018234](D:\Typora\note\算法笔记c++.assets\image-20200924001018234.png)

### 递归

1. 分治：将原问题划分成若干个结构与原问题相似的子问题，然后使用同样的划分方法，将子问题继续分解，直至问题被分解到足够小，能直接解决，最后将所有足够小的问题求解，并合并所有解即可得到原问题的解。
   1. 分解：将原问题分解为若干结构相似的子问题
   2. 解决：递归分解求解所有子问题
   3. 合并：将所有子问题的解合并为原问题的解
2. 递归的2个重要概念

   1. 递归边界：即最小的可以直接解决的子问题（递归边界在最底层返回答案）
   2. 递归式：则将原问题分解为子问题的方法（递归式向下一层递归）
3. 回溯法：在递归的过程中，在未递归到边界前，就因某些条件被筛选，进而不需要继续向下递归，而是直接向上返回。（即在递归的中途，就已经判断这种情况不符，不需要继续向下递归了）

### 贪心

1. 贪心法：在当前状态下的==局部==最优（或较优）的策略，进而使得==全局==的结果达到最优（或较优）。
2. 并不是所有问题，都能通过不断的局部最优来获得全局最优结果，需要对此进行证明。
3. 贪心的证明：证明思路一般是使用反证法和数学归纳法，即假设策略不能达到最优解，然后在推导得到矛盾，依次证明策略是最优的，最后用数学归纳法保证全局最优。（一般来说，证明比算法本身更困难，所以一般情况下，可忽视证明)
4. 区间不相交问题：给出N个开区间，从中选出最多m个区间，使得这些区间两两无交集

   2. 将所有区间按照右端点值进行从小到大排序。==最优先==选择右端点最小的区间。（因为其右端点在最左边，给其他区间剩余的空间（该剩余空间指的是其右端点以右的空间）最多）
5. 区间选点问题：给N个闭区间，求最少需要确定多少个点，才使得每一个闭区间都至少有一个点

   2. 将区间以右端点大小，从小到大排序，最优先向最小区间的右端点处标点。然后不再考虑所有包含该点的区间。

### 二分法

快速幂：![image-20200926161346571](D:\Typora\note\算法笔记c++.assets\image-20200926161346571.png)

1. (递归法)当b为奇数时，原式可以转为a的（b-1）次幂%m

2. 当b为偶数是，原式可以转为a的（b/2）次幂的平方%m

3. 使用递归的方式计算，递归边界为当b为0时

4. （迭代法）b可以转化为二进制形式，所以原式可以转化为a的$2^n$次幂相乘

5. 所以先判断b的二进制最后一位是否为1，如果是1，则ans（初值为1）等于ans乘以p

6. p等于p*p

7. q右移一位，直至q小于0

8. 判断一个整数b是否为奇数

   1. ``` c
      if(b&1){
      ;}
      ```

   2. 该判断式利用了b的二进制最后一位与1相与的结果判断，最后一位为1是奇数，为0是偶数。

   3. 此方法速度大于b%2==1

### 双指针

1. two pointers：在单调序列中，找到2个值的总和固定，所以这2个值相互制约，所以可以用two pointers法，使用1个指针位于队首，另1个指针位于队尾

   1. 归并排序

      ``` c
      //将2个递增数组合并
      void merge(int *A,int L1,int R1,int L2,int R2){
      	int i=L1,j = L2;
          //i 指向A[L1]，j指向A[L2]
          int temp [maxn], index = 0; //temp 临时存放合并后的数组， index为其下标
          while(i<=R1&&j<=R2) {
          if(A[i] <= A[j]) { // 如果A[i]<=A[j]
          temp[index++] = A[i++]; //将 A[i]加入序列temp
          } else {
          //如果 A[i]>A[j]
          temp[index++]二A[j++]; / /将A[j]加入序列temp
          ]
          while(i<= Rl) temp[index++] = A[i++]; //将[L1, R1] 的剩余元素加入序列temp
          while(j <= R2) temp [index++] = A[j++]; //将 [L2，R2] 的剩余元素加入序列temp
          for(i= 0; i < index; i++) {
          A[L1 + i]- temp[i];放//将合并后的序列赋值回数组A
      
      }
      
      //对1个无序数组使用归并排序
      void mergesort(int* A,int L,int R){
          //递归边界
          if(L==R)
              return;
      	int mid=(R-L)/2;
          mergesort(A,L,mid);
          mergesort(A,mid+1,R);
          merge(A,L,mid,mid+1,R); 
      }
      ```

      

   2. 快速排序

2. 广义上的two pointers：利用问题本身和序列的特性，使用两个下标i、j对序列进行扫描（==同向或异向==），以较低的复杂度解决问题。

## 数学问题

### 最大公因数

1. 求解最大公约数

   1. 原理：欧几里得算法（辗转相除法）：求a和b的最大公因数

      1. 假设a和b的==任意==1个公因子为d，由a=kb+r，可得r=a-kb，因为d整除a，d整除kb，所以d整除（a-kb），即d整除r。又因为d整除b（d是b的因子），所有d是r和b的一个公因子。由于d是a、b的任意1个公因子，所以有结论：==a和b的公因子集合==属于==r和b的公因子集合==
      2. 设r和b的任意1个公因子为$d_2$，由a=kb+r，同理可知，$d_2$整除a，所以$d_2$是a和b的一个公因子，因为$d_2$具有任意性，可以有结论：==r和b的公因子集合==属于==a和b的公因子集合==
      3. 根据1和2的结论可知，a和b的公因子集合==等于==b和r的公因子集合，所以自然而然可知a和b的最大公因数等于b和r的最大公因数

   2. ``` c
      int gcd(int a,int b){
          //0与任何自然数n的最大公因数都是n
      	if(b==0) 
              return a;
          else
              return gcd(b,a%b);
      }
      ```

2. 最小公倍数lcm（a,b）=ab/gcd(a,b)

   1. 因为ab可能溢出，所以更好的写法是(a/gcd(a,b))*b

### 素数

1. 素数的判断：

   1. ``` c
      bool isPrime(int n){
      	if(n<=1)
              return false;
          for(int i=2;i<=(int)sqrt(1.0*n);i++){
      		if(n%i==0)
                  return false;
          }
          return true;
      }
      ```

2. 素数表实现之筛法：已知2为素数，筛去所有2的倍数，因为3经过3之前所有素数倍数的筛选，依然存在，所以3为素数，然后接着筛选掉3的倍数....

   1. ``` c
      const int maxn=101;//素数筛选最大范围
      int prime[maxn],pNum=0;//存储所有素数，pNum为素数个数
      bool p[maxn]={0}；//元素为false，其索引为素数；元素为true，其索引为合数
      void Find_Prime(){
      	for(int i=2;i<maxn;i++){
      		if(p[i]==false){
                  prime[pNum++]=i;
                  for(int j=i+1;j<maxn;j++i){
      				p[j]=true;
                  }
              }
      	}
      }
      ```

3. 质因数分解：

   1. 对于一个整数N，在循环2-sqrt(N)的素数表素数表，找到1个因数，然后循环除以这个质因子，直至无法整除，之后再寻找其他质因子。
   2. N的质因数有2种情况：
      1. N的所有质因数都小于等于sqrt（N）
      2. N只有1个质因数即N本身
         1. 判断的方式：循环2到sqrt（N），最终的结果如果大于1，则N是素数（等价于判断素数）

4. ==因子的个数===（n1+1）\*（n2+1)\*(n3+1).......。其中n1、n2....为质因子的个数，因为因子中某个质因子可以出现0、1、2....n次

### 扩展的欧几里得算法

1. 反解参数，求解一组整数解x,y使得ax+by=gcd（a,b）。通过求解gcd的反向过程求解xy

   1. x、y的递归公式

      1. ![image-20210226223130506](D:\Typora\note\算法笔记c++.assets\image-20210226223130506.png)
      2. 注意：此处的a，b并不是指最开始的a,b，而是指每次递归函数中的==形式变量==a、b。

   2. ``` c++
      int x,y;
      //与求解gcd的函数区别，只在于顺便加上了对x、y的递推过程
      int exGcd(int a,int b){
          if(b==0){
              x=1;y=0;
              return a;
          }
          int gcd=exGcd(b,a%b);
          int tmp=x;
          x=y;y=tmp-a/b*y;
          return gcd;
      }
      ```

      

2. ax+by=c的求解

3. 同余式ax=c（mod m）的求解

4. 逆元的求解及（b/a）%m的计算

   1. 等价于求解同余式 ax=1（mod m），注意：gcd（a,m）必须为1，否则无逆元

   2. ``` c++
      int x,y;
      int getniyuan(int a,int m){
      	exGcd(a,m);//求解ax+my=1的解（x,y）
          return (x%m+m)%m;//这样处理是因为求得的x可能为负数，但逆元是最小正数。
      }
      int exGcd(int a,int b){
          if(b==0){
              x=1;y=0;
              return a;
          }
          int gcd=exGcd(b,a%b);
          int tmp=x;
          x=y;y=tmp-a/b*y;
          return gcd;
      }
      ```


### 组合数

1. n!中==质因子==的个数

   1. ![image-20200929001740959](D:\Typora\note\算法笔记c++.assets\image-20200929001740959.png)![image-20200929001749273](D:\Typora\note\算法笔记c++.assets\image-20200929001749273.png)

2. 计算组合数$C^m_n$:

   1. ==法一==：使用递推公式进行递归，递归边界为m=0时，返回1。==优先使用法一==

      ![image-20200929003330789](D:\Typora\note\算法笔记c++.assets\image-20200929003330789.png)

   2. 因为是深度优先，所有有许多重复计算，可以在返回的同时，记录此组合数存到二维数组中，需要计算组合数时，先查询数组中是否有，如果有直接返回，不需要继续递归

      1. ``` c++
         //最大计算到n为67，m为32
         //使用组合数表避免重复计算
         long long res[67][67]={0};
         long long C(long long n,long long m){
         if(m==0||m==n)return 1;
             if(res[n][m]!=0)
                 return res[n][m];
             //计算组合数的同时更新组合表
             return res[n][m]=C(n-1,m)+C(n-1,m-1);
         }
         ```

      2. 

   3. 法二：直接化简计算。虽然时间复杂度为n，但依然有可能溢出$C_n^m$,

      1. 不能证明（n-m+i）整除i，但是可以证明在==前一次的基础==上乘以(n-m+i)可以整除i，因为这样可以转化为一个组合数，而组合数又显然是个整数，所以可以整除i，然后根据==数学归纳法==可证的，每一次循环都能整除i

      2. ![image-20210224140920095](D:\Typora\note\算法笔记c++.assets\image-20210224140920095.png)

      3. ``` c++
         long long C(long long n, long long m){
             long long ans=1;
             for(long long i=1;i<=m;++i){
                 //并不是（n-m+1）能整除i，而是（ans*（n-m+1）能整除i！！）
                 ans=ans*(n-m+i)/i;
             }
         }
         ```

      4. 

3. 计算$C^{m}_{n}$%p

   1. 再上面法一的基础上modp，==主要使用该方法==

      1. ``` c++
         long long res[67][67]={0};
         long long C(long long n,long long m){
             if(m==0||m==n)return 1;
             if(res[n][m]!=0)
                 return res[n][m];
             //只需在此处加上%p即可
             return res[n][m]=(C(n-1,m)+C(n-1,m-1))%p;
         }
         ```

   2. 法4：lucas定理，适用范围最广，适用于n,m都很大（10的10次方以上），但p一定是素数且小于$10^5$

      1. ``` c++
         int lucas(int n,int m){
             if(m==0)return 1;
             return C(n%p,m%p)*lucas(n/p,m/p)%p;
         }
         ```






## C++标准模板库（STL  standard template library）

### vector

1. 常用函数

   7. vi.insert(vi.begin()+2,-1):将-1插入vi[2]的位置，后面的元素向后移动1个位置

   8. 删除：vi.erase(vi.begin()+3):删除vi[3]处的元素，后面的元素向前移动1个位置

   3. 删除vi.erase(vi.begin()+1,vi.begin()+4):删除所有1到3的元素。左闭右开

   4. vecotor初始化使用{}

      1. ``` c++
         vector<int> tmp{begin,end};
         vector<int>abc{1,2,3};
         ```


### set

4. 访问方式

   1. 只能通过迭代器访问

      ``` c++
      for(set<int>::iterator it=st.begin();it!=st.end();it++){
          //结果为2 3 5，说明集合会自动排为由小到大序列，且不会保存重复元素
      	printf("%d",*it);
      }
      ```
   
2. 常用函数：

   2. ==ad=st.find(value):返回集合中对应值的value的迭代器，再使用*可重获其值。如果value不在st中，则返回st.end()==

   3. st.erase(it):it为某个元素的迭代器，可结合find()，删去某个值

   4. st.erase(value):value为集合中某个元素的值，速度慢

   5. st.erase(first,last):first、last为迭代器，可删除一个左闭右开的区间

      1. ``` c++
         st.erase(st.find(300),st.end());//删除300之后所有元素
         ```


### string

1. 常用函数

   1. to_string()：c++内置函数，可以将int转为string类型

   3. <、>、=:可直接使用比较符号比较2个字符串的字典序

   5. str.insert(n,str2):插入一个字符串

      ``` c
      string str="abcd",str2="efg";
      str.insert(3,str2);
      cout<<str<<endl;//abcefgd
      ```

   6. str.insert(it,it2,it3):it为str需要被插入字符串位置的迭代器，it2、it3是待插入字符串的首尾迭代器

   7. str.erase():

      1. 删去单个元素：str.erase(it),被删除元素的==迭代器==

   8. 使用迭代去删除一个区间的元素：str.erase(it1,it2);

5. 使用索引删除一个区间的元素：str.erase(pos,length)，pos为开始删除的起始位置，length为删除元素的个数

6. 删除string的最后一个字符

   1. ``` c++
      //方法一：使用substr()
      	str = str.substr(0, str.length() - 1);
      //方法二：使用erase()
      	str.erase(str.end() - 1);
      //方法三：使用pop_back()
      	str.pop_back();
      ```

8. str.substr(pos，length)：返回从pos位置（pos为索引）开始的length个字符组成的子字符串（length长的字符串包括pos索引）

9. str.find(str2):str中有子字符串str2则返回第一次出现的位置，没有则返回string::npos;  str.find(str2，pos)表示从pos位置开始扫描，就是之前的不管有没有

11. str.replace(pos,len,strs):表示str从pos位开始的len个字符串替换为str2

### map

1. 访问方式：

   1. 通过下标访问：例如map<char,int> mp;mp[‘c’]

   2. 通过迭代器访问;it->first表示键；it->second表示值

2. 常用函数

   1. mp.find(key):返回key对应的迭代器。如果key值不存在，返回mp.end()

      ```c
      map<char,int>::iterator it=mp.find('b');
      ```

   2. mp.erase();

      1. 删除单个元素：mp.erase(it),it为待删除映射的迭代器
      2. 删除单个元素：mp.erase(key),key为待删除映射的键
      3. 删除一个区间的元素：mp.erase(first,last),first、last为待删除区间左闭右开的迭代器

   3. mp.count(x)：返回mp中key为x的元素的个数，可用作判断某个key是否在map中

   4. 在map<int,int>中原本没有某个key的情况下，如果使用该映射mp<key>，其初始值默认为0。例如：mp[tmp]+=1;可以直接使用，因为对于mp[tmp]其value默认为0

### unordered_map

1. unordered_map:与map的区别就是其内部元素==不会自动排序==，但是根据键值查找的速度大大提高。

   1. pair作为unordered_map的键值还要加上pair_hash

      1. ``` c++
         struct pair_hash
         {
             template<class T1, class T2>
             std::size_t operator() (const std::pair<T1, T2>& p) const
             {
                 auto h1 = std::hash<T1>{}(p.first);
                 auto h2 = std::hash<T2>{}(p.second);
                 return h1 ^ h2;
             }
         };
         
         unordered_map<pair<int, bool>, int, pair_hash> Map;
         ```


### multimap

1. multimap< int ,int > mmp:键值可重复的map

2. 插入：mmp.insert(make_pair(1,1));

3. 查找：mmp.find(key)：返回迭代器

   1. ``` c++
      //方法1
      multimap<int, string>::iterator it;
      //equal_range(key):作用：找到multimap中所有键值等于key的键值对，并返回始末的迭代器（第2个迭代器是最小大于key的迭代器！）（可理解为左闭右开）作为pair类型。(因为map内部自动按照key值排序，所以始末迭代器一定连续)
      pair<multimap<int, string>::iterator, multimap<int, string>::iterator> p = mt.equal_range(1);  
      for (it = p.first;it != p.second; ++it) {
          cout << it->second << endl;
      }
      
      //方法2
      //find（key）：只返回第一个key值的迭代器
      //count(key)：返回检索key值的个数
      it = mt.find(1);
      for (int i = 0, len = mt.count(1);i < len; ++i,++it) {
          cout << it->second << endl;
      }
      ```

5. 注意：multimap中存储的元素（键值对）实际上是是pair类型的单个元素，访问key或val的方法时候：it->first；it->second

   



### queue

3. 访问方式
   1. qu.front()：访问队首元素
   2. qu.back():访问队尾元素
4. 常用函数
   1. qu.push(x)；将元素X压入队列中
   2. front(),back()：获得队首队尾元素。使用前必须用empty判断队列是否为空，否则可能因队空而出现错误
   3. qu.pop():令队首元素出队，后面的元素向前移动一个位置
   4. qu.empty():检车队列是否为空，为空返回true，不为空返回false
   5. qu.sieze():返回队列中元素的个数

### priotity_queue

3. 访问方式：只有pq.top()访问队首元素

4. 常用函数

   1. pq.push（X）:令x入队
   2. pq.top():返回队列的队首元素
   3. pq.pop():令队首元素出队
   4. pq.empty():检测是否为空，为空返回true
   5. pq.size():返回队列元素个数

5. 元素优先级的设置

   1. 基本数据类型的优先级设置

      ``` c
      priotity_queue<int,vecotr<int>,greater<int> >q;//优先队列q是递增序列，greater换位less就变为递减队列
      ```

   2. 结构体的优先级设置

      ``` cpp
      struct fruit{
      	string name;
          int price;
          friend bool operator < (fruit f1,fruit f2){
      		return fl.price<f2.price
          }
      }
      ```

### stack

3. 访问方式
   1. st.top()：获得栈顶元素
4. 常用函数;
   1. st.push(x):将x压入栈
   2. st.top(x):获得栈顶元素，只是获得，并不会使栈顶元素消失
   3. st.pop()：弹出栈顶元素，等于删除栈顶元素，但不会返回栈顶元素
   4. st.empty():栈为空则返回true
   5. st.size():返回栈的元素

### pair

3. 初始化方式：pair<string,int>(“asd”,3)或make_pair（“asd”，3）
4. 元素访问：p.first、p.second
5. 常用函数
   1. 比较符是先比较第一个元素，再比较第二个元素
6. 常见用途，作为map的键值对插入

### algorithm头文件下的常用函数

1. 使用前提：#include<algorithm> using namespace std;

2. max（x,y）、min（x,y）：返回x、y中最大、最小值

3. abs（x）：返回绝对值，x必须为整数

4. swap（x,y）：用于交换xy的值

5. reverse（it,it2）：将数组指针或容器迭代器左闭右开区间内的元素翻转

6. next_permutation(it1,ti2):移动数组或容器内元素的位置，使变为指针或迭代器范围内的下一个全排列序列

   1. ``` c
      int a[10]={1,2,3};
      do{
      	printf("%d%d%d\n",a[0].a[1],a[2]);
      }while(next_permutation(a,a+3));
      ```

7. fill(it,it2,x):将it到it2区间内所有的元素赋值为x

8. sort()函数:

   1. ``` c
      #include<algorihm>
      using namespace std;
      int main(){
          int a[5]={5,4,3,2,1};
          sort(a,a+5);
      	return 0;
      }
      ```

   2. sort()排序范围是==左闭右开==，从小到大排序

   3. 第三个参数cmp函数。通过输入cmp函数，可以将sort改为从大到小排序，如下

      ![image-20200808181623163](D:\Typora\note\算法笔记c++.assets\image-20200808181623163.png)

   4. 结构体排序

      ![image-20200808182608598](D:\Typora\note\算法笔记c++.assets\image-20200808182608598.png)

9. lower_bound(it1,it2,val):用于寻找在容器或数组左闭右开范围内第一个值==大于等于==val元素的位置，返回迭代器或指针

10. upper_bound(it1,it2,val):用于寻找在容器或数组左闭右开范围内第一个值==大于==val元素的位置，返回迭代器或指针

## 搜索专题

1. 深度优先搜索（DFS）递归实现

   1. ``` c
      //利用栈的思想，但可以用vector实现
      //边界条件判断，或剪枝语句
      tmp.push_back(A[index])//以下为标准的DFS过程，先选择当前元素，然后递归DFS下一个索引，然后pop出当前元素，继续下一个索引的DFS
      DFS(index,nowk+1,sum+A[index])//如果每个元素可以选多次，那么还需要继续DFS当前索引的元素
      DFS(index+1,nowk+1,sum+A[index]);
      temp.pop_back();
      DFS(index+1,nowK,sum);
      ```

2. 广度优先搜索（BFS）非递归实现

   1. ``` c
      void BFS(int s){//s为第一个元素
      	queue<int> q;//使用队列实现
          q.push(s);
          while(!q.empty()){
      		//访问队首元素top
              //队首元素出队
              //将top元素能直接抵达的元素一次入队，并设置这些元素为已入队
          }
      }
      ```


### 平衡二叉树（AVL树）

   5. 答题模板

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

### 并查集

2. 并查集模板：用于解决连通图个数问题

   1. ``` c++
      //结点个数n
      int n;
      vector<int> f(n);
      
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
      int main(){
      	//初始化,使每个元素的father都是自己
          for(int i=0;i<n;i++){
              f[i]=i;
          }
          for(int i=0;i<n-1;++i){
              cin>>a>>b;
              make(a,b);
          }
      	return 0;
      }
      ```

   2. 

### 堆

1. 堆：一棵==完全二叉树==，如果每个节点的值都大于或等于孩子节点的值，称为大顶堆；如果每个节点都小于或等于孩子结点的值，称为小顶堆。

   1. ``` c++
      //判断堆
      int isMin=1,isMax=1;
       for (int i = 2; i <= n; i++) {
           	//如果孩子结点小于父节点，那一定不是小堆
              if (a[i]<a[i/2]) isMin = 0;
           	//如果孩子结点大于父节点，那一定不是大堆
              if (a[i]>a[i/2]) isMax = 0;
      }
      ```

   2. 

2. 堆的创建：

   1. 从下至上，从右至左，寻找第一个非叶子结点的节点，
   2. 然后使该节点与其孩子节点比较排序，最大者与其换位。如果没交换，则寻找下一个非叶子结点，如果交换了，则该节点继续与其孩子结点比较。
   3. （也就是说，从下至上，从左至右的非叶子节点位置都会==按顺序遍历一遍==，但是，如果发生了结点的交换则会一直对该结点进行比较，直到其无法进行位置的交换，即到达最下层或比其孩子结点大）

3. 堆排序：对于一个堆结构的数据，采用堆排序算法获得该数据结构结点值的排序

   1. 首先对堆结构进行排序：从上至下，从左至右获得序列

   2. 第一个元素一定是最大的元素，将其取出放入返回的结果排序中，然后在原序列中去掉该元素。

   3. 将原序列中的最后一个元素置于第一的位置，然后再对首个元素进行堆的调整（即调整了位置后重新调整为堆）

   4. 重复2,3步骤直至原序列为空

   5. ``` c++
      //heap[i]存储了堆的所有结点
      //low为需要调整位置的结点索引，high为最大结点索引
      //该函数调整堆的结构，使得low结点到其合适位置，并满足堆的性质
      void downAdjust(int low,int high){
          //i为待排结点，j为其左孩子
          int i=low,j=i*2;
          while(j<=high){
              //如果i右孩子存在并且大于左孩子，则j存储器右孩子，所以j是i的最大孩子
              if(j+1<=high&&heap[j+1]>heap[j])
                  j++;
              //如果i比其最大孩子j小，则交换i和j对应的值，并且再次对i交换后的结点进行排序；如果不需要交换，则退出循环
              if(heap[j]>heap[i]){
                  swap(heap[j],heap[i]);
                  i=j;
                  j=i*2;
              }
              else
                  break;
          }
      }
      ```

   6. ``` c++
      //建堆，一开始heap中的所有数都是随机位置的
      void creatHeap(){
      	for(int i=n/2;i>=1;i--)
              downAdjust(i,n);
      }
      ```

   7. ``` c++
      //删除堆顶元素
      void deleteTop(){
      	heap[1]=heap[n];
          //堆的总长度减1
          n--;
          downAdjust(1,n);
      }
      ```

   8. ``` c++
      //堆增加元素
      //向上调整函数
      void upAdjust(int low,int high){
      	int i=high,j=i/2;
          while(j>=low){
              if(heap[j]<heap[i]){
                  swap(heap[j],heap[i]);
                  i=j;
                  j=i/2;
              }
              else break;
          }
      }
      //插入函数
      void insert(int x){
          n++;
          heap[n]=x;
          upAdjust(1,n);
      }
      ```

   9. ``` c++
      //堆排序
      //对heap数组排序
      void heapSort(){
          //将heap数组初始化为堆
          creatHeap();
          for(int i=n;i>1;i--){
              swap(heap[i],heap[1]);
          	downAdjust(1,i-1);
          }
      }
      ```

   10. 

## 第 10章 图算法

### 最短路径

1. ``` c++
   const int inf=99999999;
   vector<vector<int>>pre(n);
   void djstl(vector<vector<int>>&G,int root){
       //dis[i]表示目前为止从root到i的最短路径长度；flag表示到该点的最短路径有没有找到
   	vector<int>dis(n,inf),flag(n,0);
       dis[root]=0;
       flag[root]=1;
       //遍历n次即可找完从root到所有结点的最短路径
       for(int j=0;j<n;++j){    
           //更新最短路径
           for(int i=0;i<n;++i){
               if(G[root][i]==-1||flag[i]==1)
                   continue;
               //dis[i]=min(dis[i],dis[root]+G[root][i]);
               if(dis[root]+G[root][i]<dis[i]){
                   pre[i].clear();
                   pre[i].push_back(root);
                   dis[i]=dis[root]+G[root][i];
               }
               else if(dis[root]+G[root][i]==dis[i])
                   pre[i].push_back(root);                    
           }
           //寻找本次dis中最短路径
           int mindis=inf,minno=0;
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


### 拓扑排序

1. 有向无环图
   1. 判断方法：对任意结点，通过任意路径都无法回到自身
2. 求拓扑排序的方法：
   1. 创建一个队列
   2. 将所有入度为0的结点入队，取出队首元素，将其出边的对应结点的入度减1。
   3. 不断循环2，直至队列为空



## 第11章 动态规划专题

### 动态规划

1. 动态规划(Dynamic Programming,DP):将复杂问题分解成若干子问题，然后通过综合子问题的最优解来获得原问题的最优解。注意：每个求解过的子问题的解都会被记录。

   1. 递归（记忆化搜索）

      ![image-20201116103322850](D:\Typora\note\算法笔记c++.assets\image-20201116103322850.png)

   2. 递推

2. 典型问题：

   1. 数塔问题：第n层有n个数字，问从顶至下，求数字之和最大的路径

      ![image-20201116205038767](D:\Typora\note\算法笔记c++.assets\image-20201116205038767.png)

      1. 递推：创建dp【i】【 j】二维数组记录从f【 i】【 j】 位置开始至底部的最大路径。有递推公式![image-20201116205231128](D:\Typora\note\算法笔记c++.assets\image-20201116205231128.png)，所以可以从倒数第2层开始，逐层使用该公式获得所有dp数组中的值，最终获得df【1】【1】即所求

         ![image-20201116205457554](D:\Typora\note\算法笔记c++.assets\image-20201116205457554.png)

      2. 递归：思路类似，但是是从顶至下递归求解，同时使用数组记录已求解过的dp【i】【j】

      3. 比较：递推是自底向上，逐层求解，最终获得所求。而递归是自顶向下直接求解，然后不断递归转化所求。

3. 分治与动态规划：

   1. 相同点：都是将问题分解为子问题
   2. 不同点：分治的子问题不重叠，动态规划拥有重叠子问题；分治法解决的问题不一定是最优化问题，动态规划问题一定是最优化问题

4. 贪心和动态规划：

   1. 相同点：都要求原问题必须拥有最优子结构（一个问题的最优解可以由其子问题的最优解有效构造出来）
   2. 不同点：贪心采用自顶向下，但是是在每一层只选择一条路径，而放弃其他路径，所以其结果不一定是最优解。而动态规划不论是自顶向下还是自底向下，都是最终才确定最优解。

### 最大连续子序列和

1. 最大连续子序列和：寻找在一固定序列中连续的子序列，使其子序列之和最大

   1. 定义dp【i】,表示以i结尾的最大子序列之和。
   2. 又因为dp[i]要么等于A[i]，要么等于dp[i-1]+A[i],所以有状态转移方程![image-20201117112954694](D:\Typora\note\算法笔记c++.assets\image-20201117112954694.png)
   3. 遍历所有数字，计算对应dp[i]，然后将最大的dp【i】作为输出结果

### 最长不下降子序列

1. 最长不下降子序列（LIS）：在给定序列中，找到一个最长子序列（==不一定连续==）使得序列非递减

   1. 定义dp【i】，表示以i结尾的最长子序列长度
   2. 对于每一个i，遍历i之前的数字，找到j，使得在A[j]小于等于A【i】的前提下，A[J]最大。则dp[i]=dp[j]+1；如果这样的j不存在，则dp[i]=1；即状态转移方程为：![image-20201118094337446](D:\Typora\note\算法笔记c++.assets\image-20201118094337446.png)
2. 由此例子可知：动态规划的转移方程，不一定是dp【i】和dp【i-1】的方程，而是1……i-1的方程。（也即，==i是由i之前的dp答案推出==，而不仅仅是前一个i-1推出）

### 最长公共子序列

1. 最长公共子序列（LCS）：给定2个序列，找出某个公共序列（不一定连续），使其长度最长
2. dp【i】【j】:表示第一个序列前i个字符，和第二个序列前j个字符的最长公共子序列长度
3. dp边界是i=0和j=0的情况，此时因为某个序列的长度为0，所以dp值也是0
   1. ![image-20201118102205317](D:\Typora\note\算法笔记c++.assets\image-20201118102205317.png)

### 最长回文子串

1. 最长回文子串：在给定序列中，找出最长的回文子串

   1. 使用dp【i】【j】表示从i到j的字符串是否是回文串，dp的计算：如果A【i】==A【j】，且dp【i+1】【j-1】为回文串，那么dp【i】【j】就是回文串。所以有如下状态转移方程：![image-20201118111657681](D:\Typora\note\算法笔记c++.assets\image-20201118111657681.png)
   2. dp的边界是长度为1和2的字符串
   3. 枚举方式：先循环不同长度，从3到n，然后在循环不同的字符串起点（从0开始直至结尾结点大于等于n）

### 01背包问题

1. 01背包问题：有n件物品，它们的重量分别是w【i】，价值分别为c【i】,现有一背包容量为V，问如何选择物品放入背包，使得总价值最大。（因为每件物品只有1件，所有对于每件物品只有选和不被选2种状态，因此成为01背包问题）

   1. 创建dp【i】【v】数组，存储的值的意义是对于前i件物品，使用容量为v的背包所获得的最大价值。对于第i件物品，如果不选，则dp【i】【v】等于dp【i-1】【v】；如果选了第i件物品，则dp【i】【v】=dp【i-1】【v-w【i】】+c【i】，因此有如下状态转移方程。（但是，如果使用递归的方式求解，那么每一件物品都有2种选择，2条道路，原问题依然是2的n次方种可能，复杂度没有降低，因此，不能使用递归）

      ![image-20201121181347708](D:\Typora\note\算法笔记c++.assets\image-20201121181347708.png)

### 完全背包问题

​	![image-20210411004020107](D:\Typora\note\算法笔记c++.assets\image-20210411004020107.png)



## 第12章 字符串专题

### kmp算法

4. KMP代码

   1. ``` c++
      //str是母串，ptr是子串，slen是母串长度，plen是子串长度
      int KMP(char *str, int slen, char *ptr, int plen)
      {
      	int *next = new int[plen];
      	GetNext(ptr, next, plen);//计算next数组
      	int j = -1;
      	for (int i = 0; i < slen; i++)
      	{
      		while (j >-1&& ptr[j + 1] != str[i])//ptr和str不匹配，且k>-1（表示ptr和str有部分匹配
      			j = next[j];//往前回溯
          	if (ptr[j + 1] == str[i])
              	j = j + 1;
          	if (j == plen-1)//说明k移动到ptr的最末端，匹配成功了！
          	{
              	return i-plen+1;//返回相应的位置
          	}
      	}
      	return -1;  //匹配失败了，没有匹配到合适的
      }
      void GetNext(char *str, int *next, int len) { 
      	next[0] = -1;//next[0]初始化为-1，-1表示不存在相同的最大前缀和最大后缀 
	int j = -1;//j初始化为-1，-1表示当前子串没有相同前后缀 
          //从1开始求所有长度子串的next数组值
      	for (int i = 1; i < len; i++) { 
      		while (j != -1 && str[j + 1] != str[i]) {//最后一位str[i]与相同前后缀的后一位str[j + 1]不匹配时
      			 j = next[j];//将相同前后缀缩小到下一个位次的长度，也即使当前相同前后缀的最长相同前后缀
      		}
      		if (str[j + 1] == str[i]){//如果相同，当前next【i】最长前后缀的长度是j+1
      			j = j + 1;
      		} 
      	next[i] = k;//这个是把算的j的值（就是相同的最大前缀和最大后缀长）赋给next[i] 
      	}
      }
      ```
      
   2. 

