*本来想写写PhaserV2东西,能把原来落灰的代码抖一抖,写文之前看了看官网发现V3在今年终于出了正式版,就决定把V2的内容换成学习V3的过程.笔者能力有限,写出来的东西不敢称之为"教程",我就称之为"日记"



(官方LOGO)

-PhaserV3是什么?
Phaser官网:http://www.phaser.io PhaserV3版文档:https://github.com/photonstorm/phaser3-docs(坑爹是还没有在线文档,得自己下)
PhaserV3是Phaser最新的大版本,在2018年2月13日正式发布,代码几乎全部重写(就是V2版的东西V3全不能用啦),摆脱了对Pixi的依赖,有了更多新的特性

-为什么选择Phaser
在国内可能选择白鹭或者cocos2D作为web游戏开发的更多,但是phaser在世界上是绝对受过各国开发者们考验,它的简单易用非常受独立游戏界的欢迎,Ludam Dare,Steam等地方越来越常见其身影.如果你喜欢想试着做游戏并想选择在世界上大家都喜欢框架来制作,可以选择phaser来入坑 
-BALABALA全是废话,撸个游戏?
那就走一个?
国际惯例,先按最简单的来,什么node什么ES6什么webpack都不管,直接引文件开搞

1.首先建立一个项目文件夹

如果你没有前端开发经验,建议在这里下载一个文本编辑器https://www.sublimetext.com/3,无限免费试用


键盘上按下Ctrl+N(新建文件),输入index.html,然后按下Ctrl+S(保存),保存到刚才建立的文件下
index.html通常是网站的默认入口,所以我们也这么命名

2.引入phaser
然后我们要把基本的html内容填充上,并引入phaser文件
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <!-- 这里是设置页面在浏览器的显示方式,感兴趣的可以百度 -->
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <title>
    一个Phaser游戏!
  </title>
  <meta name="description" content="做一个Phaser的游戏">
  <!-- 这里是页面样式 -->
  <style>
  * {
    margin: 0;
    padding: 0;
  }

  html,
  body {
    background: #000;
    overflow: hidden;
    -ms-touch-action: none;
    touch-action: none;
  }
  </style>
</head>

<body>
  <!-- 在这里在线引入phaser -->
  <script src="https://cdn.jsdelivr.net/gh/photonstorm/phaser@3.8.0/dist/phaser.min.js"></script>
  <script>
  // 这里开始写代码!
  // 创建一个Phaser实例
  var game = new Phaser.Game()
  </script>
</body>

</html>
双击点开index.html,右键选择'检查/检查元素',在新弹出的窗口中如果你看到这个

     Phaser v3.8.0 (WebGL | Web Audio)  https://phaser.io

恭喜你,你已经成功引用Phaser!

-那么啰嗦了这么多,那么可以写游戏了吗!
-那当然是
不行

因为现在是通过直接点击index.html的方式打开页面,此时url地址的开头是file://,浏览器出于安全策略,会使得Phaser无法读取本地的静态资源(比如音频,图片文件等)

要让我们精心准备的游戏素材可以使用上,我们需要通过访问http://xxx的方式来访问本页面
因此我需要一个


3.建立一个本地Web服务器
也许你听说过phpStudy,我们正需要的一个就是这样的东西
