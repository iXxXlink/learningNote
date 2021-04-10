## 贪心算法

1. 定义：保证每次操作都是局部最优，从而使最后得到的结果是全局最优

2. 分发糖果

   1. 老师想给孩子们分发糖果，有 N 个孩子站成了一条直线，老师会根据每个孩子的表现，预先给他们评分。

      你需要按照以下要求，帮助老师给这些孩子分发糖果：

      每个孩子至少分配到 1 个糖果。
      相邻的孩子中，评分高的孩子必须获得更多的糖果。
      那么这样下来，老师至少需要准备多少颗糖果呢？

   2. 贪心思路:所有孩子糖果个数初始化为1。从左至右遍历数组一次，如果右边的积分大于左边的积分，则右边的个数为左边个数加1；再从右至左遍历数组一次，如果左边的积分大于右边的积分，则左边的个数为当前个数和右边个数+1的最大值。（此方法的贪心思路在于，每次只考虑局部即相邻数的关系，积分大的人的个数只为相邻人的个数加1）

   3. ``` c++
      int candy(vector<int>& ratings) {
          vector<int> vt(ratings.size(),1);
          int res=0;
          for(int i=0;i<ratings.size()-1;i++){
              if(ratings[i]<ratings[i+1])
                  vt[i+1]=vt[i]+1;
          }
          res+=vt[ratings.size()-1];
          for(int i=ratings.size()-1;i>=1;i--){
              if(ratings[i-1]>ratings[i]){
                  vt[i-1]=max(vt[i-1],vt[i]+1);
              }
              res+=vt[i-1];
          }
          return res;
      }
      ```

3. 435 无重叠区间

   1. 给定一个区间的集合，找到需要移除区间的最小数量，使剩余区间互不重叠。

   2. 思路：将元素按照末区间从小到大排序，然后从左至右遍历，除去与前一个元素重叠的元素。（贪心思路：1、对于从左至右遍历而言，末结点越小，==留给其他区间的空间就越大==（贪的就是留给右侧区间的空间，2个区间取舍，取留给右侧其他区间更多空间的区间一定更好，对于前2个区间，如果末结点相同，取哪个区间都可以，之后的取不重叠的即可），越不容易重叠（同样的，按照起始结点排序，如果从右至左遍历，起始结点越大，越好））

   3. ``` c++
      class Solution {
      public:
          static bool cmp(const vector<int> &a,const vector<int>&b){
              return a[1]<b[1];
          }
          int eraseOverlapIntervals(vector<vector<int>>& intervals) {
              sort(intervals.begin(),intervals.end(),cmp);
              int size=intervals.size(),pre=0,res=0;
              for(int i=1;i<size;i++){
                  if(intervals[i][0]<intervals[pre][1]){
                      res++;
                  }
                  else{
                      pre=i;
                  }
              }
              return res;
      
      };
      ```

4. 452 用最少数量的箭引爆气球：即找出最少的点，使每一个区间都至少有1个点

   1. 思路：和前一题思路类似，先通过尾区间进行排序，此题的贪心之处在于：每次取点只取区间的尾结点，因为尾区间的点比该区间的所有其他点更靠近右侧的区间

   2. ``` c++
      class Solution {
      public:
          //注意：作为sort的参数函数cmp必须使用引用传参，速度最快！
          static bool cmp(const vector<int> &a,const vector<int> &b){
              return a[1]<b[1];
          }
          //这题的贪心之处在于每次射箭都设区间的末尾坐标
          int findMinArrowShots(vector<vector<int>>& points) {
              if(points.size()==0)
                  return 0;
              sort(points.begin(),points.end(),cmp);
              int pre=0,res=1;//pre表示某个射出弓箭的区间的尾坐标,
              for(int i=1;i<points.size();++i){
                  if(points[i][0]>points[pre][1]){
                      res++;
                      pre=i;
                  }
      
              }
              return res;
          }
      };
      
      ```

