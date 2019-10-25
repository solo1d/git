# submodule  引用项目

## submodule

**submodule:**  `一个项目中包含和引用多个项目, 同时包含进来的项目配置文件会在 .git/modified 目录下(每个依赖就有一个文件夹)`

### 增加引用依赖项目

```bash
# git_parent是引用项目, git_child是被引用的项目.
 $git submodule add git@github.com:solo1d/git_child.git mymodule
    # 在 parent 中执行, 将远程的 solo1d用户的 git_child 项目克隆过来, 并且需要一个新的文件夹来存放.
        # 执行完成后会多出 git_child项目的文件夹,还有一个git生成的  .gitmodules 文件.

   $git add .    
        # 将新引入的项目 添加到 git_parent 这个项目中.
    $git commit -m 'add submodule'
        # 在本地提交一次
    $git push 
        # 将引用这个操作推送到远程
# 推送完成后, 远程会多出一个文件夹 mymodule @ 146cfd(上面自定义的,后面是git_child项目的sha1值),
#   点击后会进入  git_child  这个项目的页面中.  
```

### 更新引用过来的项目

```bash
   $cd mymodule     
       # 进入git_child 本地的这个项目目录中

第一种方法   
    $git pull
        # 这是一种方法,  可以拉取到 git_child 项目的最新修改.
        
第二种方法  
    $git submodule foreach git pull
        # 需要在git_parent 目录下执行, 
        # 作用是 遍历依赖的所有项目,然后对每个submodule执行 git pull操作拉取最新代码.

当完成更新后,需要 $git add. 一次,和提交一次  $git commit -m 'update submodule' ,
  最好还需要$git push 到远程. 
```

### 删除引用依赖项目

```bash
首先将不需要的submodule从暂存区删除. 然后将实体文件从工作区删除, 然后将.git/submodule 目录删除.
  如果只是删除某一个依赖,那么会有一点点的区别, 就是挑选删除,不能全部删除.
     
     $git rm --cached mymodule    
         #将 mymodule 从暂存区中删除, 就变成了未跟踪状态.
     $rm -rf mymodule .gitmodules 
         # 使用系统命令 将mymodule从工作区删除. 
         #  以及.gitmodules配置文件  (.git/modules 删不删无所谓)
     $git commit -m 'remove submodule'
         #提交一次, 更新删除状态. 本地删除完成,  
     $git push 
         #更新删除状态到远程.  这样远程也删除完成了.
```

## 当使用了 submodule 之后, 新来的成员的新git仓库的初始化方式会有变化:

```bash
第一种初始化方法
    $git clone git@github.com:solo1d/git_parent.git  git_parent2
        # 复制远程版本库 solo1d用户的 git_parent项目,到 git_parent2这个新目录下(执行前不能存在).但没有依赖项目. 
    $cd  git_parent2     #来到这个新目录
    $git submodule init
        #初始化 submodule
    $git submodule update --recursive
        #执行submodule 递归更新.  这个时候就可以了.已经把所有内容都拉取回来了.
    $cd mymodule && git checkout master
        #进入依赖项目文件夹, 并且进入 master这个分支. 如果不进入那么会在一个 sha1 值的分支上.

第二种初始化方法
    $git clone git@github.com:solo1d/git_parent.git git_parent3 --recursive 
        #复制远程版本库, 并且将依赖的项目也一并复制过来.
        $cd mymodule && git checkout master
            # 顺便切换一下依赖项目所在分支.
```



