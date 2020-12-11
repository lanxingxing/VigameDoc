---
description: 腾讯YSDK
---

# YSdk

### 模块引入



本地引入，模块下载地址：[http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libPay/libPayExt_YSDK&h=master&format=zip](http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libPay/libPayExt_YSDK&h=master&format=zip)

setting.gradle中添加

```text
include ':libPayExt_YSDK'
project(':libPayExt_YSDK').projectDir = new File('目录\\libPayExt_YSDK')
```

app目录build.gradle中修改：

```text
    xxxximplementation project(':libPayExt_YSDK')
```

## 

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
|  |  | eg： |

### build.gradle中需添加

```text
  manifestPlaceholders = [
                QQ_APP_ID:"游戏的QQAPPID",
                WX_APP_ID:"游戏的微信APPID",
               ...
        ]
```

## 配置文件说明

在包名目录下添加 .wxapi 包名，然后添加WXEntryActivity.java文件， 文件内容为

```text
public class WXEntryActivity extends com.tencent.ysdk.module.user.impl.wx.YSDKWXEntryActivity {

}
```

```text
assets 目录需添加 ysdkconf.ini文件
;**************游戏相关配置, 游戏需要根据各自情况修改 START **********
;游戏的QQAPPID
QQ_APP_ID= qq appid
;游戏的微信APPID
WX_APP_ID=微信appid
;游戏的OFFER_ID
OFFER_ID= qq appid
;***************游戏配置项, 游戏需要根据各自情况修改 END **************

;************* YSDK相关配置项,游戏需要根据各自情况修改 START **********
;联调环境
;YSDK_URL=https://ysdktest.qq.com
;正式环境
YSDK_URL=https://ysdk.qq.com
;************** YSDK相关配置项,游戏需要根据各自情况修改 END **************
```

```text
如果用 ysdk支付需注意：

assets 目录需添加 feedata_ysdk.xml文件

<data>    
    <midasKey>米大师支付key</midasKey>
    <feeinfo>
        ...
    </feeinfo>
</data>
```

## 混淆过滤

```text
-optimizationpasses 5                   # 指定代码的压缩级别
-dontusemixedcaseclassnames             # 指定代码的压缩级别
-dontskipnonpubliclibraryclasses        # 是否混淆第三方jar
-dontpreverify                          # 混淆时是否做预校验
-dontoptimize
-ignorewarning                          # 忽略警告，避免打包时某些警告出现
-verbose                                # 混淆时是否记录日志
-optimizations !code/simplification/arithmetic,!field/*,!class/merging/*    # 混淆时所采用的算法

-keep public class * extends android.app.Activity
-keep public class * extends android.app.Application
-keep public class * extends android.app.Service
-keep public class * extends android.content.BroadcastReceiver
-keep public class * extends android.content.ContentProvider
-keep public class * extends android.app.backup.BackupAgentHelper
-keep public class * extends android.preference.Preference
-keep public class com.android.vending.licensing.ILicensingService

-keepclasseswithmembernames class * {
    native <methods>;
}

-keepclasseswithmembernames class * {
    public <init>(android.content.Context, android.util.AttributeSet);
}

-keepclasseswithmembernames class * {
    public <init>(android.content.Context, android.util.AttributeSet, int);
}


-keepclassmembers enum * {
    public static **[] values();
    public static ** valueOf(java.lang.String);
}

-keep class * implements android.os.Parcelable {
  public static final android.os.Parcelable$Creator *;
}

-keepattributes InnerClasses
-keep class com.tencent.bugly.**{*;}
-keep class com.tencent.stat.**{*;}
-keep class com.tencent.smtt.**{*;}
-keep class com.tencent.beacon.**{*;}
-keep class com.tencent.mm.**{*;}
-keep class com.tencent.apkupdate.**{*;}
-keep class com.tencent.tmassistantsdk.**{*;}
-keep class org.apache.http.** { * ;}
-keep class com.qq.jce.**{*;}
-keep class com.qq.taf.**{*;}
-keep class com.tencent.connect.**{*;}
-keep class com.tencent.map.**{*;}
-keep class com.tencent.open.**{*;}
-keep class com.tencent.qqconnect.**{*;}
-keep class com.tencent.mobileqq.**{*;}
-keep class com.tencent.tauth.**{*;}
-keep class com.tencent.feedback.**{*;}
-keep class common.**{*;}
-keep class exceptionupload.**{*;}
-keep class mqq.**{*;}
-keep class qimei.**{*;}
-keep class strategy.**{*;}
-keep class userinfo.**{*;}
-keep class com.pay.**{*;}
-keep class com.demon.plugin.**{*;}
-keep class com.tencent.midas.**{*;}
-keep class oicq.wlogin_sdk.**{*;}
-keep class com.tencent.ysdk.**{*;}
-keepclasseswithmembernames class * {
    native <methods>;
}

-dontwarn java.nio.file.Files
-dontwarn java.nio.file.Path
-dontwarn java.nio.file.OpenOption
-dontwarn org.codehaus.mojo.animal_sniffer.IgnoreJRERequirement
```

## 集成测试

如何判断sdk是否初始化成功？

待添加

