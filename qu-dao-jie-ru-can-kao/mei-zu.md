---
description: 魅族
---

# 魅族

## 模块引入

```text
    implementation 'com.libVigame.Pay:Meizu:2.1.7'
```

## 配置文件说明

assets目录加入feedata_meizu.xml

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