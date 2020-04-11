# Umeng推送

## 模块引入

```text
xxx_Implementation 'com.libVigame.Push:UMeng:2.2.0'
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

## 测试需注意事项

```text
Manifest.xml文件中的包名需是推送后台配置的包名 或者 在 assets 目录创建UPH.xml文件，内容如下：
<root>
    <!--友盟推送需要用的文件  包名填写 androidmanifest.xml里面的包名 不一定是build.gradle里面的applicationId -->
    <PackageName>com.wb.gzsj2</PackageName>
</root>

如果要带参数，须在自定义行为中填写如：101=60，5=10
android端没有使用到自定义参数功能
如果收不到推送，优先检查通知权限是否开启，如果开启，可以看 UMengAgent 的tag的日志，查看是否注册成功

点击推送信息无法打开应用时，将发送策略的后续动作改为 自定义行为，参数可写任意数字字符。
如需使用厂商通道，发送时需在系统通道配置打开指定页面及游戏启动页（一般为 com.libVigame.VigameStartActivity）。
华为厂商通道需 SHA256证书指纹 和 app的指纹一样

```

## 验收标准

```text
在通知权限打开的情况下，能正常收到推送通知，点击通知能正常打开游戏，如果有传递奖励道具，道具应能正常到账
```

