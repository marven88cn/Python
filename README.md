# Python
Python简单爬虫实现
# Python
Python简单爬虫实现
### 一.什么是爬虫
  一段自动抓取互联网信息的程序
  ![这里写图片描述](http://img.blog.csdn.net/20171214095233879?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast) 
### 二.爬虫的价值
互联网数据，为我使用
![这里写图片描述](http://img.blog.csdn.net/20171214095518600?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 三.简单爬虫架构
![这里写图片描述](http://img.blog.csdn.net/20171214095721592?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 四.Python简单爬虫架构动态运行流程
![这里写图片描述](http://img.blog.csdn.net/20171214100537239?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 五.URL管理器
#### 1.管理待抓取URL集合和已抓取URL集合
    -- 防止重复抓取，防止循环抓取
    ![这里写图片描述](http://img.blog.csdn.net/20171214100822535?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
 ####   2.实现URL管理器(三种方式 内存，关系数据库，缓存数据库)
![这里写图片描述](http://img.blog.csdn.net/20171214101204509?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 六.Python爬虫网页下载器简介
将互联网上的URL对应的网页下载到本地的工具
![这里写图片描述](http://img.blog.csdn.net/20171214101500288?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
#### python有哪几种网页下载器（urllib2   requests）
![这里写图片描述](http://img.blog.csdn.net/20171214101703299?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 七. python爬虫urllib2下载网页的三种方法
#### 1.最简洁的方法
```python
import urllib2
#直接请求
response = urllib2.urlopen('http://www.baidu.com')
#获取状态吗，如果是200 表示获取成功
print response.getcode()
#读取内容
cont = response.read()
```
#### 2. 添加data 、http header

```python
import urllib2
# 创建Request对象
request = urllib2.Request(url)
# 添加数据
request.add_data('a','1')
#添加http的header
request.add_header('User-Agent','Mozilla/5.0')
#发送请求获取数据
response = urllib2.urlopen(request)
```
#### 3.添加特殊情景的处理器
```python
import urllib2,cookielb
#创建cookie容器
cj = cookielib.CookieJar()
#创建1个opener
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
#创建urllib2安装opener
urllib2.install_opener(opener)
#使用带有cookie的urllib2访问网页
response = urllib2.urlopen('http://www.baidu.com')
```
### 八.python爬虫urllib2实例代码
```python

import urllib2
import cookielib
url ="http://www.baidu.com"

print '第一种方法'
response1 = urllib2.urlopen(url)
print response1.getcode()
print len(response1.read())

print '第二种方法'
# 创建Request对象
request = urllib2.Request(url)

#添加http的header
request.add_header('User-Agent','Mozilla/5.0')
#发送请求获取数据
response2 = urllib2.urlopen(request)
print response2.getcode();
print len(response2.read())

print '第三中方法'
cj = cookielib.CookieJar()
opener= urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
urllib2.install_opener(opener)
response3 = urllib2.urlopen(url)
print response3.getcode()
print len(response3.read())
```
#### 执行结果
![这里写图片描述](http://img.blog.csdn.net/20171214104633565?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
#### 九.网页解析器（正则表达式，html.parser,BeautifulSoup,lxml）
正则表达式 属于模糊解析
 html.parser ,BeautifulSoup,lxml属于结构化解析
 ![这里写图片描述](http://img.blog.csdn.net/20171214105312831?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 十.BeautifulSoup简介安装
#### 1.Beautiful Soup是python第三方库,用于从html或xml中提取数据，官网网址:http://www.crummy.com/software/BeautifulSoup/
#### 2.安装
a.查看是否安装
```python
import bs4
print bs4
```
结果报错 ImportError: No module named bs
b.打开终端
先装pip （终端）输入命令：sudo easy_install pip

安bs4 输入命令：pip install beautifulsoup4

出现错误 
OSError: [Errno 13] Permission denied:

输入命令：sudo easy_install beautifulsoup4

这时把bs装到了Mac系统自带了Python2.7

把beautifulsoup4装到Python3

输入命令：pip3 install beautifulsoup4
#### 3.语法
![这里写图片描述](http://img.blog.csdn.net/20171214111201851?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![这里写图片描述](http://img.blog.csdn.net/20171214111431917?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
代码
1.创建beautifulSoup对象
```python
from bs4 import BeautifulSoup
# 根据HTML网页字符串创建BeautifulSoup对象
soup = BeautifulSoup(
    html_doc,            #HTML文档字符串
    'html.parser'        #HTML解析器
    from_encoding='utf-8'#HTML文档的编码
)

```
2.搜索节点
```python
# 方法： find_all（name,attrs,string）
#查找所有标签为a的节点
soup.find_all('a')
#查找所有标签为a，连接符合/view/123.html形式的节点
soup.find_all('a',href='/view/123.html')
#查找所有标签为div class为abl 文字为python节点
soup.find_all('div',class_ ='abc',string='python')
```
3.访问信息
```python
# 得到节点：<a href='1.html'>Python</a>
# 获取查找到的节点的标签名称
node.name
# 获取查找到的a接单的href属性
node['href']
#查找到a节点的连接文字
node.get_text()
```
4.实例
```python
# coding:utf-8
from bs4 import BeautifulSoup

html_doc = """
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">...</p>
"""
soup = BeautifulSoup(html_doc, 'html.parser', from_encoding='utf-8')

print '获取所有链接'
links = soup.find_all('a')
for link in links:
    print link.name,link['href'],link.get_text()
 
 
print '获取lacie的链接'
link_node = soup.find('a',href='http://example.com/lacie')
print link_node.name,link_node['href'],link_node.get_text()


print '正则匹配'
link_node2 = soup.find('a',href=re.compile(r"ill"))
print link_node2.name,link_node2['href'],link_node2.get_text()

print '获取p段落文字'
link_node3 = soup.find('p',class_='title')
print link_node3.name,link_node3.get_text()
```
运行结果
![这里写图片描述](http://img.blog.csdn.net/20171214120318575?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMTE5MDY4Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)






 





    
    

