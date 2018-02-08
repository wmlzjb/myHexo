---
title: Mac环境下面的工具下载
date: 2018-01-15 19:33:09
tags: 
 - Xamarin
 - Android
 - Ios
 - C#
 - Mac
categories: 
- 移动开发
---
Mac下面的安装
1. 安装mac os，这方面就不多说了，可以百度，也可以参考下面文章
http://www.jianshu.com/p/25d2d781bd98
Mac装好之后开发Xamarin必须装XCode，XCode可以直接到AppStore上下载安装，免费的，装完之后先运行一下XCode，第一次运行需要初始化组件，完成之后再在终端里输入以下命令完成tools的安装：
xcode-select --install

如果Xamarin Studio 6.2及以上的版本代码管理无法看到svn，论坛里的解决方案是终端里创建一个链接即可：
sudo ln -s "/Applications/Xcode.app/Contents/Developer/" "/var/db/xcode_select_link"

2. 自动安装：到官方网站下载在线安装程序XamarinInstaller.dmg进行全自动安装，安装过程中要下载很多文件（国内需要翻墙），所以此步会有点漫长，等待自动安装完成即可。自动安装程序下载地址：
https://www.visualstudio.com/en-us/news/releasenotes/vs2017-mac-relnotes
自动安装后请打开Xamarin进行更新到最新版即可。

3. 手动离线安装(将suyx修改为你自己的Mac账户名)：
还是喜欢离线下载了安装，安装包下载临时目录为：
/Users/suyx/Library/Caches/XamarinInstaller/Universal
更新包临时下载目录为：
/Users/suyx/Library/Caches/VisualStudio/7.0/TempDownload
下载文件
https://dl.xamarin.com/MonoFrameworkMDK/Macx86/MonoFramework-MDK-5.4.1.7.macos10.xamarin.universal.pkg
http://download.xamarin.com/Installer/MonoForAndroid/jdk-8u101-macosx-x64.dmg
http://dl.google.com/android/android-sdk_r24.4.1-macosx.zip
https://dl.xamarin.com/VsMac/VisualStudioForMac-7.3.3.5.dmg
https://dl.xamarin.com/MonoforAndroid/Mac/xamarin.android-8.1.3-0.pkg
https://dl.xamarin.com/MonoTouch/Mac/xamarin.ios-11.6.1.3.pkg
https://dl.xamarin.com/XamarinforMac/Mac/xamarin.mac-4.0.0.215.pkg
https://dl.xamarin.com/Installer/haxm-macosx_v6_0_5.zip
https://dl.xamarin.com/profiler/profiler-mac-1.6.0-27.pkg
https://dl.xamarin.com/interactive/XamarinInteractive-1.3.2.pkg
https://download.microsoft.com/download/1/1/4/114223DE-0AD6-4B8A-A8FB-164E5862AF6E/dotnet-dev-osx-x64.1.0.3.pkg
安装完之后再更新最新的正式版即可。
以上链接如不是最新，以官方为主，官方更新地址如下：
http://xamarin.com/installer_assets/v3/Mac/Universal/InstallationManifest.xml
https://developer.xamarin.com/releases/current/

文件都下载完成之后，开始手动安装步骤：
(1)安装Java环境(开发Android必需)：打开jdk-xxx-macosx-x64.dmg进行安装，安装完成之后在终端里输入"java -version"可查看安装成功之后的版本号；
(2)安装Android SDK(开发Android必需)：将android-sdk_xxx-macosx.zip复制到目录“~/Library/Developer/Xamarin”下(目录不存在请手工创建)，然后双击android-sdk_xxx-macosx.zip解压完毕，然后在终端里进入解压之后的 tools 目录，运行“./android”即可打开SDK Manager进行更新，更新方法见Win下的安装说明，为了保证Xamarin能检测到SDK，至少必须将“Android SDK Platform-tools”更新完成，其它的根据自己开发所需进行更新(程序运行好久都不见菜单，原来是要先点下桌面，再点下sdk manager才会有)。
(3)安装Android NDK：将android-ndk-r10e-darwin-x86_64.bin复制到目录“~/Library/Developer/Xamarin/android-ndk”下(目录不存在请手工创建)，终端里切到 android-ndk 目录之后运行如下两行命令进行解压完成即可：
chmod a+x android-ndk-r10e-darwin-x86_64.bin
./android-ndk-r10e-darwin-x86_64.bin
(4)安装Mono环境：打开 MonoFramework-MDK-xxx.macos10.xamarin.x86.pkg 后安装完成即可。
(5)安装开发IDE：打开 VisualStudioForMac-xxx.dmg 后安装完成即可。
(6)安装xamarin.ios(开发iOS必需，根据个人需求选择安装)：打开 xamarin.ios-xxx.pkg 后安装完成即可。
(7)安装xamarin.android(开发Android必需，根据个人需求选择安装)：打开 xamarin.android-xxx.pkg 后安装完成即可。
(8)安装xamarin.mac(开发Mac程序必需，根据个人需求选择安装)：打开 xamarin.mac-xxx.pkg 后安装完成即可。
(9)设置Xamarin环境：打开XamarinStudio->Preferences->工程->SDK Locations->Android，可看到SDK和NDK为空，设置后的结果如下(路径可直接在你的编辑器里修改后复制进去即可)：
Android SDK(将suyx修改为你自己的Mac账户名):
/Users/suyx/Library/Developer/Xamarin/android-sdk-macosx
Java SDK(这个默认已装好):
/usr
Android NDK(将suyx修改为你自己的Mac账户名):
/Users/suyx/Library/Developer/Xamarin/android-ndk/android-ndk-r10e
(10)Xamarin自动升级的更新文件下载路径为(将suyx修改为你自己的Mac账户名)：
/Users/suyx/Library/Caches/VisualStudio/7.0/TempDownload

4. MonoTouch 8.10.x更新日志：
https://developer.xamarin.com/releases/ios/xamarin.ios_8/xamarin.ios_8.13/

5. 有时候生成的adhoc包用itools就是装不上，后来又找了个程序不错，推荐一下：
同步助手：http://zs.tongbu.com/

作者：Hegel_SU
链接：https://www.jianshu.com/p/c67c14b3110c
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。