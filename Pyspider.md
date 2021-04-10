## pyspider

1.  crawl_config={},此属性用以配置定义 Headers、设置代理等，配置之后全局生效。
2.  on_start()方法是爬取入口，在爬到对应url页面后将结果交给index_page()方法解析
3.  crawl() 方法生成一个爬取请求，其参数包括url，和解析结果的方法，返回给解析方法的结果是一个Response 对象
4.  如果更改了配置后，建议重启pyspider
5.  return 就是最终返回的结果？
6.  for each in response.doc('a[href^="http"]').items()：将response对象使用doc方法后就可以使用css选择器（items()，表示将字典转为列表返回）（==这一步就是先获得便签==）
7.  点击enable css selector helper 再点击需要爬取的内容就可以获得相应的css选择器
8.  pyquery的css选择器
    1.  doc('#container .list li')//查找id(用#)为container，class(用.)为list，标签为li的对象
    2.  each.attr.href：each标签选择了href属性，并将其返回
    3.  a.text：获得标签a中的文本
9.  对于ajax信息，在network中筛选出xhr数据，找到真正的请求url



















