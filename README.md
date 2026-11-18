# xxp-scoop-bucket

个人维护的 Scoop 软件桶（bucket）。

## 安装

```powershell
scoop bucket add xxp-scoop-bucket https://github.com/by520free/xxp-scoop-bucket
scoop install xxp-scoop-bucket/grclean
scoop install xxp-scoop-bucket/pulse
scoop install xxp-scoop-bucket/kiri
scoop install xxp-scoop-bucket/arke
```

## 包含的软件

| 名称 | 说明 | 主页 | 授权 |
| --- | --- | --- | --- |
| `grclean` | 轻量、安全、无广告的 Windows 清理与优化工具（仅 Windows x64） | https://github.com/graent/grclean | 自定义（禁止再分发） |
| `pulse` | 为 Windows 打造的现代文件管理器：多标签/多窗格、全盘索引与拼音搜索、空格快速预览（仅 Windows x64） | https://github.com/jimmgreen/pulse | Apache-2.0 |
| `kiri` | 轻量快速的容器运行时（Rust，兼容 Docker CLI/Compose，Windows 走 WSL2），Docker Desktop 替代品 | https://github.com/libracoder/kiri | Apache-2.0 |
| `arke` | 不卡顿的 Windows 文件管理器：Rust + GPUI、GPU 渲染、单文件便携版，带预览与搜索（支持 x64 / ARM64） | https://github.com/Koimsurai/Arke | AGPL-3.0-only |

> 注意：grclean 的授权禁止再分发，本 bucket 的 manifest 仅**指向官方 GitHub Releases 链接**，不托管任何二进制文件。建议仅自用或先取得作者许可。pulse、kiri 为 Apache-2.0，arke 为 AGPL-3.0，可自由再分发。

> 关于 pulse 的 PulseIndex 服务：Scoop 包以用户级方式静默安装，默认**不注册** PulseIndex 服务（注册 Windows 服务需管理员权限，会在静默安装时失败）。如需全盘索引搜索，可在 Pulse 设置中手动开启，届时按提示提权即可。

> 关于 kiri：需要 WSL2。Scoop 解包 MSI 后，`kiri` 命令和开始菜单快捷方式可用；但 kiri 首次运行会自行安装 WSL2 引擎、创建 `kiri` docker context、把 CLI 加入用户 PATH，并自带更新器。建议在 kiri 设置里关闭自动更新、改用 `scoop update kiri`；彻底卸载时先用 kiri 自带的 `kiri.ps1 -Uninstall -IfSetUp` 清理 WSL/注册表残留，再 `scoop uninstall kiri`。

## 维护说明

- **新版本检测**：`scoop update` 会通过各 manifest 里的 `checkver` 自动发现 grclean / pulse / kiri / arke 的新版本。
- **更新 manifest**：发布新版本后，修改 `bucket/<app>.json` 的 `version` 与 `hash`（setup.exe 的 sha256，可在 Release 资产页或 `releases/expanded_assets/vX.Y.Z` 页面找到），提交即可。`autoupdate` 会自动拼接下载 URL 并提取哈希。
- **新增软件**：在 `bucket/` 目录下新建 `<app-name>.json`（参考官方 [BucketTemplate](https://github.com/ScoopInstaller/BucketTemplate)）。
