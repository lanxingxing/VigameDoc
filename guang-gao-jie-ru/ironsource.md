# IronSource

```text
    implementation 'com.libVigame.AD:Ironsource:2.0.4'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keepclassmembers class com.ironsource.sdk.controller.IronSourceWebView$JSInterface {
    public *;
}
-keepclassmembers class * implements android.os.Parcelable {
    public static final android.os.Parcelable$Creator *;
}
-keep public class com.google.android.gms.ads.** {
   public *;
}
-keep class com.ironsource.adapters.** { *;
}
-dontwarn com.ironsource.mediationsdk.**
-dontwarn com.ironsource.adapters.**
-dontwarn com.moat.**
-keep class com.moat.** { public protected private *; }
-keep class com.ironsource.adapters.**
-keep class com.ironsource.adapters.** {*; }
-keep class com.applovin.**
-keep class com.applovin.** {*; }
-keep class com.integralads.**
-keep class com.integralads.** {*; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过IronSourceAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

