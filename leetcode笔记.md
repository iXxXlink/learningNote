

## leetcoede打卡记录



1. |    日期    |                      题号                       |
   | :--------: | :---------------------------------------------: |
   | 2020.11.26 |                   2,19,21,23                    |
   | 2020.11.27 |              24,25,61,82,83,86,92               |
   | 2020.11.28 |                     141,142                     |
   | 2020.11.29 |           143,147,148,160,203,206,234           |
   | 2020.11.30 |             237,328,430,445,707,725             |
   | 2020.12.1  |         817,876,1019,1171,1290,1669,94          |
   | 2020.12.2  |               95,96,98,99,100,101               |
   | 2020.12.3  |                   102,103,104                   |
   | 2020.12.4  |         105,106,107,108,109,110,111,112         |
| 2020.12.5  | 113,114,116,117,118,129,144,145,173,199,222,226 |
   | 2020.12.6  |               230,235,236,257,337               |
   | 2020.12.7  |           404,429,437,450,501,508,513           |
   | 2020.12.8  |                   515,530,538                   |
   | 2020.12.9  |    543,559,563,572,589,590,606?,617,623,637     |
   | 2020.12.10 |                  20,42?,1,4,11                  |
   | 2020.12.11 |         15,16,18,26,27,31,33,35,39,40?          |
   | 2020.12.12 |                 41,45,48,53,55                  |
   | 2020.12.13 |           54,57,59,62,63,64,66,73,74            |
   | 2020.12.14 |          75,78,79,80,81,84,88,119,120?          |
   | 2020.12.15 |                 455,135,435,605                 |
   | 2020.12.16 |             452,763,122,406,665,167             |
   | 2020.12.17 |                 76?,633,680,524                 |
   | 2020.12.18 |                 389,69,154?,540                 |
   | 2020.12.19 |                  451,695,547,7                  |
   | 2020.12.20 |                746?,46?,77?,51?                 |
   | 2020.12.21 |                     9？,14                      |
   | 2020.12.22 |                 70,198,413,542                  |
   | 2020.12.23 |                 387,221,279,136                 |
   | 2020.12.24 |                139?,300,242,205                 |
   | 2020.12.25 |                     647,934                     |
   | 2020.12.26 |                     130,91                      |
   | 2020.12.27 |                      1143                       |
   | 2020.12.28 |                       416                       |
   | 2020.12.29 |                       474                       |
   | 2020.12.30 |                       322                       |
   | 2020.12.31 |                       72                        |
   |  2021.1.1  |                       650                       |
   |  2021.1.2  |                       121                       |
   |  2021.1.3  |                       188                       |
   |  2021.1.4  |                       509                       |
   |  2021.1.5  |                       830                       |
   |  2021.1.6  |                       213                       |
   |  2021.1.7  |                       343                       |
   |  2021.1.8  |                       67                        |
   |  2021.1.9  |                      1004                       |
   
   
   
   
   
   



1. 需要按照类型进行刷题以提高效率，下面是各类型的考察频率、难度及性价比

   ![image-20201125102820770](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201125102820770.png)

2. 答题的步骤

   1. 看懂题目：深刻完整地理解题目的要求
   2. 分析算法：在此步骤中不需要想任何有关代码的实现，是需要思考在逻辑上如何解决问题。
   3. 实现代码：将上一步骤中推导出的算法，每个部分每个部分的使用代码实现。

3. 写在刷题之前的话：刷题是一件漫长的工作，不是一时兴起，也不能一蹴而就，我所刷题的目的是为了考研机试、为了大厂面试，无论是哪一个选择，刷题都是我的必经之路，所以，请你坚持一下，再坚持一下，不要让未来的我失望。

4. 少即是多



## c++使用心得

1. C++不适用NULL，而使用nullptr

2. nullptr在三目运算符中能表示0

3. NULL在CPP中就是由整型int 0 宏定义而来，所以只能表示整型0，例如，char * p=NULL；fun（p）；此时就产生矛盾！显然fun中输入的类型是char *，但是实际的效果却是输入int，又因为C++有重载的特性，int和char *产生的结果是截然不同的，所以此处存在缺陷。而nullptr的引入就是为了解决该缺陷，nullptr是std::nullptr_t类型的（constexpr）变量。它可以转换成任何指针类型和bool布尔类型，但不能转为整型。（值得注意，因为null和nullptr的值都是0，虽然类型不同，所以有：NULL==nullptr ==0）

4. map<int,char> mp：映射很好用，用于哈希映射是很轻松

5. 在CPP中，条件判断中不需要出现p！=nullptr，p可直接作为条件

6. do while和while的区别：等价于do while先执行一次循环体，然后与while完全相同（或许可以认为是，首次不需要进行判断时可以用dowhile）

7. cpp变量（vector，map）未初始化的默认值是0

8. 创建结点可直接用new，且不用加struct：

   ``` c++
   ListNode* dump=new ListNode(-1);//注意dump为指针而非结构体变量，因为new返回的就是指针！
   ```

9. 使用某指针p前，==一定要在之前使用if（p）==,最好不要用其他条件替换，因为容易产生差错，而这种方式，是一定有效的。

10. 提交前必须判断：vecotor/node为空的情况

11. 在循环结束后，必须在循环外再次判断是否再执行一次操作。（很多情况，遍历完数组后，还存在一些残留数据）

12. 推荐使用++a（即自增符在前面，速度更快）



## 链表（Linked list）

1. 创建新的结点，最好使用先创建结点指针，

   再分配内存的方式，直接定义的话有问题

   ``` c
   struct ListNode* tmp;
   tmp=(struct ListNode*)malloc(sizeof(struct ListNode));
   ```

2. 链表头结点可能为NULL

3. 对2条链表进行处理时，可以预先指定某条链表作为结果链表，但是可能存在首结点不是该链表首结点的情况（即不满足为首结点的情况），此时可以创建一个头前结点，其值自定义以确定为首结点。

   ``` c
       struct ListNode*pl1;
       pl1=(struct ListNode*)malloc(sizeof(struct ListNode));
       pl1->next=l1;
   ```

4. C语言中求模运算：a=b%c，a的符号与b的符号相同（即ab同正同负）

   ``` c
   //如果需要让结果为非负数，可进行如下运算
   a=(b%c+c)%c
   ```

5. leetcode函数中给的参数需要考虑是否为NULL、是否为空、是否为0

6. 在循环条件中，需要如果要判断x->next!=NULL,必须先判断x！=NULL

7. 判断循环的条件，必须要求在循环中==所有访问过的结点必须提前判断该结点是否为NULL==

8. 动态创建malloc的变量可以在最后用free释放，以减少内存消耗

9. 2 两数相加：链表的相加

   1. ``` c++
          ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
          ListNode vHead(0), *p = &vHead;//vhead为结果首结点，p存储当前节点的指针
              int flag = 0;//flag为进位
              //一直循环结束条件为l1、l2、flag全为空
              while (l1 || l2 || flag) {
                  int tmp = 0;
                  if (l1 != nullptr) 
                      tmp += l1->val;
                  if (l2 != nullptr) 
                      tmp += l2->val;
      
                  tmp += flag;
                  
                  flag = tmp / 10;
                  tmp %= 10;
                  
                  ListNode *next = l1 ? l1 : l2;
                  if (next == nullptr) 
                      next = new ListNode(tmp);
                  next->val = tmp;
                  
                  p->next = next;
                  p = p->next;
      
                  l1 = l1 ? l1->next : nullptr;
                  l2 = l2 ? l2->next : nullptr;
              }
              return vHead.next;
           }
      ```

10. 141环形链表的判断：使用快慢指针（快指针一次走2步，慢指针一次走1步，如果有环，则终将相遇（因为可以视作是相对运动，在环中时，慢指针不动，等到快指针超过一圈时即相遇！））

   ``` c
   bool hasCycle(ListNode *head) {
           ListNode *fast = head, *slow = head;
           while(fast != nullptr && slow != nullptr){
               if(fast->next != nullptr)
                   if(fast->next->next != nullptr)
                       fast = fast->next->next;
                   else 
                       return false;
               else
                   return false;
               if(slow->next != nullptr)
                   slow = slow->next;
               else
                   return false;
               if(fast == slow)
                   return true;
           }
           return false;
       }
   ```

