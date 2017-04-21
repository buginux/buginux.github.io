---
title: API 拾遗
date: 2017-04-21
---

## 手势共存

对于某些有互相关联的手势，如单击与双击，轻扫与长移可能会存在冲突，这时可以使用 `requireGestureRecognizerToFail` 方法。

```objc
UITapGestureRecognizer *tapGR =[[UITapGestureRecognizer alloc]initWithTarget:self action:@selector(handleTap:)];
[tapGR setDelegate:self];
[tapGR setNumberOfTapsRequired:1];
[self addGestureRecognizer:tapGR];


UITapGestureRecognizer *doubleTapGR = [[UITapGestureRecognizer alloc]initWithTarget:self action:@selector(handleDoubleTap:)];
[doubleTapGR setNumberOfTapsRequired:2];
[self addGestureRecognizer:doubleTapGR];

[tapGR requireGestureRecognizerToFail : doubleTapGR];
```

### 参考资料
 
* [http://stackoverflow.com/questions/11086280/requiregesturerecognizertofail-do-not-work](http://stackoverflow.com/questions/11086280/requiregesturerecognizertofail-do-not-work)
* [iOS开发之手势——UIGestureRecognizer 共存](http://www.cnblogs.com/iphone520/archive/2011/10/27/2226548.html)
