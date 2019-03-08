# Mobivista

## 模块引入

```text
    implementation 'com.libVigame.AD:MobVista:1.0.9'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keepattributes Signature
-keepattributes *Annotation*
-keep class com.mintegral.** {*; }
-keep interface com.mintegral.** {*; }
-keep class android.support.v4.** { *; }
-dontwarn com.mintegral.**
-keep class **.R$* { public static final int mintegral*; }
-keep class com.alphab.** {*; }
-keep interface com.alphab.** {*; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过MVAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

