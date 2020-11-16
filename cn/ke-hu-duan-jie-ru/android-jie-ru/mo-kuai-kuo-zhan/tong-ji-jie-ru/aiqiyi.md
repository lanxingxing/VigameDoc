# 爱奇艺

## 模块引入

```text
    implementation WB.fixVersions('TJ:IQiYi')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| IQiYiAppid | 在后台申请的appid | eg：123456 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置“IQiYiAppid”的值,如下：

```text
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
    ....
            IQiYiAppid:"123456",
    ...
            ]
    }
}
```

## 混淆过滤

```text
-keep class com.iqiyi.qilin.trans.**
-keep class com.iqiyi.qilin.trans.**{*;}
```

## 其他注意事项

```text
无
```

