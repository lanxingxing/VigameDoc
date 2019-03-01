---
description: 小米
---

# 小米

## 模块引入

```text
  implementation 'com.libVigame.Pay:MiPay:2.1.1'
```

## Manifest参数选项
无

## 配置文件说明

assets目录加入feedata_oppo.xml
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
-keep class com.xiaomi.**
-keep class com.xiaomi.**{*;}

```

## 集成测试

如何判断sdk是否初始化成功？

游戏打开会有oppo对应的悬浮按钮