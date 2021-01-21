# Unity

## Demo工程克隆地址 ：

### Unity工程：

```cpp
git clone http://dnsdk.vimedia.cn:8080/r/UnityDemo.git
```

### Android Studio 工程：

```cpp
git clone http://dnsdk.vimedia.cn:8080/r/UnityDemo-Android.git
```

### Android 多渠道模板工程：（仅供内部使用）

```cpp
git clone http://192.168.1.252:8080/r/android/UnityDemo-Android-Ex.git
```

### Xcode 工程：

```cpp
git clone http://dnsdk.vimedia.cn:8080/r/UnityDemo-IOS.git
```

## 导入Unity插件

### [**插件下载**](cha-jian-xia-zai.md)

将UniWb.Wb.unitypackage导入成功后，在资源管理界面中会出现名为**Streanming**与**Wb**两个文件夹。

**StreamingAssets/st.txt** 保存的是签名的信息。

**Wb** 文件夹存放业务接口，主要有 ADManger , CoreManger, PayManger, ToolManger, XyxManger等。

## 接口使用

参考业务接口进行接入：

### [业务接口](../ye-wu-jie-kou/)

## Android 接入

#### 1.添加Android相关模块

参考以下链接进行接入：

### [Android](../android-jie-ru/)

> 请跳过链接页面中第五步的第2条，因为后面已使用Activity继承代替。

#### 2.在 build.gradle 中加入Unity桥接模块

```java
implementation WB.fixVersions('Bridge:UnityBridge')
```

#### 3.将主Acitivy继承UniWbActivity或者将UniWbActivity作为主Activity。

```java
package org.vigame.demo;
import android.os.Bundle;
import com.vigame.unitybridge.UniWbActivity;

public class AppActivity extends UniWbActivity 
{    
   @Override  
   protected void onCreate(Bundle savedInstanceState) 
   {       
        super.onCreate(savedInstanceState);  
   }
}
```

> UniWbActivity已经继承UnityPlayerActivity

## iOS 接入

#### 1.添加iOS相关模块

参考以下链接进行接入：

### [iOS](../ios-jie-ru/)

