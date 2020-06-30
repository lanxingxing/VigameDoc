# Unity

## Clone URL of Demo：

### Unity Project：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo.git)

### Android Studio Project：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo-Google.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo-Google.git)

## Import Unity Plugin

download：[UniWb.Wb](http://gui.vigame.cn/UniWb/wb/UniWb.Wb.unitypackage)

Imported the UniWb.Wb.unitypackage, two folders named **Streanming**  and **Wb** will appear in the resource management interface.

**StreamingAssets/st.txt** saved signature info。

**Wb** folder is interface, there are ADManger , CoreManger, PayManger, ToolManger, XyxManger etc。

## Use interface

Reference bellow:

### [interface](ye-wu-jie-kou-1/)

## Signature verification

At the start of the game, if signature verification is required, this method is called:

```text
 Wb.CoreManager.Instance.CheckSignature();
```

StreamingAssets/st.txt save the hash of the default signature, content is：-49852205,1765204456

To add your own signature，download here: [vigame\_signature\_tool](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)。

Then sign the apk with a new signature, and then add the signature information obtained in the above tool to the st.txt file.

## Android

#### 1.Add Android modules

Reference：


> Please skip the 5.2，because we will use Activity inherit instead.

#### 2.Add UnityBridge module in build.gradle

```java
implementation WB.fixVersions('Bridge:UnityBridge')
```

#### 3.Made the main Acitivy inherit UniWbActivity Or Made the UniWbActivity as main Activity

```java
package org.cocos2dx.cpp;
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

> UniWbActivity has inherited UnityPlayerActivity

