# 暂存当前工作内容,并不提交和添加到暂存区

## git stash save '说明' 将当前工作区的内容保存起来,但是和提交有区别

```bash
 # 将当前工作内容暂存,并不提交和添加到暂存区.
    git stash save '说明'    # 将当前工作区的内容保存起来,但是和提交有区别
       $git stash save '临时存储'    # 保存了一个工作区现场, 备注是 临时存储
       $git stash list              # 查看保存的列表, 0号永远是最新的, 按时间顺延 新小 旧大
            
       $git stash apply             # 恢复最新的现场, 也就是0号.但不会删除list中的记录.需要手动删除
       $git stash apply stash@{1}   # 恢复列表中 1 号那个记录的现场, 而且不会删除.
       $git stash pop               # 恢复最新的现场,  还是0号, 但是会删除list中的记录.
            
        $git stash drop stash@{0}    # 手动删除 0 号记录.
```



