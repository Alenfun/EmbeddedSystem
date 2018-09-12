## Sublime安装

linux下

```
sudo add-apt-repository ppa:webupd8team/sublime-text-3 
sudo apt-get update 
sudo apt-get install sublime-text-installer 
```

## Sublime支持中文编码问题

打开`package control` ，然后键入`install package`进入，搜索`ConvertToUTF8`
安装成功后 打开要查看的GBK文件,点击菜单File->ReloadWithEncoding->UTF-8
这时可能会提示Error有几行提示是说：没有安装Codecs33
再次打开`install package`输入`Codecs33`并安装。
按照上述的方法reload文件时不会有错误了，如果想将文件修改为UTF-8编码,可以选择File->SaveWithEncoding->utf-8（不建议使用set encoding）

