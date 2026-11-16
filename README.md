# 12123 短信闹钟 · 发行仓

这个仓库不放源码，只放 Release。

每个版本一个 Release，里面包含：

- 更新说明（Release 正文，第一行 `versionCode: NN` 供 App 精确比版本）
- 安装包 `.apk` 资产

App 的检查升级走两条路：

1. `GET https://api.github.com/repos/xiaojiekeji/12123-sms/releases/latest` —— 主通道
2. `GET https://raw.githubusercontent.com/xiaojiekeji/12123-sms/main/release/latest.json` —— 接口限流时兜底

发版方式：改好 `release/latest.json`（tag / title / versionCode / apkUrl / apkName / notes）推到 main，
Actions 会自动下载 `apkUrl` 指向的安装包并挂到对应 tag 的 Release 上。
