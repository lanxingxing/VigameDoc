# TopOn广告



## 模块引入

app目录build.gradle中修改：

```text
  xxxxxImplementation WB.fixVersions('AD:TopOn')
  
```

## 注意事项

```text

TopOn需要在assets目录下创建topon_ad_info.xml文件
所有的广告参数都在这里配置

一个广告id同一时间只有一个广告，如果有多个广告位使用同一个id，返回的状态都是一样的。
一个广告位展示了广告，所有使用该广告id的广告位调用isAdReady方法返回的状态都会是false。

```

## 广告配置

```text
topon_ad_info的内容如下

<?xml version="1.0" encoding="utf-8"?>
<data>
    <!-- placementId是代码位ID、adsourceId是广告源ID -->
    <!-- sourcetype : toutiao-头条，qq-腾讯，mintegral-Mintegral，kuaishou-快手，sigmob-Sigmob，baidu-百度 -->
   
    <placementId>887357694</placementId>
    <adsourceId>104182</adsourceId>
    <sourcetype>toutiao</sourcetype>
</data>
```

## 混淆过滤

```text

-keep class com.androidquery.callback.** {*;}
-keep class com.ss.sys.ces.* {*;}
-keep class com.bytedance.sdk.openadsdk.** { *; }
-keep public interface com.bytedance.sdk.openadsdk.downloadnew.** {*;}
-keep class com.pgl.sys.ces.* {*;}
-keep class org.chromium.** { *; }
-keep class aegon.chrome.** { *; }
-keep class com.kwai.**{ *; }
-dontwarn com.kwai.**
-dontwarn com.kwad.**
-dontwarn com.ksad.**
-dontwarn aegon.chrome.**
-keep class com.kwad.sdk.** { *;}
-keep class com.ksad.download.** { *;}
-keep class com.kwai.filedownloader.** { *;}
-keep class com.qq.e.** {
    public protected *;
}
-keep class android.support.v4.**{
    public *;
}
-keep class android.support.v7.**{
    public *;
}
-keep class MTT.ThirdAppInfoNew {
    *;
}
-keep class com.tencent.** {
    *;
}
-dontwarn dalvik.**
-dontwarn com.tencent.smtt.**

################### anythink_banner ###########################
-keep public class com.anythink.network.**
-keepclassmembers class com.anythink.network.** {
   public *;
}

-dontwarn com.anythink.**

-dontwarn com.anythink.hb.**
-keep class com.anythink.hb.**{ *;}

-dontwarn com.anythink.china.api.**
-keep class com.anythink.china.api.**{ *;}
################### anythink_banner ###########################

################### ijkplayer #################################
#-keep class org.chromium.** {*;}
-keep class com.kwai.video.player.** { *; }
-dontwarn  com.kwai.video.player.**
-keep class com.kwai.log.** { *; }
-keep class com.kwai.video.cache.** { *; }
-keep class com.kwai.video.hodor.** { *; }
-keep class com.kwai.player.debuginfo.** { *; }

#-keep class aegon.chrome.** { *; }
#
#-dontwarn com.kwai.**
#-dontwarn com.kwad.**
#-dontwarn com.ksad.**
#-dontwarn aegon.chrome.**


#混淆保护 非必须， 增加此列是为了查日志时能够方便对应上sdk代码
-keep class com.kwad.sdk.** { *;}
-keep class com.ksad.download.** { *;}
-keep class com.kwai.filedownloader.** { *;}

-keep class kwad.support.** { *; }
-dontwarn okio.**
-dontwarn okhttp3.**
# 混淆一级即可
-keep class okhttp3.* {*;}
-keep class com.google.gson.* {*;}

#保留注解，如果不添加改行会导致我们的@Keep注解失效
-keepattributes *Annotation*



#直播相关混淆
-dontwarn io.netty.**
-dontwarn com.kuaishou.livestream.message.**
-dontwarn com.kuaishou.protobuf.**
-keep class com.google.protobuf.nano.** {*;}
-keep class com.kuaishou.livestream.message.nano.** {*;}
-keep class com.kuaishou.protobuf.livestream.nano.** {*;}
-keep class com.kuaishou.merchant.message.nano.** {*;}
-keep class com.kuaishou.protobuf.merchant.message.nano.** {*;}

# 安全sdk
-keep class com.kuaishou.android.security.**{*;}
-keep class com.kuaishou.dfp.**{*;}
-keep class com.kuaishou.dfp.KWEGIDDFP {*;}
-keep class com.kuaishou.dfp.ResponseDfpCallback {*;}
-keep class com.kuaishou.dfp.env.jni.Watermelon {*;}
-dontwarn com.squareup.okhttp3.**
-keep class com.squareup.okhttp3.** { *;}
#-dontwarn okio.**
-keep class com.google.protobuf.** {*;}
-keep class com.kuaishou.dfp.env.Proxy.** {*;}
#new added for android 10
-keep class com.bun.miitmdid.core.** {*;}


-keep class android.support.rastermill.** { *; }

######################### 穿山甲 ########################

-keep class com.bytedance.embedapplog.AppLog { public *; }
-keep public interface com.bytedance.embedapplog.IDataObserver { *; }
-keep public interface com.bytedance.embedapplog.IAppParam { *; }
-keep public interface com.bytedance.embedapplog.IExtraParams { *; }
-keep public interface com.bytedance.embedapplog.IPicker { *; }
-keep public interface com.bytedance.embedapplog.IOaidObserver { *; }
-keep public interface com.bytedance.embedapplog.ISensitiveInfoProvider { *; }
-keep class com.bytedance.embedapplog.IOaidObserver$Oaid { *; }
-keep class com.bytedance.embedapplog.GameReportHelper { public *; }
-keep class com.bytedance.embedapplog.InitConfig { public *; }
-keep class com.bytedance.embedapplog.util.UriConfig { public *; }
-keep class com.bytedance.embedapplog.tracker.Tracker { public *; }
-keep class com.bytedance.embedapplog.picker.Picker { public *; }
-keep class com.bytedance.embedapplog.tracker.WebViewJsUtil { *; }
-keep interface com.bytedance.embed_device_register.DrLogWriter { public *; }
-keep interface com.bytedance.embed_bdtracker.bt { public *; }
-keep class com.bytedance.embed_bdtracker.bt$a { public *; }
-keep class com.bytedance.embed_bdtracker.bt$a$a { public *; }

######################### 穿山甲 ########################

######################### mobvista ########################

-keep class com.anythink.china.api.**{ *;}
-keepattributes Signature
-keepattributes *Annotation*
-keep class com.mintegral.** {*; }
-keep interface com.mintegral.** {*; }
-keep interface androidx.** { *; }
-keep class androidx.** { *; }
-keep public class * extends androidx.** { *; }
-dontwarn com.mintegral.**
-keep class **.R$* { public static final int mintegral*; }
-keep class com.alphab.** {*; }
-keep interface com.alphab.** {*; }

######################### mobvista ########################


######################### sigmob ########################

# androidx

-keep class com.google.android.material.** {*;}
-keep class androidx.** {*;}
-keep public class * extends androidx.**
-keep interface androidx.** {*;}
-dontwarn com.google.android.material.**
-dontnote com.google.android.material.**
-dontwarn androidx.**

# android.support.v4

-dontwarn android.support.v4.**
-keep class android.support.v4.** { *; }
-keep interface android.support.v4.** { *; }
-keep public class * extends android.support.v4.**

# WindAd

-keep class sun.misc.Unsafe { *; }
-dontwarn com.sigmob.**
-keep class com.sigmob.**.**{*;}

# miitmdid
-keep class com.bun.miitmdid.core.** {*;}
-dontwarn com.bun.miitmdid.core.**

######################### sigmob ########################

```

## 集成测试

通过TopOnAdManager 和 UnityPlayerActivity 、anythink过滤日志查看广告状态，或者直接通过弹出的广告进行判断
