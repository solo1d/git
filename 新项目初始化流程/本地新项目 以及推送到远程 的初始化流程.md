# 本地新项目 以及推送到远程 的初始化流程:

## 本地新项目 以及推送到远程 的初始化流程:

```bash
新建一个工作目录, 进入到里面,建立本地的一个新项目仓库.
在远程也需要有 github 仓库

        $git init
        
        $git config --local user.name '名字'
        
        $git config --local user.email '邮箱'
        
        $git remote add origin  git@192.168.2.3:solo1d/mytest.github  
                # 这步关联了一个远程仓库, git@网址,用户名/仓库名字.github
                # 使用git远程命令, 添加一个远程地址, origin 代表后面的一串地址(远程仓库).
                # 后面命令用origin代替网址就是创建一个远程仓库, 并且和本地做关联, 
                # 从本地->远程, 仅仅是绑定.
                 
        $然后将本地的公匙添加到远程库. 
            生成本地公匙和私匙命令: 
                 $ssh-keygen -t rsa -C "你的邮箱" -f ~/.ssh/想要生成公匙和私匙的文件名名字 
             将私匙添加到本地的私匙列表中: 
                 $ssh-add -K ~/.ssh/私匙的文件名名字  
                     # 可以用 ssh-add -l  查看私匙列表
                     #       ssh-add -D 清空私匙列表 
                     #  还可以在 ~/.ssh/中 定义一个 config 文件
                     
        $echo '##new' > README.md && git add .  && git commit -am 'add README'
                 # 这步进行了一次提交, 提交的内容是 'add README',这是为了初始化本地仓库
                 
        $git push --set-upstream origin master  
            # 或者 $git -u origin master
            # 新建一个分支的时候,也需要这条命令来提交和新建远程分支.
            # 将本地的新仓库推送到远程 的 master分支.
```























