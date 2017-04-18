---
title: "环境配置问题"
date: 2017-04-18
---

## 问题

Could not find function xmlCheckVersion in library libxml2

## 解决办法

Homebrew doesn't link libxml and libxslt to avoid conflicts. You need to `--force` them.

```bash
brew link libxml2 --force
brew link libxslt --force
```

I faced this problem when I upgraded to latest OS X. I wrote a [blog post](http://masnun.com/2015/07/14/fixing-lxml-installation-on-os-x.html) on it detailing the issue.

## 参考资料

* [http://stackoverflow.com/questions/34240287/trouble-installing-lxml-with-pip](http://stackoverflow.com/questions/34240287/trouble-installing-lxml-with-pip)

---
