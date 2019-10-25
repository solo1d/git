### 1，生成一个公司用的SSH-Key   

```bash
$ ssh-keygen -t rsa -C "youremail@yourcompany.com” -f ~/.ssh/id-rsa
```

 

在~/.ssh/目录会生成id-rsa和id-rsa.pub私钥和公钥。 我们将id-rsa.pub中的内容粘帖到公司gitlab服务器的SSH-key的配置中。

```bash
$ ssh-keygen -t rsa -C "youremail@your.com” -f ~/.ssh/github-rsa
```



在~/.ssh/目录会生成github-rsa和github-rsa.pub私钥和公钥。 我们将github-rsa.pub中的内容粘帖到github服务器的SSH-key的配置中。

```bash
$ ssh-add ~/.ssh/id_rsa $ ssh-add ~/.ssh/github_rsa
```



如果执行ssh-add时提示"Could not open a connection to your authentication agent"，可以现执行命令：

```bash
$ ssh-agent bash
```



然后再运行ssh-add命令。

```bash
# 可以通过 ssh-add -l 来确私钥列表
$ ssh-add -l
# 可以通过 ssh-add -D 来清空私钥列表
$ ssh-add -D
```



在 ~/.ssh 目录下新建一个config文件

```bash
touch config
```



添加内容：

```bash
# gitlab
Host gitlab.com
    HostName gitlab.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
# github
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_rsa
```



![img](http://static.oschina.net/uploads/space/2015/1112/151152_7YR5_723271.png)



```bash
$ ssh -T git@github.com
```

输出

Hi stefzhlg! You've successfully authenticated, but GitHub does not provide shell access.

就表示成功的连上github了.也可以试试链接公司的gitlab.