# 360广告

## 模块引入

```text
    implementation 'com.libVigame.AD:Ad360:1.0.6'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keepclasseswithmembernames,allowshrinking class * {
    native <methods>;
 }
-keepclasseswithmembers class * { public <init>(...); }
-keepclasseswithmembernames class * {public <init>(android.content.Context, android.util.AttributeSet);}
-keepclasseswithmembernames class * {public <init>(android.content.Context, android.util.AttributeSet, int);}
-keepclassmembers enum * {public static **[] values();public static ** valueOf(java.lang.String);}
-keepclassmembers class * implements android.os.Parcelable {
  public static final android.os.Parcelable$Creator CREATOR;
}
-keepattributes *Annotation*
-keepattributes *JavascriptInterface*


-keep class com.ak.**
-keep class com.ak.** { *; }

#support-v4
-keep class android.support.v4.** { *; }

-keep class com.androidquery.**
-keep class com.androidquery.**{*;}
-keep class com.androidquery.*.**
-keep class com.androidquery.*.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过Ad360Agent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

