# vivo

## 模块引入

```text
  implementation 'com.libVigame.Pay:VivoSingle:2.0.0' (Vivo单机计费)
  和
  implementation 'com.libVigame.Pay:Vivo:2.1.9' (Vivo联运)
  和
  implementation 'com.libVigame.Pay:VivoOverseas:2.0.2' (Vivo海外)
```

## Manifest参数选项

无

## 配置文件说明

assets目录加入feedata\_vivo.xml

```text
<?xml version="1.0" encoding="UTF-8"?>
<data>
    <App-ID>68fafd6cd3495af63256172ecc87d74c</App-ID>
    <Cp-ID>a60092d44708f9b559eb</Cp-ID>
    <Cp-key>bb2f36d2d947f413eb4a9e10f7cca5c3</Cp-key>

    <feeinfo>
        <ID>1</ID>
        <price>600</price>
        <code>002</code>
        <desc>30赠25枚钻石</desc>
    </feeinfo>
   </data>
```

## 混淆过滤

```text
-keep class com.bbkmobile.**
-keep class com.bbkmobile.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

游戏打开会有vivo对应的悬浮按钮

