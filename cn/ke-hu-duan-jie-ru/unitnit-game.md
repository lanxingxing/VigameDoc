# Unity

## Demo工程克隆地址 ：

### Unity工程：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo.git)

### Android Studio 工程：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo-Android.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo-Android.git)

### Xcode 工程：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo-IOS.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo-IOS.git)

## 下载地址

[UniWb.Wb](http://gui.vigame.cn/UniWb/wb/UniWb.Wb.unitypackage)

## 使用

导入到工程后，有两个文件夹，**StreamingAssets/st.txt** 保存的是签名的信息，若需要新的签名则可以添加在这个文件中。

UniWb/wb 是业务接口，主要有 ADManger , CoreManger, PayManger, ToolManger, XyxManger

接口在对应的 interface 文件夹下， 例如 AD 在 AD/interface/ADBase

## 接口使用

AD：

```text
      Wb.ADManager.Instance.OpenAd("banner");

      bool result = Wb.ADManager.Instance.IsAdReady(adName);

      Wb.ADManager.Instance.OpenAd("home_mfzs", result =>
        {
            if (result)
            {
                ShowBottomToast("视频广告打开成功", false);
            }
            else
            {
                ShowBottomToast("视频广告打开失败", true);
            }
        });
```

其它 Manger 如此，查看 Base 基类，可比较方便的查看已实现的方法。

## 互推使用

​ 导入 UniWb.Wb.unitypackage 后， 在 Wb/Xyx/prefab/ 文件夹下 有 PushIconItem 预制体，拖入 canvas 即可，在打包安卓时 可使用 112234 项目id 测试。

注意 ：在 build.gradle 中引入 （以上版本）

```java
implementation 'com.libVigame.Bridge:UnityBridge:1.0.6'
implementation 'com.libVigame.Proxy:Features:2.6.4'
```

![](https://github.com/jieban0604/VigameDoc/tree/989e57604fc5a87cabae6f86ecd25c41f3a79362/.gitbook/assets/UniWb01.jpg)

## Android 接入

在 build.gradle 中引入

```java
implementation 'com.libVigame.bridge:UnityBridge:1.0.6'
```

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

Activity 继承 UniWbActivity 即可， 与 unity 交互的 接口在 UniWbActivity 类中，可查看。

也可直接 使用 UniWbActivity Activity

## 签名验证

```text
 Wb.CoreManager.Instance.CheckSignature();
```

在游戏开始的时候，如果需要签名验证，调用该方法， st.txt 文件保存签名的 哈希值。

st.txt 放在 StreamingAssets 文件夹下

st.txt 内容

-49852205,1765204456

## 签名配置

下载地址 [vigame签名获取工具](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)

用待添加的签名，签名上述apk，然后再 st.txt 文件里添加上述工具中获取到的签名信息

## ios 接入

ios 桥接文件修改

在 项目 Bridge 文件下 修改 AdBridge.h 和 AdBridge.mm 文件， 直接全部覆盖

```c
extern "C"
{
    // ADManager
    void OpenAd(const char* adName);
    void OpenYsAd(const char* adName,int width,int height, int x,int y);
    void CloseAd(const char* videoName);
    bool IsAdReady(const char* adName);
    bool IsAdBeOpenInLevel(const char* adName, int level);

    // CoreManager
    void UseCDKey(const char* dhm);
    void OpenActivityPage();
    void OpenActivityNotice();
    void OpenRank();
    void OpenUserAgreement();
    void OpenFeedback();
    void SetGameName(const char* adName);
    const char* GetChannel();
    const char* GetPrjid();
    const char* GetAppid();
    const char* GetLsn();
    const char* GetUuid();
    const char* GetImsi();
    const char* GetImei();

    // PayManager
    void OrderPay(int payId);
    void OrderPay2(int payId, const char* userData);
    void OrderPay3(int payId, int price, const char* userData);
    int GetGiftCtrlFlagUse(int giftId);
    bool IsSupportExit();
    void OpenExitGame();
    bool IsMoreGameBtn();
    void OpenMoreGame();
    bool IsPayReady();
    char* GetDefaultFeeInfo();

    // TjManager
    void TJCustomEvent(const char* eventId);
    void TJCustomEvent2(const char* eventId,const char* label);
    void TJCustomEvent3(const char* eventId,const char* map);
    void StartLevel(const char* level);
    void FinishLevel(const char* level, const char* score);
    void FailLevel(const char* level, const char* score);

    // ToolManger
    void ShockPhone();
    void ApplicationExit();
    void SetKeyEnable();
    void ShowToast(const char* str);

    // XyxManger
    void OnIconClicked(int id);
    const char* GetIconURL(int id);
    const char* GetGameList();
    int GetIconCount();

}
```

```cpp
#import "AdBridge.h"

#import "IOSLoader.h"
//
#include "vigame_core.h"
////广告
#include "vigame_ad.h"
////统计
#import "vigame_tj.h"
////支付
#import "vigame_pay.h"
#include "pay/FeeInfo.h"

//字符串分割函数
vector<string> split(string str, string pattern)
{
    string::size_type pos;
    vector<string> result;

    str += pattern;//扩展字符串以方便操作
    int size = str.size();

    for (int i = 0; i<size; i++) {
        pos = str.find(pattern, i);
        if (pos<size) {
            std::string s = str.substr(i, pos - i);
            result.push_back(s);
            i = pos + pattern.size() - 1;
        }
    }
    return result;
}

extern "C"
{
    /////////////////////////////////////////// ADManager
    static bool isFistOpenAD = true;

    void OpenAd(const char* adName)
    {
        string str = adName;
        vigame::ad::ADManager::openAd(adName,[=](vigame::ad::ADSourceItem* adSourceItem, int result){
            char param[64] = {0};
            /*打开视频成功*/
            if (result==0) sprintf(param, "%s#true",str.c_str());
            /*打开视频失败*/
            else sprintf(param, "%s#false",str.c_str());
            printf("%s\n",param);
            UnitySendMessage("ADManager", "VideoCallBack" ,param);
        });

        // 如果是第一次打开，改变状态？
        if(isFistOpenAD)
        {
            isFistOpenAD = false;
            vigame::ad::ADManager::setAdStatusChangedCallback([=](vigame::ad::ADSourceItem* adSourceItem){
                std::string type = adSourceItem->adSourcePlacement->type;
                int stute = adSourceItem->getStatus();
                if (stute == 9 && type == "plaque") {
                    UnitySendMessage("ADManager", "VideoCallBack" ,"false");
                }
            });
        }
    }

    void OpenYsAd(const char* adName,int width,int height, int x,int y)
    {
        NSLog(@"width = %d height = %d x=%d y= %d",width,height,x,y);
        CGFloat kScreenScale = (NSInteger)[UIScreen mainScreen].scale;
        CGSize size = [UIScreen mainScreen].bounds.size;
        if ((NSInteger)size.height==736) {
            kScreenScale/=1.15;
        }
        // 打开广告同时设置size
        vigame::ad::ADManager::openAd(adName, width/kScreenScale, height/kScreenScale, x/kScreenScale, y/kScreenScale);
    }

    void CloseAd(const char* adName)
    {
        vigame::ad::ADManager::closeAd(adName);
    }

    bool IsAdReady(const char* adName)
    {
        bool result = vigame::ad::ADManager::isAdReady(adName);
        return result;
    }

    bool IsAdBeOpenInLevel(const char* adName, int level)
    {
        return vigame::ad::ADManager::isAdBeOpenInLevel(adName, level);
    }

    /////////////////////////////////////////// CoreManager
    void UseCDKey(const char* dhm) { vigame::dhm::use(dhm);}
    void OpenActivityPage() { vigame::activity::open();}
    void OpenActivityNotice() { vigame::notice::open();}
    void OpenRank() { vigame::rank::open();}
    void OpenUserAgreement() { vigame::UserAgreement::open();}
    void OpenFeedback(){ vigame::feedback::open();}
    void SetGameName(const char* adName){ vigame::CoreManager::setGameName(adName);}
    const char* GetChannel() { return vigame::SysConfig::getInstance()->getChannel().c_str();}
    const char* GetPrjid(){ return vigame::SysConfig::getInstance()->getPrjid().c_str();}
    const char* GetAppid(){ return vigame::SysConfig::getInstance()->getAppid().c_str();}
    const char* GetLsn(){ return vigame::SysConfig::getInstance()->getLsn().c_str();}
    const char* GetUuid(){ return vigame::SysConfig::getInstance()->getUUID().c_str();}
    const char* GetImsi(){ return vigame::SysConfig::getInstance()->getImsi().c_str();}
    const char* GetImei(){ return vigame::SysConfig::getInstance()->getImei().c_str();}

    /////////////////////////////////////////// PayManager
    void OrderPay(int payId) { vigame::pay::PayManager::orderPay(payId);}
    void OrderPay2(int payId, const char* userData) { vigame::pay::PayManager::orderPay(payId,userData);}
    void OrderPay3(int payId, int price, const char* userData) { vigame::pay::PayManager::orderPay(payId,price,userData);}
    int GetGiftCtrlFlagUse(int giftId) { return vigame::pay::PayManager::getGiftCtrlFlag(giftId);}
    bool IsSupportExit(){ return vigame::pay::PayManager::isExitGame();}
    void OpenExitGame() { vigame::pay::PayManager::openExitGame();}
    bool IsMoreGameBtn() { return vigame::pay::PayManager::isMoreGame();}
    void OpenMoreGame() { vigame::pay::PayManager::openMoreGame();}
    bool IsPayReady()
    {
        return true;

    }
    char* GetDefaultFeeInfo()
    {
//        vigame::pay::FeeInfo* fee = vigame::pay::PayManager::getDefaultFeeInfo();
//        if(fee == nullptr) return  nullptr;
//        return fee.
        return nullptr;
    }

    /////////////////////////////////////////// TjManager
    void TJCustomEvent(const char* eventId) { vigame::tj::DataTJManager::event(eventId);}
    void TJCustomEvent2(const char* eventId,const char* label) { vigame::tj::DataTJManager::event(eventId,label);}
    void TJCustomEvent3(const char* eventId,const char* map)
    {
        std::unordered_map<std::string,std::string > umap;

        vector<string> spv =  split(map,"#");
        for (int i =0; i< spv.size(); i++) {
            if(spv[i].length() <=0) continue;
            vector<string> kv = split(spv[i],",");
            umap.insert(std::pair<std::string,std::string>(kv[0],kv[1]));
        }
        vigame::tj::DataTJManager::event(eventId,umap);
    }
    void StartLevel(const char* level) { vigame::tj::DataTJManager::startLevel(level);}
    void FinishLevel(const char* level, const char* score) { vigame::tj::DataTJManager::finishLevel(level,score);}
    void FailLevel(const char* level, const char* score) { vigame::tj::DataTJManager::failLevel(level,score);}

    /////////////////////////////////////////// ToolManger
    void ShockPhone() {}
    void ApplicationExit() {}
    void SetKeyEnable() {}
    void ShowToast(const char* str) {}

    /////////////////////////////////////////// XyxManger
    void OnIconClicked(int id)
    {
//        vigame::XYXItemList* list = vigame::XYXManager::getInstance()->getConfig()->getXYXItemList();
//        if(list == nullptr || list->size() <=0) return;
//        list->at(id);
//        vigame::XYXManager::getInstance()->getConfig()->ha
    }
    const char* GetIconURL(int id) { return nullptr;}
    const char* GetGameList() { return nullptr;}
    int GetIconCount(){ return -1;}

}
```

