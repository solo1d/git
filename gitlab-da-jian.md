# gitlab 搭建

gitlab 安装 官网: [https://about.gitlab.com/install](https://about.gitlab.com/install)

!! 这个网页有详细的介绍和安装步骤. 每个版本可能不同, 需要按照官网的去做\(也可以按清华大学的\). 绝对不能按下面的走.!!!

```bash
全部root执行:
#curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
 因为国内根本无法下载 github 上的 gitlab安装包 , 所以上面那条命令根本无法执行成功.需要离线包去下面这个网址下载离线安装包:
        https://packages.gitlab.com/gitlab/gitlab-ce
    # 里面的内容是安装包,需要注意系统, el/7 是centos7, 

    # 有个防火墙的命令需要注意, 如果出错,可能是你没有启动防火墙. 去搜索一下对应的怎么开防火墙.
    # 下面全都是依赖 还有个防火墙, 如果防火墙失败,那么就是没有启动防火墙,需要启动.
    $sudo yum install -y curl policycoreutils-python openssh-server
    $sudo systemctl enable sshd
    $sudo systemctl start sshd

    $sudo firewall-cmd --permanent --add-service=http
    $sudo systemctl reload firewalld

    $sudo yum install postfix
    $sudo systemctl enable postfix
    $sudo systemctl start postfix

在没有出错的情况下使用接下来的命令:  <gitlab.rpm>

    $sudo rpm -i gitlab.rpm     // 默认我下载了离线安装包了.
    $sudo vim /etc/gitlab/gitlab.rb    // 修改这个文件中的设置    
            # 主要是修改这一行 ( external_url 'http://gitlab.com' )
            # 修改后面的ip地址域   ( external_url 'http://192.168.2.3' )
            # 配置为这台服务器的ip地址, 这个是对外提供网页访问的.
    #修改完成后执行下面的重读配置文件的命令
    $sudo gitlab-ctl reconfigure
            # 这个时候会刷屏和配置服务器, 出现Chef Client finished, 和 gitlab Reconfigured! 就算是成功了. 

    上面全都完成后,进入这个网页来进行配置和root密码设置,添加用户和权限之类的.
        http://服务器的ip
            #  第一次进入会直接提示让你输入两次密码.  这个是root密码.
            
gitlab 服务开启 重启 关闭命令
        $sudo gitlab-ctl start
        $sudo gitlab-ctl restart
        $sudo gitlab-ctl stop

gitlab 服务 关闭 开机自动启动  
        $sudo systemctl disable gitlab-runsvdir.service

gitlab 服务 开启 开机自动启动 
        $sudo systemctl enable gitlab-runsvdir.service
```

```text
gitlab 使用:
    一定要把项目放入组中, 这样方便管理. 组设置为  Internal 属性(只有组成员才能访问).
```

