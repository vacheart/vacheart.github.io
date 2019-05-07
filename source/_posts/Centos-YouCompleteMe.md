---
title: Centos YouCompleteMe
date: 2019-05-07 22:15:17
categories: 记录
tags:
	- Vim
---

## 一、更新Vim

我安装这个插件的时候，提示：YouCompleteMe unavailable : YouCompleteMe unavailable: requires Vim 7.4.1578+
<br>所以不得不把系统自带的Vim更新到8.0

```
# 移除旧版本
sudo yum remove vim -y
# 安装必要组件
sudo yum install ncurses-devel python-devel -y
# 下载源码编译安装
git clone https://github.com/vim/vim.git
cd vim/src
# 根据自己实际情况设置编译参数
./configure --with-features=huge --enable-pythoninterp=yes --enable-cscope --enable-fontset --with-python-config-dir=/usr/lib64/python2.7/config
make
sudo make install
```

编译参数说明：
–with-features=huge：支持最大特性
–enable-rubyinterp：打开对ruby编写的插件的支持
–enable-pythoninterp：打开对python编写的插件的支持
–enable-python3interp：打开对python3编写的插件的支持
–enable-luainterp：打开对lua编写的插件的支持
–enable-perlinterp：打开对perl编写的插件的支持
–enable-multibyte：打开多字节支持，可以在Vim中输入中文
–enable-cscope：打开对cscope的支持
–with-python-config-dir=/usr/lib64/python2.7/config 指定python 路径
–with-python-config-dir=/usr/lib64/python3.5/config 指定python3路径

注意：必须带上Python编写插件支持，最好带上Python路径，否则使用时会报这个错误：YouCompleteMe unavailable: requires Vim compiled with Python (2.6+ or 3.3+) support

编译安装好Vim后，默然是安装在/usr/local/bin目录下，所以把该目录加入到PATH方便terminal全局使用：

```
sudo vi /etc/profile
```
