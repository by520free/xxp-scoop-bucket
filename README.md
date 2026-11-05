# xxp-scoop-bucket

个人维护的 Scoop 软件桶（bucket）。

## 安装

```powershell
scoop bucket add xxp-scoop-bucket https://github.com/by520free/xxp-scoop-bucket
scoop install xxp-scoop-bucket/grclean
scoop install xxp-scoop-bucket/pulse
```

## 包含的软件

| 名称 | 说明 | 主页 | 授权 |
| --- | --- | --- | --- |
| `grclean` | 轻量、安全、无广告的 Windows 清理与优化工具（仅 Windows x64） | https://github.com/graent/grclean | 自定义（禁止再分发） |
| `pulse` | 为 Windows 打造的现代文件管理器：多标签/多窗格、全盘索引与拼音搜索、空格快速预览（仅 Windows x64） | https://github.com/jimmgreen/pulse | Apache-2.0 |

> 注意：grclean 的授权禁止再分发，本 bucket 的 manifest 仅**指向官方 GitHub Releases 链接**，不托管任何二进制文件。建议仅自用或先取得作者许可。pulse 为 Apache-2.0，可自由再分发。

> 关于 pulse 的 PulseIndex 服务：Scoop 包以用户级方式静默安装，默认**不注册** PulseIndex 服务（注册 Windows 服务需管理员权限，会在静默安装时失败）。如需全盘索引搜索，可在 Pulse 设置中手动开启，届时按提示提权即可。

## 维护说明

- **新版本检测**：`scoop update` 会通过各 manifest 里的 `checkver` 自动发现 grclean / pulse 的新版本。
- **更新 manifest**：发布新版本后，修改 `bucket/<app>.json` 的 `version` 与 `hash`（setup.exe 的 sha256，可在 Release 资产页或 `releases/expanded_assets/vX.Y.Z` 页面找到），提交即可。`autoupdate` 会自动拼接下载 URL 并提取哈希。
- **新增软件**：在 `bucket/` 目录下新建 `<app-name>.json`（参考官方 [BucketTemplate](https://github.com/ScoopInstaller/BucketTemplate)）。
