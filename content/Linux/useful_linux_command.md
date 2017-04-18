---
title: "一些有用的 Linux 命令"
date: 2017-04-17
---

* 递归查找目录中文件的文本

```bash
find <folder> -type f -name <pattern> -print0 | xargs -0 grep <text>
```
