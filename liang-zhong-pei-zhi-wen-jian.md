# 两种配置文件

## git config 配置文件

```bash
 git config --级别    
      #包括 global用户级(在~/.中), local仓库级(在.git中), 文件名: config ,仓库优先级最高
         $git config --global user.name  "名字"     
               # 添加用户到用户级家目录中.
         $git config --lobal user.email "邮箱"      
                #添加用户的邮箱到仓库目录中.  
         
         # system 是系统级别,等级最低 ,不建议添加
```

## .gitignore 配置文件

**`man git-config 查看配置文件帮助`**

**将不加入版本系统控制的`文件名`写入下面名字的** `.gitignore`  **这个文件, 就可以`自动排除在外`.支持正则表达式,和通配符. 空目录自动忽略.**

**`使用前需要在工作目录的根目录下创建这个 忽略文件`**

```bash
文件名:    .gitignore   
  配置文件书写格式    
    文件内容:  
         #         作用 : 注释
         *.b       作用: 忽略所有.b结尾的文件,不纳入到版本控制系统中.
         !a.b      作用: a.b除外, 这个文件可以纳入到版本控制系统中.
         /TODO     作用: 仅忽略根目录下的完全同名文件, 但不包括其他目录的. 
                        例 sub/DODO  是不忽略的.
         build/    作用: 忽略 build 目录下的所有文件. 包括二级和多级目录.
         doc/*.txt 作用: 忽略doc目录下的.txt文件,但不包括doc目录下的二级目录中的同名文件.doc/a/a.txt
         /*/a.txt        忽略所有二级目录中的所有a.txt文件. 但不包括三级目录和多级目录.
         /**/*.txt       忽略所有目录中的所有.txt文件. 包括所有的多级目录.
```


