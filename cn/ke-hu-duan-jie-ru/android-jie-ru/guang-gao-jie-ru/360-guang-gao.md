# 360广告

## 模块引入

1.1.0版本 采用本地导入的方式： 1.模块下载地址：

```text
http://192.168.1.252:8080/tree/VigameAndroidLibrary.git/master/libAD
```

下载libAD\_Ad360的zip格式的模块到本地并解压；

2.采用本地导入的方式，将libAD\_Ad360当做一个module引入你的工程当中

3.在app的build.gardle的dependencies前加入如下代码：

```text
    repositories {        flatDir {            dirs 'libs'            dirs project(':libAD_Ad360').file('libs')        }    }
```

4.在app的build.gardle的dependencies中加入以下代码

```text
    implementation project(':libAD_Ad360')    compile(name: 'msadsdk-release', ext: 'aar')    compile(name: 'news-lib-newssdk-release', ext: 'aar')
```

## 注意事项

```text
下面这个gif模块会和360广告冲突：implementation 'pl.droidsonroids.gif:android-gif-drawable:1.2.6'处理方式有下面两种，任选一种：1.注释掉pl.droidsonroids.gif:android-gif-drawable:1.2.6模块，不过出其他渠道的包需要这个模块，建议采用第二种方式2.在build.gradle的dependencies之前加入模块去重复的代码```textconfigurations {    all*.exclude group: 'pl.droidsonroids.gif'}```
```

## 混淆过滤

```text
-ignorewarning-repackageclasses ''-allowaccessmodification-optimizationpasses 2# Show line number when crash#-keepattributes SourceFile,LineNumberTable-dontskipnonpubliclibraryclassmembers-keepattributes Signature-keepattributes *Annotation*#Ad code-dontwarn com.qihoo.**-dontwarn com.qihoo360.**-dontwarn pl.droidsonroids.**-dontwarn com.androidquery.**-dontwarn com.lucan.ajtools.**-dontwarn okhttp3.**-dontwarn org.aspectj.**-dontwarn com.qq.e.**-dontwarn android.net.http.**-dontwarn okhttp3.**-dontwarn com.ak.torch.**-dontwarn okio.**-dontwarn javax.annotation.**-dontwarn org.conscrypt.**-dontwarn com.bytedance.**-dontwarn com.ss.android.**-dontwarn org.apache.http.**-keep class com.qihoo.** {*;}-keep class com.qihoo360.** { *; }-keep class pl.droidsonroids.** { *; }-keep class com.makeramen.** { *; }-keep class com.bytedance.sdk.openadsdk.** { *; }-keep class com.androidquery.callback.** {*;}-keep public interface com.bytedance.sdk.openadsdk.downloadnew.** {*;}-keep class android.support.v4.app.NotificationCompat**{    public *;}-keep class **.R$* {     *;}-keep class com.qq.e.** {    public protected *;}-keepclassmembers class * extends android.webkit.WebChromeClient{    public void openFileChooser(...);}-keep class org.apache.** {*;}-keep class android.net.http.** {*;}# A resource is loaded with a relative path so the package of this class must be preserved.-keepnames class okhttp3.internal.publicsuffix.PublicSuffixDatabase#Ad code End
```

## 集成测试

如何判断sdk是否初始化成功？

通过Ad360Agent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

## 广告接入

2019-8-8：banner广告存在关不掉的情况，因为是传入的Activity去加载banner广告，所以会在closebanner之后openBanner里加载360banner广告的代码还在进行。解决办法：添加flag在调用QihooGameSDK.stopShowBanner\(\)修复

