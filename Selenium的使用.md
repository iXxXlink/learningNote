# Selenium的使用

1. 声明浏览器对象

   ``` python
   from selenium import webdriver
   
   browser = webdriver.Chrome()
   ```

2. 访问页面

   ``` python
   browser.get('https://www.taobao.com')
   ```

3. 一般访问页面后需要过一段时间才能加载全部ajax，所以需要等待

   ``` python
   time.sleep(20)
   ```

4. 浏览器对象browser可以向输入框中输入，首先需要获得输入框

   ``` python
   input_first = browser.find_element_by_id('q')
   input_second = browser.find_element_by_css_selector('#q')
   input_third = browser.find_element_by_xpath('//*[@id="q"]')
   ```

5. Selenium 还提供了通用方法 find_element()

   ``` python
   input_first = browser.find_element(By.ID, 'q')
   # find_element_by_id(id) 二者等价
   ```

6. 使用bs4的css选择器选择元素

   ``` python
   from bs4 import BeautifulSoup
   soup = BeautifulSoup(html, 'lxml')
   # 选择所有title标签
   soup.select("title")
   # 选择body标签下的所有a标签
   soup.select("body a")
   
   # 选择a标签，其类属性为mysis的标签
   soup.select("a.mysis")
   
   # 选择a标签，其id属性为link1的标签
   soup.select("a#link1")
   
   # 选择a标签，其属性中存在myname的所有标签
   soup.select("a[myname]")
   
   #获得文本
   s[0].get_text()
   
   #获得属性
   s[0].get("class")  
   ```

7. pyquery的使用

   ``` python
   from pyquery import PyQuery as pq
   #将源码转为pq对象
   doc = pq(html)
   #css选择器(自顶向下选择，可出现类名、id名、标签名)
   print(doc('#container .list li'))
   
   #遍历li,需要在选择到的列表后+items()
   lis=doc('li').items()
   #再遍历输出每个元素
   for li in lis:
       print(li)
   #获得标签中的属性
   doc.attr('href')
   #获得文本
   doc.text()
   ```

   

8. 执行JavaScript，例如拉下进度条到最底部

   ``` python
   browser.execute_script('window.scrollTo(0, document.body.scrollHeight)')
   ```

9. 获取属性（先选中节点，在获取属性）

   ``` python
   logo = browser.find_element_by_id('zh-top-link-logo')
   logo.get_attribute('class')
   ```

10. 获得文本值

    ``` python
    input = browser.find_element_by_class_name('zu-top-add-question').text
    ```

    

