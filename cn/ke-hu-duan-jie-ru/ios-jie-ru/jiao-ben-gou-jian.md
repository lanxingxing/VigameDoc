# 脚本构建

## 1.cd当前工程目录

```text
cd /User/XXXX
```

## 2.下载Vigame到工程

## 2.1 执行clone命令下载

```text
git clone https://github.com/hohua88/Vigame.git
git clone https://github.com/hohua88/deps.git
```

## 2.2 手动下载

[地址](https://github.com/hohua88/Vigame)
[地址](https://github.com/hohua88/deps)
## 3.修改ExportOptions.plist
测试包不需要更改，正式包建议自己打包，用脚本需改动较多
![&#x4FEE;&#x6539;&#x8BC1;&#x4E66;&#x914D;&#x7F6E;](https://github.com/jieban0604/VigameDoc/tree/ae57de14708d5444e6f1ef3b4a82ef875535b3a9/.gitbook/assets/xiu_gai_zheng_shu.png)

## 4.执行auto.sh脚本

```text
./Vigame/auto.sh a03cfead89f5934d #执行脚本 参数为singleid是必须
```

脚本执行完成后会上传到fir.im，之后会打开打包的文件夹，里面有个二维码图片，可以把这个图片给到测试下载。

