# \*远程协作 命令

## 远程协作

### git pull   将远程版本库的文件拉取到本地

```bash
    git pull    将远程版本库的文件拉取到本地
        $git pull origin dest:src
            #这个其实是完整版, origin 是远程库的别名, 从远程dest的分支来, 到 src 本地的分支上去
            # 作用也就是  将远程的 dest 分支推送到我本地的 src分支上去
            # 就是  从哪里来: 到哪里去
```

### git push   将本地版本库的内容推送到远程

```bash
 git push    将本地版本库的内容推送到远程
     $git push origin src:dest   
        #这个其实是完整版, origin 是远程库的别名, src是本地分支的名字, dest 是远程分支的名字
        # 作用也是 将本地的 src分支 推送到远程 dest分支上. 
   # 虽然名字可能不同,也可能相同,但是如果不同那么必须这么写 git push 本地分支名字:远程分支名字
   
        $git push --set-upstream origin develop    
              # 将当前的本地的分支 develop, 推送到远程, 并且在远程也新创建一个 develop和他同名的分支.
              # 而且将这两个分支关系对应上, 也就是说远程是这个分支的上游分支.
              #  提示的信息 Branch 'develop' set up to track remote branch 'develop' from 'origin'.
              #  意思是: 远程的develop的分支已创建, 而且它会追踪着来自origin的远程develop分支.

         $git push -u origin master
              #将本地的master 这个分支上推送到远程, 并且将远程的master与本地的master做一次关联. 

         $git push origin develop
            # 将本地分支 develop 推送到远程, 而且在远程也会新建一个和这个名字相同的分支

         $git push origin  :develop
            # 推送一个空的分支给远程版本库中的 develop分支, 这就相当于删除分支.
            # 他会提示 [delete]  分支名字.  
              # 恢复操作, 在本地 未删除develop的情况下才能行.  $git push --set-upstream origin develop 

         $git push origin --delete develop
            # 这个是新版的远程分支删除写法. 等价于上面的写法, 提示也一样 ,但是更直观.

         $git push origin v1.0 v2.0 
                # 将本地标签 v1.0 和 v2.0 推送到远程
         $git push origin --tags
                # 将本地所有未推送到远程的分支,全部推送过去.
```

### **git pull 和 git push 原理**

```bash
$git pull 和 $git push 原理: 
       它连续执行两个命令. git fetch 和 git merge origin/master 两个操作
```

