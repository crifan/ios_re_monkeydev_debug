# 常见错误

## curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused

```bash
curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused
Failed to download https://raw.githubusercontent.com/AloneMonkey/frida-ios-dump/3.x/dump.py to /opt/MonkeyDev/bin/dump.py
```

解决办法：

另外单独下载`frida-ios-dump`：

```bash
git clone https://github.com/AloneMonkey/frida-ios-dump.git
```

然后把其中的`dump.py`和`dump.js`拷贝到`/opt/MonkeyDev/bin/`

->

* `/opt/MonkeyDev/bin/dump.py`
* `/opt/MonkeyDev/bin/dump.js`

## Failed to extract /xxx/md-install.gvGnDuMp/file.tar.gz to

```bash
Failed to extract /var/folders/zz/zyxvpxvq6csfxvn_n0000000000000/T/md-install.gvGnDuMp/file.tar.gz to /var/folders/zz/zyxvpxvq6csfxvn_n0000000000000/T/md-install.KQllUKhp
```

解决办法：

自己新建一个临时目录：

```bash
mkdir -p /tmp/md_install/tempdirs
```

改`bin/md-install`为：

```bash
# export tempDirsFile="`mktemp -d -t $scriptName`/tempdirs"
export tempDirsFile="/tmp/md_install/tempdirs"
```

## Failed to echo into

错误现象：

```bash
line 82行：Failed to echo into
```

解决办法：

注释掉

```bash
    # echo "$tempDir" >> "$tempDirsFile" || \
    #     panic $? "Failed to echo into $tempDirsFile"
```

## File /xxx/Specifications/MacOSX Package Types.xcspec not found

```bash
➜  bin sudo bash md-install
...
File /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/Library/Xcode/Specifications/MacOSX Package Types.xcspec not found
```

解决办法：

* Xcode <13
  * 背景：存在`MacOSX Package Types.xcspec`，只是路径不对
  * 解决办法：改动路径或换用软链接
* Xcode 13+
  * 背景：不存在`MacOSX Package Types.xcspec`（和`MacOSX Product Types.xcspec`），所以要去网上下载后，再去：改动路径或换用软链接
    * 下载`MacOSX Package Types.xcspec`和`MacOSX Product Types.xcspec`
      * [qbs/share/qbs/modules/bundle at master · qbs/qbs](https://github.com/qbs/qbs/tree/master/share/qbs/modules/bundle)中，下载
        * https://github.com/qbs/qbs/blob/master/share/qbs/modules/bundle/MacOSX-Package-Types.xcspec
          * 保存为：`MacOSX Package Types.xcspec`
        * https://github.com/qbs/qbs/blob/master/share/qbs/modules/bundle/MacOSX-Product-Types.xcspec
          * 保存为：`MacOSX Product Types.xcspec`
      * 拷贝到（旧版Xcode中对应的）目录：`/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/Library/Xcode/PrivatePlugIns/IDEOSXSupportCore.ideplugin/Contents/Resources`

然后继续去操作：

* 【推荐】方法1：使用软链接

```bash
sudo ln -s /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/Library/Xcode/PrivatePlugIns/IDEOSXSupportCore.ideplugin/Contents/Resources /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/Library/Xcode/Specifications
```

* 方法2：（修改`md-install`脚本）改动路径

修改`/opt/MonkeyDev/bin/md-install`

修改路径，改为：

```bash
# macosxSDKSpecificationsPath=$macosSdkPlatformPath/Developer/Library/Xcode/Specifications
# packageTypesForMacOSXPath="$macosxSDKSpecificationsPath/MacOSX Package Types.xcspec"
# productTypesForMacOSXPath="$macosxSDKSpecificationsPath/MacOSX Product Types.xcspec"
macosxSDKSpecificationsPath=$macosSdkPlatformPath/Developer/Library/Xcode/PrivatePlugIns
packageTypesForMacOSXPath="$macosxSDKSpecificationsPath/IDEOSXSupportCore.ideplugin/Contents/Resources/MacOSX Package Types.xcspec"
productTypesForMacOSXPath="$macosxSDKSpecificationsPath/IDEOSXSupportCore.ideplugin/Contents/Resources/MacOSX Product Types.xcspec"
```

最后重新运行：

```bash
sudo bash md-install
```

即可

## File /xxx/IDEiOSSupportCore.ideplugin/xxx/Embedded-Device.xcspec not found

* 问题：

Xcode 14.3.1的Mac中，报错：

```bash
➜  bin sudo bash md-install
...
File /Applications/Xcode.app/Contents/PlugIns/IDEiOSSupportCore.ideplugin/Contents/Resources/Embedded-Device.xcspec not found
```

* 原因：`Xcode 13+`之后，部分路径变化了，所以找不到对应路径
* 解决办法：从Xcode中搜索到Embedded-Device.xcspec的实际位置，然后拷贝到报错的路径（如果不存在，先创建对应目录）即可
* 具体步骤

（1）找到Embedded-Device.xcspec

```bash
➜  ~ cd /Applications/Xcode.app/Contents
➜  Contents find . -name Embedded-Device.xcspec
./Developer/Library/Xcode/Plug-ins/XCBSpecifications.ideplugin/Contents/Resources/Embedded-Device.xcspec
```

找到：

* `/Applications/Xcode.app/Contents/Developer/Library/Xcode/Plug-ins/XCBSpecifications.ideplugin/Contents/Resources/Embedded-Device.xcspec`

（2）拷贝到报错目录

先新建该目录

```bash
sudo mkdir -p /Applications/Xcode.app/Contents/PlugIns/IDEiOSSupportCore.ideplugin/Contents/Resources/
```

再去拷贝：

```bash
sudo cp /Applications/Xcode.app/Contents/Developer/Library/Xcode/Plug-ins/XCBSpecifications.ideplugin/Contents/Resources/Embedded-Device.xcspec /Applications/Xcode.app/Contents/PlugIns/IDEiOSSupportCore.ideplugin/Contents/Resources/
```

确认文件的确存在：

```bash
➜  PlugIns ll /Applications/Xcode.app/Contents/PlugIns/IDEiOSSupportCore.ideplugin/Contents/Resources/
total 8
-rw-r--r--@ 1 root  wheel   437B 10 12 15:34 Embedded-Device.xcspec
```

最后重新去操作：

`sudo bash md-install`
