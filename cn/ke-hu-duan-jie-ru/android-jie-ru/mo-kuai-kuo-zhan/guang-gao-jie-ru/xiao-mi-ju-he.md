# 小米聚合

## 模块引入

需本地引入，模块下载链接：[http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libAD/libAD\_Mi\_Mediation&h=master&format=zip](http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libAD/libAD_Mi_Mediation&h=master&format=zip)

setting.gradle中添加

include ':libAD\_Mi\_Mediation' project\(':libAD\_Mi\_Mediation'\).projectDir = new File\('目录\libAD\_Mi\_Mediation'\)

app目录build.gradle中修改：

```text
repositories {
    flatDir {
      ...
        dirs project(':libAD_Mi_Mediation').file('libs')
      ...  
    }
}



xxxxxImplementation project(':libAD_Mi_Mediation')
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
-keep class com.xiaomi.ad.**{*;}
-keep class com.miui.zeus.**{*;}
```

## 集成测试

如何判断sdk是否初始化成功？

通过MiAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

