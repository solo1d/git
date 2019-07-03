# \*删除远程版本库中的分支

```bash
远程操作: 删除远程版本库中的分支
  $git push origin  :develop
      # 推送一个空的分支给远程版本库中的 develop分支, 这就相当于删除分支.
      # 他会提示 [delete]  分支名字.  
      # 恢复操作, 在本地 未删除develop的情况下才能行.  
      #     $git push --set-upstream origin develop 

  $git push origin --delete develop
      # 这个是新版的远程分支删除写法. 等价于上面的写法, 提示也一样 ,但是更直观.
      
删除掉远程分支之后同步的将本地分支也裁剪掉
        $git remote prune origin
            # 需要使用 git remote show origin 来查看远程分支状态,然后在执行, 
            #    这个命令会删除远程没有的本地分支.小心使用.
```

