title: Vim 的Markdown语法高亮设置
date: 2016-03-03 22:16:09
tags:
- vim
- Markdown
categories:
- editor
---

### 安装插件

1. 到[配置文件地址](https://github.com/plasticboy/vim-markdown/archive/master.tar.gz)下载文件

2. 安装方法：

```bash
$mkdir ~/.vim/
$cd ~/.vim
$tar --strip=1 -zxf vim-markdown-master.tar.gz
```
<!-- more -->

3. 设置vim的配置文件

> 在用户目录`~`下新建配置文件`.vimrc`（如果没有此文件的话）
> 打开`.vimrc`文件，向其中写入`syntax on`保存，重新打开vim即可

Vim开启语法高亮

编辑~/.vimrc，写入syntax on
