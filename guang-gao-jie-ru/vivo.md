# vivo

## 模块引入

```text
    implementation 'com.libVigame.AD:VIVO:2.4.1'
```

## 注意事项
```text
    无
```

## 混淆过滤

```text
-keep class com.qq.e.** {
      public protected *;
  }
-keep class android.support.v4.app.NotificationCompat**{
      public *;
}
#百度SDK
-keep class com.baidu.mobads.*.** { *; }
#vivoSDK
-keep class com.vivo.mobilead.*.** { *; }
-dontwarn com.androidquery.auth.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过Vivo或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断