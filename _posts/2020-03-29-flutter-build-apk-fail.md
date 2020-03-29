---
layout: post
title: Flutter build apk failed 解决办法
category: Flutter
desc: Flutter build apk failed 解决办法
tag: [Flutter]
---

在写好 flutter APP 的之后，打包安装到手机，会出现失败的情况。出现这个 bug 有两种情况：

## ProcessException: ProcessException: Permission denied

1. 对于这个 bug ，把项目建在有读写执行权限的路径，而不要建在 <code>/usr/bin</code> 之类的文件夹下面

2. 如果显示 <gradlew> 文件没有执行权限的话，就要对该文件执行 <code>chmod +x</code> 来获取执行权限

> 解决方法来自 [stackoverflow](https://stackoverflow.com/search?q=ProcessException%3A+ProcessException%3A+Permission+denied){:target="_blank"}

## Execution failed for task ':path_provider:verifyReleaseResources'.

看到了 <code>path_provider</code> ，应该是 <code>path_provider</code> 的问题。解决办法就是修改 <code>path_provider</code> 的 <code>build.gradle</code> 中的 <code>compileSdkVersion</code> 版本为 28，就可以成功了。

打开了 <code>Android Studio</code> 的就可以直接在 <code>Android Studio</code> 里改了，在  <code>Gradle Script</code> 下面可以找到该文件。

没有的话可以直接到目录查找，该文件的目录是在 flutter 的安装目录 /flutter/flutter/.pub-cache/hosted/pub.flutter-io.cn/path_provider-0.4.1/android/build.gradle