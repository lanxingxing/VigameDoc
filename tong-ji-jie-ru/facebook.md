# Facebook

## 模块引入

```text
    implementation 'com.libVigame.TJ:Facebook:2.1.3'
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- |
| facebook_app_id | 在facebook上申请的参数 | eg：344465672947670 |

## 配置文件说明

```text
	需要在res/values/strings.xml目录下添加：("344465672947670"是你的faceAPPId)

	<string name="facebook_app_id">344465672947670</string>
```

## 混淆过滤

```text
-keep class com.facebook.**{*;}
```