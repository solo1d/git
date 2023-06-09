## 解决git status不能显示中文

现象
status查看有改动但未提交的文件时总只显示数字串，显示不出中文文件名，非常不方便。如下![img](assets/3f6f41a20f3da19933ec07a71951c12f.jpeg)







- 原因
  在默认设置下，中文文件名在工作区状态输出，中文名不能正确显示，而是显示为八进制的字符编码。
- 解决办法
  将git 配置文件 `core.quotepath`项设置为false。
  quotepath表示引用路径
  加上`--global`表示全局配置

git bash 终端输入命令：

```bash
$ git config --global core.quotepath false
```

## 解决git bash 终端显示中文乱码

要注意的是，这样设置后，你的git bash终端也要设置成中文和utf-8编码。才能正确显示中文，例如对比如下：

![img](assets/d1492adcd31a9b828fd957c1f711af38.jpeg)



在git bash的界面中右击空白处，弹出菜单，选择`选项->文本->本地Locale`，设置为`zh_CN`，而旁边的字符集选框选为`UTF-8`。

英文显示则是：
`Options->Text->Locale改为zh_CN，Character set改为UTF-8`

![img](assets/2ee6f4ffa3453f4b900e6a3643064666.jpeg)

## 通过修改配置文件来解决中文乱码

如果你的git bash终端没有菜单选项显示，还可以通过直接修改配置文件的方式来解决中文乱码问题。

进入git的安装目录

1. 编辑 `etc\gitconfig` 文件，也有些windows系统是存放在``C:\Users\Administrator\.gitconfig` 路径或 `安装盘符:\Git\mingw64\etc\gitconfig`，在文件末尾增加以下内容：

```bash
[gui]  
    encoding = utf-8  
    # 代码库统一使用utf-8  
[i18n]  
    commitencoding = utf-8  
    # log编码  
[svn]  
    pathnameencoding = utf-8  
    # 支持中文路径  
[core]
	quotepath = false 
	# status引用路径不再是八进制（反过来说就是允许显示中文了）
```

2. 编辑`etc\git-completion.bash`文件,在文件末尾增加以下内容：

```bash
# 让ls命令能够正常显示中文
alias ls='ls --show-control-chars --color=auto' 
```

3. 编辑`etc\inputrc`文件，修改output-meta和convert-meta属性值：

```bash
set output-meta on  # bash可以正常输入中文  
set convert-meta off  
```

4. 编辑profile文件，在文件末尾添加如下内容：

```bash
export LESSHARESET=utf-8
```





还有一种情况出现乱码而且上面的方法解决不了的，就是你windows安装git bash的时候框选了字体，然后你系统中没有那个字体导致。这种情况下只能先卸载git bash，重装不要选字体。

当然区分这两种情况很简单，没有字体那种实际上敲ls命令查看的时候还是能看到中文的，但在git status的时候就会出现乱码。
