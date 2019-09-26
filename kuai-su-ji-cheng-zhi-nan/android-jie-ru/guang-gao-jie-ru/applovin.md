# Applovin

## 模块引入

```text
implementation 'com.libVigame.AD:AppLovin:2.1.6'
```

## 注意事项

```text

```

## 混淆过滤

```text
-keep class com.applovin.**
-keep class com.applovin.** {*; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过AppLovinAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

## 广告集成

2.1.6版本，2019年8月20号，视频广告只能播放完一个再加载另外一个，不然会黑屏。

