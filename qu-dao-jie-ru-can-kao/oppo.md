# oppo

## 模块引入

```text

```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| OPPO\_APPKEY | OPPO的APPKEY | eg：59fc9873a2c244c9a085554ca31f63b5 |

## 配置文件说明

assets目录加入feedata\_oppo.xml

```text
<?xml version="1.0" encoding="UTF-8"?>
<data>
    <AppKey>59fc9873a2c244c9a085554ca31f63b5</AppKey>
    <AppSecret>8b87f2413df14ddba017087536bdef26</AppSecret>

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
-keep class com.oppo.** {
public protected *;
}
-keep class okio.**{ *; }
-keep class com.squareup.wire.**{ *; }
-keep public class * extends com.squareup.wire.**{ *; }
# Keep methods with Wire annotations (e.g. @ProtoField)
-keepclassmembers class ** {
 @com.squareup.wire.ProtoField public *;
 @com.squareup.wire.ProtoEnum public *;
}
-keep public class com.cdo.oaps.base.**{ *; }
-keepattributes *Annotation*
-keepattributes *JavascriptInterface*
```

## 集成测试

如何判断sdk是否初始化成功？

游戏打开会有oppo对应的悬浮按钮

