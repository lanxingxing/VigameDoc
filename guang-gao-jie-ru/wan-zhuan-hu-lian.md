# 玩转互联

## 模块引入

```text
    implementation 'com.libVigame.AD:Uniplay:2.1.6'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-dontwarn com.uniplay.**
-keep class com.uniplay.** { *; }
-dontwarn com.wzhl.**
-keep class com.wzhl.** { *; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过UniplayAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

