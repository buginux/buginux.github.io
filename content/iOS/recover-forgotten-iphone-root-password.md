---
title: 找回 iPhone 的 root 密码
date: 2017-03-25 11:18:07
---

此方法针对的是越狱手机，非越狱手机本身也无法使用 ssh 跟 root 用户，所以无所谓找不找回 root 密码。

1. 从 cydia 中安装 iFile
2. 使用 iFile 打开 `/etc/master.passwd`
3. 找到类似 `root:UIGASB5XWDrOc:0:0::0:0:` 的内容
4. 使用 [Crypt Tool](http://www.functions-online.com/crypt.html) 生成一个新密码
5. 使用新的生成密码替换 root: 第一个 :0 间的内容
6. 保存
7. 完成，使用新的 root 密码进行 ssh 登录，验证更新是否成功


## 参考资料
- [Recover forgotten iPhone root password](http://realityloop.com/blog/2009/12/31/recover-forgotten-iphone-root-password)
