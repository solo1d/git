# \*获取状态 , 初始化, 远程到本地复制 命令

## 获取状态 , 初始化, 远程到本地复制

**\*表示重要命令,以及常用命令**

###  git status  获取状态 

```bash
*       git status  获取当前工作的处于一个什么样的状态.
```

###  git init  初始化本地版本库

```bash
*       git init    初始化一个新的仓库
                # 一般情况下使用 git init 直接来创建一个库
                    $git init --bare
                        # 这个命令是来创建一个裸库的, 一般不是开发者使用 ,而是版本服务器
```

### git clone  将远程版本库复制一份到本地

```bash
*       git clone   将远程版本库复制一份到本地
            $git clone git://github.com/schacon/grit.git 
                    # 将 github上 schacon 用户的 grit 项目复制到本地的当前所在文件夹.
            $git clone git@github.com:solo1d/grit.git 
                    # 将 github上 schacon 用户的 grit 项目复制到本地的当前所在文件夹.
            $git clone git@github.com:solo1d/grit.git  ~/new_mkdir
                    # 将 github上 schacon 用户的 grit 项目
                    #  复制到本地的指定用户目录下的new_mkdir目录中

   # 如果远程库中包含了 submodules 的话就需要在复制后重新初始化 submodules 和更新. 
   #  注意当使用了 submodule 之后, 新来的成员的新git仓库的初始化方式会有变化:
    使用了 submodule 之后的 第一种初始化方法:
      $git clone git@github.com:solo1d/git_parent.git  git_parent2
        # 复制远程版本库 solo1d用户的 git_parent项目,到 git_parent2这个新目录(执行前不能存在).
        # 但没有依赖项目.
      $cd  git_parent2     #来到这个新目录
      $git submodule init
        #初始化 submodule
      $git submodule update --recursive
        #执行submodule 递归更新.  这个时候就可以了.已经把所有内容都拉取回来了.
      $cd mymodule && git checkout master
        #进入依赖项目文件夹, 并且进入 master这个分支. 如果不进入那么会在一个 sha1 值的分支上.
    
    使用了 submodule 之后的 第一种初始化方法: 
      $git clone git@github.com:solo1d/git_parent.git git_parent3 --recursive 
          #复制远程版本库, 并且将依赖的项目也一并复制过来.
         $cd mymodule && git checkout master
             # 顺便切换一下依赖项目所在分支.
```

