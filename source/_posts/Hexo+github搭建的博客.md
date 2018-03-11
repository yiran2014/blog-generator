---
title: 使用Hexo+github搭建的个人博客
date: 2018-03-11 08:34:44
tags:
---
#### Hexo博客的本地搭建
1.搭建博客之前，必须已安装好Node.js（无脑安装且自带npm）和Git（Git Bash自带）
2.使用npm完成Hexo的安装
```
$ npm install -g hexo-cli
```
3.Hexo安装完成后，执行下列命令，Hexo将会在指定文件夹中新建所需的文件
```
$ hexo init myBlog //创建myBlog文件夹，并初始化它
$ cd myBlog //进入myBlog文件夹
$ npm install //安装依赖(貌似可以省略，init myBlog时已安装了依赖)
```
4.启动server，即可在本地访问
```
$ hexo server
```
5.如何写博客
```
$ hexo new 博客开张.md //新建博客
$ start source/_posts/博客开张.md //自动打开博客，可以使用md格式写博客啦！
```
6.至此，本地Hexo博客已经搭建完成了。
#### Hexo博客部署至github
1.在github账号上新建空仓库（create a new repository），仓库名repo为[你的用户名.github.io]
2.打开根目录myBlog下的_config.yml文件，配置最后的deploy
i.把最后一行的type改成type: git
ii.最后一行后面新增一行，左边与type对齐，加上一行 `repo: 仓库地址` ,仓库地址为：git@github.com:xxx/xxx.github.io.git）
3.安装git部署插件
```
$ npm install hexo-deployer-git --save
```
4.将博客部署到服务器上（github）
```
$ hexo deploy
```
5.这样就可以用GitHub Pages功能，打开博客了，至此Hexo博客部署至github完成了。
###### 在上面第三步部署的过程中，很有可能会报错，下面是我遇到的原因。
本地与github没有建立通信。
生成公私钥
```
$ ssh-keygen -t rsa -C "$your_email"
```
通过所提示的公私钥路径，把公钥的内容拷贝到github上（Settting--SSH and GPG key--New SSH key）
#### 第二篇博客
```
$ hexo new 第二篇博客
$ start xxxx.md //xxx为第二篇博客的相对路径
$ hexo generate //使用hexo生成静态文件
$ hexo deploy
```
#### 换主题
1.https://github.com/hexojs/hexo/wiki/Themes 上面有主题合集
2.随便找一个主题，进入主题的 GitHub 首页，比如我找的是 https://github.com/iissnan/hexo-theme-next
3.复制它的 SSH 地址或 HTTPS 地址，假设地址为 git@github.com:iissnan/hexo-theme-next.git
4.`$ cd themes`
5.`git clone git@github.com:iissnan/hexo-theme-next.git`
6.`$ cd ..`
7.将 _config.yml 的第 75 行改为 theme: hexo-theme-next，保存
8.`$ hexo generate`
9.`$ hexo deploy`