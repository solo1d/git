# \*远程操作 : 推送到远程版本库

## 远程操作 : 推送到远程版本库

### 准备工作

```text
        推送之前要先在工作目录创建和编写 README.md 文件.来初始化.
    gitHub的操作:  
            首先在网页端点击创建仓库(new repository), 
                Repository  是仓库名(会作为url的一部分,就是网址)
                Description 项目说明
```

### https 推送的设置和操作内容

```bash
网页创建完成之后的操作:
*  $git remote add origin https://github.com/solo1d/gitlecture.git
         #使用git远程命令, 添加一个远程地址, origin 代表后面的一串地址(远程仓库).后面命令用origin代替网址
         # 就是创建一个远程仓库, 并且和本地做关联, 从本地->远程, 仅仅是绑定.
*  $git push -u origin master
         #将本地的master 这个分支上推送到远程, 并且将远程的master与本地的master做一次关联.
             然后会弹出验证界面
                Username for 'https://github.com':  后面是我的账户, 286233475@qq.com
                Password for 'https://solo1d@github.com':  后面是我账户的密码
                    # 验证通过后会自动上传 而且提示.
                    # 验证之后可以使用 $git push 来将本地的 master 主分支进行推送.
#https完成 ,缺点是每次都要输入账户和密码
```

### ssh 推送的设置和操作内容

```bash
*  ssh 的设置内容:
         网页创建完成之后的操作:
            选择 SSH 连接, 然后复制后面的内容 一般是:   git@github.com:solo1d/gitlecture.git
               然后使用添加一个远程地址.
*       $git remote add origin git@github.com:solo1d/gitlecture.git
             #使用git远程命令, 添加一个远程地址, origin 代表后面的一串地址(远程仓库).后面命令用origin代替网址
           * 然后生成自己的公匙和私匙
*      $$ssh-keygen -t rsa -C "你的邮箱" -f ~/.ssh/想要生成公匙和私匙的文件名名字
           #然后两下回车就可以生成, 掠过的内容主要是需要密码. 可以回车跳过的,然后就生成了两个文件.
           接着打开生成的公匙文件(你自己定义的.pub), 复制其中的内容, (私匙绝对不能拿出来. 文件内容短的是公匙)
           随后打开网页来到项目页面, 进入Settings 中的 Deploy keys 的页面, 来设置公匙
        点击 Add deploy key 来添加. *而且一定要把下面的 'Allow write access' 选上, 这是写入权限.
                    # key 填写 公匙的内容, (公匙内容比私匙短)
                        
        随后将本地内容推送到远程并且在远程创建个 master的分支.下面两个命令二选一 (新远程项目才会使用)
                $git push --set-upstream origin master:master
*               $git push -u origin master        
                    #推送命令, 如果成功了就表示没问题了, 如果出错那么就是远程钥匙出了问题.
                    
             紧接着输入以下命令,检测显示与我这个本地仓库有关联的远程.     
*                   $git remote show origin 
                #ssh完成.
```

