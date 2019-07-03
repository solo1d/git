# \*将本地的一个新分支推送到远程

```bash
**    将本地的一个新分支推送到远程,而且远程也没有这个分支.新建远程分支

*   $git push --set-upstream origin develop:develop    
         # 将当前的本地的分支 develop, 推送到远程, 并且在远程也新创建一个 develop和他同名的分支.
         # 而且将这两个分支关系对应上, 也就是说远程是这个分支的上游分支.
    # 提示的信息 Branch 'develop' set up to track remote branch 'develop' from 'origin'.
    # 意思是: 远程的develop的分支已创建, 而且它会追踪着来自origin的远程develop分支.

*   $git checkout -b develop origin/develop 
         # 在本地新建一个develop分支, 它要跟远程分支 origin/develop 保持对应关系. 而不是master
         # 这个命令一般用在远程有个新分支, 而我 git push 之后,就会发现一个新的分支,
         #  那么通过这条命令 来追踪远程的这个分支, 这样就和提交的那个人相同了,
         #  第三个参数 devlop 可以改为其他名称, 并不是绝对和 origin/develop 相同.

*   $git checkout --track origin/test 
         # 实现和上面相同的功能,只不过不能改名,  他只会在在本地创建一个和远程名字一摸一样的分支.


```



