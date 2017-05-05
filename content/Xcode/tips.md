---
title: "常用小技巧"
date: 2017-05-02
---

## Code Snippets 目录

```bash
/Users/<username>/Library/Developer/Xcode/UserData/CodeSnippets
```

## 获取 Xcode 的 UUID

```bash
$ defaults read /Applications/Xcode.app/Contents/Info DVTPlugInCompatibilityUUID
```

## 升级 Xcode 插件失效修复

``Bash
$ find ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins -name Info.plist -maxdepth 3 | xargs -I{} defaults write {} DVTPlugInCompatibilityUUIDs -array-add `defaults read /Applications/Xcode.app/Contents/Info.plist DVTPlugInCompatibilityUUID`
```
