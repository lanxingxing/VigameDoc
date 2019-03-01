# Facebook

## 模块引入

```text
    implementation 'com.libVigame.Social:Facebook:2.1.7'
```

## Manifest参数选项

```text
    需要配置两个参数，两个参数的值一样，但是配置的方式不一样
```

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| facebook\_app\_id | 在facebook上申请的appId | eg：344465672947670 |
| Fb\_share\_appId | 在facebook上申请的appId，用于分享 | eg：344465672947670 |
| fb\_login\_protocol\_scheme | fb+在facebook上申请的appId,用于登录 | eg：fb344465672947670 |

## 配置文件说明
1.需要在app的build.gradle的manifestPlaceholders中设置“Fb_share_appId”的值,示例如下：
```text
    
        android {
            compileSdkVersion 28
            buildToolsVersion '28.0.3'
            publishNonDefault true
            defaultConfig {
                 manifestPlaceholders = [
            ....
                        Fb_share_appId:"370338263768260",
            ...
                        ]
                }
        }
```
2.需要在res/values/strings.xml目录下添加：("344465672947670"是你的faceAPPId)
```text
        <string name="facebook_app_id">370338263768260</string>
        <string name="fb_login_protocol_scheme">fb370338263768260</string>
```
## 混淆过滤

```text
-keep class com.facebook.**{*;}
```