5. 763 划分字母区间：

   1. 贪心思路：此题求最多的区间，所以从左至右遍历时，需要按照起始区间排序

   2. ``` c++
      class Solution {
      public:
          static bool cmp(const vector<int>&a,const vector<int>&b){
              return a[0]<b[0];
          }
          vector<int> partitionLabels(string S) {
              vector<int> res;
              if(S.size()==0)
                  return res;
              vector<vector<int>> vt(26,vector<int>(2,-1));
              //删去不存在的字母元素
              vector<vector<int>> vt2;
              int left,right;
              for(int i=0;i<S.size();i++){
                  if(vt[S[i]-'a'][0]!=-1){
                      vt[S[i]-'a'][1]=i;      
                  }
                  else{
                      vt[S[i]-'a'][0]=i;
                      vt[S[i]-'a'][1]=i;
                  }
              }
              
              //删去vt中不存在的字母
              for(int i=0;i<vt.size();i++){
                  if(vt[i][0]!=-1){
                      vt2.push_back(vt[i]);
                  }
              }
              sort(vt2.begin(),vt2.end(),cmp);
      
              left=vt2[0][0];
              right=vt2[0][1];
              for(int i=1;i<vt2.size();i++){
                  if(vt2[i][0]<right){
                      right=max(right,vt2[i][1]);
                  }
                  else{
                      res.push_back(right-left+1);
                      right=vt2[i][1];
                      left=vt2[i][0];
                  }
              }
              res.push_back(right-left+1);
              return res;
      
      
      
      
      
          }
      };
      ```

6. 406 根据身高排序

   1. 先按身高从高到底排序，然后遍历vector，将当前元素插入res的people[now]\[1\]位置，原因：因为当前元素一定比之前插入的元素小，所以其第二个元素的意义就是前面比该元素高的数量，所以插入第二个元素的位置，符合题意。而又因为当前元素比插入位置后面的所有元素都小，所以对被插队的元素没有任何影响。

   2. ``` c++
      class Solution {
      public:
          static bool cmp(vector<int>& a, vector<int>& b)
          {
              if(a[0]==b[0])
              {
                  return a[1]<b[1];
              }
              else
              {
                  return a[0]>b[0];
              }
          }
          
          vector<vector<int>> reconstructQueue(vector<vector<int>>& people) 
          {
              int n=people.size();
              sort(people.begin(),people.end(),cmp);
              vector<vector<int>> res;
              for(int i=0;i<n;i++)
              {
                  res.insert(res.begin()+people[i][1],people[i]);
              }
              return res;
          }
      };
      ```

7. 665 非递减数列：给你一个长度为 `n` 的整数数组，请你判断在 **最多** 改变 `1` 个元素的情况下，该数组能否变成一个非递减数列。

   1. ``` c++
      class Solution {
      public:
          bool checkPossibility(vector<int>& nums) {
              int flag=0,pre=-1;
              for(int i=1;i<nums.size();i++){
                  if(nums[i-1]>nums[i]){
                      //需要分2种情况，nums[i]大于等于pre时，因为nums[i-1]>nums[i]，所以最贪要是nums[i]最小，即将nums[i-1]改为pre或nums[i]
                      //当nums[i]小于pre,要使nums[i]大于等于pre且大于等于nums[i-1]，nums最小为nums[i-1]
                      if(nums[i]<pre)
                          nums[i]=nums[i-1];
                      flag++;
                      if(flag==2)
                          return false;
                  }
                  pre=nums[i-1];
              }
      
              return true;
      
          }
      };
      ```



## 双指针

1. 双指针主要用于同一数组，分别指向不同元素，协同工作

   1. 遍历方向相同且不相交。也称为滑动窗口（被包围区域称为窗口）,经常用于区间搜索
   2. 遍历方向相反，则可以用来进行搜索（待搜索数组通常已排序）

2. 167 两数之和||-输入有序数组（同一数组，2指针逆向）

   1. 给定一个升序排列的有序数组，找到2个数的索引，使得这2个索引在数组中值的和等于目标值

   2. 思路：创建左右2个指针，如果当前2值大于目标值，则右指针自减，如果小于目标值，则左指针自增。如果相等，则退出，并返回这2索引。

   3. 证明：这左右指针为l,r，而真正答案的索引为L,R，那么因为l,r每次都是变化1，==所以l和r中一定有1个指针时先达到对应的L或R位置==，当l达到L时，因为r>R，l==L，所以总和大于目标和，r会一直减少直至R（r先达到R同理）

   4. ``` c++
      class Solution {
      public:
          vector<int> twoSum(vector<int>& numbers, int target) {
              int left=0,right=numbers.size()-1;
              while(left<right){
                  int sum=numbers[left]+numbers[right];
                  if(sum==target)
                      break;
                  if(sum>target)
                      right--;
                  else
                      left++;           
              }
              return vector<int>{left+1,right+1};
      
          }
      };
      ```

