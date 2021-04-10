# 第三章 java基本结构

## 基本规则

1. 类的命名遵循驼峰原则：每个单词的首字母大写

2. 文件名.java，文件名必须与类名相同

3. 基本框架

   1. ``` java
      //Test.java
      public class Test{
          //主函数必须在主类下，且与下一行所示一致
      	public static void main(String[] args){
      		System.out.println("Hello world");
          }
      }
      ```

4. 打印

   1. ``` java
      //println是自动换行
      System.out.println("Hello world");
      //print不自动换行
      System.out.print("Hello world");
      ```





## 数据类型

1. 整型：java中整型都是有符号的，不存在无符号数（unsigned）
   1. int
   2. short
   3. long：长整型数值有一个后缀L或l，例如400000L
   4. byte
   5. ![image-20210222073736611](D:\Typora\note\java基础语法.assets\image-20210222073736611.png)
2. 浮点类型：
   1. float：float类型浮点数要有后缀F或f，如6.3F
   2. ==double==：一般都使用double，默认的浮点数都是double，如6.3
   3. ![image-20210222074046184](D:\Typora\note\java基础语法.assets\image-20210222074046184.png)
3. char类型：最好不要使用，而使用长度为1的String代替
   1. 字面量值需要用单引号，如 ‘A’
   2. ![image-20210222074811187](D:\Typora\note\java基础语法.assets\image-20210222074811187.png)
4. boolean类型
   1. 布尔值false和true，整型和布尔值之间不能相互转换





## 数学函数

1. 开平方根

   1. ``` java
      //开平方根
      Math.sqrt(x);
      //幂运算
      Math.pow(x,a);
      ```

2. ![image-20210222075837710](D:\Typora\note\java基础语法.assets\image-20210222075837710.png)

3. 在文件顶部加**import** **static** **java.lang**.**Math**.*  ，就不需要在后面的方法前加Math.



## 类型转换

1. 强制类型转换

   1. ``` java
      double x=9.6;
      //和C语言中一样，这种强转是直接截断小数部分
      int nx=(int)x
      //Math.round（x）是将X转为最接近的整数
      int nx=(int)Math.round(x)
      ```

   2. ![image-20210222091251978](D:\Typora\note\java基础语法.assets\image-20210222091251978.png)



## 字符串

1. java没有内置的字符串类型，只有String类（因为是类，所以S是大写）

2. 获得子字符串：String s2=s1.substring(0,3)。s2是s1的索引0到3的字符串（左闭右开）

3. 字符串拼接：+加号。注意：s=“123”+4，也是正确的写法，int类型的4会自动转换为字符串，这适用任何一个对象

4. String类对象是不可变字符串，即某个函数不能改变该对象的值，只能生产一个新的对象

5. 判断2个字符串是否相等：s1.equals(s2)

   1. 不区分大小写：s1.equalsIgnoreCase(s2)
   2. 不能使用==

6. 字符串长度：s.length();

7. 访问x索引处的代码单元：s.charAt(x)

8. 按字典序比较2字符串：s1.compareTo(s2)。s1小于s2返回负数，等于返回0，大于返回正数

9. 转换大小写：s1.toLowerCase()，s1.toUpperCase()

10. 创建字符串

    1. ``` java
       //定义StringBuilder类
       StringBuilder builder=new StringBuilder();
       //向字符串中添加内容
       builder.append(asd);
       //使用toString生成最终String
       String res=builder.toString();
       ```

11. 创建格式化字符串: String.format

    1. ``` java
       String message = String.format("Hello, %s. Next year, you'll be %d", name , age);
       ```

    2. 



## 输出输入

1. 输入

   1. ``` java
      import java.util.*;
      Scanner in=new Scanner(System.in);
      //输入一行
      String s1=in.nextLine();
      //输入1个字符串(以空格分隔的单词)
      String s1=in.next();
      //输入1个整数
      int x=in.nextInt();
      //输入1个浮点数
      double y=in.nextDouble();
      ```

2. 格式化输出

   1. ``` java
      //和C中相同
      //保留2位小数
      System.out.printf("%.2f",x);
      ```

   2. ![image-20210222101736860](D:\Typora\note\java基础语法.assets\image-20210222101736860.png)



## 大数值

