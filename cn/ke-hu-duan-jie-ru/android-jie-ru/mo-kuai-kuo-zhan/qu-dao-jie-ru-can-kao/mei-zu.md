---
description: 魅族
---

# 魅族

## 模块引入

本地引入，模块下载地址：http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libPay/libPayExt_Meizu&h=master&format=zip

setting.gradle中添加

```
include ':libPayExt_Meizu'
project(':libPayExt_Meizu').projectDir = new File('目录\\libPayExt_Meizu')
```

app目录build.gradle中修改：

```text
    xxxximplementation project(':libPayExt_Meizu')
```

## 配置文件说明

assets目录加入feedata\_meizu.xml

```text
<data>
    <appid>3227804</appid>
    <appkey>8a5e3ccb238e4b0aa9bb09eda9b97617</appkey>
    <appsecret>QaZmRVJiEDd0Up3m1SdlbkgmfOTTN1ph</appsecret>

    <feeinfo>
        <ID>1101</ID>
        <price>1</price>
        <desc>30赠25枚钻石</desc>
    </feeinfo>

</data>
```

## 混淆过滤

```text
-keep class com.meizu.**
-keep class com.meizu.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

游戏打开会有魅族的悬浮按钮