11. 142环形链表之环起点判断：

    1. 设fast=2slow,起点到入口为的长度为M, 入口到p的距离为P。环形的周长为c,此时 slow = M+P， fast=M+P+rc。(r为一个变量），也就是当rc = slow时，它们两个会相遇。
    2. 所以有fast = 2slow = M+P + slow = M+P+rc。所以slow = rc. M = rc - P = (r-1)c + (c- P),其中（ c - P） 等于从相遇的p点再走回到环的起点。
    3. 因此，可以在快慢指针相遇后，再在起点设置一个慢指针X，当X走M步时，即slow再走了(r-1)c + (c- P)步，二者刚好在环的起点相遇！
    4. ![image-20201129180647384](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201129180647384.png)

12. 在访问指针内容时，为了保证不是访问空指针可以在之前使用 if（p）

13. 143重排链表：对序号为1,2,3,4…N的链表，重排为1,N,2,N-1…的链表。

    1. 首先使用快慢指针找到链表的中点，将链表分成两部分。
    2. 然后将中点往后的链表倒序排列
    3. 最后将倒序排列的链表间隔插入中点前面的链表中即可。

14. 148排序链表：将一条链表排为升序链表

    1. 1

       ``` c++
       //归并排序
       class Solution {
       public:
           //合并2条有序链表
           ListNode *mergeList(ListNode *l1,ListNode *l2){
               ListNode dummy(-1),*root=&dummy;
               if(l1==NULL) return l2;
               if(l2==NULL) return l1;
               while(l1&&l2){
                   root->next=l1->val<=l2->val?l1:l2;
                   if(l1->val<=l2->val)
                       l1=l1->next;
                   else
                       l2=l2->next;
                   root=root->next;
               }
               root->next=l1==NULL?l2:l1;
               return dummy.next;
           }
           ListNode* sortList(ListNode* head) {
               //递归边界：链表为空或只有1个元素
               if(head==NULL||head->next==NULL) return head;
               ListNode *slow=head,*fast=head;
               //寻找链表中点，使链表平分
               while(slow->next&&fast->next&&fast->next->next){
                   slow=slow->next;
                   fast=fast->next->next;
               }
               fast=slow->next;
               slow->next=NULL;
               ListNode *p1=sortList(head);
               ListNode *p2=sortList(fast);
               return mergeList(p1,p2);
           }
       };
       ```

       

    2. ``` c++
       //使用multimap进行排序，但空间时间都不行，唯一优势，容易写出。。
       class Solution {
       public:
           ListNode* sortList(ListNode* head) {
               //multimap表示map内键值可重复，且因为map内部自动排序
               multimap<int,ListNode*> mul;
               while(head){
                   mul.insert(make_pair(head->val,head));
                   head=head->next;
               }
               ListNode dummy(-1);
               head=&dummy;
               for(auto it=mul.begin();it!=mul.end();it++){
                   head->next=it->second;
                   head=head->next;
               }
               head->next=NULL;
               return dummy.next;
           }
       };
       ```

    3. 

    4. 

15. 链表找中点的方法：

    ``` c++
    while(slow->next&&fast->next&&fast->next->next){
        slow=slow->next;
        fast=fast->next->next;
    }
    ```

16. 160相交链表：寻找2个链表最开始的相交点，不相交返回null

    1. 算法：A,B两条链表先分别从起点开始遍历，当某个点达到终点后，将其转移到另一条链表的起点，这样，2个点相交时就是所求的起始相交点
    2. 解释：因为A,B两个点走过的距离是相同的，所以必定有2个点第2次到达终点必定是同时的（因为2个点都是走过（A+B）的长度），而同时达到终点，必定也是同时到达倒数第二个点，依次类推，必定同时达到相交点！

17. 206翻转链表：很简单就不多说了。

    1. ``` c++
       //递归
       ListNode* reverseList(ListNode* head) {
               if(!head||!head->next)
                   return head;
               ListNode* res;
               res=reverseList(head->next);
               head->next->next=head;
               head->next=nullptr;
               return res;
       
           }
       ```

       

    2. ``` c++
       //非递归
       ListNode* reverseList(ListNode* head) {
               if(!head||!head->next)
                   return head;
               ListNode* pnow=nullptr,*now=head,*anow=head->next;
               while(anow){
                   now->next=pnow;
                   pnow=now;
                   now=anow;
                   anow=anow->next;
               }
               now->next=pnow;
               return now;
       
           }
       ```

18. 234 回文链表：判断一个链表是否为回文

    1. ``` c++
       //快慢指针获得中点+栈
       if(!head||!head->next)
                   return true;
               ListNode* fast,*slow,*right;
               stack<int> st;
               int x=0;
               fast=head;
               slow=head;
               st.push(head->val);
               while(fast->next&&fast->next->next){
       
                   fast=fast->next->next;
                   slow=slow->next;           
                   st.push(slow->val);
               }
               if(!fast->next)
                   st.pop();
               right=slow->next;
               while(right){
                   x=st.top();
                   st.pop();
                   if(right->val!=x)
                       return false;
                   right=right->next;
               }
               return true;
       ```

    2. ``` c++
       //最土味但最易用的方法，我竟然没有第一时间想到这种最简单的方法。。
       if (!head) return true;
       
               vector<ListNode*> v;
               ListNode* p = head;
               while (p) {
                   v.push_back(p);
                   p = p->next;
               }
       
               int i = 0, j = v.size() - 1;
       		//土味但却好用
               while (i < j && v[i]->val == v[j]->val) {
                   ++i;
                   --j;
               }
       
               if (i < j)
                   return false;
               else
                   return true;
       ```

    3. 

    ``` c++
    //一般做法
    class Solution {
    public:
        bool isPalindrome(ListNode* head) {
            if(!head||!head->next)
                return true;
            ListNode*slow,*fast,*right;
            slow=head;
            fast=head;
            //这就是快慢指针的魅力
            while(fast->next&&fast->next->next){
                fast=fast->next->next;
                slow=slow->next;
            }
            //无论奇偶结点个数,右链表第一个元素都是slow->next
            right=slow->next;
            right=reverseList(right);
            while(right){
                if(right->val!=head->val)
                    return false;
                right=right->next;
                head=head->next;
            }
            return true;
            
        }
        //链表翻转函数
        ListNode* reverseList(ListNode* head) {
            if(!head||!head->next)
                return head;
            ListNode* pnow=nullptr,*now=head,*anow=head->next;
            while(anow){
                now->next=pnow;
                pnow=now;
                now=anow;
                anow=anow->next;
            }
            now->next=pnow;
            return now;
    
        }
    };
    ```

19. ​	430扁平化多级双向链表：

    1. ``` c++
       //迭代法，逐步扁平化
       Node *p = head;
       while (p) {
           //不断循环，找到用于child的元素
           if (p->child) {
               Node *next = p->next;
               Node *child = p->child;
               p->next = child;
       
               p->child = nullptr;
               child->prev = p;
       		//找到P的子链的最后一个元素
               while (child->next) {
                   child = child->next;
               }
               //将子链嵌入一级链表中
               child->next = next;
               if (next) {
                   next->prev = child;
               }
           }
           p = p->next;
       }
       return head;
       ```

20. 445 两数相加2：2条链表以高位为起点，所以不能正常的从低位开始对应每位再与进位相加算出该为数值和进位。

    1. 可以先算出链表长度，然后低位对齐，从高位开始==不带进位==的对应位相加，计算出该位的结果和进位，最后得出的结果链表再与每一位的进位相加得到最终结果（注意：暂时结果与进位相加也可能产生进位）。（==此处涉及到加法的本质，十分有趣==，即可以先不算进位，最后再将进位一起处理，就是并行加法器，n个位同时相加）

    2. ==注意==：4与6相加的进位1是与百位上的结果相加

    3. ![image-20201130110122230](C:\Users\Lch\AppData\Roaming\Typora\typora-user-images\image-20201130110122230.png)

    4. ``` c++
       //不翻转链表,一种思路仅供参考
       class Solution {
       public:
           ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
               
               int n1 = countListNodeNumber(l1);
               int n2 = countListNodeNumber(l2);
               
               ListNode* long_list = NULL;
               ListNode* short_list = NULL;
               int bigger_n = 0;
               int smaller_n = 0;
               
               if (n1 <= n2)
               {
                   long_list = l2;
                   short_list = l1;
                   bigger_n = n2;
                   smaller_n = n1;
               }
               else
               {
                   long_list = l1;
                   short_list = l2;
                   bigger_n = n1;
                   smaller_n = n2;   
               }
               int temp = bigger_n - smaller_n + 1;
               int sum_array[bigger_n + 1] = {0};
               int carry_array[bigger_n + 1] = {0};
               int sum = 0;
               int carry = 0;
               
               ListNode* long_temp = long_list;
               ListNode* short_temp = short_list;
               
               for (unsigned int i = 1; i <= bigger_n; i++)
               {
                   carry = 0;
                   if (i < temp)
                   {
                       sum = long_temp->val;
                   }
                   else
                   {
                       sum = long_temp->val + short_temp->val;
                       if (sum >= 10)
                       {
                           sum = sum % 10;
                           carry = 1;
                       }
                       short_temp = short_temp->next;
                   }
                   sum_array[i] = sum;
                   carry_array[i-1] = carry;
                   long_temp = long_temp->next;
               }
               
                      
               ListNode* new_head = new ListNode(0);
               long_temp = new_head;
               
               for (unsigned int i = bigger_n; i > 0; i--)
               {
                   // 在链表头部进行插入
                   sum = sum_array[i] + carry_array[i];
                   if (sum >= 10)
                   {
                       sum = sum % 10;
                       carry_array[i-1] = 1;
                   }
                   short_temp = new ListNode(sum);
                   short_temp->next = long_temp->next;
                   long_temp->next = short_temp;
               }
               
               sum = sum_array[0] + carry_array[0];
               if (sum)
               {
                   short_temp = new ListNode(sum);
                   short_temp->next = long_temp->next;
                   long_temp->next = short_temp;
               }
               
               return new_head->next;
       
           }
           
           int countListNodeNumber(ListNode *head)
           {
               int node_num = 0;
               ListNode* slow = head; 
               ListNode* fast = head; 
               
               while(fast && fast->next) 
               {
                   slow = slow->next; 
                   fast = fast->next->next; 
                   node_num++; 
               } 
               
               if (fast) 
               { 
                   node_num = node_num * 2 + 1;
               } 
               else 
               { 
                   node_num = node_num * 2; 
               }
               
               return node_num;
           }
           
           
       };
       ```

    5. 

21. 707 设计链表：设计一个链表类，实现其中一些基本函数，要点：在类外自定义一个节点结构体，==类内的成员变量为head，该变量的next指向第一个元素（而非head指向第一个元素！）==

    1. ``` c++
       struct node{
               int val;
               node* next;
       };
       class MyLinkedList{
       private:
           node* head;//成员变量一般为private
       public:
       
           /** Initialize your data structure here. */
           MyLinkedList() {
               node* x=new node;
               x->val=-1;
               x->next=nullptr;
               head=x;
           }
           
           /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
           int get(int index) {
               node* now=head->next;
               int i;
               for(i=0;now&&i<index;i++){
                   now=now->next;
               }
               if(now)
                   return now->val;
               else
                   return -1;
           }
           
           /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
           void addAtHead(int val) {
               node *x=new node;
               x->val=val;
               x->next=head->next;
               head->next=x;
           }
           
           /** Append a node of value val to the last element of the linked list. */
           void addAtTail(int val) {
               node* now=head;
               node *x=new node;
               x->next=nullptr;
               x->val=val;
       
               while(now->next){
                   now=now->next;
               }
               now->next=x;
           }
           
           /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
           void addAtIndex(int index, int val) {
               node*x=new node,*now,*pnow;
               int i;
       
               now=head->next;
               pnow=head;
               x->val=val;
               x->next=nullptr;
               
               if(index<=0){
                   x->next=head->next;
                   head->next=x;
               }
       
               for(i=0;now&&i<index;i++){
                   now=now->next;
                   pnow=pnow->next;
               }
               if(!now&&i==index){
                   pnow->next=x;
                   return;
               }
               if(!now)
                   return;
               else{
                   pnow->next=x;
                   x->next=now;
                   return;
               }
       
       
           }
           
           /** Delete the index-th node in the linked list, if the index is valid. */
           void deleteAtIndex(int index) {
               if(index<0)
                   return;
               node*now,*pnow;
               int i;
               pnow=head;
               now=head->next;
               for(i=0;now&&i<index;i++){
                   now=now->next;
                   pnow=pnow->next;
               }
               if(now)
                   pnow->next=now->next;
       
           }
       };
       
       /**
        * Your MyLinkedList object will be instantiated and called as such:
        * MyLinkedList* obj = new MyLinkedList();
        * int param_1 = obj->get(index);
        * obj->addAtHead(val);
        * obj->addAtTail(val);
        * obj->addAtIndex(index,val);
        * obj->deleteAtIndex(index);
        */
       ```

       

22. 1171:在链表中反复删除连续结点，直至链表中不存在连续结点之和为0.

    1. ``` c++
       ListNode* removeZeroSumSublists(ListNode* head) {
               //递归
            if(head->next==nullptr)
           {
               if(head->val==0)
                   return nullptr;
               else  
                   return head;
           }  
           ListNode* result=removeZeroSumSublists(head->next);
           head->next=result;
           if(head->val==0)
               return result;
           else
           {
               ListNode* p=head;
               int sum=0;
               while(p!=nullptr)
               {
                   sum+=p->val;
                   if(sum==0)
                   {
                       return p->next;
                   }   
                   p=p->next;
               }
               result=head;
           }  
           return result; 
       ```

       

23. 2





## 树（tree）

1. 不同二叉搜索树2：给定一个n，输出一个vector，元素为所有由（1…n）组成的不同二叉搜索树

   1. 这种复杂题一般使用递归解决，

   2. 然后确定递归返回类型：一定不可能是node*类型，要转为vector的结果太复杂了，一般和所求的类型是一样的，所以是vector<node * >类型。

   3. 然后是递归参数：参数需不需要有root呢？我觉的是不需要的，因为如果参数中有root，那么最顶层的递归函数需要遍历n次，还要将root添加到vector的每一个元素中，调用不美观，也不符合模块化（递归函数本身就要解决这些问题），但也不是不能用。所以为使调用最简洁，只有左右边界l、f。

   4. 最后是递归边界：需不需要考虑l==f的情况呢？不用，因为如果递归边界是l ==r，那么结果中就没有nullptr，与题意不符，要是结果中有nullptr元素，递归边界只能是l>r

   5. ``` c++
      class Solution {
      public:
          vector<TreeNode*> generateTrees(int n) {
      
              vector<TreeNode*> res;
              if(!n)
                  return res;
              res=digui(1,n);
              return res;
          }
      
          vector<TreeNode*> digui(int l,int r){
              //不需要管l==r的情况,只管root为nullptr的情况
              if(l>r){
                  vector<TreeNode*>res;
                  res.push_back(nullptr);
                  return res;
              }
      
              vector<TreeNode*> lres,rres,res;
              for(int p=l;p<=r;p++){
                  lres=digui(l,p-1);
                  rres=digui(p+1,r);
                  for(auto lone:lres){
                      for(auto rone:rres){
                          TreeNode*  root_node=new TreeNode;
                          root_node->val=p;
                          root_node->left=lone;
                          root_node->right=rone;
                          res.push_back(root_node);
                      }
                  }
              }
              return res;
      
          }
      };
      ```

2. Morris Traversal：用于数的遍历

   1. ``` c++
      class Solution {
      public:
          vector<int> inorderTraversal(TreeNode *root) {
              vector<int> res;
              if (!root) return res;
              TreeNode *cur, *pre;
              cur = root;
              while (cur) {
                  if (!cur->left) {
                      res.push_back(cur->val);
                      cur = cur->right;
                  } else {
                      pre = cur->left;
                      while (pre->right && pre->right != cur) pre = pre->right;
                      if (!pre->right) {
                          pre->right = cur;
                          cur = cur->left;
                      } else {
                          pre->right = NULL;
                          res.push_back(cur->val);
                          cur = cur->right;
                      }
                  }
              }
              return res;
          }
      };
      
      ```

3. 101 对称二叉树：判断输入的二叉树是否是对称的结构

   ``` c++
   class Solution {
   public:
       bool check(TreeNode* l , TreeNode* r) {
           //若左右子树都为空，返回true
           if(!l && !r) {
               return true;
           }
   		//只有一方为空，返回false
           if(!l || !r) {
               return false;
           }
   		//此步是关键，注意是将左子树结点的左右孩子和右子树结点的右左孩子进行对比
           return l->val == r->val && check(l->left, r->right) && check(l->right, r->left);
       }
   
       bool isSymmetric(TreeNode* root) {
           return check(root, root);
       }
   };
   ```
   
4. 102 二叉树的层序遍历：注意返回类型是vector<vector<int>>，即每一层的元素在同一vector中

   1. 一般方法：逐层将元素加入一个vector中，再将该vector加入res中

   2. ``` c++
      	queue<TreeNode*>qu;
       vector<vector<int>> res;
       vector<vector<int>> levelOrder(TreeNode* root) {
       	if(!root)
       		return res;
       	qu.push(root);
       	chengci();
       	return res;
       }
       void chengci(){
       	int len=qu.size();
       	if(len==0)
       		return ;
       	vector<int>tmp;
       	TreeNode* x;
       	//此题的关键在于此，难点是每一层的元素都在同一vector中
       	//当前队列中的所有元素是该层的所有元素，所以只将该数量的元素存入vector中，所有子节点为下一层元素
       	for(int i=0;i<len;i++){
       		x=qu.front();
       		qu.pop();
               //下面的判断至关重要
       		if(x->left)
       			qu.push(x->left);
       		if(x->right)
       			qu.push(x->right);   
       		tmp.push_back(x->val);
       	}
       	res.push_back(tmp);
       	chengci();
       }
      ```
      
   3. 另一种方法：遍历该数（怎样遍历都行），遍历时，但在递归遍历时，在参数中加上该结点的深度，然后将该结点值push进相应深度的vector中

   4. ``` c++
      class Solution {
      public:
          vector<vector<int>> ans;
          vector<vector<int>> levelOrder(TreeNode* root) {
              pre(root, 0);
              return ans;
          }
          
          void pre(TreeNode *root, int depth) {
              if (!root) return ;
              //此处为重点，如果深度大于等于res元素的个数（也就是现存深度vector），那么将往res中push一个空的vector<int>作为该层vector，注意：不能通过索引访问res中还没创建的vector
              if (depth >= ans.size())
                  ans.push_back(vector<int> {});
              ans[depth].push_back(root->val);
              pre(root->left, depth + 1);
              pre(root->right, depth + 1);
          }
      };
      ```

5. 108 将==有序==数组转换为平衡二叉搜索树：即平衡二叉搜索树的建立

   1. ``` c++
      class Solution {
      public:
          TreeNode* sortedArrayToBST(vector<int>& nums) {
              return help(nums, 0, nums.size() - 1);
          }
          TreeNode* help(vector<int>& nums, int l, int r) {
              if (r < l) return nullptr;
              //找出中点作为根节点
              int mid = l + ((r - l) >> 1);
      
              TreeNode* root = new TreeNode(nums[mid]);
              root->left = help(nums, l, mid - 1);
              root->right = help(nums, mid + 1, r);
              return root;
          }
      
      };
      ```

6. 110 平衡二叉树：判断一棵二叉树是否是平衡二叉树(即树的每一个节点的左右子树高度之差小于等于1)

   1. 十分好奇，为什么我用unordered_map速度反而更慢

   2. ``` c++
      class Solution {
      public:
          bool isBalanced(TreeNode* root) {
                      if(!root)
                  return true;
              return (abs(fun(root->left)-fun(root->right))<=1)&&digui(root->right)&&digui(root->left);
          }
      
      
          int fun(TreeNode* root){
              if(!root)
                  return 0;
              return max(fun(root->left),fun(root->right))+1;
          }
      };
      ```

7. 自创：遍历所有从根节点到叶子结点的路径，并存储于vector<vector<int>>中

   1. ``` c++
      //参数的设置时关键,参数中的vector<int> tmp储存了从根结点到上一结点的值
      vector<vector<int>> res;
      void digui(TreeNode* root,vector<int> tmp){
          if(!root)
              return;
      
          tmp.push_back(root->val);
          if(!root->left&&!root->right){
              res.push_back(tmp);
              return;
          }
          if(root->left){
              digui(root->left,tmp);
          }
          if(root->right){
              digui(root->right,tmp);
          }
      }
      ```

8. 有些题目需要判断根节点是否为nullptr，可以不用再递归函数中判断，这会使每次调用递归函数都判断一次，而就在main函数中判断，然后在递归函数的处理过程中，不将nullptr指针进入递归。

9. 对于某结点有无左右孩子结点的情况判断，可以使用如下方法判断

   1. ``` c++
      if(!root->left&&!root->right){//是否是叶子结点，即左右孩子都空
      ;}
      if(root->left){//是否有左孩子
      ;}
      if(root->right){//是否有右孩子
      ;}
      ```

   2. 

10. 113 路径之和||：

    1. ``` c++
       vector<vector<int>> res;
       vector<vector<int>> pathSum(TreeNode* root, int sum) {
           //此处排除了根节点为空的情况
           if(!root)
               return res;
           vector<int> tmp;
           dfs(root,tmp,sum);
           return res;        
       }
       void dfs(TreeNode* root,vector<int> tmp,int sum){
           tmp.push_back(root->val);//因为root不为空，所有能直接用val
           if(!root->left&&!root->right&&(sum==root->val)){
               res.push_back(tmp);
               return;
           }
           if(root->left)
               dfs(root->left,tmp,sum-root->val);
           if(root->right)
               dfs(root->right,tmp,sum-root->val);
       }
       ```

    2. 下面这种方法与上面的区别只在于使用了引用tmp，但速度却快很多，这是为什么呢？

    3. 如果没使用tmp的引用，那么每次在dfs中使用tmp，需要将tmp中所有元素复制一遍，开销增加许多，而直接传引用只是传了一个地址，可以直接使用，所以更快。

    4. ``` c++
       //这个也太快了吧
       vector<vector<int>> res;
       vector<vector<int>> pathSum(TreeNode* root, int sum) {
           if(!root)
               return res;
           vector<int> tmp;
           dfs(root,tmp,sum);
           return res;
       }
       void dfs(TreeNode* root,vector<int> &tmp,int sum){
           tmp.push_back(root->val);
           if(root->val==sum&&(root->left==NULL&&root->right==NULL)){
               res.push_back(tmp);
           }
           if(root->left)
               dfs(root->left,tmp,sum-root->val);
           if(root->right)
               dfs(root->right,tmp,sum-root->val);
           tmp.pop_back();
       }
       ```

11. 222 完全二叉树的结点个数

    1. 对于完全二叉树，,左孩子的编号为根节点编号乘2，右孩子编号为根节点编号乘2加1

    2. ``` c++
       //虽然写法简单，但没有第二种快，也没利用到完全二叉树的条件
       int countNodes(TreeNode* root) {
           if(!root)
               return 0;
           return countNodes(root->left)+countNodes(root->right)+1;
       }
       ```

    3. 

    4. 

       ``` c++
       class Solution {
       public:
           int res=0;
           int countNodes(TreeNode* root) {
               if(!root)
                   return 0;
               digui(root,1);
               return res;
           }
           void digui(TreeNode* root,int no){
               if(!root->left&&!root->right){
                   res=(no>res)?no:res;
                   return;
               }
       
               if(root->right){
                   digui(root->right,2*no+1);
               }
               if(root->left){
                   digui(root->left,2*no);
               }
                          
           }
       };
       ```

12. 235 二叉搜索树的最近公共祖先：给定2个结点地址，返回最近祖先的地址

    1. 挺有趣的题目，思考后发现，从上至下，最先满足某结点的值介于给定的2结点之间的值的结点就是这2点的最近祖先

    2. ``` c++
       class Solution {
       public:
           TreeNode* res=nullptr;
           TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
               int big,small;
               big=(p->val>=q->val)?p->val:q->val;
               small=(p->val<q->val)?p->val:q->val;
               digui(root,big,small);
               return res;
                      
           }
           void digui(TreeNode* root,int &big,int &small){
               if(!root)
                   return;
               if(root->val>=small&&root->val<=big){
                   res=root;
                   return;
               }           
               if(!res)
                   digui(root->left,big,small);
               if(!res)
                   digui(root->right,big,small);
           }
       };
       ```

13. 236 二叉树的最近公共祖先

    1. 因为是普通的二叉树，而不是搜索二叉树，所以思考普遍的算法。想到之前有道题，有个获得从根结点到所有叶子结点的路径的算法，所以能够使用它获得从根结点到2个目标结点的路径，然后在2条路径中最后1个相同的结点就是最近公共祖先。

    2. 还有如果已经找到了2条路径，那么就没必要继续递归寻找了，可以结束寻找过程了。

    3. ``` c++
       class Solution {
       public:
           vector<vector<TreeNode*>> vt;
           TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
               vector<TreeNode*> tmp;
               digui(root,tmp,p,q);
               int i;
               //注意必须先判断i<size
               for(i=0;(i<vt[0].size())&&i<vt[1].size()&&vt[0][i]==vt[1][i];i++);
               return vt[0][i-1];       
               
           }
           void digui(TreeNode* root,vector<TreeNode*>&tmp,TreeNode* p, TreeNode* q){
       
               if(!root||vt.size()==2)
                   return;
               tmp.push_back(root);
               if(root==p){
                   vt.push_back(tmp);
               }
               if(root==q){
                   vt.push_back(tmp);
               }
               digui(root->left,tmp,p,q);
               digui(root->right,tmp,p,q);
               tmp.pop_back();
       
           }
       };
       ```

14. 437 路径总和|||（未完成）：题意为在二叉树中寻找路径（必须从上之下）的数量，使得路径上结点值之和为目标sum

    1. ``` c++
       //纯恶心人，调试到最后，还让我超时，草
       class Solution {
       public:
           vector<vector<int>> vt1;
           vector<vector<TreeNode*>> vt3;
           int pathSum(TreeNode* root, int sum) {
               vector<int> tmp;
               vector<TreeNode*>tmp2;
               tmp2.push_back(nullptr);
               digui(root,tmp,tmp2);
               vector<vector<int>> vt2;//累积和
               multimap<TreeNode*,TreeNode*> mp;
               int num=0;
               if(!root)
                   return 0;
               if(!root->left&&!root->right){
                   if(root->val==sum)
                       return 1;
                   else
                       return 0;
               }
       
               for(int n=0;n<vt1.size();n++){
                   int sum2=0;
                   vector<int> tmp2;
                   tmp2.push_back(sum2);//每一个累积和首元素设置为0，方便接下来的遍历
                   for(int m=0;m<vt1[n].size();m++){
                       sum2+=vt1[n][m];
                       tmp2.push_back(sum2);
                   }
                   vt2.push_back(tmp2);
               }
       
               for(int n=0;n<vt2.size();n++){
                   for(int q=0;q<vt2[n].size()-1;q++){
                       for(int p=q+1;p<vt2[n].size();p++){
       
       
                           if(sum==(vt2[n][p]-vt2[n][q])){
                               num++;
                               
       
                               auto it = mp.find(vt3[n][q]);
                               int i = 0, len = mp.count(vt3[n][q]),tmp=num;
                               for (;i < len; ++i,++it) {
                                   if(it->second==vt3[n][p]){
                                       num--;
                                       break;
                                   }
                                       
                               }
                               if(tmp==num){
                                   mp.insert(make_pair(vt3[n][q],vt3[n][p]));
                               }
       
                           }
       
       
                       }
                   }
               }
       
               return num;
       
               
           }
           void digui(TreeNode* root,vector<int> &tmp,vector<TreeNode*>&tmp2){
               if(!root)
                   return;
               tmp.push_back(root->val);
               tmp2.push_back(root);
               if(!root->left&&!root->right){
                   vt1.push_back(tmp);
                   vt3.push_back(tmp2);
               }
       
               digui(root->left,tmp,tmp2);
               digui(root->right,tmp,tmp2);
       
               tmp.pop_back();
               tmp2.pop_back();
           }
       };
       ```

    2. ``` c++
       //双层递归
       //最清晰的递归方法，思路也很明了，对于每一个结点，都以该结点为根节点，向下搜索连通根节点（当前结点）的路径和为目标sum。
       class Solution {
       public:
           int res=0;
           int pathSum(TreeNode* root, int sum) {
               if(!root)
                   return 0;
               //以当前结点为根结点，搜索从根节点出发的目标路径和
               digui(root,sum);
               //遍历所有结点
               pathSum(root->left,sum);
               pathSum(root->right,sum);
               return res;
           }
           void digui(TreeNode* root,int sum){
               if(!root)
                   return;
               if(sum==root->val)
                   res++;
               digui(root->left,sum-root->val);
               digui(root->right,sum-root->val);
           }
       };
       ```

    3. ``` c++
       //前缀和！顶级方法
       //思路归纳：前缀和思想+直系传递思想(将直系祖先数据递归给子结点)+遍历结点思想
       //思路：对于每个结点，用前缀和计算从根结点到该结点的结点中，有多条路径以该结点结尾满足路径和为sum
       class Solution {
       public:
           int res=0;
           unordered_map<int,int>mp;//mp表示在当前结点的直系路径中，前缀和与数量的映射
           int pathSum(TreeNode* root, int sum) {
               //0与1的映射，特指当前前缀和与sum相同时，res增加1
               mp[0]=1;
               digui(root,sum,0);
               return res;
           }
           void digui(TreeNode* root,int sum,int psum){
               if(!root)
                   return;
               //将当前结点值加入前缀和
               psum+=root->val;
       		//此步为关键步骤：假设x=psum-sum，x的映射存在，说明在直系结点中，至少有1个结点的前缀和为x，因为psum-x=sum，所以有从前缀和x的结点到本结点的路径和即为sum，而路径的数量也为前缀和为x的路径数量，所以res需要增加mp[x]
               if(mp.find(psum-sum)!=mp.end()){
                   res+=mp[psum-sum];
               }
               //因为需要继续到子节点进行递归，所以需要对当前节点前缀和映射数量增加1
               mp[psum]++;
               //进入子节点的递归
               digui(root->left,sum,psum);
               digui(root->right,sum,psum);
            //因为上面的语句结束了对子节点的递归，所以本结点处理完毕后，将会处理兄弟结点或父节点的兄弟结点，而这2种情况都不是本结点的直系情况，需要将之前自增的映射数量清除。
               mp[psum]--;
           }
       };
       ```
       
    4. 

    

15. 450 删除二叉搜索树中的结点：

    1. ``` c++
       //极度朴实丑陋，但思路正确，可以在多个方面改进
       //思路：在BST中删除某个结点，可以把该结点的前继或后序结点的值赋到该结点上，然后递归删除那个前继结点，递归边界为该结点为叶子结点，可以之际额删除
       class Solution {
       public:
           TreeNode* res=nullptr;
           TreeNode* Father=new TreeNode;
           int tar;
           TreeNode* deleteNode(TreeNode* root, int key) {
               TreeNode* tmp=Father;
               Father->left=root;
               Father->val=0;
               tar=key;
               digui(root,Father);
               if(!res)
                   return root;
               delete_(res,Father);
               return tmp->left;
               
           }
           //找目标结点就嗯找，没利用BST性质
           void digui(TreeNode* root,TreeNode* father){
               if(!root||res)
                   return;
               digui(root->left,root);
               if(root->val==tar){
                   res=root;
                   Father=father;
               }
               digui(root->right,root);
           }
           //不管干啥都要找父节点，这个有father变量太烦了，得想办法简化
           void delete_(TreeNode*root,TreeNode* father){
               //有很多雷同代码，应该可以合并
               if(root->left){
                   TreeNode* tmp=root->left;
                   TreeNode* ftmp=root;
                   while(tmp->right){
                       ftmp=tmp;
                       tmp=tmp->right;
                   }
                       
                   root->val=tmp->val;
                   delete_(tmp,ftmp);
               }
               else if(root->right){
                   TreeNode* tmp=root->right;
                   TreeNode* ftmp=root;
                   while(tmp->left){
                       ftmp=tmp;
                       tmp=tmp->left;
                   }
                       
                   root->val=tmp->val;
                   delete_(tmp,ftmp);
               } 
               else{
                   if(father->left==root)
                       father->left=nullptr;
                   else
                       father->right=nullptr;
               }
           }
       };
       ```

    2. ``` c++
       class Solution {
       public:
           //函数的作用：在以root为根结点的树中，删除key结点，并返回根结点，即返回值为新的根节点
           TreeNode* deleteNode(TreeNode* root, int key) {
               //根节点不存在
               if(!root)
                   return root;
       		//key在左子树
               if(key<root->val){
                   root->left=deleteNode(root->left,key);
                   return root;
               }
       		//key在右子树
               if(key>root->val){
                   root->right=deleteNode(root->right,key);
                   return root;
               }
       		//key为根节点
               if(key==root->val){
                   //key为叶子结点
                   if(!root->left&&!root->right)
                       return nullptr;
                   
       			//key左右子结点都存在
                   if(root->left&&root->right){
                       //tmp为root的后继
                       TreeNode* tmp=root->right;
                       while(tmp->left)
                           tmp=tmp->left;
                       
                       root->val=tmp->val;
                       root->right=deleteNode(root->right,tmp->val);
                       return root;
                   }
                  	//key只有左孩子
                   if(root->left)
                       return root->left;
                   //key只有右孩子
                   if(root->right)
                       return root->right;
                   
               }
        
              return root;
               
           }
       
          
       };
       ```
```
       
    
16. 543 二叉树的直径：给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过也可能不穿过根结点。

    1. ``` c++
       //思路一般都是这样的：求每个节点深度，然后左右子树深度之和即为该点的直径。但是可以不需要分2步做，可在遍历求每个节点深度的同时，计算该点的直径，并与max相比
       class Solution {
       public:
           int max1=0; 
           int diameterOfBinaryTree(TreeNode* root) {
               dep(root);
               return max1;
           }
           int dep(TreeNode* root){
               if(!root)
                   return 0;
       
               int left=dep(root->left),right=dep(root->right);
               //tmp表示以tmp为转折点的树的直径，为左右子树深度之和
               int tmp=left+right;
               if(tmp>max1)
                   max1=tmp;
               tmp=max(right,left)+1;
               return max(right,left)+1;
           }
       };
```

17. 572 另一树的子树：

    1. ``` c++
       //一般思路，写出判断2树是否相等的函数和在树中寻找key节点的函数
       class Solution {
       public:
           vector<TreeNode*>vt;
           bool isSubtree(TreeNode* s, TreeNode* t) {
               find(s,t->val);
               for(int i=0;i<vt.size();i++){
                   if(isSame(vt[i],t))
                       return true;
               }
               return false;
           }
           void find(TreeNode* root,int key){
               if(!root)
                   return ;
               if(root->val==key){
                   vt.push_back(root);
       
               }       
               find(root->left,key);
               find(root->right,key);   
           }
           bool isSame(TreeNode*a,TreeNode*b){
               if(!a&&!b)
                   return true;
               if((a&&!b)||(!a&&b)||(a->val!=b->val))
                   return false;
               return isSame(a->left,b->left)&&isSame(a->right,b->right);
           }
       };
       ```

    2. ``` c++
       //没有find函数，直接开始遍历结点进行判断
       class Solution {
       public:
           bool isSubtree(TreeNode* s, TreeNode* t) {
               if(isSame(s,t))
                   return true;
               if(!s&&!t)
                   return true;
               if(!s||!t)
                   return false;
               return isSubtree(s->left,t)||isSubtree(s->right,t);
       
           bool isSame(TreeNode*a,TreeNode*b){
               if(!a&&!b)
                   return true;
               //因为之前处理了2节点全为空的情况，所以如果某个节点为空，另一个节点一定不为空。
               if(!b||!a||(a->val!=b->val))
                   return false;
               return isSame(a->left,b->left)&&isSame(a->right,b->right);
           }
       
       };
       ```

18. 652 寻找重复的子树：

    1. ``` c++
       class Solution {
       public:
           
           multimap<int,TreeNode*>mp;
           vector<TreeNode*> findDuplicateSubtrees(TreeNode* root) {
               bianli(root);
               vector<TreeNode*> res;
               for(auto i=mp.begin();i!=mp.end();){
                   auto it=i;
                   for(int n=0;n<mp.count(i->first)-1;n++,it++){
                       int flag=0;
                       auto it2=it;
                       it2++;
                       for(int l=1;l<mp.count(i->first);l++,it2++){
                           if(isSame(it->second,it2->second)){
                               flag=1;
                               res.push_back(it->second);
                               break;
                           }
       
                       }
                       if(flag==1)
                           break;
                   }
                   int cnt=mp.count(i->first);
                   for(int k=0;k<cnt;k++){
                       i++;
                   }
       
               }
               return res;
           }
           bool isSame(TreeNode* a,TreeNode* b){
               if(!a&&!b)
                   return true;
               if(!a||!b)
                   return false;
               return isSame(a->left,b->left)&&isSame(a->right,b->right);
           }
           void bianli(TreeNode* root){
               if(!root)
                   return;
               mp.insert(make_pair(root->val,root));
               bianli(root->left);
               bianli(root->right);
           }
       };
       ```

    2. ``` c++
       class Solution {
       public:
           vector<TreeNode*> findDuplicateSubtrees(TreeNode* root) {
               vector<TreeNode*> result;
               unordered_map<string,int> mp;
               helper(root,result,mp);
               return result;
           }
           string helper(TreeNode*root,vector<TreeNode*>&result,
                         unordered_map<string,int>&mp)
           {
               string str;
               if(!root) return "#";
               str = to_string(root->val) + ' ' + helper(root->left,result,mp) + ' '+helper(root->right,result,mp);
               if(mp[str] == 1) result.push_back(root);
               mp[str]++;
               return str;
           }
       };
       ```
    

## 栈（stack）

1. 



## 向量（vector）

1.  1 两数之和：

   1. ``` c++
      //2循环太简单了，用哈希
      ```

2.  27 移出元素：原地移出某个数组中所有val值元素

    1.  ``` c++
        //独创的，挺有意思的移出方式
        //每次都是向next索引中赋值，因为next是一定小于等于i的，所以想next中赋值不会覆盖未处理的数据
        class Solution {
        public:
            int removeElement(vector<int>& nums, int val) {
                int next=0;
                for(int i=0;i<nums.size();i++){
                    if(nums[i]!=val){
                        nums[next++]=nums[i];
                    }
                }
                return next;
        
            }
        };
        ```

3.  31 下一个排列：将该数组转为字典序的下一个排列

    1.  从该题中，我理解了字典序的意义

    2.  ``` c++
        class Solution {
        public:
            void nextPermutation(vector<int>& nums) {
                int tmp,i,p;
                //从vector末尾开始，找到第一个从右至左不是递增的元素
                //因为如果从右至左递增的话，说明该数组是字典序最大的,找到了某个元素非递增，即表里从该元素开始，从左至右的元素序列不是字典序最大，就可以将这个序列转为字典序的下一个序列
                for(i=nums.size()-2;i>=0;i--){
                   if(nums[i]>=nums[i+1])
                        continue;
                    else
                        break;
                
                    
                }
                //还有一种情况就是遍历了所有元素没找到非递增的，说明该数组就是字典序最大的，根据题意转为字典序最小的即可
                if(i==-1){
                    for(int x=0,l=nums.size()-1;x<l;x++,l--){
                        tmp=nums[x];
                        nums[x]=nums[l];
                        nums[l]=tmp;
                    }
                    return;
                }
        
                //已找到非递增元素tmp，接下来要在其右侧的序列中，找到某个最小的元素nums[p]，使得nums[p]大于tmp，然后再狡猾nums[p]和tmp，再将右侧的序列转为从左至右递增的序列
                tmp=nums[i];
                for(p=i+1;p<nums.size();p++){
                    if(nums[p]<=tmp)
                        break;
                }
        		//交换nums[p]和tmp
                p=p-1;
                nums[i]=nums[p];
                nums[p]=tmp;
        
                //将右侧的序列转为从左至右递增的序列
                //将i+1到nums.size()-1排为升序
                for(int x=i+1,l=nums.size()-1;x<l;x++,l--){
                    tmp=nums[x];
                    nums[x]=nums[l];
                    nums[l]=tmp;
                }
                return ;
        
            }
        
        
        };
        ```

4.  33 搜索旋转排序数组

    1.  ``` c++
        class Solution {
        public:
            int search(vector<int>& nums, int target) {
                int l=0,r=nums.size()-1,mid;
                while(l<=r){
                    mid=l+((r-l)>>1);
                    if(nums[mid]==target)
                        return mid;
                    //l到mid为递增序列
                    if(nums[mid]>=nums[l]){
                        //target在l和mid间
                        if(target>=nums[l]&&target<nums[mid])
                            r=mid-1;
                        else
                            l=mid+1;
                    }
                    //mid到r为递增序列
                    else{
                        //target在mid到r间
                        if(target>nums[mid]&&target<=nums[r])
                            l=mid+1;
                        else
                            r=mid-1;
        
                    }
                }
                return -1;
            }
        };
        ```

5.  34 在排序列表中查找元素的起止

    1.  ``` c++
        //二分法找到其中一个值，然后左右延伸，感觉虽然简化了些，但还是n的时间复杂度
        class Solution {
        public:
            vector<int> searchRange(vector<int>& nums, int target) {
                vector<int> res;
                int l=0,r=nums.size()-1,mid,now;
                while(l<=r){
                    mid=l+((r-l)>>1);
                    if(nums[mid]==target)
                        break;
                    if(target>nums[mid])
                        l=mid+1;
                    else
                        r=mid-1;
                }
                if(l>r){
                    res.push_back(-1);
                    res.push_back(-1);
                    return res;
                }
                for(now=mid-1;now>=0&&nums[now]==target;now--);
                res.push_back(now+1);
                for(now=mid+1;now<nums.size()&&nums[now]==target;now++);
                res.push_back(now-1);
                return res;
                
            }
        };
        ```

    2.  ``` c++
        //这种写法加深了我对二分法的理解
        //两次二分法分别找到目标起止
        class Solution {
        public:
            vector<int> searchRange(vector<int>& nums, int target) {
                vector<int> res {-1, -1};
                if(nums.empty()) return res;
                int begin = 0, end = nums.size() - 1;
               
                while(begin < end){
                    int mid = (begin + end) / 2;
                    //注意此处是end=mid，因为mid的求法问题，会使得mid偏向左边，所以end=mid不会陷入死循环
                    if(nums[mid] >= target) end = mid;
                    else begin = mid + 1;
                    
                }
                if(nums[begin] !=  target) return res;
                res[0] = begin;
                end = nums.size();
                while(begin < end){
                    int mid = (begin + end) / 2;
                    //注意此处是begin=mid+1,因为mid求法，mid偏向左边，所以如果写成begin=mid，则可能陷入死循环，所以写出begin=mid+1,但是这样写必定会导致begin到end的区间错过target，但因为二分法的性质，结果最终会趋向于target，也就是最终begin=end=target的最大索引+1。
                    if(nums[mid] <= target) begin = mid+1;
                    else end = mid;
                }
                res[1] = begin - 1;
                return res;
            }
        };
        ```

6.  39 组合之数

    1.  ``` c++
        //回溯法
        class Solution {
        public:
            vector<vector<int>> res;
            vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
                vector<int> tmp;
                digui(candidates,tmp,0,target);
                return res;
            }
            void digui(vector<int>& candidates,vector<int>& tmp,int index,int target){
                if(target<0)
                    return;
                if(target==0)
                    res.push_back(tmp);
        
                while(index<candidates.size()){
                    tmp.push_back(candidates[index]);
                    digui(candidates,tmp,index,target-candidates[index]);
                    tmp.pop_back();
                    index++;
                }
            }
        };
        ```

7.  40 组合总和||：与1相比，数组中存在重复元素，且每个元素只能使用一次，其结果也不能相同组合（排列不同也不行）

    1.  ``` c++
        class Solution {
        public:
            vector<vector<int>> res;
            vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
                vector<int> tmp;
                sort(candidates.begin(),candidates.end());
                digui(candidates,tmp,0,target);
                return res;
            }
            void digui(vector<int>& candidates,vector<int>& tmp,int index,int target){
                if(target<0)
                    return;
                if(target==0){
                    auto it=find(res.begin(),res.end(),tmp);
                    if(it==res.end())
                        res.push_back(tmp);
                }
                    
        
                if(index<candidates.size()){
                    tmp.push_back(candidates[index]);
                    digui(candidates,tmp,index+1,target-candidates[index]);
                    tmp.pop_back();
                    digui(candidates,tmp,index+1,target);
                }
            }
        };
        ```

    2.  ``` c++
        //整体思路是通过深度优先遍历所有情况，但同时通过某种方式筛选了多余的情况，（但还是没弄懂如何筛选的）
        //每个元素第一次选择的时候没有进行筛选
        //重复元素的第一个元素进入深度搜索后就已经出现了足够多的情况
        //相比于对任意一个元素选择是或否的搜索，dfs能够在搜索的同时去重
        void dfs(int i,int sum,int tar,vector<int>& candidates,vector<vector<int>>& ans,vector<int> &now){
                if(sum == tar){
                    ans.push_back(now);
                }
                if(sum < tar){
                    for(; i<candidates.size(); i++){
                        now.push_back(candidates[i]);
                        dfs(i+1,sum+candidates[i],tar,candidates,ans,now);
                        //通过此步筛选
                        while(i<candidates.size()-1 && candidates[i]==candidates[i+1])  i++;		//避免选取相同的数
                        now.pop_back();
                    }
                }
            }
            vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
                sort(candidates.begin(),candidates.end());	
                vector<vector<int>> ans;
                vector<int> now;
                dfs(0,0,target,candidates,ans,now);
                return ans;
            }
        ```

8.  53 最大子序和：返回最长连续的元素和

    1.  ``` c++
        //经典动态规划 
        vector<int> dp(nums.size());
                int max=nums[0];
                dp[0]=nums[0];
                for(int i=1;i<nums.size();i++){
                    dp[i]=(dp[i-1]+nums[i])>nums[i]?(dp[i-1]+nums[i]):(nums[i]);
                    max=(max>dp[i])?max:dp[i];
                }
                return max;
        ```

9.  56 合并区间

    1.  ``` c++
        //独特思路：先将区间按照起点从小达到排序
        class Solution {
        public:
            //注意：作为sort的参数的函数cmp，必须为静态函数static
            static bool cmp(const vector<int> &a,const vector<int> &b){
                return a[0]<b[0];
            }
            vector<vector<int>> merge(vector<vector<int>>& intervals) {
                vector<vector<int>> res;
                sort(intervals.begin(),intervals.end(),cmp);
                int begin=intervals[0][0],end=intervals[0][1];
                for(int i=1;i<intervals.size();i++){
                    if(intervals[i][0]<=end){
                        end=(intervals[i][1]>end)?intervals[i][1]:end;
                    }
                    else{
                        vector<int> tmp{begin,end};
                        res.push_back(tmp);
                        begin=intervals[i][0];
                        end=intervals[i][1];
                    }
                }
                vector<int> tmp{begin,end};
                res.push_back(tmp);
                return res;
        
            }
        
        
        };
        ```

10.  59 螺旋矩阵||

     1.   ``` c++
         //比较规范的的写法
         class Solution {
         public:
             vector<vector<int>> generateMatrix(int n) {
                 int up=0,down=n-1,left=0,right=n-1,now=1,i;
                 vector<vector<int>> res(n,vector<int>(n,0));
                 while(1){
                     for(i=left;i<=right;i++){
                         res[up][i]=now++;
                     }
                     up++;
                     if(up>down)
                         break;
                     for(i=up;i<=down;i++){
                         res[i][right]=now++;
                     }
                     right--;
                     if(right<left)
                         break;
                     for(i=right;i>=left;i--){
                         res[down][i]=now++;
                     }
                     down--;
                     if(down<up)
                         break;
                     for(i=down;i>=up;i--){
                         res[i][left]=now++;
                     }
                     left++;
                     if(left>right)
                         break;
                 }
                 return res;
             }
         };
         ```

11.  62 不同路径

     1.  ``` c++
         //再找一个避免溢出的组合方法
         class Solution {
         public:
             int res=0;
             int uniquePaths(int m, int n) {
                 //动态规划，vt[i][p]的意义表示从起点到（i,p）的路径数量之和
                 vector<vector<int>> vt(m,vector<int>(n,1));
                 for(int i=1;i<m;i++){
                     for(int p=1;p<n;p++){
                         //dp状态转移方程，到某一点的路径数量和等于其上方点和左方点路径数量之和
                         vt[i][p]=vt[i-1][p]+vt[i][p-1];
                     }
                 }
                 return vt[m-1][n-1];
                 
             }
         
         };
         ```

12.  最标准二分查找

     1.  ``` c++
                 while(begin < end){
                     int mid = (begin + end) / 2;
                     //注意此处是end=mid，因为mid的求法问题，会使得mid偏向左边，所以end=mid不会陷入死循环
                     if(nums[mid] >= target) end = mid;
                     else begin = mid + 1;
                     
                 }
         		//此方法不是在循环过程中找到target，而是最终left==right等于target的索引
                 if(nums[begin] !=  target) return res;
         ```

13.  78 子集：给定一组**不含重复元素**的整数数组 *nums*，返回该数组所有可能的子集（幂集）。

     1.  ``` c++
         //我第一想到的方法
         //dfs
         class Solution {
         public:
             vector<vector<int>> res;
             vector<vector<int>> subsets(vector<int>& nums) {
                 vector<int> tmp;
                 huisu(nums,0,tmp);
                 return res;
             }
             void huisu(vector<int>& nums,int now,vector<int> tmp){
                 if(now==nums.size()){
                     res.push_back(tmp);
                     return;
                 }
         
                 tmp.push_back(nums[now]);
                 huisu(nums,now+1,tmp);
         
                 tmp.pop_back();
                 huisu(nums,now+1,tmp);
             }
         };
         ```

     2.  ``` c++
         //动态规划：123的子集为在12的子集基础上，再在12子集元素中加上3（所以每加1个数字，子集为原来的2倍）
         class Solution {
         public:
             vector<vector<int>> subsets(vector<int>& nums) {
                 vector<vector<int>> res;
                 vector<int> temp;
                 res.push_back(temp);//初始化
                 for(int i=0; i<nums.size(); i++)
                 {
                     for(auto x:res){
         				x.push_back(nums[i]);
                         res
                     }
                     /*int st = res.size();
                     for(int j=0; j<st; j++)
                     {
                         temp = res[j];
                         temp.push_back(nums[i]);
                         res.push_back(temp);
                     }*/
                 }
                 return res;
             }
         };
         ```

     3.  ``` c++
         //回溯算法
         class Solution {
         public:
             void dfs(vector<vector<int>> &res, vector<int> &temp, vector<int> &nums, int k)
             {
                 res.push_back(temp);
                 for(int i=k; i<nums.size(); i++)
                 {
                     temp.push_back(nums[i]);
                     dfs(res, temp, nums, i+1);
                     temp.pop_back();
                 }
             }
             vector<vector<int>> subsets(vector<int>& nums) {
                 vector<vector<int>> res;
                 vector<int> temp;
                 dfs(res, temp, nums, 0);
                 return res;
             }
         };
         ```

14.  79 单词搜索

     1.  ``` c++
         //我的朴实方法
         class Solution {
         public:
             int m,n;
             bool exist(vector<vector<char>>& board, string word) {
                 m=board.size(),n=board[0].size();
                 for(int q=0;q<m;q++){
                     for(int w=0;w<n;w++){
                         if(board[q][w]==word[0]){
                             board[q][w]=' ';
                             if(digui(board,q,w,word,1))
                                 return true;
                             board[q][w]=word[0];
                         }
                     }
                 }
                 return false;
             }
         
             bool digui(vector<vector<char>>& board,int q,int w,string word,int now){
                 if(now==word.size())
                     return true;
                 bool r1=false,r2=false,r3=false,r4=false;
                 if(q-1>=0&&board[q-1][w]==word[now]){
                     board[q-1][w]=' ';
                     r1=digui(board,q-1,w,word,now+1);
                     board[q-1][w]=word[now];
                     if(r1)
                         return r1;
                 }
         
                 if(q+1<m&&board[q+1][w]==word[now]){
                     board[q+1][w]=' ';
                     r2=digui(board,q+1,w,word,now+1);
                     board[q+1][w]=word[now];
                     if(r2)
                         return r2;
                 }
         
                 if(w-1>=0&&board[q][w-1]==word[now]){
                     board[q][w-1]=' ';
                     r3=digui(board,q,w-1,word,now+1);
                     board[q][w-1]=word[now];
                     if(r3)
                         return r3;
                 }
         
                 if(w+1<n&&board[q][w+1]==word[now]){
                     board[q][w+1]=' ';
                     r4=digui(board,q,w+1,word,now+1);
                     board[q][w+1]=word[now];
                     if(r4)
                         return r4;
                 }
         
         
                 return r1||r2||r3||r4;
         
             }
         };
         ```

15.  81 搜索旋转排序数组||

     1.  ``` c++
         //太恶心了，还是没理解含重复元素的二分法，代码太丑陋了，面向试例编程？
         class Solution {
         public:
             bool search(vector<int>& nums, int target) {
                 int left=0,right=nums.size()-1;
                 if(nums.size()==0)
                     return false;
                 while(left<right){
                     int mid=(left+right)>>1;
                     if(nums[mid]==target)
                         return true;
         
                     if(nums[mid]==nums[left]){
                         if(mid==left){
                             if(nums[left]==target)
                                 return true;
                             if(nums[right]==target)
                                 return true;
                             return false;
                         }
                         else{
                             left++;
                             continue;
                         }
                     }
                     //旋转点在mid右侧
                     if(nums[mid]>nums[left]){
                         //target在mid左侧
                         if(target>=nums[left]&&target<nums[mid]){
                             right=mid;
                         }
                         else{
                             left=mid+1;
                         }
         
                     }
                     //旋转点在mid左侧
                     else{
                         //target在mid右侧
                         if(nums[mid]<target&&target<=nums[right]){
                             left=mid+1;
                         }
                         else{
                             right=mid;
                         }
                     }
                 }
                 if(nums[left]==target)
                     return true;
                 else  
                     return false;
             }
         
                
         
         };
         ```

     2.  ``` c++
         class Solution {
         public:
             bool search(int A[], int n, int target) {
                 if (n == 0) return false;
                 int left = 0, right = n - 1;
                 while (left <= right) {
                     int mid = (left + right) / 2;
                     if (A[mid] == target) return true;
                     else if (A[mid] < A[right]) {
                         if (A[mid] < target && A[right] >= target) left = mid + 1;
                         else right = mid - 1;
                     } else if (A[mid] > A[right]){
                         if (A[left] <= target && A[mid] > target) right = mid - 1;
                         else left = mid + 1;
                     } else --right;
                 }
                 return false;
             }
         };
         ```

     3.  

     

16.  84 柱状图中最大的矩形

     1.  ``` c++
         //执行用时：1920 ms 在所有 C++ 提交中击败了5.20%的用户内存消耗：8 MB, 在所有 C++ 提交中击败了94.77%的用户
         //太慢了，说明方法有问题
         //遍历每一个元素，并且以该元素值作为矩形的宽度，左右延拓记录此最大面积
         class Solution {
         public:
             int largestRectangleArea(vector<int>& heights) {
                 int max=0,l,r;
                 for(int n=0;n<heights.size();n++){
                     for(l=n-1;l>=0&&heights[l]>=heights[n];l--);
                     for(r=n+1;r<heights.size()&&heights[r]>=heights[n];r++);
                     max=max>(heights[n]*(r-l-1))?max:heights[n]*(r-l-1);
                     for(;(n+1<heights.size())&&heights[n]==heights[n+1];n++);
                 }
                 return max;
                 
             }
         };
         ```

     2.  ``` c++
         //单调栈
         class Solution {
         public:
             int largestRectangleArea(vector<int>& heights) {
                 int n=heights.size();
                 stack<int> index;
                 int area=0;
                 for(int i=0;i<heights.size();i++){
                     if(index.empty()||heights[index.top()]<heights[i]) index.push(i);
                     else{
                         while(!index.empty()&&heights[index.top()]>=heights[i]){
                             int tmp=index.top();
                             index.pop();
                             int length=0;
                             if(index.empty()) length=i;
                             else length=i-index.top()-1;
                             area=max(area,length*heights[tmp]);
                         }
                         index.push(i);
                     }
                 }
                 while(!index.empty()){
                     int tmp=index.top();
                     index.pop();
                     int length=0;
                     if(index.empty()) length=n;
                     else length=n-index.top()-1;
                     area=max(area,length*heights[tmp]);
                 }
                 return area;
             }
         };
         
         ```

17.  



