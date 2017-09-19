title: 文档
---

欢迎使用 MonkeyDev，本文档将帮助您快速上手。如果您在使用过程中遇到问题，请查看 [问题解答](troubleshooting.html) 中的解答，或者在 [GitHub](https://github.com/AloneMonkey/MonkeyDev/issues) 上提问。

## MonkeyDev是什么？

MonkeyDev是一个基于Xcode模块技术快速开发越狱和非越狱插件的工具，可以自动完成逆向中的固定步骤，一键集成非越狱插件，大大提升逆向分析和开发效率！

MonkeyDev主要包括如下几个模块:

* Logos Tweak

使用[theos](https://github.com/theos/theos/wiki/Installation)提供的`logify.pl`工具将`*.xm`文件转成`*.mm`文件进行编译，集成了`CydiaSubstrate`，可以使用`MSHookMessageEx`和`MSHookFunction`来`Hook` OC函数、C/C++函数或指定地址。

* CaptainHook Tweak

使用[CaptainHook](https://github.com/rpetrich/CaptainHook/)提供的头文件进行OC函数的Hook，增加方法属性以及获取私有属性。

* Command-line Tool

可以直接创建运行于越狱设备的命令行工具

* MonkeyApp

自动给第三方应用集成Reveal、Cycript和注入dylib的模块，支持调试dylib和第三方应用，支持Pod给第三方应用集成SDK，只需要准备一个砸壳后的ipa或者app文件即可。

* MonkeyPod

将开发的非越狱插件制造成Pod以供其它人通过`pod install`的方法来使用。

* MonkeyAppMac

针对Mac逆向开发的模块，可以自动集成substitute，注入以及符号还原工作。

## 安装

安装 MonkeyDev 只需几分钟时间，若您在安装过程中遇到问题或无法找到解决方式，请 [提交问题](https://github.com/AloneMonkey/MonkeyDev/issues)，我会尽力解决您的问题。

### 安装前提

安装 MonkeyDev 相当简单。然而在安装前，您必须检查电脑中是否已安装并配置如下程序：

* 安装最新的theos

``` bash
sudo git clone --recursive https://github.com/theos/theos.git /opt/theos
```

* 安装ldid(如安装theos过程安装了ldid，跳过)

``` bash
brew install ldid
```

* 配置免密码登录越狱设备(如果没有越狱设备，跳过)

``` bash
ssh-keygen -t rsa -P ''
ssh-copy-id -i /Users/username/.ssh/id_rsa root@ip
```

### 安装MonkeyDev

有必备的应用程序安装完成后，即可开始安装MonkeyDev。

你可以通过以下命令选择指定的Xcode进行安装:

``` bash
sudo xcode-select -s /Applications/Xcode-beta.app
```

默认安装的Xcode为:

``` bash
xcode-select -p
```

执行安装命令:

``` bash
sudo /bin/sh -c "$(curl -fsSL https://raw.githubusercontent.com/AloneMonkey/MonkeyDev/master/bin/md-install)"
```

{% note info 影响Xcode吗？ %} 

MonkeyDev支持基于Xcode提供的自定义模块功能，并不会影响Xcode本身的功能，上面选择Xcode只是为了对Command-line Tool进行处理，模块安装后会在所有Xcode上面显示。

{% endnote %}

## 卸载与更新

### 卸载

如果不想使用MonkeyDev通过如下命令卸载即可:

``` bash
sudo /bin/sh -c "$(curl -fsSL https://raw.githubusercontent.com/AloneMonkey/MonkeyDev/master/bin/md-uninstall)"
```

### 更新

如果没有发布特殊说明，使用如下命令更新即可:


``` bash
sudo /bin/sh -c "$(curl -fsSL https://raw.githubusercontent.com/AloneMonkey/MonkeyDev/master/bin/md-update)"
```

更新之后重启下Xcode再新建MonkeyDev项目。

