title: OSX下利用Github Pages和Hexo搭建个人博客
date: 2016-02-20 16:18:45
tags:
- 博客
- Hexo
- OSX
- Github Pages
categories:
- 技术
- 搭建博客
---

这两天由于要使用**Github Pages**搭建一个静态博客，就去网上搜了一些教程。对比几个不同的方法之后决定使用**Hexo**来搭建，在搭建过程中也遇到了一些错误和问题，故在这里将自己的搭建过程记录下来，以备以后参考。

**下面就切入正题，介绍我的安装过程。**

<!-- more -->

### 本地环境
---
##### 安装Node

- 由于Hexo依赖于Node.js故首先需要安装Node.js。去[Node.js官网](https://nodejs.org/en/)下载OSX的最新安装包，按照默认方式安装即可。

##### 安装Git

- 去[git-scm.com](https://git-scm.com/downloads)下载OSX平台的安装包，然后按照默认方式安装。

### GitHub准备
##### 创建Repository

- 首先需要一个[Github](https://github.com/)账户,没有的需要先注册。登录Github后点击页面右上角的`+`号创建新的Repository，并且Repository的名字要跟你的账户名一致（账户名可以点击Github页面右上角头像会弹出`Signed in as 你的用户名`），其他的选项全部默认，然后保存即可。

##### 添加SSH公钥到Github

- 点击Github页面右上角头像，选择`Settings`,然后点击新页面左侧的`SSH keys`，在点击右侧的`New SSH key`按钮。之后会弹出下图的文本框：
![Add SSH key](http://ww3.sinaimg.cn/mw690/64c6894bgw1f16x42325lj20rw0itn0d.jpg)

- 在`Title`处填写个名数字（例如MBPkey）。

- 打开`Terminal`或者`iTerm`然后输入以下命令，将打印出的信息复制下来粘贴到`Key`文本框中，然后点击保存。

	```bash
	cat ~/.ssh/id_rsa.pub
	```

##### 设置本地git的Github账号信息

- 打开`Terminal`或`iTerm`输入以下命令

	```bash
	git config --global user.email "xxx@gmail.com" #输入注册Github时的邮箱
	git config --global user.name "yyy"            #输入注册Github时的邮箱
	```
##### 验证是否设置成功

- 最后可以通过在`Terminal`或`iTerm`中输入以下命令。

    ```bash
    ssh -T git@github.com
    ```
    
    如弹出以下信息则说名设置成功。
    >Hi xxx(你的用户名)! You've successfully authenticated, but GitHub does not provide shell access.

### 安装Hexo
---
- Node和Git此时已经在本机安装好了，然后执行以下指令安装hexo：

    ```bash
    $ sudo npm install -g hexo
    ```
    
    我之前按照网上的教程总是遇到文件夹无法写的错误，所以需要加`sudo`进行提权
    
- 如果遇到以下错误：
    
    > { [Error: Cannot find module './build/Release/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
{ [Error: Cannot find module './build/default/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
{ [Error: Cannot find module './build/Debug/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }

    可以执行以下命令：
    
    ```bash
    $ sudo npm install hexo --no-optional
    ```

### 初始化
---
- 初始化有两种方式，一种事先建立好文件夹后，然后cd进入文件夹执行以下命令：

    ```bash
    $ hexo init
    ```

- 另一种方式是直接在命令后制订文件夹名称：
    
    ```bash
    $ hexo init <folder>
    ```
到这里安装工作已经完成了。

### 生成静态页面
---

- 在上述建立的目录中执行以下命令，也可简写成`hexo g`

    ```bash
    $ hexo generate
    ```
此命令可将`/source/_posts`下的MarkDown文件转换成静态网页并。

### 在本地启动服务
---
- 执行以下命令，启动本地服务，也可简写成`hexo s`

    ```bash
    $ hexo server
    ```
然后在浏览器中输入`http://localhost:4000`即可看到搭建好的博客。