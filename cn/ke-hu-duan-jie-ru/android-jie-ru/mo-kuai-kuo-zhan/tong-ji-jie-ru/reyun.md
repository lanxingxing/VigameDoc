# 热云

## 模块引入

```text
    implementation WB.fixVersions('TJ:ReYun')    
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



**问题排查**

通过 tracking 字段过滤 log,查看 是否有热云上报数据输出

