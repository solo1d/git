# 将一个分支的提交内容, 复制到另一个分支上

```bash
将一个分支的提交内容, 复制到另一个分支上  git cherry-pick
    $git cherry-pick  +commitID
        # 后面是commitID 通过git log 查看, 需要在复制的分支上进行该命令. 一次复制一个提交,绝对不能跨越提交. 
        # 比如是把 dev分支的提交复制到 master上, 那么这个操作是在 master上,  后面的commitID 是dev的.就是被复制的
        # 而且这个复制并不是完全的拷贝, 而是另一种提交(前后的commitID 都不相同.)


    复制完成之后, 可能有恢复被复制分支到改动前的要求,那么操作如下.
        来到被赋值分支(比如是dev) , 并且确定需要还原的点(commitID, 比如是 a12bc ).
            $git checkout a12bc     
                #先来到这个commitID 的提交点上, 这个时候是游离状态.
            $git branch -D dev 
                # 删除dev 这个分支, (但是我们现在是被删除的游离状态的提交点,所以绝对不能切换到其他分支)
            $git branch -b new_dev
                # 通过这个游离状态的提交点创建了一个新分支. 然后这个游离状态就会变成这个分支.
         #恢复到未改动之前的操作结束

```



