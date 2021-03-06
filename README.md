
# 1. 概述

[book118-downloader 下载](https://github.com/wxynihao/book118-downloader/releases)

这是一个用于下载book118可预览文档的下载器（暂不支持ppt和收费才能预览的文件）。

该项目基于java开发，使用httpclient进行下载，使用itex进行pdf的生成。

# 2. 使用手册

0. 下载解压

1. 双击`run.bat`即可运行该软件，如果不能运行请检查是否已安装jre 8+（Java Runtime Environment）

2. 文档编号是预览页链接中最后的数字如：https://max.book118.com/html/2017/0611/113657916.shtm ，文档编号就是113657916。

3. 输入编好后需要获取下载链接，文件页数越多等待越长，请耐心等待，开始下载后会有进度提示。

4. 下载完成的文件存放在out文件夹中。

如有问题，可至[github](https://github.com/wxynihao/book118-downloader) 查看Bug Fix，或提交Issue

# 3. 实现逻辑

做完没多久在freebuf看到有其他人的实现，做的没我好，所以自己也写了一篇，编辑答应帮我调格式我就没要稿费了。
[《另一种绕过限制下载论文的思路》](http://www.freebuf.com/articles/web/167359.html)

该下载器的原理是通过模拟通过网页预览，获取文档的全部预览图片，然后将图片转换为pdf实现。

实现逻辑主要围绕网站的两个js函数展开，这两个函数在resources/temp.js中。
openFull用于获取预览起始页，getNextPage用于获取后面的页。通过这两个函数就可以获取到一个文档的全部预览图片的地址。

# 4. Bug Fix
* 2020/10/18

book118的下载逻辑变更，当前已修复支持；除核心解析、下载功能，其余功能由其他小伙伴提供，我没有测试，所以不保证能用。

* 2019/03/13

修复 [issue#3](https://github.com/wxynihao/book118-downloader/issues/3)   [下载](jar)

* 2018/11/17

修复某些时候URL拼接不正确导致的下载失败（156906400 下载失败）

* 2018/11/11

修改为异步下载，不再需要等待获取全部页面链接

* 2018/9/14

优化提示信息的显示  [网盘下载](https://pan.baidu.com/s/1RyRZP0mSFHhWT_M9iYKZjQ)

* 2018/9/12

修改viewHost为根据返回值获取  [网盘下载](https://pan.baidu.com/s/1waRfVY62YtDzh7BIusyP8g)

* 2018/9/7

基于hutool重构代码

* 2018/6/26

修改结束字符变成Over后，获取页数不能停止，导致下载失败的问题。
