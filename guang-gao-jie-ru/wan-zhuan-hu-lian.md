# 玩转互联

## 模块引入

```text
    implementation 'com.libVigame.AD:Uniplay:2.1.7'
    和
    implementation 'com.libVigame.AD:UniplayA:1.0.1'（隐藏广告）
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.uniplay.adsdk.**
-keep class com.joomob.**
-keep class * implements android.os.Parcelable {   public static final android.os.Parcelable$Creator *; }
-keepattributes Annotation
-keepattributes JavascriptInterface
-keepclassmembers class * { @android.webkit.JavascriptInterface <methods>; }
-keepclassmembers public class com.uniplay.adsdk.JavaScriptInterface{ <fields>; <methods>; public *; private *; }
-dontwarn com.wzhl.**
-keep class com.wzhl.** { *; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过UniplayAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

