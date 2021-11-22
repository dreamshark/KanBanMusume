看板娘涉及Live2D技术，简单来说就是用许多连续的图像和建模在2D上做出动态的效果，有兴趣可以自行上网了解，效果如下

![录制_2021_08_15_16_56_36_841](http://etherealdreamfuture.com/wp-imgs/录制_2021_08_15_16_56_36_841-1629020488533.gif)

接下来是在WordPress搭建的网站上添加看板娘的方法

> **本文学习自该博客**
>
> https://blog.csdn.net/THMAIL/article/details/105932140

> **首先去下载看板娘相关文件**
>
> https://github.com/ixixii/KanBanMusume

将下载的看板娘相关文件（live2d文件夹）上传到该目录下

随后在服务器上找到WordPress站点目录，如笔者的是/www/wwwroot/[站点文件名]

在目录底下找到 wp-content/themes/[WordPress使用的主题名称]/header.php

在`<head>`和`</head>`之中添加以下代码


```html
<!--Live2D show start-->
<link rel="stylesheet" href="http://etherealdreamfuture.com/wp-content/myPlugins/live2d/css/live2d.css" />
<script type="text/javascript" src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.js"></script>
<!--Live2D show end-->
```

在目录底下找到 wp-content/themes/[WordPress使用的主题名称]/footer.php

在`</body>`之前添加以下代码

```html
<div id="landlord">
 <div class="message" style="opacity:0"></div>
 <canvas id="live2d" width="280" height="250" class="live2d"></canvas>
 <div class="hide-button">隐藏</div>
 <div class="switch-button">换装</div>
</div>
 
<script type="text/javascript">
 var message_Path = '/live2d/'
 var home_Path = 'http://etherealdreamfuture.com' //此处修改为你的域名
</script>
<script type="text/javascript" src="/wp-content/myPlugins/live2d/js/live2d.js"></script>
<script type="text/javascript" src="/wp-content/myPlugins/live2d/js/message.js"></script>
<script type="text/javascript">
 var index = Math.ceil(Math.random()*37)
 //index表示服装编号，此处表示随机切换服装
 loadlive2d("live2d", "/wp-content/myPlugins/live2d/model/pio/model_"+index+".json");
</script>
```

其中`index`表示服装编号，取值范围是1-37，服装具体样式可在 live2d/model/pio/textures 中查看

![image-20210815173730516](http://etherealdreamfuture.com/wp-imgs/image-20210815173730516.png)

可以自行对服装样式进行简单的修改，如笔者不想要翅膀，则在PS里对png图片进行编辑，将翅膀部分删去即可。

> **没有翅膀的该看板娘版本相关文件可以从这里下载**
>
> https://github.com/dreamshark/KanBanMusume

