# 拼多多

## 模块引入

```text
    implementation WB.fixVersions('TJ:PDD')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| PDD\_APPID | appid,商务/需求单提供 | eg：12345 |
| PDD\_APPSECRET | appsecret,商务/需求单提供 | eg：12345 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置 PDD\_APPID 和 PDD\_APPSECRET 的值,如下：

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

## 注意事项

查看接入是否成功 可以过滤 PAPTrans 查看log,如果输出 PAPTrans-e: report success 则是接入正常，其他是有问题。需参数和包名一致，产品名不一致也有可能导致上报失败

