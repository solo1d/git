# \*版本管理 命令

## 版本管理

### git add    将当前已修改的文件纳入到暂存区当中

```bash
*       git add     将当前已修改的文件纳入到暂存区当中
                $git add text.txt   将text.txt 这个文件纳入到暂存区中.
                $git add .          将工作目录下所有的文件全部纳入到暂存区, 非常常用
```

### git remote add  本地库关联远程库

```bash
*      $git remote add origin https://github.com/solo1d/gitlecture.git
              # 使用git远程命令, 添加一个远程地址, 
              #       origin 代表后面的一串地址(远程仓库).后面命令用origin代替网址
              # 就是创建一个远程仓库, 并且和本地做关联, 从本地->远程, 仅仅是绑定.
        $git remote rm origin 
             # 这是绑定出错的删除操作,  删除后重新绑定就好了.
```

### git commit 将暂存区当中的文件纳入到版本库中

```bash
*       git commit  将暂存区当中的文件纳入到版本库中
                $git commit -m '提交注释和说明'       
                      # 提交和注释说明
                $git commit --amend  -m '修正说明'   
                      # 修改上次一提交的注释和说明, 而且不是二次提交.
                $git commit -am '提交注释和说明'      
                      # 提交所有已经修改的文件, 可以省略git add. 这步.不可以对新文件使用
                $git commit --amend --reset-author  
                      #重新修改提交的用户配置信息.
```

### git rm  删除工作目录当中一个特定的文件, 将被删除的文件纳入到暂存区.

```bash
*       git rm      删除工作目录当中一个特定的文件, 将被删除的文件纳入到暂存区.
                $git rm text.txt       
                     # 删除工作区的text.txt文件, 删除后可以直接提交.
                $git rm --cached file  将文件或者目录从暂存区中移除.(但是工作内的实体还在)
                     # 若想恢复被删除文件,需要执行下面两个动作.
                             $git reset HEAD text.txt          
                                       #将待删除的文件从暂存区恢复到工作区.
                             $git checkout -- text.txt         
                                       #将工作区删除的这个修改丢弃. 文件恢复结束.
          #如果是使用系统的 rm 来删除的话 需要多进行一步, 将修改纳入到暂存区.在执行上面两步.
                             $git add text.txt
```



### git mv  和系统mv相同,然后将操作纳入暂存区. 这个动作对于git来说就是删除一个文件,然后复制一份新名字文件.

```bash
*       git mv      和系统mv相同,然后将操作纳入暂存区. 这个动作对于git来说就是删除一个文件,然后复制一份新名字文件.
                $git mv old.txt new.txt     # 将old.txt 重命名为 new.txt
                   # 若想恢复成原名,需要执行下面两个动作
                        $git reset HEAD old.txt      
                             # 将待改名的文件从暂存区恢复到工作区.
                        $git reset HEAD new.txt      
                             # 将新文件的文件从暂存区恢复到工作区
                        $git checkout -- new.txt     
                             # 将工作区的修改操作丢弃,文件恢复完成.
                        # 这个时候会出现一个新文件和一个旧文件 同时存在, 可以删除一个. 然后再拉入暂存区.
                        # 如果是使用系统的mv 命令来改名, 也需要多一步操作
                             $git add new.txt old.txt      
                                  #这样git就会自动识别到,这是个重命名操作.
```

### git reset --hard HEAD^   回退到当前分支的上个版本,固定格式

```bash
       git reset --hard HEAD^    # 回退到当前分支的上个版本,固定格式
            $git reset --hard HEAD^^    
                 #回退两个版本.
            $git reset --hard +哈希字串   
                 #回退到 哈希子串(commit ID)的版本, 曾经版本去 git reflog 中找.
            $git reset --hard HEAD~2    
                 #也是回退两个版本
```

### git reset HEAD +文件   将之前添加到暂存区的文件从暂存区移除出去

```bash
*       $git reset HEAD +文件  将之前添加到暂存区的文件从暂存区移除出去.
```

