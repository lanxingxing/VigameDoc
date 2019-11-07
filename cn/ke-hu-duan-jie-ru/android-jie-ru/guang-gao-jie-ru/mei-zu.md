# 魅族

## 模块引入

```text
    implementation 'com.libVigame.AD:Meizu:2.1.0'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.meizu.advertise.api.** {*;}-keep class com.meizu.advertise.plugin.api.Mzsdk {*;}-keep class com.meizu.advertise.plugin.api.Mzsdk$* {*;}-keep class com.meizu.advertise.config.** {*;}-keep class com.android.volley.** {*;}-keep class com.google.protobuf.** {*;}-dontwarn com.google.protobuf.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过MeizuAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

