# oppo

## 模块引入

```text
    implementation WB.fixVersions('AD:OPPO')
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.oppo.** {
public protected *;
}
-keep class okio.**{ *; }
-keep class com.squareup.wire.**{ *; }
-keep public class * extends com.squareup.wire.**{ *; }
# Keep methods with Wire annotations (e.g. @ProtoField)
-keepclassmembers class ** {
 @com.squareup.wire.ProtoField public *;
 @com.squareup.wire.ProtoEnum public *;
}
-keep public class com.cdo.oaps.base.**{ *; }
-keepattributes *Annotation*
-keepattributes *JavascriptInterface*
#support-v4
-keep class android.support.v4.** { *; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过OPPO或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

