---
description: 九游广告
---

# Ngad

```text
    implementation 'com.libVigame.AD:Ngad:2.2.8'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keepattributes SourceFile,LineNumberTable
-keepattributes Signature
-keepattributes *Annotation*

## common
-keep public class * extends android.app.Activity
-keep public class * extends android.app.Application
-keep public class * extends android.app.Service

-keep class android.app.**{*;}
-dontwarn  android.app.**

-keep class android.support.v7.media.*{public *;}
-keep class android.support.v4.** { *; }
-dontwarn android.support.**

## network libs
-keep class android.net.http.** { *; }
-dontwarn android.net.**
-dontnote android.net.http.*

-keep class org.apache.http.** { *; }
-dontwarn org.apache.**
-dontnote org.apache.commons.codec.**
-dontnote org.apache.http.**

# Keep native methods
-keepclasseswithmembers class * {
    native <methods>;
}

### utdid
-keep class com.ta.utdid2.**{*;}
-keep class com.ut.device.**{*;}
-dontwarn com.ta.utdid2.**
-dontwarn com.ut.device.**

# Keep ngad-sdk classes
-keep interface cn.sirius.nga.** {*; }
-keep class cn.sirius.nga.** {*; }
-dontwarn cn.sirius.nga.**

-keep class cn.ninegame.library.** {*; }
-dontwarn cn.ninegame.library.**

-keep class cn.uc.gamesdk.** {*; }
-dontwarn cn.uc.gamesdk.**

-keep class com.qq.e.** {*; }
-dontwarn com.qq.e.**

-keep class com.taobao.** {*; }
-dontwarn com.taobao.**
-keep class android.taobao.** {*; }
-dontwarn android.taobao.**

-keep class com.UCMobile.Apollo.**{*;}


-keepattributes Signature
-keepattributes *Annotation*
-keep class com.mintegral.** {*; }
-keep interface com.mintegral.** {*; }
-keep class android.support.v4.** { *; }
-dontwarn com.mintegral.**
-keep class **.R$* { public static final int mintegral*; }
-keep class com.alphab.** {*; }
-keep interface com.alphab.** {*; }

-dontwarn com.uniplay.adsdk.**
-keep com.uniplay.adsdk.** {*;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过NgadAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

