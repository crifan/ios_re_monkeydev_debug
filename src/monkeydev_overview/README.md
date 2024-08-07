# MonkeyDev概览

[iOS逆向开发](https://book.crifan.org/books/ios_reverse_dev/website/)期间，其中常会涉及到[动态调试](https://book.crifan.org/books/ios_re_dynamic_debug/website/)和[写tweak插件](https://book.crifan.org/books/ios_re_jailbreak_tweak/website/)，其中有个很好用的工具就是：`MonkeyDev`

* `MonkeyDev`
  * 是什么：iOS逆向开发的成套工具
  * 概述：**iOSOpenDev的升级版** = 集成XCode和其他各种工具的更强的集成环境
  * 一句话描述：一个基于Xcode模块技术快速开发越狱和非越狱插件的工具，可以自动完成逆向中的固定步骤，一键集成非越狱插件，大大提升逆向分析和开发效率
  * 形式：Xcode的一个插件，可以新建MonkeyDev的相关不同类型的项目，做相关的逆向开发
  * 典型的用途
    * 砸壳出ipa后，用MonkeyDev+Xcode去动态调试
    * 用MonkeyDev去写（iPhone越狱后的）tweak插件
  * 主要包含模块
    * `Logos Tweak`
      * 使用theos提供的logify.pl工具将*.xm文件转成*.mm文件进行编译，集成了CydiaSubstrate，可以使用MSHookMessageEx和MSHookFunction来Hook OC函数、C/C++函数或指定地址
    * `CaptainHook Tweak`
      * 使用CaptainHook提供的头文件进行OC函数的Hook，以及属性的获取
    * `Command-line Tool`
      * 可以直接创建运行于越狱设备的命令行工具
    * `MonkeyApp`
      * 自动给第三方应用集成Reveal、Cycript和注入dylib的模块，支持调试dylib和第三方应用，支持Pod给第三方应用集成SDK，只需要准备一个砸壳后的ipa或者app文件即可
    * `MonkeyPod`
      * 将自动开发的非越狱插件制造成Pod以供其它人通过pod的方法来使用
    * `MonkeyAppMac`
      * 针对Mac逆向开发的模块，可以自动集成substitute，注入以及符号还原工作

## MonkeyDev vs iOSOpenDev

* MonkeyDev vs iOSOpenDev
  * MonkeyDev比iOSOpenDev）多出一些更加有用的参数：
    * MonkeyDevDevicePassword
      * 默认值：`alpine`
    * MonkeyDevTheosPath
      * 默认值：`/opt/theos`
    * MonkeyDevKillProcessOnInstall
      * 默认值：`SpringBoard`

## 官方资料
* 官方资料
  * Github
    * AloneMonkey/MonkeyDev: CaptainHook Tweak、Logos Tweak and Command-line Tool、Patch iOS Apps, Without Jailbreak.
      * https://github.com/AloneMonkey/MonkeyDev
    * wiki
      * https://github.com/AloneMonkey/MonkeyDev/wiki
        * [开始使用](https://github.com/AloneMonkey/MonkeyDev/wiki/%E5%BC%80%E5%A7%8B%E4%BD%BF%E7%94%A8)
        * [非越狱App集成](https://github.com/AloneMonkey/MonkeyDev/wiki/%E9%9D%9E%E8%B6%8A%E7%8B%B1App%E9%9B%86%E6%88%90)
    * 代码
      * [MonkeyDev/bin/md at master · AloneMonkey/MonkeyDev](https://github.com/AloneMonkey/MonkeyDev/blob/master/bin/md)
        * `export PATH=/opt/MonkeyDev/bin:$MonkeyDevTheosPath/bin:/usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin:$PATH`
    * 相关
      * AloneMonkey/MonkeyDev-Xcode-Templates: MonkeyDev-Xcode-Templates
        * https://github.com/AloneMonkey/MonkeyDev-Xcode-Templates
  * Blog
    * https://blog.alonemonkey.com/
      * [iOSOpenDev修改版MonkeyDev](https://blog.alonemonkey.com/2017/06/28/monkeydev/)