3. 88 合并两个有序数组（2个指针在2个数组，同向）

   1. 我之前做时，没有理解nums1数组空间足够时什么意思，使用的方式也很朴实，再创一个数组。当从头开始赋值可能会覆盖时，可以考虑从末尾开始赋值。

   2. ``` c++
          void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
              //因为由题目一直nums1空间足够，所以竟然可以从后面开始
              int l1=m-1,l2=n-1,now=m+n-1;
              while(l1>=0&&l2>=0){
                  if(nums1[l1]>=nums2[l2]){
                      nums1[now--]=nums1[l1--];
                  }
                  else{
                      nums1[now--]=nums2[l2--];
                  }
              }
              //甚至于连l1>=0的情况都不用考虑了，因为L2先用完时，l1等于now
              while(l2>=0){
                  nums1[now--]=nums2[l2--];
              }
      ```

4. 524 通过删除字母撇皮到字典里最长单词：给定一个字符串和一个字符串字典，找到字典里面最长的字符串，该字符串可以通过删除给定字符串的某些字符来得到。如果答案不止一个，返回长度最长且字典顺序最小的字符串。如果答案不存在，则返回空字符串。

   1. 双指针思想：应该体现在，判断s字符串中有没有不连续的d字符串，通过设置2个指针分别在字符串开头，遍历s字符串，当s中某字符与d当前字符相等时，d指针自增，结束遍历后，如果d指针指向d字符串末尾，则说明s字符串中含有d字符串

   2. ``` c++
      class Solution {
      public:
          string findLongestWord(string s, vector<string>& d) {
              vector<string> res;
              for(auto x:d){
                  int j=0;
                  for(int i=0;i<s.size();i++){
                      if(s[i]==x[j])j++;
                  }
                  if(j==x.size())
                      res.push_back(x);
              }
      
              if(res.size()==0)
                  return "";
              //此处的匿名函数很有意思，先按字符串长度从大到小排序，相同大小的直接比较a<b即是字典序从小到大排序（即默认排序a<b就是按字典序排序）
              sort(res.begin(),res.end(),[](auto &a,auto &b){
                  return a.size()>b.size() || a.size()==b.size()&&a<b;
              });
              return res[0];
          }
      
      };
      
      ```





## 二分查找

1. 二分查找：每次查找时，都将排除一半的待查序列
2. 关于区间划分的技巧
   1. 一般使用左闭右开，或左闭右闭
   2. 思考在最后一个区间内，只剩1个或2个元素时，是否会陷入死循环





## 常用排序算法

1. 快速排序：

   1. 一般用于找到第k大的数问题，时间复杂度O(n)

   2. ``` c++
      int quickSelection(vector<int>& nums, int l, int r) {
      	//l作为枢纽(第一个元素设置为枢纽？)，i是从左遍历指针，j是右遍历指针
          int i = l + 1, j = r;
          while (true) {
              //i指针一直向前移动，直至指向比枢纽大的点
              while (i < r && nums[i] <= nums[l]) {
              	++i;
              }
              //j指针一直向后移动，直至指向比枢纽小的点
              while (l < j && nums[j] >= nums[l]) {
              	--j;
          	}
              //循环退出条件
              if (i >= j) {
                  break; 
              }
              //交换ij指向的值，使得i又指向比枢纽小的点，而j依然指向比枢纽大的点
          	swap(nums[i], nums[j]);
          }
          //退出时，一定有j<=i，这是退出条件
          //且j指针一定小于枢纽，这是子循环退出条件,所以交换l，j，使得l左边的元素逗比l小，右边元素逗比l大
          swap(nums[l], nums[j]);
          return j;
      }
      ```

2. 桶排序：用以解决频次相关的排序

   1. 创建一个unordered_map\<int ,int\>mp（第一个元素表示次数，第二个元素表示是哪个元素）,遍历数组for(auto i:nums)，使++mp[i]。并且同时记录max_count

   2. 创建一个二维数组vecotor\<vector<int>\> vt,遍历mp，使得vt[mp[i]->second].push_back(mp[i]->first)。最终获得一个二维数组，其行数表示出现的次数，每行的元素表示出现了行数次数的元素

   3. ``` c++
      vector<int> topKFrequent(vector<int>& nums, int k) {
          unordered_map<int, int> counts;
          int max_count = 0;
          for (const int & num : nums) {
          	max_count = max(max_count, ++counts[num]);
          }
          vector<vector<int>> buckets(max_count + 1);
          for (const auto & p : counts) {
          	buckets[p.second].push_back(p.first);
          }
          vector<int> ans;
          for (int i = max_count; i >= 0 && ans.size() < k; --i) {
          	for (const int & num : buckets[i]) {
          		ans.push_back(num);
          		if (ans.size() == k) {
          			break; 
                  } 
              } 
          }
          return ans;
      }
      ```

