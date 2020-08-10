# HeadlineTrcking

## 模块引入

```text
    implementation WB.fixVersions('TJ:HeadLine')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| HEADLINE\_APPID | 在头条统计上申请的appId | eg：153354 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置“HEADLINE\_APPID”的值,如下：

```text
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
    ....
            HEADLINE_APPID:"153354",
    ...
            ]
    }
}
```

## 混淆过滤

```text
-keep com.bytedance.**
-keep com.bytedance.**{*;}
-keep com.ss.android.common.**
-keep com.ss.android.common.**{*;}
```





可通过过滤  TeaLog 查看log