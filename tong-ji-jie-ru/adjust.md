# Adjust

## 模块引入

```text
    implementation 'com.libVigame.TJ:Adjust:1.0.1'
```

## 配置文件说明

```text
在工程目录下的 build.gradle中添加
buildscript {    
    dependencies {
        ...
        classpath 'com.google.gms:google-services:3.0.0'   // 使用 firebase 要添加
       ...
    }
}
```

```text
需要在app的build.gradle的添加如下配置：
apply plugin: 'com.google.gms.google-services'//一定要有，不然统计不到卸载数据
android {
    manifestPlaceholders = [
    ....
                ADJUST_KEY:"xxx", //应用识别码,adjust后台获取               
                ADJUST_TESTMODEL:"false", //是否是测试模式， 测试时设置为 true，注意正式版一定要为false
                ADJUST_APPSECRET:"1,2,1,4,5", //签名配置，再adjust后台 sdk签名中获取 注意不能带 （ ）字符

    ...
            ]
    }
}
```

## 混淆过滤

```text
-keep class com.adjust.sdk.** { *; }
-keep class com.google.android.gms.common.ConnectionResult {
    int SUCCESS;
}
-keep class com.google.android.gms.ads.identifier.AdvertisingIdClient {
    com.google.android.gms.ads.identifier.AdvertisingIdClient$Info getAdvertisingIdInfo(android.content.Context);
}
-keep class com.google.android.gms.ads.identifier.AdvertisingIdClient$Info {
    java.lang.String getId();
    boolean isLimitAdTrackingEnabled();
}
-keep public class com.android.installreferrer.** { *; }
```

##其他注意事项
```text
通过 AdjustAgent tag过滤，查看是否有 FirebaseInstanceId  pushToken 输出，在装有 googleplay的手机上测试，如果有输出则正常，无输出则不能统计卸载需要排查上面步骤是否都正确
```

```text
正式包 ADJUST_TESTMODEL 一定要设置为 false
可通过 Adjust tag过滤日志，在测试模式下可看到如下输出说明接入没有问题
V/Adjust: Path:      /sdk_click
    ClientSdk: android4.6.0
    Parameters:
      app_token        abc123abc123
      click_time       yyyy-MM-dd'T'HH:mm:ss.SSS'Z'Z
      created_at       yyyy-MM-dd'T'HH:mm:ss.SSS'Z'Z
      environment      sandbox
      gps_adid         12345678-0abc-de12-3456-7890abcdef12
      needs_attribution_data 1
      referrer         adjust_reftag=abc1234&tracking_id=123456789&utm_source=network&utm_medium=banner&utm_campaign=campaign
      reftag           abc1234
      source           reftag
      tracking_enabled 1

其他问题可查看 https://github.com/adjust/android_sdk/blob/master/doc/chinese/README.md
```

