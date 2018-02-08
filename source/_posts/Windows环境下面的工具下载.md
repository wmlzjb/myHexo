---
title: Windows环境下面的工具下载
date: 2018-01-15 19:33:18
tags: 
 - Xamarin
 - Android
 - Ios
 - C#
categories: 
- 移动开发
---
Windows下面的安装
1. 安装环境介绍：
    Win10 企业版64位、VS2017

2. 安装jdk
    到oracle官方下载 jdk-8u152-windows-x64.exe 并安装
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
    默认是安装到C盘的，根据自己的情况选择目录后完成安装，接下来进行环境变量的设置
    添加环境变量 JAVA_HOME：
    C:\Program Files\Java\jdk1.8.0_152
    添加环境变量 CLASSPATH：
    %JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
    修改环境变量 Path，在最前面加入以下值：
    %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
    安装完成之后在CMD里输入“java -version”可查看成功安装之后的版本号

3. 安装Android SDK，下载 installer_r24.4.1-windows.exe，我这里是安装到“E:\Develop\Android\android-sdk”目录下，安装完后设置环境变量，右键我的电脑——属性——高级系统设置——高级——环境变量——系统变量里，找到 Path，双击进行修改，在最前面增加：
    .;E:\Develop\Android\android-sdk\tools;E:\Develop\Android\android-sdk\platform-tools;
    （注意末尾必须有 ; 英文分号，如果 Path 里面已经有这个值，就不需要添加）
    如果要更新SDK，以下两种方式选其一：
    (1) (推荐)目前国内用户可以直接下载了，速度还不错
    (2) 打开Android SDK Manager，Tools -> Options...，HTTP Proxy Server里填“mirrors.neusoft.edu.cn”，Http Proxy Port里填“80”，然后勾选“Force https://...sources to be fetched using http://...”，Close后在Packages里Reload或者关闭重新打开都可。
大连东软信息学院镜像服务器地址:
- IPv4: http://mirrors.neusoft.edu.cn 端口：80

4. 安装NDK，复制 android-ndk-r10e-windows-x86_64.exe 至指定目录下，双击解压即可，我这里是安装到“E:\Develop\Android\android-ndk”目录下，安装完后新建一个环境变量 ANDROID_NDK_PATH，值如下：
    E:\Develop\Android\android-ndk\android-ndk-r10e
    装完NDK之后记得最后在Virsual Studio和VS里去设置NDK路径。

5. 在线安装，VS2017安装程序勾选移动模块即可

6. (推荐)离线安装，微软收购Xamarin之后也只需要安装一个文件了，原来的XamarinStudio也不用了
    1) Xamarin.VisualStudio_x.x.x.x.msi

附官方下载地址：
http://dl.google.com/android/ndk/android-ndk-r10e-windows-x86_64.exe
http://dl.google.com/android/installer_r24.4.1-windows.exe
http://download.xamarin.com/GTKforWindows/Windows/gtk-sharp-2.12.30.msi
https://dl.xamarin.com/XamarinforVisualStudio/Windows/Xamarin.VisualStudio_4.8.0.1242444.msi
http://download.xamarin.com/studio/Windows/XamarinStudio-5.10.3.26-0.msi
以上链接如不是最新，以官方最新为主，官方更新地址如下：
http://xamarin.com/installer_assets/v3/Windows/Universal/InstallationManifest.xml
https://developer.xamarin.com/releases/current/

更新日志：
https://developer.xamarin.com/releases/current/

8. 关于在Window下开发安卓用什么模拟器，这里必须推荐一款(如果是VS2015那就用自带的吧)：
首页直接下载模拟器 ：http://www.droid4x.cn/
装完之后即可使用，可连VS调试，速度很不错。

作者：Hegel_SU
链接：https://www.jianshu.com/p/c67c14b3110c
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。