---
description: 小米
---

# 小米

## 模块引入

```text
  implementation 'com.libVigame.Pay:MiPay_New:2.2.4'
  和
  implementation 'com.libVigame.Pay:MiSingle:2.1.3' （单机计费）
```

## Manifest参数选项

无

## 配置文件说明

assets目录加入feedata\_oppo.xml

```text
<?xml version="1.0" encoding="utf-8"?>
<data>
    <AppId>2882303761517881611</AppId>
    <AppKey>5691788142611</AppKey>

    <feeinfo>
        <ID>1</ID>
        <price>600</price>
        <code>code2</code>
        <desc>30赠25枚钻石</desc>
    </feeinfo>
</data>
```

## 混淆过滤

```text
-dontwarn com.xiaomi.**
-keep class com.xiaomi.** {*;}
-dontwarn org.xiaomi.**
-keep class org.xiaomi.** {*;}
-dontwarn com.wali.**
-keep class com.wali.** {*;}
-dontwarn com.mi.milink.**
-keep class com.mi.milink.** {*;}
-dontwarn cn.com.wali.**
-keep class cn.com.wali.** {*;}
-keep class com.example.milinksdkcore.** {*;}
-dontwarn  org.apache.**
-keep class org.apache.** {*;}
-dontwarn android.net.**
-keep class android.net.** {*;}
-keep class android.** {*;}
-keep class com.android.** {*;}
-keep class com.google.** {*;}
-keep class com.alipay.** {*;}
-keep class com.ut.device.** {*;}
-keep class com.ta.utdid2.** {*;}
-keep class org.greenrobot.** {*;}
-keep class com.bumptech.** {*;}
-keep class com.payeco.** {*;}
```

## 集成测试

如何判断sdk是否初始化成功？

游戏打开会有oppo对应的悬浮按钮

