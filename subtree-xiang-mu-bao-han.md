# subtree  项目包含

## subtree

**subtree** 也是一种**`多重项目包含`**的命令\(**`不是引用或者指针`, `而是一个真正存在于该项目下的目录和文件`**\). 可以使用`$git subtree` 来查看参数.  

**而且还能在包含项目中修改被包含的项目的代码,还能提交更新被包含项目的代码.**

### 创建项目包含

```bash
首先在一个本地库下使用该命令添加一个远程库(本地库需要初始化完成,并且会关联一个远程库)
  $git remote add subtree-origin git@github.com:solo1d/git_subtree_child.git
      # 新添加一个远程库别名是 subtree-origin,关联到远程库, 
      #  这个被关联的库就是即将要被包含的库,  代码会拉取到本地来.
      #     可以使用$git remote show 来查看是否关联了.  



  $git subtree add --prefix=subtree2  subtree-origin master   后面还有个可选参数(--squash)
      # 调用 subutree add --prefix 来将远程的被依赖的那个库的代码克隆到本地的 subtree2 这个自定义目录下
      # subtree-origin  是被依赖库的别名(上面那条命令定义的),  而且是从 mastre 分支拉取代码
      #而且 还有一个可选项 --squash 作用是将远程库的提交信息合并成一次提交并提交,继续合并本地两个仓库代码,进行第二次提交.
      #    被依赖的库的原本的提交还是存有的, 使用命令 $git log subtree2-origin/master   查看这个分支的提交历史.
        !!!!如果添加了这个 --squash 这个参数, 那么后面所有的命令全部都要添加这个参数, 否则会造成提交出错.!!!!!


   这样本地的创建就完成了,  可以在顶层工作区将修改推送到远程来进行同步.
            $git push

```

### 更新被包含的项目代码 \(本地和远程都会更改\)

```bash
*     依赖项目如果更新的话需要如下命令来 更新本地和远程的项目代码
        $git subtree pull --prefix=subtree2 subtree-origin master  后面还有个可选参数(--squash)
            # 更新本地 包含项目的代码, 到目录subtree2 , 后面是和远程对应的仓库别名和分支, 
            #   并且会弹出一次提交信息,  :wq (保存退出)就好了
            更新本地之后可以在工作区顶层更新远程库了
                $git push


*** 如果在创建的时候使用了 --squash 这个可选项来进行创建, 那么在更新的时候也必须加上这个命令,否则会报错导致无法合并.
        如果在创建的时候没有使用 --squash 这个可选项来进行创建, 那么在后面所有的操作中,绝对不可以使用这个参数.
    $git subtree add  --prefix=subtree2 subtree-origin master --squash
    $git subtree pull --prefix=subtree2 subtree-origin master --squash

```

### 更新包含和被包含两个项目的远程库

```bash
*** 在本地修改被依赖的远程库的代码并且推送到远程,更新包含和被包含两个项目的远程库. 
        默认我已经修改了本地被包含项目的代码了. 而且在项目包含的时候使用了 --squash  这个参数!!!!
           
           首先在 工作区顶层目录下执行了 $git add .  && git commit -m '提交信息' 
                $git push
                   # 这个命令仅仅是更新了本地库对于的远程库, 被依赖的库是没有被更新的,(就是 git_subtree_child 库).
            
            然后执行更新 git_subtree_child 这个远程库,它所在的本库的代码.
                $git subtree push --prefix=subtree2 subtree-origin master  --squash
                    # 这样就更新了 git_subtree_child 这个远程库库中的源代码.



*** 更新本地被包含库 git_subtree_child 的命令
               $git subtree pull --prefix=subtree2 subtree-origin master  --squash
                    # 将被依赖的库 git_subtree_child 它所有的更改合并到本地. 不需要我提交.
               $git push  
                    # 再将修改提交到远程. 同步远程库.

```

## 项目中有包含操作, 新成员使用新目录进行新建项目的时候需要的操作会有变化

```bash
* 当是新成员使用新目录进行新建项目的时候需要的操作
        $git init && git config --local user.name 'xxx' && git config --local user.email 'xxx' 
        $git remote add subtree-origin git@github.com:solo1d/git_subtree_child2.git
        $git remote add origin  git@github.com:solo1d/git_subtree_parent2.git
        $git pull origin master:master
        $git branch --set-upstream-to=origin/master master
        #完成了, 这样就可以实现直接 git push 和 git pull 了

# 参照网址 https://stackoverflow.com/questions/32056324/there-is-no-tracking-information-for-the-current-branch

```









