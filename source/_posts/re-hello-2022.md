---
title: Re- Re- Hello World?
date: 2022-3-20 17:28:10
tags:
---
我又回来了。这其实是这个blog第二次rebuild了。
最早的第一版里的文章都直接丢掉了呢。（嘛就算留下也没什么用所以其实也无所谓了）
然后二代目根本就没写东西，只写了个一万人写过的，Hexo怎么初期配置。

于是这是三代目。主要做了这几件事。

1. 把HasukaPoi/hexo-source里的东西搬下来重新建了本地repo，并force push到HasukaPoi/HasukaPoi.github.io的hexo_src分支。（这个分支在二代目就创建了但是里面没东西，干啥呢我。）
2. 把Hexo的版本升级到最新。这个下面贴一下简单操作过程（虽然也是抄来的）。
3. 把使用的主题版本升级到最新。其中默认主题Landscape就升一下依赖版本以解决GitHub的Dependabot alerts（目前还没解决），NexT是重新替换了最新版进来。

<!-- more -->

## 闲扯

为什么我的GitHub出现了这么长的一个空窗期呢，我也不知道。但是也补不上了xsk
这次突然意识到VSCode很好用。
哦对了最新版NexT怎么没有像样的文档…………还是我眼瞎找不到。
以及为什么写点东西这么费劲。

## 关于升级

参考这里：[hexo 版本升级 | Geneliunx](https://geneliunx.com/2020/10/29/hexo-version-upgrade/)

简而言之，`npm-check` → `npm-upgrade` → `npm update --save`
前两个都是以包的形式存在的，没有的话`npm install -g`一下哦。

## 另一个奇怪的警告信息

启动本地hexo server的时候会提示

```shell
Hasuka@DESKTOP-A4FIAHE MINGW64 /d/Learning/hexo-source-2019 (hexo_src)
$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
(node:21164) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:21164) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:21164) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:21164) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:21164) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:21164) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
```

搜索之后知道是由于stylus这个包引起的。而nib又指定了0.54.5（解决问题的最低版本是0.54.8），所以修改package-lock.json可以解决问题。
修改后需要执行`npm install`以使设置生效。

解决方法参考这里：[解决 Hexo 使用 Node.js 14 Accessing non-existent property问题](https://zhuanlan.zhihu.com/p/397813964)

UPDATE：修改版本号从`0.54.5`为`~0.54.5`并没有用。改成`0.54.8`也……没有用…………

上文中提到

> 如果还是有警告，可以cd node_module/nib，强行把它的stylus升级到0.54.8（不推荐这么做）

估计这样可以解决，但算了，是warning又不是error（てへぺろ

## Velocity is not defined

deploy出来的静态HTML出来这玩意儿。

…………为什么本地Server的时候是好的，generate和deploy就坏了啊。

搜了一圈解决方法没用，倒是偶然发现早年设置的CNAME（不再使用）删掉之后莫名其妙就好了。看来问题就在这里

感谢您的阅读。

