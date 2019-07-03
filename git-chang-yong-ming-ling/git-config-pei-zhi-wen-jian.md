# git config 配置文件

## 修改配置文件

```bash
 git config --级别    
      #包括 global用户级(在~/.中), local仓库级(在.git中), 文件名: config ,仓库优先级最高
         $git config --global user.name  "名字"     
               # 添加用户到用户级家目录中.
         $git config --lobal user.email "邮箱"      
                #添加用户的邮箱到仓库目录中.  
         
         # system 是系统级别,等级最低 ,不建议添加
```



