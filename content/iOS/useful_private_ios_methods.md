---
title: 有用的私有方法
date: 2017-04-18
---

* `recursiveDescription` 递归打印出视图层级
* `_printHierarchy` 打印出控制器视图层级
* `_autolayoutTrace` 简化版的 `recursiveDescription` 
* `_ivarDescription` 打印一个对象的所有实例变量
* `_methodDescription` 打印一个对象的所有类方法与实例方法

```objc
cy# [[UIApp keyWindow] recursiveDescription].toString()
<iConsoleWindow: 0x156b6410; baseClass = UIWindow; frame = (0 0; 320 480); autoresize = W+H; gestureRecognizers = <NSArray: 0x156b6bc0>; layer = <UIWindowLayer: 0x156b6720>>
   | <UILayoutContainerView: 0x16258d80; frame = (0 0; 320 480); autoresize = W+H; layer = <CALayer: 0x16258e00>>
   |    | <UITransitionView: 0x16259610; frame = (0 0; 320 480); clipsToBounds = YES; autoresize = W+H; layer = <CALayer: 0x16259760>>
   |    |    | <UIViewControllerWrapperView: 0x16243bb0; frame = (0 0; 320 480); autoresize = W+H; layer = <CALayer: 0x1625a670>>
   |    |    |    | <UILayoutContainerView: 0x1601dd70; frame = (0 0; 320 480); autoresize = W+H; gestureRecognizers = <NSArray: 0x16001650>; layer = <CALayer: 0x16073fe0>>
   |    |    |    |    | <UINavigationTransitionView: 0x16004cc0; frame = (0 0; 320 480); clipsToBounds = YES; autoresize = W+H; layer = <CALayer: 0x16004e10>>
   |    |    |    |    |    | <UIViewControllerWrapperView: 0x1629d9a0; frame = (0 0; 320 480); layer = <CALayer: 0x1629da10>>
...
   |    |    | <MMBadgeView: 0x160055a0; baseClass = UIImageView; frame = (203 1; 20 20); opaque = NO; userInteractionEnabled = NO; layer = <CALayer: 0x16005640>>
   |    |    |    | <MMUILabel: 0x16004ec0; baseClass = UILabel; frame = (0 0; 0 0); hidden = YES; userInteractionEnabled = NO; tag = 10032; layer = <CALayer: 0x16004f70>>
   |    |    | <MMBadgeView: 0x16259810; baseClass = UIImageView; frame = (283 -4; 30 30); hidden = YES; opaque = NO; userInteractionEnabled = NO; layer = <CALayer: 0x162598b0>>
   |    |    |    | <MMUILabel: 0x1625a180; baseClass = UILabel; frame = (0 0; 0 0); userInteractionEnabled = NO; tag = 10032; layer = <CALayer: 0x1625a230>>
```

```objc
cy# [[UIApp keyWindow] _autolayoutTrace].toString()
*<iConsoleWindow:0x156b6410>
|   *<UILayoutContainerView:0x16258d80>
|   |   *<UITransitionView:0x16259610>
|   |   |   *<UIViewControllerWrapperView:0x16243bb0>
|   |   |   |   *<UILayoutContainerView:0x1601dd70>
|   |   |   |   |   *<UINavigationTransitionView:0x16004cc0>
|   |   |   |   |   |   *<UIViewControllerWrapperView:0x1629d9a0>
...
|   |   |   |   <MMUILabel:0x1624b250>
|   |   |   <MMBadgeView:0x160055a0>
|   |   |   |   <MMUILabel:0x16004ec0>
|   |   |   <MMBadgeView:0x16259810>
|   |   |   |   <MMUILabel:0x1625a180>
```

```objc
cy# [choose(SBApplication)[0] _ivarDescription].toString()
<SBApplication: 0x1766cab0>:
in SBApplication:
    _bundleIdentifier (NSString*): @"com.apple.social.remoteui.SocialUIService"
    _displayIdentifier (NSString*): @"com.apple.social.remoteui.SocialUIService"
    _path (NSString*): @"/Applications/SocialUIService.app"
    _bundleVersion (NSString*): @"87"
    _defaultImageNamesByScreenType (NSMutableDictionary*): <__NSDictionaryM: 0x17672a90>
    _defaultImageNamesForOrientation (NSDictionary*): nil
...
in NSObject:
    isa (Class): SBApplication
```

```objc
cy# [choose(SBApplicationController)[0] _methodDescription].toString()
<SBApplicationController: 0x17642990>:
in SBApplicationController:
    Class Methods:
        + (void) setClearSystemAppSnapshotsWhenLoaded:(BOOL)arg1; (0x1b2ad1)
...
        + (id) sharedInstanceIfExists; (0x1b2b6d)
    Instance Methods:
        - (id) setupApplication; (0x1b3e3d)
...
    - (id) applicationWithDisplayIdentifier:(id)arg1; (0x1b3d0d)
in NSObject:
    Class Methods:
        + (bool) cy\$hasImplicitProperties; (0xdb45d80)
...
        + (void) finalize; (0x39a49ad1)
    Properties:
        @property (nonatomic) BOOL isAccessibilityElement;  (@dynamic isAccessibilityElement;)
...
        @property (nonatomic) BOOL shouldGroupAccessibilityChildren;  (@dynamic shouldGroupAccessibilityChildren;)
    Instance Methods:
        - (id) cy\$toCYON:(bool)arg1 inSet:(set<void *, std::less<void *>, std::allocator<void *> >*)arg2; (0xdb45b60)
...
        - (void) finalize; (0x39a49ad5)
```
