# Creator

## Demo工程克隆地址 ：

### Creator工程：

```cpp
git clone http://dnsdk.vimedia.cn:8080/r/CreatorDemo.git
```

## Creator插件

将CreatorDemo项目中的assets/Wb目录拷贝到自己的工程目录下即可使用。

主要有 ADManger , CoreManger, PayManger, ToolManger等。

## 接口使用

导入头文件并使用接口

```typescript
import {Wb} from "../../Wb/Scripts/Define";

Wb.ADManager.Instance.openAd("home_mfzs");
```

具体使用，请参考业务接口进行接入：

### [业务接口](../ye-wu-jie-kou/)

## Android对接

