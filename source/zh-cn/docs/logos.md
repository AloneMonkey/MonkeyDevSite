title: 文档
---

## 项目说明

选择Logos Tweak模板之后，新建出来的工程目录结构如下图所示，注意.xm文件格式Xcode不识别需要在Xcode右侧选择Type为Objective-C++ Source，然后重新打开。

![image](http://7xtdl4.com1.z0.glb.clouddn.com/logstemplate.png)

* Logs.xm: 文件和theos中的文件一样直接写Logs语法即可，编译时会通过logos.pl转成Logs.mm参与编译，想要查看原理可以看这个文件。
* control: 和theos中的control一样用于指定deb包的一些信息
* Logs.plist: 和theos中plist文件一样用于指定需要注入的目标应用的过滤器
* CydiaSubstrate: Logos Tweak依赖于CydiaSubstrate库，项目会自动链接

## 项目配置

另外在Build Settings的最下面会提供一些选项来设置相关操作，如下图，关于这些设置的说明可以查看表格。

![image](http://7xtdl4.com1.z0.glb.clouddn.com/logsbuildsettings.png)

|设置项|意义|
|--|--|
|MonkeyDevBuildPackageOnAnyBuild|每次build都生成deb包|
|MonkeyDevClearUiCacheOnInstall|安装时clear uicache|
|MonkeyDevCopyOnBuild|build的时将deb包拷贝到设备的/var/root/MonkeyDevBuilds/目录|
|MonkeyDevDeviceIP|目标设备的ip地址，默认USB连接，localhost|
|MonkeyDevDevicePort|目标设备的端口，默认22|
|MonkeyDevInstallOnAnyBuild|每次build都将deb安装到设备|
|MonkeyDevInstallOnProfiling|点击Profile才将deb安装到设备|
|MonkeyDevPath|MonkeyDev的安装路径，默认的，不用修改|
|MonkeyDevTheosPath|theos的安装路径|
|MonkeyDevKillProcessOnInstall|安装的时候杀掉指定的进程，填写进程名|

其中需要设置的就是MonkeyDevDeviceIP和MonkeyDevDevicePort，如果没有设置默认读取环境变量中的MonkeyDevDeviceIP和MonkeyDevDevicePort。

编写完成代码之后，按快捷键Commonand + B就会以Debug模式安装到手机上面，按快捷键Command + Shift + i以Release模式安装，但是这种方式不会输出Log信息。