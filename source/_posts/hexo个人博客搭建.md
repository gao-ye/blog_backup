---
title: hexo个人博客搭建
date: 2019-05-12 16:32:03
categories: 其他
---

使用gitee托管平台搭配hexo工具搭建个人博客

<!--more--> 

[烨然的个人博客](https://gao-ye.gitee.io/)
<br/><br/>

#### 第一部分 HEXO安装(win10安装过程)

##### 1.安装git
安装后配置环境变量

```
C:\Program Files\Git\bin
C:\Program Files\Git\libexec\git-core
```

##### 2.安装Node.js
[快速下载链接](https://www.lanzous.com/i44o1dg)

安装后配置环境变量
环境变量写入


```
C:\Program Files\nodejs

```


##### 3.安装hexo
``` 
npm install -g hexo-cli
```

查看版本验证是否安装成功
```
hexo -v
```

接下来初始化一个本地博客目录
```
hexo init myblog##myblog是我自己起的文件夹名字
```

然后
```
cd myblog
npm install
```

启动本地服务
```
hexo g
hexo server
```
打开浏览器，输入localhost:4000即可看到刚刚生成的博客
<br/>
#### 第二部分 gitee个人博客仓库生成（github过程类似）
##### 1. 创建和用户名相同的仓库(gitee创建同名仓库，而github创建 userame.github.io仓库）
之后是简单的仓库配置，此处不赘述

##### 2.将hexo部署到GitHub
安装deploy-git ，也就是部署的命令,这样你才能用命令部署到gitee。
```
npm install hexo-deployer-git --save
```
在本地博客文件夹下找到**_config.yml**,翻到最下面修改为如下格式：
```
deploy:
  type: git
  repo: https://gitee.com/YourgithubName/YourgithubName.git
  branch: master
```
repo后面是自己对应的用户名和仓库。

然后发布博客
```
hexo clean
hexo generate
hexo deploy
```
其中 hexo clean清除了你之前生成的东西，也可以不加。
hexo generate 顾名思义，生成静态文章，可以用 hexo g缩写
hexo deploy 部署文章，可以用hexo d缩写
如果没有报错则说明部署成功了，过一会儿就可以在http://yourname.github.io 这个网站看到自己的博客。

<br/>
#### 第三部分 个性域名设置
    在阿里云购买域名后进行解析。192.30.252.153 和 192.30.252.154 是GitHub的服务器地址。（如果是gitee则选择对应的服务器地址）
注意，解析线路选择默认。

登录gitee,进入之前创建的仓库，点击settings，设置Custom domain，输入你的域名xxxxx.xyz
然后在你的博客文件source中创建一个名为CNAME文件，不要后缀。写上你的域名。

然后命令行回到博客文件夹下面执行：
```
hexo clean
hexo g
hexo d
```
等待一段时间后打开浏览器，输入自己的域名，即可浏览个人博客。