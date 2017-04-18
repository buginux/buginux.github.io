---
title: "环境配置问题"
date: 2017-04-18
---

## 问题

解决 Xcode 7 编译出现大量警告

Xcode7后运行以前的项目后出现大量的警告如：

```bash
(null): warning: /var/folders/p4/z7zy68r92hd3p5ry5g2v3k_8rlwzzr/C/org.llvm.clang.dalmo/ModuleCache/1TXZDLI9N2EMV/Foundation-3DFYNEBRQSXST.pcm: No such file or directory。
```

作为一个有洁癖的我反正是不能忍，出现警告的大致原因跟我上面提到的开启Bitcode，.dSYM文件不能用来符号化有关，Xcode试图去创建dSYM文件，但是你又不需要。

## 解决办法

1. Build Settings ——>Build Options——>Debug Information Format

2. Debug下的DWARF with dsYM File改成DWARF

3. Release下的还是之前默认的DWARF with dsYM File不变

---

## 问题

从项目中删除了某个目录、文件以后，编译出现警告信息：

```bash
ld: warning: directory not found for option“XXXXXX”
```

很奇怪，为什么已经从项目中删除了文件和文件夹还是报这个警告呢？

## 解决方法

1.选择工程, 编译的 (targets)

2.选择 Build Settings 菜单

3.查找 Library Search Paths 和 Framework Search Paths， 删掉编译报warning的路径

