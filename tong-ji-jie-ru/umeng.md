# Umeng

## 模块引入

```text
    implementation 'com.libVigame.TJ:UMeng:2.0.5'
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| UMENG\_APPKEY | 在友盟上申请的appKey | eg：5bbb2803b465f5c58c000017 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置“UMENG\_APPKEY”的值,如下：

```text
android {
    compileSdkVersion 28
    buildToolsVersion '28.0.3'
    publishNonDefault true
    defaultConfig {
    manifestPlaceholders = [
    ....
            UMENG_APPKEY:"5bbb2803b465f5c58c000017",
    ...
            ]
    }
}
```

## 混淆过滤

```text
-keep class com.umeng.**
-keep class com.umeng.**{*;}
```

## 其他注意事项

```text
须在工程根目录的build.gradle中添加
buildscript {
    repositories {
        ...
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }
   }
   
   allprojects {
    repositories {
      ...
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }
}
```

