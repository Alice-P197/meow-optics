# 光学宝典 · 官网与安卓版

小黑喵工作室的手机端光学手册。小程序版是底座，这个仓库只放**官网/落地页**和**安卓安装包的分发**。

- 官网（GitHub Pages）：https://alice-p197.github.io/meow-optics/
- 下载最新安装包：https://github.com/Alice-P197/meow-optics/releases/latest
- 更新清单：https://alice-p197.github.io/meow-optics/update.json
- 小程序源码（另一个仓库）：https://github.com/Alice-P197/meow-optics-miniprogram

## 仓库内容

```
index.html    官网 / 下载页（单文件，图片在 assets/）
assets/       官网用的应用截图
update.json   应用内更新清单
```

## 发新版本的流程

1. 打出新的 APK，改 `versionCode`（必须递增）与 `versionName`
2. 新建 Release，资产名固定为 `MeowOptics.apk`（`latest/download/MeowOptics.apk` 这个链接才不会失效）
3. 更新 `update.json` 里的 `versionCode` / `versionName` / `url` / `size`，推送
4. 已安装的用户下次启动就会收到提示，点一下即覆盖安装（签名固定，不丢数据）
