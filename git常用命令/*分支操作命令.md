# \*分支操作 命令

## 分支操作

### git branch   看版本库中所有的分支

```bash
*       git branch        # 查看版本库中所有的分支, 前面有*号的表示当前所在的分支.
*       git branch +名字   # 创建新的分支
*               $git branch new_branch     # 创建一个新分支, 名字是 new_branch
*
*       git branch -d +名字       # 删除分支
*               $git branch -d  new_branch   # 删除这个分支
*               $git branch -D  new_branch   # 强制删除这个分支,忽略未合并错误.
        
*       git branch -m 旧分支名字  新分支名字     # 修改分支名字
*
*       git branch -v    # 显示当前所处的分支的最后一条提交记录和消息.
*       git branch -av   # 显示当前分支,网络分支,和commit号,库信息.
```

### git checkout +名字 切换到某个分支

```bash
 *       git checkout +名字    # 切换到某个分支
 *            $git checkout new_branch    
                   #切换到 new_checkout 这个分支上 
 *            $git checkout -- test.txt   
                   #丢弃掉相对于工作区中最后一次添加的文件内容所做的变更.
                   
 *       git checkout -b new_branch2      
                   #创建一个新分支, 同时切换到这个分支.
 *       $git checkout -b develop origin/develop 
            # 在本地新建一个develop分支, 它要跟远程分支 origin/develop 保持对应关系. 而不是master
            # 这个命令一般用在, 远程有个新分支, 而我 git push 之后,就会发现一个新的分支. 那么通过这条命令
            #     来追踪远程的这个分支, 这样就和提交的那个人相同了.
            #   第三个参数 devlop 可以改为其他名称, 并不是绝对和 origin/develop 相同.
        $git checkout --track origin/test 
            # 实现和上面相同的功能,只不过不能改名,  他只会在在本地创建一个和远程名字一摸一样的分支.
```



