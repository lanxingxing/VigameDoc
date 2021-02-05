# Creator

## Clone URL of Demo

### Creator Project：

```cpp
git clone http://dnsdk.vimedia.cn:8080/r/CreatorDemo.git
```

## Import Creator Plugin

Copy the 'assets/Wb' folder from CreatorDemo into your project to complete import.

The main interfaces include 'ADManger' , 'CoreManger', 'TjManger', 'ToolManger' etc.

## Use interface

Import 'Define.ts' and then use interface: 

```typescript
import {Wb} from "../../Wb/Scripts/Define";

Wb.ADManager.Instance.openAd("home_mfzs");
```

Reference bellow:

### [interface](ye-wu-jie-kou-1/)