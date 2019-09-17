# CheckPlugin 模块版本自动更新插件
## 功能

   主要提供一个接口 fixVersions，接口作用主要是自动使用当前最新版本，也可以指定版本；
   自动更新混淆文件；
## 工程根目录下 build.gradle 中添加
```text
   buildscript {
    repositories {
       ...
        maven { url uri('\\\\192.168.1.252\\产品配置\\工具\\plugins')}
    }
    
     dependencies {
        ...
        classpath 'com.wb.check:plugin:1.0.1'          
        }
```
## app目录下 build.gradle 中添加
```text
apply plugin: 'Wb-check'
def WB = getPlugins().findPlugin('Wb-check')
```

## 混淆文件配置 
混淆文件配置中添加  'vigame_proguard.pro'
例如：
```text
buildTypes {
     debug {
       ...
     }
     release {
        ...
         proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro', 'vigame_proguard.pro'
        ...
     }
 }
```

## build.gradle 中模块引入方式修改
1. 模块用WB.fixVersions()包裹
2. com.libVigame可以省略不写
3. 版本号不写时会使用当前最新版本
4. 可以指定版本

原来使用最新版本：
```text
implementation 'com.libVigame.Core:CoreManager:2.4.3'
```
现在使用最新版本：
```text
implementation WB.fixVersions('Core:CoreManager')
```
原来使用指定版本：
```text
implementation 'com.libVigame.Core:CoreManager:2.4.3'
```
现在使用指定版本：
```text
implementation WB.fixVersions('Core:CoreManager','2.4.3')
```
