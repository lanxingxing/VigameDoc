# Umeng推送

## 模块引入

```text
xxx_Implementation 'com.libVigame.Push:UMeng:2.1.9'
```

## 其他注意事项

```text
须在工程根目录的build.gradle中添加buildscript {    repositories {        ...        maven { url 'https://dl.bintray.com/umsdk/release' }    }   }   allprojects {    repositories {      ...        maven { url 'https://dl.bintray.com/umsdk/release' }    }}
```

## 测试需注意事项

```text
Manifest.xml文件中的包名需是推送后台配置的包名如果要带参数，须在自定义行为中填写如：101=60，5=10android端没有使用到自定义参数功能如果收不到推送，优先检查通知权限是否开启，如果开启，可以看 UMengAgent 的tag的日志，查看是否注册成功
```

## 验收标准

```text
在通知权限打开的情况下，能正常收到推送通知，点击通知能正常打开游戏，如果有传递奖励道具，道具应能正常到账
```

