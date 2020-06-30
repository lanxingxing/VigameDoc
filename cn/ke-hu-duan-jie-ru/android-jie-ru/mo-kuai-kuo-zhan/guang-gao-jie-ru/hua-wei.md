# 华为广告

## 模块引入

需本地引入，模块下载地址： [http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libAD/libAD\_Huawei&h=master&format=zip](http://192.168.1.252:8080/zip/?r=VigameAndroidLibrary.git&p=libAD/libAD_Huawei&h=master&format=zip)

setting.gradle中添加

```text
include ':libAD_Huawei'
project(':libAD_Huawei').projectDir = new File('目录\\libAD_Huawei')
```

根目录build.gradle中修改：

```text
buildscript {
    repositories {
       ...
        maven {url 'http://developer.huawei.com/repo/'}
       ...
    }    
}

allprojects {
    repositories {
       ...
        maven {url 'http://developer.huawei.com/repo/'}
       ...
    }
}
```

app目录build.gradle中修改：

```text
repositories {
    flatDir {
      ...
        dirs project(':libAD_Huawei').file('libs')
      ...  
    }
}


  xxxxxImplementation project(':libAD_Huawei')
```

## 注意事项

```text
华为提测时需注意
问题1.开屏广告出现之前不能出现游戏界面  
答案1：ConfigVigame.xml中添加
    <BlackFirst>true</BlackFirst><!--是否黑屏启动-->
    <SplashTime>1500</SplashTime><!--开屏图片持续时间-->
    两个配置，如果游戏内没用适配异形屏需多添加
    <FixSpecialScreen>false</FixSpecialScreen><!--是否适配异形牌-->

    如果AndroidManifest.xml中的 activity 或 application中配置了     android:theme="@style/AppWelcome" ，需删除 AppWelcome 中的android:windowBackground标签

问题2：点击开屏广告后跳转到落地页之前不能出现游戏内容
答案2：模块已做修改，点击后不马上关闭广告
问题3：提测时广告配置的问题
答案3：首次提测时需配置测试广告，待华为测试结束后才可在华为后台提审，审核通过后需改为正式广告，并同步给华为广告那边协助配置广告，后续更新包可以直接配置正式广告
问题4：首次提测，交付件描述问题
答案4：交付件中广告位的描述需和广告配置中的一致，不能出现广告位有配置，交付件中没有提到的情况。
问题5：banner刷新问题
答案5：banner刷新改为在华为中做自动刷新，咱们自己的配置不需配置刷新时间
```

## 混淆过滤

```text
-keep class com.huawei.**
-keep class com.huawei.**{*;}
```

## 集成测试

通过HuaweiAgent 和 HuaweiNativeAgent 、ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

