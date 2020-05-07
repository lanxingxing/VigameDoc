# 热云

## 模块引入

```text
    //不带opposdk的引入方式
    implementation WB.fixVersions('TJ:ReYun')
     //带opposdk用以下方式
     implementation WB.fixVersions('('TJ:ReYun_OPPO')')
```

## Manifest参数选项

| 参数 | 说明 | 备注 |
| :--- | :--- | :--- |
| ReYunAppKey | 在热云上申请的appKey（商务提供） | eg：5bbb2803b465f5c58c000017 |

## 配置文件说明

需要在app的build.gradle的manifestPlaceholders中设置“ReYunAppKey”的值,如下：

```text
android {
   ...
    defaultConfig {
    manifestPlaceholders = [
    ....
            ReYunAppKey:"5bbb2803b465f5c58c000017",
    ...
            ]
    }
}
```

