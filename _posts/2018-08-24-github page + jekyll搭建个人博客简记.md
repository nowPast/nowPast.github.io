# github page + jekyll搭建个人博客简记

## step 1 建立pages功能仓库

- github提供了pages功能，被认为是用户编写的、托管在github上的静态网页；
- 开启github Pages特别简单，只需要建立一个以**[github 用户名].github.io**为命名规则的仓库即可； 
- 访问**[github 用户名].github.io**这个网址，页面就会加载该仓库根目录的index.html文件，因此github可以实现对静态页面的托管；

## step 2 安装git环境并建立与个人github的连接

- git官网下载并一路下一步进行安装，无需调整安装选项；

- 为本地git环境配置全局的github账号信息

  **git config --global user.name** "Your Name"
  **git config --global user.email** "email@example.com"

- 生成ssh连接github

  打开git bush输入ssh-keygen -t rsa，接着联系敲三次回车即可生成 ssh key,默认在：C:\Users\Administrator\.ssh目录下；

  找到id_rsa.pub，用任意编辑器打开，并全选复制；

  .接下来到GitHub上，打开“Account settings”--“SSH Keys”页面，然后点“Add SSH Key”，填上Title（随意写），在Key文本框里粘贴 id_rsa.pub文件里的全部内容；至此便建立了本地git与个人github的连接；

## step 3 安装ruby环境

- （Jekyll 是基于 Ruby 开发的，因此需要安装Ruby环境）

- 官网下载，一路下一步进行安装，无需做任何安装选项的调整；

## step 4 安装gem

- gem也就是Ruby环境下的包管理器 [RubyGems](http://rubygems.org/pages/download)

- 从[官网](https://rubygems.org/pages/download)下载压缩包，解压到你想要的目录下，路径不要有空格，然后cmd命令指到这个文件夹下面，输入“**ruby setup.rb**”执行安装即可；

## step 5 安装jekyll

- **Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件**；
- 通过Ruby环境下的包管理器---gem，执行“**gem install jekyll**”即可进行安装；

## step 6 创建本地博客

- clone github pages所在的仓库（**[github 用户名].github.io** ）

- 在检出的仓库中创建博客

  ```
  $ jekyll new .
  ```

- 启动本地服务

  ```
  $ jekyll serve
  ```

启动jekyll服务后，在浏览器里输入： [http://localhost:4000](http://localhost:4000/)，就可以看到博客展示效果；

## step 7 编写文章

- 所有的文章都是 _posts 目录下面，文章格式为 mardown 格式，文章文件名可以是 .mardown 或者 .md。
- 文章名的格式前面必须为 xxxx-xx-xx- ，日期可以修改，但必须为 年-月-日- 格式；

## step 8 更新博客至github

```
$ git add .
$ git commit -m "提交信息"
$ git push
```

　　



