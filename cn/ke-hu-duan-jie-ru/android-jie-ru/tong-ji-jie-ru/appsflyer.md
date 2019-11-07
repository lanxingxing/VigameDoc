# AppsFlyer

## 模块引入

```text
    implementation 'com.libVigame.TJ:AppsFlyer:2.0.8'
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| AppsFlyer\_DevKey | 在AppsFlyer上申请的参数 | eg：X9NxxaMp4neHCFYreDxtd5 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置“AppsFlyer\_DevKey”的值,如下：

```text
android {    compileSdkVersion 28    buildToolsVersion '28.0.3'    publishNonDefault true    defaultConfig {    manifestPlaceholders = [    ....                AppsFlyer_DevKey:"X9NxxaMp4neHCFYreDxtd5",    ...            ]    }}
```

## 混淆过滤

```text
-dontwarn com.android.installreferrer-keep class com.appsflyer.** { *; }
```

