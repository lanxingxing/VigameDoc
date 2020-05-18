# PDD 拼多多追踪

## 模块引入

```text
    implementation WB.fixVersions('TJ:PDD')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| PDD_APPID | appid,商务/需求单提供 | eg：12345 |
| PDD_APPSECRET | appsecret,商务/需求单提供 | eg：12345 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置 PDD_APPID 和 PDD_APPSECRET 的值,如下：

```text
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
    ....
            PDD_APPID:"xxx",
            PDD_APPSECRET:"xxx",
    ...
            ]
    }
}
```

## 混淆过滤

```text
-dontwarn com.xunmeng.pap.**
-keep class com.xunmeng.pap.** {*;}
```

