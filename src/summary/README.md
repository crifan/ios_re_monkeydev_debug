# 心得

TODO：

* 【已解决】MonkeyDev的XCode项目编译报错：Unable to install This application’s application-identifier entitlement does not match that of the installed application
* 【记录】用XCode和MonkeyDev调试Logos越狱插件代码的效果
* 【已解决】用XCode和MonkeyDev去调试iOS抖音app
* 【未解决】给MonkeyDev的pack.sh加上echo的log日志调试分析运行逻辑
* 【记录】分析XCode+MonkeyDev编译抖音ipa详细过程的log
* 【未解决】XCode+MonkeyDev调试iOS的ipa除了首次外后续调试均会异常
* 【基本解决】Mac中用MonkeyDev+XCode去调试抖音脱壳ipa

---

* 每次调试
  * 先Clean再Build：绕过bug，否则导致调试ipa会崩溃
    * 详见：
      * 【已解决】XCode+MonkeyDev调试18.9.0抖音的崩溃问题：先Clean后再调试
* Xcode中，新增.xm文件的流程
  * 先新增.xm文件，再Build出.mm，再把.mm加到要编译的文件列表
    * 好像还要做一个什么映射还是关联？以便确保 自动从.xm生成.mm ？
