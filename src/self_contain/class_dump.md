# class-dump

TODO：

* 【记录】支持iOS的Swift和ObjC混编的class-dump
* 【已解决】MonkeyDev安装失败：Failed to download AloneMonkey/frida-ios-dump/3.x/dump.py
* 【已解决】Mac中用class-dump导出YouTube头文件

---

* `class-dump`：是编译好的二进制支持swift混淆的版本
  * 对应路径：`/opt/MonkeyDev/bin/class-dump`
  * 版本信息
    ```bash
    ➜  ~ class-dump --version
    class-dump 3.5 (64 bit) (Debug version compiled Sep 17 2017 16:24:48) compiled Sep 17 2017 16:24:48
    ```

## 让MonkeyDev的class-dump全局可用

此次，之前已安装好`iOSOpenDev`的环境和设置了相关的环境变量：

* `~/.zshrc`
  ```bash
  export iOSOpenDevPath=/opt/iOSOpenDev
  export iOSOpenDevDevice=
  export PATH=/opt/iOSOpenDev/bin:$PATH
  ```

使得此处找到的`class-dump`是`iOSOpenDev`版本的：

```bash
➜  ~ which class-dump
/opt/iOSOpenDev/bin/class-dump
```

此处想要，把全局的，命令行行中找到的`class-dump`换成（支持Swift和ObjC混淆的）`MonkeyDev`的

可以去：设置PATH环境变量，加上MonkeyDev的路径

编辑`~/.zshrc`，在最末尾加上：

```bash
export MonkeyDevPath=/opt/MonkeyDev
export MonkeyDevDeviceIP=
export PATH=/opt/MonkeyDev/bin:$PATH
```

保存退出。重启终端，即可实现我们的效果：

```bash
➜  ~ which class-dump
/opt/MonkeyDev/bin/class-dump
```
