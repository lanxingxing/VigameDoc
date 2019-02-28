# 广点通

## 模块引入

```text
    implementation 'com.libVigame.AD:GDTUnion:2.4.3'  (带MobVisita用）
    和
    implementation 'com.libVigame.AD2:GDTUnion:2.4.3' （不带MobVisita用）
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.qq.e.** {public protected *;}
-keep class android.support.v4.**{public *;}
-keep class android.support.v7.**{public *;}
#    如果您使用的是 X5 内核加强版 SDK，还需要在混淆配置文件中加入下面的代码
-keep class MTT.ThirdAppInfoNew {*;}
-keep class com.tencent.** { *;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过GDT或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

