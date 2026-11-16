# 光学宝典 · 官网与安装包分发

小黑喵工作室的手机端光学设计与仿真工作台。本仓库承担 **官网页面** 与 **安卓安装包的发布**；客户端源码与电脑端源码在私有仓库维护，服务端安装包在 `Alice-P197/Meow-optics-V2` 的 Releases 发布。

- 官网（GitHub Pages）：https://alice-p197.github.io/meow-optics/
- 本仓库发布页（安卓安装包）：https://github.com/Alice-P197/meow-optics/releases
- 服务端发布页：https://github.com/Alice-P197/Meow-optics-V2/releases
- 更新清单：https://alice-p197.github.io/meow-optics/update.json

## 仓库内容

```
index.html        官网 / 下载页（单文件样式内置）
assets/           官网截图（对话页、深色对话页、计算器页、服务端控制台）
update.json       应用内更新清单
```

## 约定

**以后所有光学宝典 APK 都发在本仓库的 Releases**，不再往别的仓库放客户端。

## 发新版本的流程

1. 打出新的 APK，`versionCode` 必须递增，`versionName` 按 `主.次.补-阶段.号` 写
2. 在本仓库建 Release，tag 形如 `v<build>-<阶段><号>`，上传 APK，资产名带版本号
3. 改 `update.json`：`versionCode` / `versionName` / `url`（指向本仓库该 tag 的 APK 直链）/ `size` / `sha256`
4. 改 `index.html`：顶部版本号、hero 的体积与按钮、下载卡片的版本与字节数、本页说明
5. 提交后 Pages 自动重建，已安装用户在下次启动时收到更新提示，覆盖安装不丢数据

## 旧包说明

根目录曾直放 `MeowOptics.apk` 与 `MeowOptics-1.1.apk` 两个早期安装包，现已改由 Releases 分发。
