# KuaiShou

## 模块引入

```text
    implementation WB.fixVersions('TJ:KuaiShou')
```

## 配置文件说明

```text
需要在app的build.gradle的添加如下配置：
android {
    manifestPlaceholders = [
    ....
                KuaiShou_Appid:"", //快手appid参数，需求单里面可以拿到               
                KuaiShou_Appname:"", //快手appname参数，需求单里面可以拿到       

    ...
            ]
    }
}
```



## 混淆过滤

```text
-keep class com.kwai.monitor.** { *; }
```

## 查看接入是否正常

```text
运行应用程序，然后在logcat中过滤 KS_LOG tag
成功log:
register sdk success

report log success eventName:EVENT_ACTIVE

失败log:
register sdk fail :  
```

