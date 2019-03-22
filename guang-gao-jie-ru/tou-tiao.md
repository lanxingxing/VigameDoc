# 头条

## 模块引入

```text
    implementation 'com.libVigame.AD:Headline:2.5.5'
```

## 混淆过滤

```text
#穿山甲(今日头条)
###Toutiao v1.9.3.2
-keep class com.bytedance.sdk.openadsdk.** { *; }
-keep class com.androidquery.callback.** {*;}
-keep class com.bytedance.sdk.openadsdk.service.TTDownloadProvider
```

## 集成测试

如何查看广告日志？

可通过名为"HeadlineAgent"的Tag查看日志。

