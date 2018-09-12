# Typora安装及使用

## 安装

Linux下官方提供安装方法：

```sh
# optional, but recommended
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE

# add Typora's repository
sudo add-apt-repository 'deb https://typora.io ./linux/'
sudo apt-get update

# install typora
sudo apt-get install typora
```

window	[官方下载](https://www.typora.io)：https://www.typora.io

		[百度网盘](https://pan.baidu.com/s/16i-WqaFU91BZo0jktFEWpg)：https://pan.baidu.com/s/16i-WqaFU91BZo0jktFEWpg 密码：mog4

## 使用

### 1、添加目录

目录其实就是大纲，不同的是，大纲是自己看的，目录是读者看的。为此，我们需要在文章中插入目录。当用户点击某一具体标题的时候，会跳转到对应的内容。Typora是一款强大的markdown编辑器，在生成大纲或者目录的时候，其实是根据我们所使用的标题来进行生成。

将光标放在要生成目录的地方，点击`Paragraph->Table of Contents`生成目录[TOC]