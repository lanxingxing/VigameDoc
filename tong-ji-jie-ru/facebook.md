# Facebook

## 模块引入

```text
    implementation 'com.libVigame.TJ:Facebook:2.1.3'
```

## Manifest
###1.参数选项
| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| facebook\_app\_id | 在facebook上申请的参数 | eg：344465672947670 |
###2.测试检测
反编译出包的apk，搜索“com.facebook.sdk.ApplicationId”看看它的value值是否为344465672947670
```text
    com.facebook.sdk.ApplicationId
```

## 配置文件说明

需要在res/values/strings.xml目录下添加：\("344465672947670"是你的faceAPPId\)

```text
    <string name="facebook_app_id">344465672947670</string>
```

## 混淆过滤

```text
-keep class com.facebook.**{*;}
```

