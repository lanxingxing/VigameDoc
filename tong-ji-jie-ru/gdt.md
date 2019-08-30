# GDT

## 模块引入

```text
    implementation 'com.libVigame.TJ:GDT:2.0.0'
```
##配置文件说明
```text
需要在app的build.gradle的添加如下配置：
android {
    manifestPlaceholders = [
    ....
                GDTAppId:"", //appid参数，配置工具统计参数里面可以拿到               
                GDTAppKey:"", //appkey参数，配置工具统计参数里面可以拿到       
                

    ...
            ]
    }
}

```
## 混淆过滤

```text
-dontwarn com.qq.gdt.action.**
-keep class com.qq.gdt.action.** {*;}
```

## 测试 引荐安装
```text
测试方法包含以下两步：
1.日志过滤GDTAction，查看是否初始化成功
2.抓包。向a.gdt.qq.com发出请求，dp3.qq.com会返回校验结果。SDK会校验包名：安装SDK的包和上传到应用宝的包，如果包名不一致，会返回报错 '51000 package name check failed';如果包名校验成功：{"ret":0,"msg":"success"}
```