3. 回溯法：在递归深度搜索到某一结点时，如果发现该节点（及其子节点）不符合所求时，回退到原来的节点，并且将在目前节点修改的状态还原

   1. 需要一个数据结构保留从根节点到当前节点状态信息（且该数据结构传递引用）
   2. 发现该节点不符合要求时，及时回退到祖先节点，并将数据结构还原

4. 排列：

   1. ``` c++
      //这种全排列的时间复杂度是
      class Solution {
      public:
          vector<vector<int>> res;
          
          vector<vector<int>> permute(vector<int>& nums) {
              vector<int> tmp;
              vector<bool> flag(nums.size(),false);
              dfs(nums,tmp,flag);
              return res;
          }
          void dfs(vector<int>& nums,vector<int>& tmp,vector<bool>& flag){
              if(tmp.size()==nums.size()){
                  res.push_back(tmp);
                  return;
              }
              
              for(int i=0;i<nums.size();++i){
                  if(flag[i]==false){
                      flag[i]=true;
                      tmp.push_back(nums[i]);
                      dfs(nums,tmp,flag);
                      tmp.pop_back();
                      flag[i]=false;
                  }
              }
          
          }
      };
      ```

5. 组合：

   1. ``` c++
      class Solution {
      public:
          int x,y;
          vector<vector<int>> res;
          vector<vector<int>> combine(int n, int k) {
              x=n;
              y=k;
              vector<int> vt(n);
              vector<bool> flag(n,false);
              vector<int>tmp;
              for(int i=0;i<n;i++){
                  vt[i]=i+1;
              }
              digui(vt,tmp,0);
              return res;
      
          }
          
          void digui(vector<int> &vt,vector<int> &tmp,int index){
              if(tmp.size()==y){
                  res.push_back(tmp);
                  return;
              }
              for(int i=index;i<x;i++){
                  tmp.push_back(vt[i]);
                  digui(vt,tmp,i+1);
                  tmp.pop_back();
              }
          }
      };
      ```
   
6. 934 最短的桥

   1. ``` c++
      class Solution {
      public:
          //第一个dfs找到一个岛屿，将其所有1变为2，并且将其边缘的0收入队列中
          //以第一次收集的队列为基础，进行BFS第一次接触到1时，层数即为最短距离
          int m,n;
          queue<pair<int,int>>qu;
          int shortestBridge(vector<vector<int>>& A) {
              m=A.size();
              n=A[0].size();
              int flag=0,lev=0;
              for(int i=0;i<m;i++){
                  for(int q=0;q<n;q++){
                      if(A[i][q]==1){
                          dfs(A,i,q);
                          flag=1;
                          break;
                      }
                  }
                  if(flag==1)
                      break;
              }
      
              while(!qu.empty()){
                  int size=qu.size(),x,y;
                  lev++;
                  pair<int,int> tmp;
                  for(int i=0;i<size;i++){
                      tmp=qu.front();
                      qu.pop();
                      x=tmp.first;
                      y=tmp.second;
                      if(x>0){
                          if(A[x-1][y]==0){
                              qu.push(make_pair(x-1,y));
                              A[x-1][y]=2;
                          }
                          else if(A[x-1][y]==1)
                              return lev;
                      }
                      if(x<m-1){
                          if(A[x+1][y]==0){
                              qu.push(make_pair(x+1,y));
                              A[x+1][y]=2;
                          }
                          else if(A[x+1][y]==1)
                              return lev;
                      }
                      if(y>0){
                          if(A[x][y-1]==0){
                              qu.push(make_pair(x,y-1));
                              A[x][y-1]=2;
                          }
                          else if(A[x][y-1]==1)
                              return lev;
                      }
                      if(y<n-1){
                          if(A[x][y+1]==0){
                              qu.push(make_pair(x,y+1));
                              A[x][y+1]=2;
                          }
                          else if(A[x][y+1]==1)
                              return lev;
                      }
      
                  }
      
              }
              return lev;
      
      
          }
          void dfs(vector<vector<int>>& A,int x,int y){
              if(A[x][y]==0){
                  qu.push(make_pair(x,y));
                  A[x][y]=2;
                  return;
              }
              if(A[x][y]==2)
                  return;
      
              A[x][y]=2;
              if(x>0)
                  dfs(A,x-1,y);
              if(x<m-1)
                  dfs(A,x+1,y);
              if(y>0)
                  dfs(A,x,y-1);
              if(y<n-1)
                  dfs(A,x,y+1);
          }
      };
      ```

7. 








## 动态规划

1. 