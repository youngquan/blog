---
title: 添加 sudo 用户
date: 2020-02-15 21:21:51
tags: Linux
categories: 工作记录
---

因为之前工作的原因，经常使用 root 用户来操作系统，实质上这是一种很不合适的用法，因为 root 用户的权限实在是太大了，不应该在日常的操作中使用，这也是我们经常在网上的很多文章里看到 sudo 的身影。下面记录一下在麒麟操作系统上创建一个 sudoers，让普通的用户无须知道 root 用户的密码也能拥有 root 权限。

<!-- more -->

```bash
# 查看 `/etc/sudoers` 的内容
$ cat /etc/sudoers
...
# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
...
# 将用户 yq 加入到 admin 和 sudo 两个用户组中
$ sudo usermod -a -G admin yq
$ sudo usermod -a -G sudo yq
```