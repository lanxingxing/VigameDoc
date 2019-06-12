# Umeng推送

## 模块引入
```text
xxx_Implementation 'com.libVigame.Push:UMeng:2.1.9'
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
Manifest.xml文件中的包名需是推送后台配置的包名
如果要带参数，须在自定义行为中填写如：101=60，5=10
android端没有使用到自定义参数功能
```
