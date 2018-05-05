# autodownload

根据同一个二维码识别当前系统（iOS或Android），跳转对应App应用市场或下载界面

本文测试地址：https://xiaze.github.io/autodownload/index.html

一、使用场景

开发了一款App，包括iOS及Android版，到了推广阶段，准备生成二维码让用户扫码下载，那这个二维码该怎么生成？iOS及Andorid各自生成一个二维码让用户区分下载？当然这种方式是可行的，但却增加了用户的使用成本！那是不是有一种方式可以通过一个二维码使手机自动下载相应App包？

本文主要讲的就是如何在没有个人/公司网站的情况下，利用同一个二维码自动识别手机系统（Android/iOS）跳转不同的下载页面。

二、解决方案

我们可以编写一个html网页，通过js识别当前终端属性，根据相应终端属性重定向到相应下载界面。然后将该html网页上传至网站，生成该网页链接的二维码图片，用户扫描二维码会自动进入对应下载界面。

三、代码部分：index.html

(见工程文件）

在使用的时候将相应链接替换即可

四、制作二维码

本人推荐两个制作二维码的网址

草料二维码：http://cli.im

联图网：http://www.liantu.com

![image](https://github.com/xiaze/autodownload/raw/master/image/jianting.png)
如果没有个人/公司网站可以上传上述html网页文件，请继续浏览以下内容；如果已经有了相应网站，那么你可以直接制作相应二维码了。

五、将网页文件上传至github，配置相关选项实现网页自动跳转

1. 注册一个github账号：https://github.com

2. 创建一个工程

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_1.png)

3. 填写相关工程信息创建工程

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_2.png)

4. 进入工程页面复制工程的git链接

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_3.png)

5. 利用git工具（本例使用Mac系统下的Tower）clone工程

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_4.png)

6. 进入本地工程文件夹可以看到工程已经被clone下来了，不过目前只有一个初始的说明文件

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_7.png)

7. 将之前建好的html文件导入本地工程文件夹

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_8.png)

8. 进入Tower填写相关信息并提交文件到github库中

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_9.png)
![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_10.png)

9. 刷新github工程网页可以看到文件已经提交成功

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_11.png)

10. 点击Settings进入工程设置页面

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_12.png)

11. 滚动到GitHub Pages项

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_13.png)

12. 选择分支并保存

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_14.png)

13. 保存完后可以看到工程对应的网址链接

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_16.png)

14. 直接在该链接后拼接之前创建的html文件即可生成最终链接，用最终链接生成的二维码就可实现自动跳转的功能了。欢迎大家通过图中二维码下载简听App哦，不过目前只有iOS版。(简听 - 懒人听网页听小说的神器)

![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_17.png)

本文测试地址：https://xiaze.github.io/autodownload/index.html
