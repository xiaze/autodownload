# autodownload
根据同一个二维码识别当前系统（iOS或Android），跳转对应App应用市场或下载界面
一、使用场景

开发了一款App，包括iOS及Android版，到了推广阶段，准备生成二维码让用户扫码下载，那这个二维码该怎么生成？iOS及Andorid各自生成一个二维码让用户区分下载？当然这种方式是可行的，但却增加了用户的使用成本！那是不是有一种方式可以通过一个二维码使手机自动下载相应App包？

本文主要讲的就是如何在没有个人/公司网站的情况下，利用同一个二维码自动识别手机系统（Android/IOS）跳转不同的下载页面。

二、解决方案

我们可以编写一个html网页，通过js识别当前终端属性，根据相应终端属性重定向到相应下载界面。然后将该html网页上传至网站，生成该网页链接的二维码图片，用户扫描二维码会自动进入对应下载界面。

三、代码部分：index.html

<!DOCTYPE HTML>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<title>美食街 - 厨房菜谱大全</title>
<script type="text/javascript">
// 获取终端的相关信息
var Terminal = {
// 辨别移动终端类型
platform : function(){
var u = navigator.userAgent, app = navigator.appVersion;
return {
// android终端或者uc浏览器
android: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1,
// 是否为iPhone或者QQHD浏览器
iPhone: u.indexOf('iPhone') > -1 ,
// 是否iPad
iPad: u.indexOf('iPad') > -1
};
}(),
// 辨别移动终端的语言：zh-cn、en-us、ko-kr、ja-jp...
language : (navigator.browserLanguage || navigator.language).toLowerCase()
}

// 根据不同的终端，跳转到不同的地址
var theUrl = 'https://itunes.apple.com/app/id1247266869';
if(Terminal.platform.android){//安卓端
document.write('抱歉，“美食街 - 厨房菜谱大全”暂时没有安卓版APP!');
//theUrl = 'https://itunes.apple.com/app/id1247266869';
//location.href = theUrl;
} else {
if(Terminal.platform.iPhone){//iPhone端
theUrl = 'https://itunes.apple.com/app/id1247266869';
}else if(Terminal.platform.iPad){//iPad端
// 还可以通过language，区分开多国语言版
switch(Terminal.language){
case 'en-us'://iPad英文版APP Store地址
theUrl = 'https://itunes.apple.com/app/id1247266869';
break;
case 'ko-kr'://iPad韩语版APP Store地址
theUrl = 'https://itunes.apple.com/app/id1247266869';
break;
case 'ja-jp'://iPad日文版APP Store地址
theUrl = 'https://itunes.apple.com/app/id1247266869';
break;
default://iPad默认APP Store地址
theUrl = 'https://itunes.apple.com/app/id1247266869';
}
}

location.href = theUrl;
}

</script>
</head>
<body>
<!--
 
 -->
</body>
</html>
在使用的时候将相应链接替换即可

四、制作二维码

本人推荐两个制作二维码的网址

草料二维码：http://cli.im
联图网：http://www.liantu.com
![image](https://github.com/xiaze/autodownload/raw/master/image/美食街二维码.png)
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

14. 直接在该链接后拼接之前创建的html文件即可生成最终链接，用最终链接生成的二维码就可实现自动跳转的功能了。欢迎大家通过图中二维码下载美食街App哦，不过目前只有iOS版。
![image](https://github.com/xiaze/autodownload/raw/master/image/Snip20170804_17.png)

本文测试地址：https://xiaze.github.io/autodownload/index.html
