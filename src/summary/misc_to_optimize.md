# 待改进的细节

MonkeyDev调试时，偶尔有些细节，不是我们期望的=不尽如人意 的地方，整理如下：

## image list的输出的加载镜像列表，其中app自身的路径，不是iPhone端的app的自身路径

概述：

```bash
(lldb) image list -o -f
[  0] 0x0000000002bfc000 /Users/crifan/Library/Developer/Xcode/DerivedData/WhatsApp-fukxiohktyjtjqfvzmmrwluorwjn/Build/Products/Debug-iphoneos/WhatsApp.app/WhatsApp
[  1] 0x00000001069fc000 /Users/crifan/Library/Developer/Xcode/iOS DeviceSupport/13.3.1 (17D50)/Symbols/usr/lib/dyld
...
```

* 其中的app的路径是
  * `/Users/crifan/Library/Developer/Xcode/DerivedData/WhatsApp-fukxiohktyjtjqfvzmmrwluorwjn/Build/Products/Debug-iphoneos/WhatsApp.app/WhatsApp`
* 很明显是个Mac端的app的路径
* 而不是移动端=iPhone端的app的实际路径
* 而我们期望的是：iPhone端的app的实际路径
* 其值应该是
  * 【记录】iOS逆向WhatsApp：lldb+debugserver调试时加载的image镜像列表
* 中
```bash
(lldb) image list -o -f
[  0] 0x0000000004c6c000 /private/var/containers/Bundle/Application/CCFD22D2-32EE-4F23-9C81-226663100D40/WhatsApp.app/WhatsApp(0x0000000104c6c000)
[  1] 0x0000000108a44000 /Users/crifan/Library/Developer/Xcode/iOS DeviceSupport/13.3.1 (17D50)/Symbols/usr/lib/dyld
...
```
* 的
  * `/private/var/containers/Bundle/Application/CCFD22D2-32EE-4F23-9C81-226663100D40/WhatsApp.app/WhatsApp`
* 这种，app在iPhone中实际的真实的路径

详见

* 【记录】iOS逆向WhatsApp：MonkeyDev调试时加载的image镜像列表
