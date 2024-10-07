# 初始化MonkeyDev开发环境

> [!WARNING|title:安装路径/opt不能变]
> 后续的`MonkeyDev`、`theos`等的安装路径选择，虽然按道理可以自定义，但是此处内部很多脚本貌似只支持固定的默认的路径
> 
> 所以，只能安装到默认的固定路径：
> * `/opt/MonkeyDev`
> * `/opt/theos`
> 
> 而不能轻易改变路径，否则后续会出现很多诡异的问题

初始化搭建MonkeyDev环境=初始化安装MonkeyDev：

* 下载theos
  ```bash
  sudo git clone --recursive https://github.com/theos/theos.git /opt/theos
  ```
* 下载MonkeyDev（到固定位置：`/opt/MonkeyDev`）
  ```bash
  sudo git clone https://github.com/AloneMonkey/MonkeyDev.git /opt/MonkeyDev
  ```
* 本地运行脚本去安装
  ```bash
  cd MonkeyDev/bin
  sudo bash md-install
  ```

## 搭建好的环境，对应目录的文件

```bash
 crifan@licrifandeMacBook-Pro  ~  ll /opt/MonkeyDev
total 88
drwxr-xr-x   7 root  wheel   224B  6 28 22:01 Frameworks
-rw-r--r--   1 root  wheel    34K  6 28 22:26 LICENSE
drwxr-xr-x   3 root  wheel    96B  6 28 22:01 Librarys
drwxr-xr-x   4 root  wheel   128B  6 28 22:01 MFrameworks
-rw-r--r--   1 root  wheel   1.7K  6 28 22:26 README.md
drwxr-xr-x   3 root  wheel    96B  6 28 22:01 Resource
drwxr-xr-x   4 root  wheel   128B  6 28 22:01 Tools
drwxr-xr-x  12 root  wheel   384B  6 28 22:07 bin
-rw-r--r--   1 root  wheel   802B  6 28 22:26 change.log
drwxr-xr-x   4 root  wheel   128B  6 28 22:01 include
drwxr-xr-x  14 root  wheel   448B  6 28 22:03 templates

 crifan@licrifandeMacBook-Pro  ~  ll /opt/theos
total 112
-rw-r--r--   1 root  wheel   5.1K  6 28 21:59 CODE_OF_CONDUCT.md
-rw-r--r--   1 root  wheel    35K  6 28 21:59 LICENSE.md
-rw-r--r--   1 root  wheel   1.0K  6 28 21:59 Prefix.pch
-rw-r--r--   1 root  wheel   3.1K  6 28 21:59 README.md
drwxr-xr-x  17 root  wheel   544B  6 28 21:59 bin
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 extras
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 include
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 lib
drwxr-xr-x  28 root  wheel   896B  6 28 21:59 makefiles
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 mod
-rw-r--r--   1 root  wheel   657B  6 28 21:59 package.json
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 sdks
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 templates
drwxr-xr-x   3 root  wheel    96B  6 28 21:59 toolchain
drwxr-xr-x   8 root  wheel   256B  6 28 21:59 vendor
```