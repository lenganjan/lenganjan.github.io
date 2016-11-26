---

title: 如何搭建Hexo博客，加上Yilia 主题。
---
几年前有使用过Google的blogger写过一段时间博客，不过后来渐渐懒惰了。最近工作遇到问题查找资料时，发现一些牛人把一些技术上难题的解决方法，以及自己所学得的技术，用Blog记录。觉得这是个不错的想法，一直有用word记录的习惯，不过Blog漂亮的书写，清晰的结构，配上图片，给人更美的感觉。不仅如此，最大的优点是，将自己的遇到的难题、所得所获分享给需要的人，当我们遇到难题希望从互联网上寻找到答案时，我们所渴望的就是我们应该付出的。

在网上看到一个不错的的博客，布局完美，还有一些好的资源，附上链接[码农明明桑](http://blog.isming.me/)。刚开始想学习他的Blog来搭建自己的博客，不过无从下手，从他的域名看不出用什么网站搭建的，他的blog主页也没有发现有关信息（其实右下角有两个英文单词超链接就是所有答案，不过刚开始点击后，都是英文，觉得是无关的，没在意。）最后上网搜了几个类似的Blog，从他们的域名发现的答案，很多是以github.io为结尾，Github上搭建的Blog。
下面的搭建过程的记录。(运行环境Windows10_x64)
参考[blog](http://www.zipperary.com/2013/05/28/hexo-guide-2/)

## 创建Github Blog

### 创建Github账号
在[Github](http://www.github.com)上注册

### 在Github上搭建Blog
在自己Github主页右下角，创建一个新的repository。比如我的Github账号是zippera，那么我应该创建的repository名字应该是zippera.github.io。
进入博客后，会出现404错误，很多网友说是github缓存的原因，等待几分钟就可以了，但是本人等待很久也没有反应，最后解决的方式是，github发送一条认证邮件到你的邮箱，点击链接，添加一个新的邮箱。

## 本地搭建环境

### 安装Git
下载并安装[git](https://git-for-windows.github.io/)

### 安装Node.js
下载并安装[Node.js](https://nodejs.org/en/)

### 安装hexo
利用 npm 命令即可安装。（在任意位置点击鼠标右键，选择Git bash）
(实测超级慢)


``` bash
npm install -g hexo

```

### 创建hexo文件夹
安装完成后，在你喜爱的文件夹下（如H:\hexo），执行以下指令(在H:\hexo内点击鼠标右键，选择Git bash)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。

``` bash
hexo init


```

### 安装依赖包
（很慢，等待完成。）

``` bash
npm install


```

### 本地查看

现在我们已经搭建起本地的hexo博客了，执行以下命令(在H:\hexo)，然后到浏览器输入localhost:4000看看。

``` bash
hexo generate
hexo server


```

好了，至此，本地博客已经搭建起来了，只是本地哦，别人看不到的。下面，我们要部署到Github。

### 部署
编辑_config.yml(在H:\hexo下)。你在部署时，要把下面的zippera都换成你的账号名。
(注意这一步很容易出错，:后面一定要空格，比如"type: git"，中间有个空格)

``` bash
deploy:
  type: git
  repository: https://github.com/zippera/zippera.github.io.git
  branch: master


```
### 提交

执行下列指令即可完成部署并提交。
(我在执行hexo deploy遇到问题，无法提交到Github，最后[参考](https://segmentfault.com/q/1010000002764038)解决方法，使用一条命令：
"npm install hexo-deployer-git --save"
然后再执行下面两条命令。)

``` bash
hexo generate
hexo deploy


```

你的blog已经部署到github上，在浏览器上输入你blog的网址即可查看，如：zippera.github.io.git。查看本地：http://localhost:4000

## 部署Yilia主题

### 下载主题
可参考[blog](http://www.a-ho.com/2016/01/05/hexo-%E5%8D%9A%E5%AE%A2%E4%BC%98%E5%8C%96/)或者[项目地址](https://github.com/litten/hexo-theme-yilia)
进入 hexo 主目录,右击鼠标选择git bash

``` bash
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia

```
### 修改配置文件

配置:
修改hexo根目录下的
_config.yml ： theme: yilia

### 更新
此步执行多次失败，在主目录修改_config.yml后，先
hexo generate
hexo deploy
再执行后面内容


``` bash
cd themes/yilia
git pull

```

你的blog已经更新，浏览器输入地址可查看，如：zippera.github.io.git。

### 提示

每次修改后更新

``` bash
hexo generate
hexo deploy
```

或者他们的缩写

``` bash
hexo g
hexo d
```

### 配置多说



## 写Blog

### 部署blog主页

#### 头像
首先你得把头像图片上传到网上, 我是在网上找的图片。 [参考](http://www.a-ho.com/2016/01/05/hexo-%E5%8D%9A%E5%AE%A2%E4%BC%98%E5%8C%96/)
然后配置文件 themes/yilia/\_config.yml :
设置头像

``` bash
avatar: "https://www.thongtincongnghe.com/sites/default/files/imagecache/xw640/images/2014/9/18/img-1411027212-1.jpg"
```

网页icon

``` bash
favicon: "http://7xpsj5.com1.z0.glb.clouddn.com/%E5%B0%8F%E9%BB%84.jpg"
```

### 写blog

我们的blog默认有一条Hello World，它不仅告诉我们怎么创建blog，我们还可以参考它的源代码，写出和它相同的效果。
Hello World代码的地址： hexo主页/source/_posts/hello_world.md

我们创建一条blog

``` bash
hexo new "My New Post"
```

生成文件：hexo主页/source/_posts/My-New-Post.md
可以用记事本打开编辑它。参考Hello World来写。
写完保存。

执行命令更新内容。

``` bash
hexo generate
hexo deploy
```

一般情况下会乱码。


### 解决乱码
[参考](http://blog.csdn.net/jiluben/article/details/40656935)
将博客文件保存为UTF-8即可解决问题。
方法：
    1.将博客文件保存为UTF-8:
	用记事本打开本地的博客文件“xxx.md”，然后点“另存为”，“编码(E):”选择“UTF-8”，点击“保存”，替换原文件。
    2.重新生成，部署，博客乱码即消除。

### 无法更新到Github上
个人遇到的问题：创建博客后，执行
hexo generate
hexo deploy
发生错误，无法更新到Github上。本地可以看到更新内容。

网上寻找方法，好像是因为没有添加ssh，可[参考](http://jingyan.baidu.com/article/d8072ac47aca0fec95cefd2d.html),当我进入Github准备添加ssh时，发现Github上有一句话说：如果你有windows版github客户端，就不需要添加ssh。

个人最终解决方法：
安装github客户端后，桌面会有Git Shell图标，进入后执行命令，进入hexo主目录（用Linux命令），执行
hexo generate
hexo deploy
浏览器输入blog网址，更新成功。

### 使用图片
首先确认 _config.yml 中有 post_asset_folder:true 。[参考](https://codefalling.com/2015/12/19/no-pains-with-hexo-local-image/)
在 hexo 目录，执行

``` bash
npm install https://github.com/CodeFalling/hexo-asset-image --save
```
执行成功后，将图片放在/hexo主目录/public/日期/项目名/图片.jpg
例如：public/2016/07/07/My-New-Post/p1.jpg
![logo](/2016/07/07/My-New-Post/p1.png)
使用时,引用语法：
``` bash
![logo](/2016/07/07/My-New-Post/p1.png)

```
### 配置多说评论
[参考](http://www.a-ho.com/2016/01/05/hexo-%E5%8D%9A%E5%AE%A2%E4%BC%98%E5%8C%96/)

