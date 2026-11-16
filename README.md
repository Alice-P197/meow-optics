# 光学宝典 · 官网与安卓版

小黑喵工作室的手机端光学手册。这个仓库只放**官网/落地页**与**安卓安装包的分发**，应用源码不在这里。

- 官网（GitHub Pages）：https://alice-p197.github.io/meow-optics/
- 下载最新安装包：https://github.com/Alice-P197/meow-optics/releases/latest
- 更新清单：https://alice-p197.github.io/meow-optics/update.json

## 仓库内容

```
index.html    官网 / 下载页（单文件，图片在 assets/）
assets/       官网用的应用截图
update.json   应用内更新清单
```

## 发新版本的流程

1. 打出新的 APK，改 `versionCode`（必须递增）与 `versionName`
2. 在 `Alice-P197/Meow-optics-V2` 新建 Release，上传 APK 与 `Guangyu-Server.exe``n3. 更新 `update.json` 的 `versionCode` / `versionName` / `url` / `size` / `sha256`，`url` 填该 tag 下的 APK 直链
4. 更新 `index.html` 里的版本号、体积、下载按钮与本段说明
5. 已安装的用户下次启动会收到提示，覆盖安装不丢数据（签名固定）

- 光屿服务端：https://github.com/Alice-P197/Meow-optics-V2/releases/download/v151-test64/Guangyu-Server.exe