1. 使用BigInteger和BigDecimal来处理整数和浮点数精度不够的问题

   1. ``` java
      import java.math.*;
      //定义大数对象
      BigInteger a=BigInteger.valueOf(10000);
      //不能使用正常的+ *处理大数对象
      BigInteger c=a.add(b);
      BigInteger d=a.multiply(b);
      ```

   2. 返回大整数：valueOf(long x)

   3. 加法：add()

   4. 减法：subtract()

   5. 乘法：multiply

   6. 除法：divide

   7. 模：mode

   8. 比较：compareTo



## 数组

1. 定义数组 int[] a;

   1. ``` java
      //表示a是一个数组，数组中每个元素都是int,并且用new创建的100个int大小的空间
      int[] a=new int[100];
      ```

2. 获得数组元素个数：a.length.(注意：length是成员变量，不是方法名)

3. 初始化数组

   1. ``` java
      int[] a={1,2,3};
      ```

4. 数组排序

   1. ``` java
      //对数组x进行默认从小到大排序
      Arrays.sort(x);
      ```

5. 数组赋值

   1. ``` java
      //将数组x中所有元素赋值为1
      Arrays.fill(x,1);
      ```

6. 判断数组是否相等

   1. ``` java
      Arrays.equals(a,b);
      ```

7. 定义二维数组

   1. ``` java
      int[][] x=new int[2][2];
      ```



# 第四章 对象与类



## 类

1. 封装：将数据和方法组合再一个包中，并对对象的使用者隐藏数据的实现方式

2. 封装的关键在于绝对不能让a类中的方法直接访问b类中的数据，而只能让a类通过==b类的方法==来访问b类中的数据

3. 构造器：

   1. 构造器的使用一定伴随则new
   2. 构造器名与类名同名
   3. 每个类可以有多个构造器
   4. 构造器没有返回值

4. 

   



## 对象

1. 对象的三个特征：

   1. 行为
   2. 状态
   3. 表示

2. 因为封装性，对象的状态（成员变量）必须通过其方法才会改变

3. 对象与对象变量

   1. ``` java
      //x是对象变量，new Date()产生了对象并返回了其引用，所以对象变量存储的只是该对象的引用
      Date x=new Date();
      ```

   2. 对象变量其实就是C++中对象的指针

4. 自定义类

   1. ``` java
      class ClassName{
      	int a;
          public int fun1(int a,int b){
      		return a+b;
          }
          //与类名同名的方法即构造器，注意：构造器无返回值
          public ClassName(int x){
      		a=x;
          }
      }
      //使用构造器,初始化对象
      //构造器的使用和new绑定！
      ClassName tmp=new ClassName(1);
      ```

5. 在每个方法中，this表示该方法的隐式变量，即调用该方法的对象

6. 每个类中的static是该类的==类域==，即使该类有100个实例对象，也同时==共享==该类域，该类域只有1个，而不是100个。因为类域属于类，所以即使没有实例对象，该类域也是能够使用的

7. 静态方法不能访问对象的实例域，但能访问自身类的静态域和显式输入的参数

8. 工厂方法：类的静态方法，返回1个对象

9. java总是==按值传递==，但因为传递对象时，传递的是对象的==引用==的拷贝，通过引用仍然能够访问并修改该对象。

   1. 一个对象，包括对象和引用，引用是能够访问对象的一个变量

10. 重载：一个类中可以有多个同名函数，但这些同名函数必须有不同数量或不同类型或不同顺序的参数

11. 如果类中没有构造器，则系统会提供一个默认无参构造器；如果类中至少有一个构造器，但不是无参，则使用无参构造器会报错

12. 



## 包

1. 将类放入包中

   1. ``` java
      //在类文件的顶端加了下面这一行，就将该文件中定义的所有类都加入到了该包中（之后就可以在其他文件中通过import使用该包）
      package com.horstiann.corejava;
      class Test{
      
      }
      ```

2. 将包中的文件放到与完整的包名匹配的子目录中。例如，com.horstmann.corejava 包中的所有源文件应该被放置在子目录 com/horstmann/corejava

3. 包作用域：private表明该变量或方法只能被该类访问，public表示可以被任意类使用；其他没有表明的，则可以被同包内的所有类访问

4. 注释

   1. ``` java
      以/**开始
      以*/结尾
      ```

   2. 





# 第五章 继承

### 子类和超类

1. 定义子类

   1. ``` java
      public class Manager extends Employee
      {
      //添加新的方法和域
      }
      ```

