# 狂热广告

## 模块引入

```text
    1.采用本地导入的方式，将libAD_UpAds当做一个module引入你的工程当中
    2.在app的build.gardle的dependencies前加入如下代码：
        repositories {
            flatDir {
                dirs 'libs'
                dirs project(':libAD_UpAds').file('libs')
            }
        }
    3.在app的build.gardle的dependencies中加入以下代码
    implementation project(':libAD_UpAds')
        fileTree(dir: 'libs', include: ['*.aar']).each { file ->
            api(name: file.name.lastIndexOf('.').with {
                it != -1 ? file.name[0..<it] : file.name
            }, ext: 'aar')
        }
```

## 注意事项

```text
    1.当打包结束的时候，建议把build.gradle中加入的代码注释掉，
      以免接其他渠道的时候还带了狂热聚合广告的代码。
    2.当接入狂热广告的时候不建议再接入我们的其他家广告，因为狂热广告是一个聚合广告，
      有可能带来广告的版本冲突和收益不知道算哪边的问题。
```

## 混淆过滤

```text
# avidly
-keep class com.avidly.ads.** {*;}
-keep class com.up.ads.** {*;}
-keep interface com.up.ads.** {*;}
-keep class com.avidly.channel.** { *; }
-keep class com.up.channel.** { *; }
-keep class com.sm.avid.decode.** {*;}
-keep class com.avidly.playablead.ext.** {*;}
-keep interface com.avidly.ads.** {*;}
-keep interface com.sm.avid.decode.** {*;}
-keep class com.hola.sdk.* {*;}
-keep class com.statistics.channel.* {*;}
-keep class com.aly.analysis.sdk.api.* {*;}
-keepclasseswithmembernames class * {
    native <methods>;
}
-dontwarn com.avidly.**
-dontwarn com.up.**
-keep class com.statistics.channel.* {*;}
# avidly end

# support
-keep public class * extends android.support.v4.app.Fragment
-keep class android.support.** {*;}
-keep class com.google.gson.** {*;}
-dontwarn android.support.**
# support end

# facebook
-keep class com.facebook.ads.InterstitialAd {*;}
-keep class com.facebook.ads.AdView {*;}
-keep class com.facebook.ads.Ad {*;}
-keep class com.facebook.ads.RewardedVideoAd {*;}
-keep class com.facebook.ads.AdListener {*;}
-keep class com.facebook.ads.BuildConfig {*;}
-dontwarn com.facebook.ads.internal.**
-keep class com.facebook.bidding.** {*;}
-keep class com.google.android.exoplayer2.** {*;}
-dontwarn com.google.android.exoplayer2.**
# facebook end

# google
-keep class * extends java.util.ListResourceBundle {
    protected java.lang.Object[][] getContents();
}
-keep public class com.google.android.gms.common.internal.safeparcel.SafeParcelable {
    public static final *** NULL;
}
-keepclassmembers enum * {
  public static **[] values();
  public static ** valueOf(java.lang.String);
}
-keepnames @com.google.android.gms.common.annotation.KeepName class *
-keepclassmembernames class * {
    @com.google.android.gms.common.annotation.KeepName *;
}
-keepnames class * implements android.os.Parcelable {
    public static final ** CREATOR;
}
-keep class * extends java.util.ListResourceBundle {
    protected java.lang.Object[][] getContents();
}
-keep class com.google.android.gms.ads.** {*;}
-keep class com.google.android.gms.common.** {*;}
-dontwarn com.google.android.gms.**
-dontwarn com.google.protobuf.**
-keep class com.google.ads.mediation.** {*;}
-dontwarn com.google.ads.mediation.**
# google end

# adcolony
-keep class com.adcolony.** { *; }
-dontwarn com.adcolony.**
-dontnote com.adcolony.**
# adcolony end

# vungle
-keep class com.vungle.warren.** { *; }
-keep class com.moat.** { *; }
-keep class com.google.android.gms.internal.** { *; }
-dontwarn com.vungle.warren.error.VungleError$ErrorCode
-dontwarn org.codehaus.mojo.animal_sniffer.IgnoreJRERequirement
-dontwarn retrofit2.Platform$Java8
-keepattributes Signature
-keepattributes *Annotation*
-dontwarn sun.misc.**
-dontwarn com.vungle.warren.**
-dontwarn okio.**
-dontwarn retrofit2.**
-dontwarn com.moat.**
-dontwarn com.google.android.gms.ads.identifier.**
-dontwarn org.codehaus.mojo.animal_sniffer.IgnoreJRERequirement
-keeppackagenames 'net.vrallev.android.cat'
-keeppackagenames 'retrofit2.converter.gson'
-keeppackagenames 'com.tonyodev.fetch'
-keeppackagenames 'okhttp3.logging'
-keeppackagenames 'okhttp3'
-keeppackagenames 'okio'
-keeppackagenames 'retrofit2'
# vungle end

# unity
-keepattributes SourceFile,LineNumberTable
-keepattributes JavascriptInterface
-keep class android.webkit.JavascriptInterface {*;}
-keep class com.unity3d.ads.** {*;}
-keep class com.unity3d.services.** {*;}
-dontwarn com.google.ar.core.**
# unity end

# applovin
-keep class com.applovin.** { *; }
-dontwarn com.applovin.**
# applovin end

# chartboost
-keep class com.chartboost.** { *; }
-dontwarn com.chartboost.**
# chartboost end

# playable
-keep class com.avidly.playablead.app.** { *; }
# playable end

# ironsource
-keep class com.ironsource.mediationsdk.IronSource
-keep class com.moat.** { *; }
-keepclassmembers class com.ironsource.sdk.controller.IronSourceWebView$JSInterface {
    public *;
}
-keepclassmembers class * implements android.os.Parcelable {
    public static final android.os.Parcelable$Creator *;
}
-keep public class com.google.android.gms.ads.** {
   public *;
}
-keep public class com.google.ads.** {
   public *;
}

-keep class com.ironsource.adapters.** { *;
}
# ironsource end

# vk
-keep class com.my.target.** {*;}
-dontwarn com.my.target.**
-dontwarn com.mopub.**
# vk end

# maio
-keep class jp.maio.sdk.android.** { *; }
-dontwarn jp.maio.sdk.android.**
-dontnote jp.maio.sdk.android.**
# maio end

# nend
-keep class net.nend.android.** { *; }
-dontwarn net.nend.android.**
-dontnote net.nend.android.**
# nend end

# oneway
-keepattributes *Annotation*
-keep enum mobi.oneway.sdk.* {*;}
-keep class mobi.oneway.sdk.** {*;}
# oneway end

# gdt
-keep class com.qq.e.** {*;}
-keep class android.support.v4.** {public *;}
-keep class android.support.v7.** {public *;}
# gdt end

# toutiao
-keep class com.bytedance.sdk.openadsdk.** { *; }
-keep class com.androidquery.callback.** {*;}
-dontwarn com.bytedance.sdk.**
-dontwarn com.androidquery.**
-dontwarn com.ss.android.**
# toutiao end

# amazon
-keep class com.amazon.device.ads.** { *; }
# amazon end
```

## 集成测试

如何判断sdk是否初始化成功？

通过UpADSAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

