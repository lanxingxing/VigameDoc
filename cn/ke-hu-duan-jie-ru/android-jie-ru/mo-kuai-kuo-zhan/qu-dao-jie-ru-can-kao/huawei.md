# 华为

## 模块引入

```text
    implementation WB.fixVersions('Pay:Huawei')
```

## 配置文件说明

根目录 build.gradle中需添加：

```text
buildscript {
    repositories {
        google()
        jcenter()
        maven {url 'http://developer.huawei.com/repo/'}
    }
    dependencies {
         ...
        classpath 'com.huawei.agconnect:agcp:1.3.1.300'   
    }
}

allprojects {
    repositories {
        ...
        maven {url 'http://developer.huawei.com/repo/'}
    }

    ...
}
```

app目录 build.gradle中需添加：

```text
apply plugin: 'com.huawei.agconnect'  //引入华为插件    需要商务提供 agconnect-services.json 文件，不然会报错


manifestPlaceholders = [
                ...
                HWCpId:"",// 华为商户id
                HWAppId:"",// 华为应用id
        ]
```

assets目录加入feedata\_huawei.xml

```text
<?xml version="1.0" encoding="UTF-8"?>
<data>
    <company>深圳市动能无线传媒有限公司</company>
    <!--华为支付公钥-->
    <appkey>MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAlohZLPbK/tKC7YlAhc81gV2pNEap1Odty3C+10FMyCrzb5PdCc6rSXboNhJTK6UdskAI3GADkcpDE7aohlxkQCOPChTTXQ5b6P712WyR0unORLod3bkJ6i/RluuW9QhycdR7k2zLgbYlCL35on3L7SJDJxJ1IwcTSZc0EkhmGifTV/5+ubAt/RtiCBtm7O8Q7hmWqSSXE+uFi+MlE8Y0KzkdWh3VTsb1928R7MIAVou1ob4i3eKcSQH6ieWId9+Cqk0u4zfXr6zYjv/CmJCGV2HFHP8I3WdDGd9Q7loyYm+eyQsN5DwOw0e1CvVKgSrB5TOBY4i8eaSng9HH4krlAwIDAQAB</appkey>
    <!--华为应用id-->
    <appid>10762302</appid>
    <!--华为商户id-->
    <merchantId>890086000102058425</merchantId>
    <!--计费点-->
    <feeinfo>
        <ID>1101</ID>
        <price>1</price>
        <desc>测试华为计费</desc>
    </feeinfo>
</data>
```

## 混淆过滤

```text
#华为
-keep class com.huawei.**
-keep class com.huawei.**{*;}
-keep class com.android.huawei.**
-keep class com.android.huawei.**{*;}
-keep class com.hianalytics.**
-keep class com.hianalytics.**{*;}
-ignorewarning
-keepattributes *Annotation*
-keepattributes Exceptions
-keepattributes InnerClasses
-keepattributes Signature
-keepattributes SourceFile,LineNumberTable
-keep class com.hianalytics.android.**{*;}
-keep class com.huawei.updatesdk.**{*;}
-keep class com.huawei.hms.**{*;}
-keep class com.huawei.gamebox.plugin.gameservice.**{*;}
-keep public class com.huawei.android.hms.agent.** extends android.app.Activity { public *; protected *; }
-keep interface com.huawei.android.hms.agent.common.INoProguard {*;}
-keep class * extends com.huawei.android.hms.agent.common.INoProguard {*;}
```

## 集成测试

1.如何判断sdk是否初始化成功？

可通过名为"HuaweiAgent"的Tag查看日志，登陆成功会有“game login: onResult: retCode=”等日志输出。

2.官方错误码参考文档 [https://developer.huawei.com/consumer/cn/service/hms/catalog/HuaweiJointOperation.html?page=hmssdk\_jointOper\_api\_reference\_errorcode](https://developer.huawei.com/consumer/cn/service/hms/catalog/HuaweiJointOperation.html?page=hmssdk_jointOper_api_reference_errorcode)

