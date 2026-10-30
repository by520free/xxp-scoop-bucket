# my-scoop-bucket

个人维护的 Scoop 软件桶（bucket）。

## 安装

```powershell
# 把 YOUR_USERNAME 换成你的 GitHub 用户名
scoop bucket add my-scoop-bucket https://github.com/YOUR_USERNAME/my-scoop-bucket
scoop install my-scoop-bucket/grclean
```

## 包含的软件

| 名称 | 说明 | 主页 |
| --- | --- | --- |
| `grclean` | 轻量、安全、无广告的 Windows 清理与优化工具（仅 Windows x64） | https://github.com/graent/grclean |

> 注意：grclean 的授权禁止再分发，本 bucket 的 manifest 仅**指向官方 GitHub Releases 链接**，不托管任何二进制文件。建议仅自用或先取得作者许可。

## 维护说明

- **新版本检测**：`scoop update` 会通过 manifest 里的 `checkver` 自动发现 grclean 的新版本。
- **更新 manifest**：发布新版本后，修改 `bucket/grclean.json` 的 `version` 与 `hash`（setup.exe 的 sha256，可在 Release 资产页或 `releases/expanded_assets/vX.Y.Z` 页面找到），提交即可。`autoupdate` 会自动拼接下载 URL。
- **新增软件**：在 `bucket/` 目录下新建 `<app-name>.json`（参考官方 [BucketTemplate](https://github.com/ScoopInstaller/BucketTemplate)）。
