---
title: 利用github+jsDelivr搭建图床
date: 2021-11-26 11:57:09
tags: 程序員技術
categories: 我的Coding生涯
cover: https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/desk_flat.jpeg
---

## 前言

图床是什么？图床就是图片存放的地址，用来节省服务器的资源，也可以变相的提升网站加载速度 你是否正在遭遇以下问题： 
1.在用静态博客网站写文章，图片不知怎么保存，保存在哪里 

2.网上复制的心仪图片链接，用着用着某一天就失效了 

3.特意花钱租个[云服务器](https://cloud.tencent.com/product/cvm?from=10680)托管图片，划不来，而且上传操作好繁琐 

4.市面上形形色色的免费图床，但都有时间期限，要么就是速度慢，存储空间小，有的还限流量 



现在可以利用jsdelivr加速github仓库来实现图床，无论是否使用jsdelivr你都可以利用github搭建一个图床，但缺点是国内加载速度非常慢，严重影响我们的需求，为此我们还需要利用jsdelivr的[cdn](https://cloud.tencent.com/product/cdn?from=10680)加速，jsdelivr在国内的节点有上百个，这样我们就得到了一个访问速度贼快，且免费，空间无限的一个图床。 下面就是教程了，有疑问有错误请评论指出，谢谢，仅以此文章帮助烂记性的自己和正在观看此博客的你。

## 新建github仓库用来存储图片

1.登录你的 github 账号，[点击跳转登录](https://github.com/)，右上角加号处点击此选项，创建一个新的仓库



<img src="https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/dd3d43b810fa006d148b835e8493ba33.jpeg" style="zoom:50%;" />

2.详细设置



![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/468826bf45623c300e6eecad9a936b67.png)



3.此仓库你可以上传你的图片，用来达到存储的目的

## 利用jsdelivr加速访问

1.现在我们直接访问图片的链接时，速度是很慢的，所以我们需要利用jsdelivr加速访问我们的图片 2.假设我们的仓库中有一张`test.png`的图片 3.使用github的链接直接访问是这样访问的`https://github.com/github用户名/仓库名/raw/master/test.png`，经过测试得知，加载速度是非常不理想的，此时将图片链接放入我们的网站内，将会导致网页加载速度十分缓慢，图片会一直在加载状态 4.现在使用jsdelivr访问非常简单，即把图片地址链接域名改为 CDN 的域名，是这样的访问格式，`https://cdn.jsdelivr.net/gh/github用户名/仓库名@master/test.png`，经过测试，现在的访问速度已经起飞了

## 利用PicGo工具便捷管理图片

1.前往picgo的GitHub仓库下载此工具，[点击前往下载](https://github.com/Molunerfinn/PicGo)，如果下载速度太慢，科学上网下载会快一点，下载好后安装即可 2.然后，在 github 上创建一个 token1，点击右上角账号上的 settings

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/1c2528d2a8e6e9a58a51a91e2c5207dd.png)



3.然后左侧点击 developer settings ，再点击 personal access tokens ，然后点击 generate new token



![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/ff87b08f8c2f7a2b534880240adfef91.png)

4.Note 用来说明你创建 token 的用途，然后 scopes 只需要选 repo 的所有选项即可



![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/455006a56bbea4bd48e3a976cca31762.png)



5.最后拉到底部，点击 generate token ，即可成功 



6.找个地方记下这一串 token，等会需要用到。（如果没有记住，等再查看时就只能重新生成了）

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/78b68fca4d052b832cb2d74e28680423.png)



7.打开picgo工具进行配置



![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/81e2217a93f056042a1ffa82b36fc945.jpeg)

- 在 PicGo 中，找到图床设置 -> GitHub图床。
- 仓库名即为你的github账号/图片仓库名
- 分支名就用默认的 master
- Token 就填写刚才我们生成的 Token
- 存储路径如果需要指定子目录可以填写例如 img/ 。我这里没有填，就会上传到我图片仓库的根目录。
- 自定义域名就填写 jsDelivr 的域名，`https://cdn.jsdelivr.net/gh/github用户名/仓库名@master`
- 最后设为默认图床，下次在 typora 上传图片就会自动上传到 github 图床了

## 总结-便捷使用方法

1.点击上传图片，此时如果你上面的配置正确，上传的图片将会同步至github仓库内

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/f8b6d564267ba617d49216d602a842c3.jpeg)

2.点击相册，可见你的图片，点击此按钮，即可复制图片链接

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/dbbd49a6d24bc6f6cc4edbef951847d4.jpeg)

3.你也可以指定上传后的链接格式

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/4466c69df1bb036fa3a8508ac66b4a5a.jpeg)

4.得到链接后，你就可以尽情的使用了，加载速度十分迅速，白嫖真香，以后想要存图片就上传，接着复制链接出来使用，非常的方便