# 小米

## 模块引入

```text
    implementation 'com.libVigame.AD:Mi:2.2.6'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.xiaomi.ad.**{*;}
-keep class com.miui.zeus.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过MiAgent、MiNativeAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

