# \*查看信息 命令

## 查看信息

```bash
        git help     获取帮助
        git log      查看提交日志
                 $git log -4      查看最近4条提交的日志消息.
                 $git log --pretty=oneline    查看简短的日志, 只显示ID 和提交说明.
                 $git log --pretty=format:"%h - %an,%ar : %s"    定制格式显示日志.
                 $git log --graph       图形化显示日志.
                 $git log  refs/remotes/origin/master   查看远程分支master的一个历史记录
        
        git reflog      操作日志和曾经版本的 commit ID, 回退版本和提交信息都可以去这里找.

        git diff        比较版本库和暂存区以及工作区文件的差别
                $git diff        比较暂存区文件和工作区文件之间的差别, -源文件, +目标文件
                $git diff HEAD   比较当前分支的版本库最新提交文件和工作区文件的差别, -版本库 +工作区, 可以换成commit ID
                $git diff --cached  +ID    比较当前版本库和暂存区之间的文件差别,  ID是commit ID ,也可以不写


        git blame +文件名    显示修订版和作者上次修改文件的每一行


*       $git remote show origin  与本地相关联的 origin 的详细信息. 和对应关系,全部详细的罗列出来.
            # 列表中的Fetch URL 是拉取地址(远->本).   Push 是推送地址.(本->远)

*       $git remote show         显示与我这个本地仓库有关联的远程名称.
```

