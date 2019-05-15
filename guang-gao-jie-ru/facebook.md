# Facebook

## 模块引入

```text
    implementation 'com.libVigame.AD:Facebook:2.2.4' 
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.facebook.ads.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过FBADAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

