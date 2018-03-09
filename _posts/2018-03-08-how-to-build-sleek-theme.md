---
layout: post
title: 安装Sleek Theme全流程
featured-img: test1
mathjax: true
---

* Table of content
{:toc}

# Jekyll (Sleek Theme)
## 一、Install VMware Workstation 14 Pro

```
1、用360软件管家下载安装VMware Workstation 14 Pro
2、输入Key
CG54H-D8D0H-H8DHY-C6X7X-N2KG6

ZC3WK-AFXEK-488JP-A7MQX-XL8YF

AC5XK-0ZD4H-088HP-9NQZV-ZG2R4

ZC5XK-A6E0M-080XQ-04ZZG-YF08D

ZY5H0-D3Y8K-M89EZ-AYPEG-MYUA8
```

## 二、Install CentOS 7
```
官网https://www.centos.org/ 下载最新DVD版本CentOS 7 
可以在这个下载地址中选择 torrent 或 iso文件下载：
http://isoredirect.centos.org/centos/7/isos/x86_64/
```

###  2.1 CentOS 7 配置与升级
#### 2.1.1 赋予账号root权限

```
useradd sha
passwd sha   创建用户及密码
gpasswd -a sha wheel   赋予  sha   root权限

vi /etc/sudoers
Allow root to run any commands anywhere
root    ALL=(ALL)       ALL    #原有行
sha     ALL=(ALL)       ALL   #添加此行
保存后   登陆sha用户    使用   sudo   即可

vi /etc/sudoers
## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL      #找到此行  如果前面有   #    删掉#后保存
执行  usermod -g root sha 
登陆sha   使用sudo 
```

#### 2.1.2 更新CentOS7的软件和内核
```
Applications - System Tools - Software Update
```

## 三、Install ruby(2.2)
```
1.yum -y remove ruby
2.gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
3.\curl -sSL https://get.rvm.io | bash -s stable
4.source ~/.rvm/scripts/rvm
5.rvm list known
6.rvm install 2.2
7.rvm use 2.2 --default

配置每次打开终端都生效：
vim ~/.bashrc
在.bashrc中添加：
source .rvm/scripts/rvm
export PATH="$PATH:$HOME/.rvm/bin"
```

## 四、Install python(2.x)
```
yum install python
```

## 五、Install jekyll
```
gem install jekyll
```

## 六、Install Nodejs
```
1.cd /usr/local/src/
2.wget https://nodejs.org/dist/v8.10.0/node-v8.10.0-linux-x64.tar.xz
3.tar -xvf node-v8.10.0-linux-x64.tar.xz
4.vim /etc/profile
  在最下面增加：
  #set nodejs env
  export NODE_HOME=/usr/local/src/node-v8.10.0-linux-x64
  export PATH=$PATH:$NODE_HOME/bin
  export NODE_PATH=$NODE_HOME/lib/node_modules:$PATH
5.source /etc/profile
  vim ~/.bashrc
  在.bashrc中添加：
  source /etc/profile
```

## 七、Install others(gulpfile/gulp/bundle及其他依赖项)
```
1.npm install -g gulpfile    #如果npm安装报错，切换到root用户
2.gem install bundle

#进入文件夹执行下面命令
3.bundle install 
4.npm install  #如果安装出错，安装下面几项
  npm install gulp-cli -g
  npm install gulp -D
  npm install node-sass
  npm install sharp
```

## 八、Start jekyll service
```
1.如果使用gulp启动可以输入 gulp 或 npm start 
2.如果不使用gulp，可以使用bundle exec jekyll serve 启动
```