2. 子类的性质

   1. 子类不能直接访问超类中的私有域（尽管子类继承了超类的私有域，但仍然不是子类自己类的域）
   
3. 特定调用超类的方法（即使子类有同名的方法）,使用super关键字

   1. ``` java
      super.getSalary();
      ```

4. 子类的继承可以增加域，或者覆盖或增加方法，但不能删减域或方法

5. 子类的构造器

   1. ``` java
      public Manager(String name, double salary, int year, int month, int day) {
      	//因为子类不能访问父类的私有域，所以要调用父类的构造器完成对父类私有域的初始化
          super(name, salary, year, month, day);
      	bonus = 0; 
      }
      ```

6. 多态：超类变量可以引用子类对象，但是该超类变量只能使用超类的域和方法，==不能使用子类特别的域和方法==

   1.  ``` java
      Emlpyee e = new Manager();
      ```

7. 受保护访问

   1. private:只有自己类才能访问
   2. proteced：子类能访问超类的内容
   3. 没有修饰符：能被同包内的类访问
   4. public：能被所有类访问

### Object

1. Object是所有类的始祖，如果某个类没有明确继承哪个类，则默认继承Object
2. 常用方法
   1. equals（）：用于检测一个对象是否等于另一个对象
   2. getClass().getName():获得类名
   3. toString()：输出表示对象值的字符串
      1. x对象与一个字符串通过“+”连接，就会==自动调用x对象的toString方法==来代替x对象
      2. Object默认的toString方法是打印类名+散列码

### 泛型数组列表

1. ArrayList

   1. 定义

      1. ``` java
         ArrayList<typename> arr=new ArrayList<>();
         ```

   2. add(x)：末尾插入x

   3. add（i,x）：在索引为i处插入x，并使后面的元素向后移1位

   4. remove（i）:删除索引为i处的元素，并使后面的元素向前移动1位

   5. get（i）：返回索引为i处的元素

   6. size()

   7. 改变第i个元素的值为harry: staff.set(i,harry)

   8. toArray（a）：将ArrayList转为一个数组，该数组变量为a

   9. 



# 第九章 集合









# java实践笔记

1. string

   1. length():字符串长度

   2. 字符串转为int

      1. ``` java
         i = Integer.parseInt(s);
         ```

   3. int转为字符串

      1. ``` java
         String s = String.valueOf(i);
         ```

   4. 访问某个字符：charAt(n)

   5. 

2. ArrayList

   1. 定义

      1. ``` java
         ArrayList<Integer> qu=new ArrayList<>();
         ```

   2. 访问某个元素:get(n);

   3. 数组大小：size()

   4. 增加元素：add（n）,向后添加

   5. 在索引i出增加n元素：add(i,n)

   6. 删除i索引出元素：remove（i)

   7. 修改索引i处的元素为n：set(i,n);

   8. 泛型只能是包装类，不能是基本类，例如只能是Integer，不能是int

   9. 自定义排序：

      1. ``` java
         arr.sort();
         
         public int compareTo(Object o) {
             Student s = (Student) o;
             if (this.age > s.age) {
                 return 1;
             }
             else if (this.age < s.age) {
                 return -1;
             }
             else {
                 if (this.height >= s.height) {
                     return 1;
                 }
                 else {
                     return -1;
                 }
             }
         
         ```

      2. 

3. int

   1. 由于jdk1.5新特性自动装箱和拆箱，包装类与其简单类之间可以自由转换

   2. 转为Integer

      1. ``` java
         Integer A=Integer.valueOf(a);
         ```

   3. Integer转为int

      1. ``` java
         int a=A.intValue();
         ```

4. 数组 

   1. 定义

      1. ``` java
         int[][] arr=new int[2][2];
         ```

   2. 长度：arr.length;arr[0].length

   3. 整体赋值：Arrays.fill(arr, value);

5. HashSet：元素无序，没有重复元素的集合（元素只能是类，不能是基本类型）

   1. 定义

      1. ``` java
         HashSet<String> set = new HashSet<String>();
         ```

   2. 添加元素：set.add(x);

   3. 判断元素是否存在：set.contains(x)。在则返回true，不在返回false

   4. 删除元素：set.remove(x)

   5. 大小：set.size();

   6. 遍历：

      1. ``` java
         for(String i:set){
             System.out.println(i);
         }
         ```

   7. 









