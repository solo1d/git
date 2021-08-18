切换协议：

### 查看当前remote

```bash 
git remote -v
```

### 先增加协议

```bash
#添加并切换到http：
   git remote set-url --add origin https://github.com/solo1d/Linux.git

#添加并切换到ssh：
   git remote set-url --add origin git@github.com:solo1d/Linux.git
```

### 删除原先的协议

```bash
#切换到 ssh 之后,需要删除 http协议:
	git remote set-url --delete origin  https://github.com/solo1d/Linux.git

#切换到 http 之后,需要删除 ssh协议:
	git remote set-url --delete origin  origin git@github.com:solo1d/Linux.git
```



### 也可以直接改当前git目录里面有个配置文件。

