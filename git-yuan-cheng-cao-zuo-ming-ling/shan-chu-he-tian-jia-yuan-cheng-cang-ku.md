# \*删除和添加远程仓库

## 删除远程仓库

```bash
     首先删除存留在本地的远程仓库的绑定信息
          $git remote rm origin
            #将本地的远程仓库信息删除了, git remote show 也不会显示远程信息 ,但是远程仓库和本地还是存在的.


     添加远程仓库
          $git remote add origin git@github.com:solo1d/gitlecture.git
            # 如果本地残留这个库的话,会直接复原. 如果没有会去远程拉取.
```

