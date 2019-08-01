# TuiA

## 模块引入

```text
    implementation 'com.libVigame.AD:TuiA:1.0.2'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-dontwarn com.tuia.**
-keep class com.tuia.** { *; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过TuiAAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

