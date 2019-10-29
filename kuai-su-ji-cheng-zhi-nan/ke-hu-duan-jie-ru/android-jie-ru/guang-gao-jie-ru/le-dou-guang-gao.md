# 乐逗广告

## 模块引入

```text
    implementation 'com.libVigame.AD:LeDou:2.1.0'

## 注意事项

```text
    无
```

## 混淆过滤

```text
-dontnote android.net.http.*
-dontnote org.apache.http.**

-keepclasseswithmembernames class * {                                           # 保持 native 方法不被混淆
    native <methods>;
}

-keepclasseswithmembers class * {                                               # 保持自定义控件类不被混淆
    public <init>(android.content.Context, android.util.AttributeSet);
}

-keepclasseswithmembers class * {
    public <init>(android.content.Context, android.util.AttributeSet, int);     # 保持自定义控件类不被混淆
}

-keepclassmembers class * extends android.app.Activity {                        # 保持自定义控件类不被混淆
   public void *(android.view.View);
}

-keepclassmembers enum * {                                                      # 保持枚举 enum 类不被混淆
    public static **[] values();
    public static ** valueOf(java.lang.String);
}

-keep class * implements android.os.Parcelable {                                # 保持 Parcelable 不被混淆
  public static final android.os.Parcelable$Creator *;
}

-keep public class com.mobgi.MobgiAds {*;}
-keep public class com.mobgi.MobgiAds$FinishState {*;}
-keep public class com.mobgi.MobgiAdsError {*;}
-keep public class com.mobgi.MobgiAdsConfig {*;}
-keep public class com.mobgi.MobgiInterstitialAd {*;}
-keep public class com.mobgi.MobgiVideoAd {*;}
-keep public class com.mobgi.MobgiNativeAd {*;}
-keep public class com.mobgi.MobgiSplashAd {*;}
-keep public class com.mobgi.adutil.parser.NativeAdBeanPro {*;}
-keep public interface com.mobgi.** {*;}
-keep public class com.mobgi.platform.** {*;}

# apponboard
-keep class com.apponboard.** { *; }

#AdView
-dontwarn
-keep public class com.kyview.** {*;}
-keepclassmembers class * {public *;}
-keep public class com.kuaiyou.**.** {*;}
-optimizationpasses 5
-dontusemixedcaseclassnames
-dontskipnonpubliclibraryclasses
-dontpreverify
-verbose

# Inmobi
-keepattributes SourceFile,LineNumberTable
-keep class com.inmobi.** { *; }
-dontwarn com.inmobi.**
-keep public class com.google.android.gms.**
-dontwarn com.google.android.gms.**
-dontwarn com.squareup.picasso.**
-keep class com.google.android.gms.ads.identifier.AdvertisingIdClient{
public *;
}
-keep class com.google.android.gms.ads.identifier.AdvertisingIdClient$Info{
public *;
}
# skip the Picasso library classes
-keep class com.squareup.picasso.** {*;}
-dontwarn com.squareup.picasso.**
-dontwarn com.squareup.okhttp.**
# skip Moat classes
-keep class com.moat.** {*;}
-dontwarn com.moat.**
# skip AVID classes
-keep class com.integralads.avid.library.* {*;}

#
-keep public class com.kuaiyou.** {*;}

#Centrixlink
-dontwarn com.centrixlink.**
-keep public class com.centrixlink.**  { *; }

#Mobvista
-keepattributes Signature
-keepattributes *Annotation*
-keep class com.mintegral.** {*; }
-keep interface com.mintegral.** {*; }
-keep class android.support.v4.** { *; }
-dontwarn com.mintegral.**
-keep class **.R$* { public static final int mintegral*; }
-keep class com.alphab.** {*; }
-keep interface com.alphab.** {*; }

#Kingsoft
-keep class com.ksc.ad.sdk.**{ *;}
-dontwarn com.ksc.ad.sdk.**

#AdMod国内版
-keep class * implements com.google.android.gms.ads.mediation.MediationAdapter {
  public *;
}
-keep class * implements com.google.ads.mediation.MediationAdapter {
  public *;
}
-keep class * implements com.google.android.gms.ads.mediation.customevent.CustomEvent {
  public *;
}
-keep class * implements com.google.ads.mediation.customevent.CustomEvent {
  public *;
}
-keep public class com.google.android.gms.common.internal.safeparcel.SafeParcelable {
    public static final *** NULL;
}

-keep class com.google.android.gms.common.internal.ReflectedParcelable
-keepnames class * implements com.google.android.gms.common.internal.ReflectedParcelable
-keepclassmembers class * implements android.os.Parcelable {
  public static final *** CREATOR;
}
-keep @interface android.support.annotation.Keep
-keep @android.support.annotation.Keep class *
-keepclasseswithmembers class * {
  @android.support.annotation.Keep <fields>;
}
-keepclasseswithmembers class * {
  @android.support.annotation.Keep <methods>;
}
-keep @interface com.google.android.gms.common.annotation.KeepName
-keepnames @com.google.android.gms.common.annotation.KeepName class *
-keepclassmembernames class * {
  @com.google.android.gms.common.annotation.KeepName *;
}
-keep @interface com.google.android.gms.common.util.DynamiteApi
-keep @com.google.android.gms.common.util.DynamiteApi public class * {
  public <fields>;
  public <methods>;
}
-dontwarn android.security.NetworkSecurityPolicy
-dontwarn android.app.Notification
-dontwarn sun.misc.Unsafe
-dontwarn libcore.io.Memory
# AdMob国内版 -end

#蓝莓
#视频
-keep class com.lam.** { *; }
#插屏
-keepattributes Exceptions,InnerClasses,Signature,*Annotation*
-keepnames class * implements java.io.Serializable
-keep public class com.androidquery.**{*;}
-keep public class com.tencent.analytics.sdk.** {*;}

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

#穿山甲(今日头条)
###Toutiao v1.9.3.2
-keep class com.bytedance.sdk.openadsdk.** { *; }
-keep class com.androidquery.callback.** {*;}
-keep class com.bytedance.sdk.openadsdk.service.TTDownloadProvider

#Unity
###Unity v2.1.0
# Keep filenames and line numbers for stack traces
-keepattributes SourceFile,LineNumberTable
# Keep JavascriptInterface for WebView bridge
-keepattributes JavascriptInterface
# Sometimes keepattributes is not enough to keep annotations
-keep class android.webkit.JavascriptInterface {
*;
}
# Keep all classes in Unity Ads package
-keep class com.unity3d.ads.** {
*;
}

#Vungle
###Vungle v6.3.18
# Vungle
-keep class com.vungle.warren.** { *; }
-dontwarn com.vungle.warren.error.VungleError$ErrorCode
# Moat SDK
-keep class com.moat.** { *; }
-dontwarn com.moat.**
# Okio
-dontwarn org.codehaus.mojo.animal_sniffer.IgnoreJRERequirement
# Retrofit
-dontwarn okio.**
-dontwarn retrofit2.Platform$Java8
# Gson
-keepattributes Signature
-keepattributes *Annotation*
-dontwarn sun.misc.**
-keep class com.google.gson.examples.android.model.** { *; }
-keep class * implements com.google.gson.TypeAdapterFactory
-keep class * implements com.google.gson.JsonSerializer
-keep class * implements com.google.gson.JsonDeserializer
# Google Android Advertising ID
-keep class com.google.android.gms.internal.** { *; }
-dontwarn com.google.android.gms.ads.identifier.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过LeDouAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

