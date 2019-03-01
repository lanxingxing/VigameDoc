# umeng

## 模块引入

```text
    implementation 'com.libVigame.TJ:AppsFlyer:2.0.4'
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| UMENG_APPKEY | 在友盟上申请的APPKEY | eg：5bbb2803b465f5c58c000017 |
| WB_CHANNEL | 渠道 | eg：vivo |

## 配置文件说明

```text
	需要在app的build.gradle的manifestPlaceholders中设置参数的值,如下：
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
	....
                UMENG_APPKEY:"5bbb2803b465f5c58c000017",
				WB_CHANNEL:"vivo",
	...
            ]
    }
}
```

## 混淆过滤

```text
-keep class com.umeng.**
-keep class com.umeng.**{*;}
```