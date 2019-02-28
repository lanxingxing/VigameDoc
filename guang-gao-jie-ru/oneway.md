# OneWay

## 模块引入

```text
    implementation 'com.libVigame.AD:OneWay:2.1.7'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
############################################
##           OneWaySDK 混淆配置             ##
############################################
-keepattributes *Annotation*
-keep enum mobi.oneway.sdk.* {*;}
-keep class mobi.oneway.sdk.** {*;}


############################################
##           OkDownload 混淆配置            ##
############################################

-dontwarn com.liulishuo.okdownload.**
-keep class com.liulishuo.okdownload.core.breakpoint.BreakpointStoreOnSQLite {
    public com.liulishuo.okdownload.core.breakpoint.DownloadStore createRemitSelf();
    public com.liulishuo.okdownload.core.breakpoint.BreakpointStoreOnSQLite(android.content.Context);
}
# okdownload:okhttp
-keepnames class com.liulishuo.okdownload.core.connection.DownloadOk


############################################
##             OkHttp 混淆配置              ##
############################################

# okhttp https://github.com/square/okhttp/#proguard
-dontwarn okhttp3.**
-dontwarn okio.**
-dontwarn javax.annotation.**
-dontwarn org.conscrypt.**
# A resource is loaded with a relative path so the package of this class must be preserved.
-keepnames class okhttp3.internal.publicsuffix.PublicSuffixDatabase
```

## 集成测试

如何判断sdk是否初始化成功？

通过OneWayAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

