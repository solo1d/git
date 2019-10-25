# \*更新 在本地 的 远程分支

```bash
*    $git fetch     
           # 将远程的修改拉取到本地 并更新本地的远程分支. 但是他不会执行合并操作.(git merge)
        $git fetch origin tag v7.0
                #将在远程的 v7.0 这个标签从远程拉取到本地.
        $git fetch  origin master:refs/remote/origin/mymaster
                #将远程的 masert 拉取到本地的 mymaster  
```

