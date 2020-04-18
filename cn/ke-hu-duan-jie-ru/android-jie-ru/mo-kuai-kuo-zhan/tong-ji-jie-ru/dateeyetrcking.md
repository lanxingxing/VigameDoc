# DateEyeTrcking

## 模块引入

```text
    implementation WB.fixVersions('TJ:DateEye')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| DC\_APPID | 无 | eg：可为空 |
| WB\_CHANNEL | 渠道 | eg：vivo |
| DC\_TRACKING\_APPID | dataeye tracking | eg：C6079041E388322EAB5F6D7718E86DB6F |
| DC\_REPORT\_MODE | 无 | eg：可为空 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置各个参数的值, 一般只需要设置DC\_TRACKING\_APPID和WB\_CHANNEL的值，如下：

```text
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
    ....
                DC_APPID:"",
                DC_TRACKING_APPID:"C6079041E388322EAB5F6D7718E86DB6F",
                DC_REPORT_MODE:"",
                WB_CHANNEL:"vivo",
    ...
            ]
    }
}
```

## 混淆过滤

```text
-dontwarn com.android.installreferrer
-keep class com.appsflyer.** { *; }
```

