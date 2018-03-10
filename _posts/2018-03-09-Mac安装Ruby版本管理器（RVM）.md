---
date: 2018-03-09 15:27:31
layout: post
title: Mac安装Ruby版本管理器（RVM）
category: Mac工具
tags: Mac工具
keywords: Mac ruby
description: Mac ruby
---

#### 如需转载请备注地址～ 谢谢 ～ [简书地址](https://www.jianshu.com/u/bee103cd1f97)  [个人博客](https://kaqijiang.github.io/)

#### [RVM](https://rvm.io/)是一个命令行工具，它允许您轻松地安装，管理和使用从解释器到多组宝石的多个ruby环境。

> 使用Ruby原因：

- 虽然 macOS 自带了一个 ruby 环境，但是是系统自己使用的，所以权限很小，只有 system。而/Library 目录是 root 权限,所以很多会提示无权限。

- 使用自带ruby更新,管理不方便

- 一系列无原因的报错


> 删除系统ruby方法[⚠️删除容易出现问题，尽量不要删除，不要删除，不要删除]

```
cd /System/Library/Frameworks/Ruby.framework/Versions;sudo rm Current; sudo ln -s 1.8 Current;
```

要检查您当前正在使用系统Ruby，请打开终端并输入以下内容：

```which ruby```

如果您使用的是Ruby系统，OS X将回应：

```/usr/bin/ruby```

您可以检查使用哪个版本的Ruby OS X：

```ruby -v```

## 安装RVM

### [RVM安装页面](https://rvm.io/rvm/install)

> 1.安装mpapis公钥。但是，正如安装页面所记录的，您可能需要gpg。Mac OS X不附带gpg，因此在安装公钥之前，您需要安装gpg。我用Homebrew安装了gpg ：

 ```
 brew install gnupg 
```

> 2.安装完gpg之后，你可以安装mpapis公钥：

```
gpg --keyserver hkp://pgp.mit.edu --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

> 3.安装最新版本的Ruby的RVM

```
\curl -sSL https://get.rvm.io | bash -s stable --ruby
```

![](https://raw.githubusercontent.com/kaqijiang/kaqijiang.github.io/master/images/Snip20180309_1.png)

> 安装成功，推出重新打开终端

## 使用RVM&Ruby

> 您可以列出可供RVM使用的Ruby版本rvm list

 ![](https://raw.githubusercontent.com/kaqijiang/kaqijiang.github.io/master/images/Snip20180309_2.png)

> 选择使用的版本

```
rvm use 2.4.1
```

>检查现在使用RVM管理的Ruby版本

```
$ which ruby
```

> 返回/Users/seven/.rvm/rubies/ruby-2.4.1/bin/ruby

> 则说明已经使用RVM管理的Ruby了非系统自带的。

### 常用指令

- ruby rvm 常用指令

```
$ ruby -v # 查看ruby 版本
$ rvm list known # 列出已知的 ruby 版本
$ rvm install 2.3.0 # 选择指定 ruby 版本进行更新
$ rvm get stable # 更新 rvm
$ rvm use 2.2.2 # 切换到指定 ruby 版本
$ rvm use 2.2.2 --default # 设置指定 ruby 版本为默认版本
$ rvm list # 查询已安装的 ruby 版本
$ rvm remove 1.9.2 # 卸载移除 指定 ruby 版本

$ curl -L https://get.rvm.io | bash -s stable # 安装 rvm 环境
$ curl -sSL https://get.rvm.io | bash -s stable --ruby # 默认安装 rvm 最新版本
$ curl -sSL https://get.rvm.io | bash -s stable --ruby=2.3.0 # 安装 rvm 指定版本
$ source ~/.rvm/scripts/rvm # 载入 rvm

```

- Gem

```
$ gem -v # 查看 gem 版本
$ gem source # 查看 gem 配置源
$ gem source -l # 查看 gem 配置源目录
$ gem sources -a url # 添加 gem 配置源（url 需换成网址）
$ gem sources --add url # 添加 gem 配置源（url 需换成网址）
$ gem sources -r url # 删除 gem 配置源（url 需换成网址）
$ gem sources --remove url # 删除 gem 配置源（url 需换成网址）
$ gem update # 更新 所有包
$ gem update --system # 更新 Ruby Gems 软件

$ gem install rake # 安装 rake，从本地或远程服务器
$ gem install rake --remote # 安装 rake，从远程服务器
$ gem install watir -v 1.6.2 # 安装 指定版本的 watir
$ gem install watir --version 1.6.2 # 安装 指定版本的 watir
$ gem uninstall rake # 卸载 rake 包
$ gem list d # 列出 本地以 d 打头的包
$ gem query -n ''[0-9]'' --local # 查找 本地含有数字的包
$ gem search log --both # 查找 从本地和远程服务器上查找含有 log 字符串的包
$ gem search log --remoter # 查找 只从远程服务器上查找含有 log 字符串的包
$ gem search -r log # 查找 只从远程服务器上查找含有log字符串的包

$ gem help # 提醒式的帮助
$ gem help install # 列出 install 命令 帮助
$ gem help examples # 列出 gem 命令使用一些例子
$ gem build rake.gemspec # 把 rake.gemspec 编译成 rake.gem
$ gem check -v pkg/rake-0.4.0.gem # 检测 rake 是否有效
$ gem cleanup # 清除 所有包旧版本，保留最新版本
$ gem contents rake # 显示 rake 包中所包含的文件
$ gem dependency rails -v 0.10.1 # 列出 与 rails 相互依赖的包
$ gem environment # 查看 gem 的环境

$ sudo gem -v # 查看 gem 版本（以管理员权限）
$ sudo gem install cocoa pods # 安装 CocoaPods（以管理员权限）
$ sudo gem install cocoapods # 安装 CocoaPods（以管理员权限）
$ sudo gem install cocoapods --pre # 安装 CocoaPods 至预览版（以管理员权限）
$ sudo gem install cocoapods -v 0.39.0 # 安装 CocoaPods 指定版本（以管理员权限）
$ sudo gem update cocoapods # 更新 CocoaPods 至最新版（以管理员权限）
$ sudo gem update cocoapods --pre # 更新 CocoaPods 至预览版（以管理员权限）
$ sudo gem uninstall cocoapods -v 0.39.0 # 移除 CocoaPods 指定版本（以管理员权限）

```

>pod

```

$ pod setup # CocoaPods 将信息下载到~/.cocoapods/repos 目录下。如果安装 CocoaPods 时不执行此命令，在初次执行 pod intall 命令时，系统也会自动执行该指令
$ pod --version # 检查 CocoaPods 是否安装成功及其版本号
$ pod install # 安装 CocoaPods 的配置文件 Podfile

```


支持一下，请他去喝杯咖啡
   