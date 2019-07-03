# \*标签 命令

## 标签

```bash
*       git tag     标签命令,一般是正式版本才会发布标签
            $git tag           
                #会弹出标签列表
            $git tag -l '内容'  
               #查找本地标签,内容可以使用通配符,  一般是 v*.* 什么的
            
            $git tag v1.0                   
                #创建一个本地轻量级标签
            $git tag -a v2.0 -m '标签说明'    
                #创建一个本地标签 并且添加说明

            $git tag -d v1.0     
                #删除本地 v1.0 这个标签
            $git show v1.0        
                # 显示本地标签 1.0的改动和内容

            $git push origin v1.0 v2.0 
                # 将本地标签 v1.0 和 v2.0 推送到远程
            $git push origin --tags
                # 将本地所有未推送到远程的分支,全部推送过去.
            $git push origin refs/tags/v7.0:refs/tags/v7.0
                # 将本地的 v7.0标签推送到远程的7.0标签(远程在推送前可以没有7.0这个标签), 这个是完整写法

            $git push origin :refs/tags/v6.0
                #删除远程标签 v6.0
            $git push origin --delete tag v5.0
                # 将在远程的标签 v5.0 删除掉   新版本的写法, 1.7
           
            $git fetch origin tag v7.0
                #将在远程的 v7.0 这个标签从远程拉取到本地.
```









