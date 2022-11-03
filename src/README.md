# iOS逆向开发：MonkeyDev调试

* 最新版本：`v0.8`
* 更新时间：`20221103`

## 简介

整理iOS逆向开发中动态调试和插件tweak开发都会涉及到的工具MonkeyDev。先是概览；然后介绍环境搭建，包括初始化安装MonkeyDev，以如何及用Xcode+MonkeyDev去动态调试YouTube的ipa的过程；然后介绍MonkeyDev内部包含的内容，class-dump、LLDBTools等；然后总结心得，包括内部脚本逻辑、项目代码结构。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/ios_re_monkeydev_debug: iOS逆向开发：MonkeyDev调试](https://github.com/crifan/ios_re_monkeydev_debug)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [iOS逆向开发：MonkeyDev调试 book.crifan.org](https://book.crifan.org/books/ios_re_monkeydev_debug/website)
* [iOS逆向开发：MonkeyDev调试 crifan.github.io](https://crifan.github.io/ios_re_monkeydev_debug/website)

### 离线下载阅读

* [iOS逆向开发：MonkeyDev调试 PDF](https://book.crifan.org/books/ios_re_monkeydev_debug/pdf/ios_re_monkeydev_debug.pdf)
* [iOS逆向开发：MonkeyDev调试 ePub](https://book.crifan.org/books/ios_re_monkeydev_debug/epub/ios_re_monkeydev_debug.epub)
* [iOS逆向开发：MonkeyDev调试 Mobi](https://book.crifan.org/books/ios_re_monkeydev_debug/mobi/ios_re_monkeydev_debug.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 更多其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)
