# luci-app-unblockneteasemusic

## 依赖 [UnblockNeteaseMusic](https://github.com/cnsilvan/UnblockNeteaseMusic)

## 前言

1. 有问题，请开issues，有空会修复（我更希望有人pr）

2. 可能会和lede或其他openwrt固件自带的UnblockNeteaseMusic插件冲突（编译界面找不到该插件），编译前移除其他插件（包括依赖库）

## 编译与升级

编译分两个ipk，需要一并安装。

如果只需要升级UnblockNeteaseMusic依赖包，可以直接从[UnblockNeteaseMusic](https://github.com/cnsilvan/UnblockNeteaseMusic/releases)中下载对应的版本解压到/usr/bin/下 ，且赋予运行权限
`chmod +x /usr/bin/UnblockNeteaseMusic`,最后在luci界面重新启用该插件即可完成依赖包的升级。

## luci界面

![Image text](https://raw.githubusercontent.com/cnsilvan/luci-app-unblockneteasemusic/master/pic/1.png)

## 感谢

  [这个版本Luci](https://github.com/project-openwrt/luci-app-unblockneteasemusic)
