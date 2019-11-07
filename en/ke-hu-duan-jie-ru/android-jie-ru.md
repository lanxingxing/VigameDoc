# Android

### Clone URL of Demo：

[http://dnsdk.vimedia.cn:8080/r/VigameDemo-Android.git](http://dnsdk.vimedia.cn:8080/r/VigameDemo-Android.git)

## 1:Add maven repositories

```text
buildscript {    repositories {        google()        jcenter()        //umeng        maven { url 'https://dl.bintray.com/umsdk/release' }    }    }
```

```text
allprojects {    repositories {        google()        jcenter()        //vigame        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }        //umeng        maven { url 'https://dl.bintray.com/umsdk/release' }    }}
```

## 2：implementation necessary modules

```text
    //vigame    implementation 'com.libVigame.Proxy:Features:2.6.2'    implementation 'com.libVigame.Loader:VigameLoader:2.6.0'    implementation 'com.libVigame.Core:CoreManager:2.4.6'    implementation 'com.libVigame.Pay:PayManager:2.2.8'    implementation 'com.libVigame.AD2:ADManager:2.3.8'    implementation 'com.libVigame.TJ:TJManager:2.0.8'    implementation 'com.libVigame.Social:SocialManager:2.1.8'    implementation 'com.libVigame.Extention:ExtManager:2.0.1'    //third library    implementation 'com.libVigame.Core:android-query:2.1.1'    implementation 'com.android.support:support-v4:28.0.0'    implementation 'com.android.support:appcompat-v7:28.0.0'
```

## 3：Add code in the project

Modify MyApplication.java And add code in the corresponding life cycle:

```text
public class MyApplication extends Application {    @Override    public void onCreate() {        super.onCreate();        VigameLoader.applicationOnCreate(this);    }    @Override    protected void attachBaseContext(Context base) {        super.attachBaseContext(base);        VigameLoader.applicationAttachBaseContext(this, base);    }}
```

Modify MainActivity And add code in the corresponding life cycle：

```text
    @Override    protected void onResume() {        super.onResume();        VigameLoader.activityOnResume(this);    }    @Override    protected void onPause() {        super.onPause();        VigameLoader.activityOnPause(this);    }    @Override    protected void onDestroy() {        super.onDestroy();        VigameLoader.activityOnDestroy(this);    }    @Override    public void onWindowFocusChanged(boolean hasFocus) {        super.onWindowFocusChanged(hasFocus);        VigameLoader.activityOnWindowFocusChanged(this,hasFocus);    }    @Override    protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {        super.onActivityResult(requestCode, resultCode, data);        VigameLoader.activityOnActivityResult(this,requestCode,resultCode,data);    }    @Override    protected void onRestart() {        super.onRestart();        VigameLoader.activityOnRestart(this);    }
```

## 4. Modify AndroidManifest.xml

Add related parameter configuration, And use VigameStartActivity as launch item.

```text
<meta-data    android:name="com.vigame.sdk.appid"    android:value="10001" /><meta-data    android:name="com.vigame.sdk.appkey"    android:value="abcdefg" /><meta-data    android:name="com.vigame.sdk.prjid"    android:value="333360" /><meta-data    android:name="com.vigame.purchase.channel"    android:value="${WB_CHANNEL}" /><activity android:name="com.libVigame.VigameStartActivity"    android:theme="@android:style/Theme.NoTitleBar.Fullscreen">    <intent-filter>        <action android:name="android.intent.action.MAIN" />        <category android:name="android.intent.category.LAUNCHER" />    </intent-filter></activity>
```

## 5. Put in the configuration file and modify

Copy VigameConfig.xml and agrement.html to assets dictionary.

And You can configurate ConfigVigame.xml in assets. Property description is as follows:

| Name | description | necessary |
| :--- | :--- | :--- |
| GameOpenActivity | the path of your main Activity | yes |
| ScreenOrientation | the orientation of screen | no |
| SupportAdPositions | the adPositionName of supports | no |
| WithSplashAD | Support splash ad | no |
| IsSDK | 'true' always and don't modify | yes |
| CompanyIndex | the index of company，default 1 | yes |

## 6：Configuration items of test

#### 1.Open app/build.gradle，modify package/channel/umeng appkey.

Recommendation the package name as follows for Advertising display

```text
defaultConfig {        applicationId "com.dn.tgxm.gg"        ...        manifestPlaceholders = [                UMENG_APPKEY     : "",                WB_CHANNEL       : "gg"        ]}
```

#### 2. Modify the background of Splash AD.

If needs,repalace bg\_splash\_vigame.png file in res/drawable.

