# Tapjoy

## 模块引入

```text
    implementation 'com.libVigame.AD:Tapjoy:1.0.0'
```

## 注意事项

```text
    manifestPlaceholders 中需要添加 TAPJOY_SDK_KEY:"aeNKt_BqS4WQ19eZX3t9LAECNKgVAqhf9alfSTCU3VPEiPqchINE-2R1O99Q"
```

## 混淆过滤

```text
-dontwarn com.tapjoy.**
-keep class com.tapjoy.** { *; }
-dontwarn com.moat.analytics.mobile.tjy.**
-keep class com.moat.analytics.mobile.tjy.** { *; }
```

## 集成测试

通过TapjoyAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

