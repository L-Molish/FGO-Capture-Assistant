# FGO抓包助手 v2.2.2

Windows 单文件程序，支持 MuMu 安卓 12 / 15 ROOT 实例，可生成游戏数据快照、查看抽卡统计和迦勒底报告，也支持打开已有的本地数据文件。两个安卓版本共用同一程序与操作流程，选择实例后自动识别，无需手动切换安卓版本。

[下载 Windows 程序](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.2/FGO-v2.2.2.exe) · [使用说明](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.2/instructions.txt) · [文件校验](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.2/SHA256SUMS.txt)

## 支持范围

| MuMu 实例 | 国服 | 日服 |
| --- | --- | --- |
| 安卓 12 ROOT | 已实测：普通网络、FlClash VPN 开启时抓包 | 尚未实机验证 |
| 安卓 15 ROOT | 保持原有支持 | 保持原有支持 |

助手会按实例和实际证书库自动处理差异：安卓 12 不再因为缺少 Conscrypt APEX 证书库而初始化失败；安卓 15 继续核验系统与 Conscrypt 两处证书库。普通网络检查不要求安装 KernelSU。

## 这个版本保存什么

- 新快照只保留生成统计和报告所需的游戏数据，包括卡池抽数、从者图鉴、技能、羁绊、关卡和资源。快照中的从者实例编号只用于关联本文件内的记录。
- 程序在内存中筛选数据。磁盘文件和剪贴板得到相同的统计快照；失败时只显示错误类别。新版不生成完整登录响应、解码副本或失败响应转储。
- 快照不包含账号 ID、好友码、御主名或签名。导入旧文件时，这些字段的显示取决于旧文件自身。

## 开始使用

1. 将 EXE 放在可写文件夹，无需安装 Python。升级时可放回原程序目录，沿用已有设置、公开统计资料和本机证书。
2. 选择区服和 MuMu 安卓 12 或 15 实例，点击“初始化环境”，再点“检查环境”。公开版使用内置 mitmproxy，无需下载 Reqable。初始化会先检查 MuMu 设置中的 ROOT 开关；未开启时自动打开、核验设置已保存，并自动重启运行中的所选实例，再等待安卓和 ADB ROOT 就绪。首次初始化会把本机公开 CA 安装到该安卓版本实际使用的证书库并立即核验，无需手动导入证书或操作 KernelSU；ROOT 已开启且证书已匹配时不会重复安装或重启。证书使用运行时挂载，模拟器重启后需再次初始化。
3. 先让游戏进入标题画面，再点击“开始抓包”并正常登录。若已进入游戏主页面，先返回标题；“请点击游戏界面”的加载完成提示和标题的“点击屏幕”都需要继续点击。抓取成功后，国服快照保存在 `results/`，日服保存在 `results/JP/`。
4. 在“统计”页读取最新文件，或选择已有的本地文件。可查看抽数、五星数、UP 出货率和报告，并导出 PNG 长图。移动带有 `.origin` 的文件时请一起移动区服标记。

安卓 12 上的 FlClash 本次验证使用 0.9.1 x86_64 包；ARM64 包在本机启动退出。国服自动抓包在 FlClash VPN 开启时已通过验证，但仍使用电脑出口；经 FlClash 本地 HTTP 代理出站的链路已单独实测通过，当前国服界面不会自动切换到这条链路。

## 文件兼容性

新版快照用于本助手。Chaldea 的“HTTPS 抓包导入”要求完整数据中含有成功登录记录；新版文件省略了该记录，不能直接用于这个入口。过去保留的原始文件仍可按旧方式使用。[Chaldea 导入器源码](https://github.com/chaldea-center/chaldea/blob/ba81b31307ad48f531d09828916abc15ea13815c/lib/app/modules/import_data/import_https_page.dart#L1004)

旧版程序和说明仍在各自的发布页。[v2.1.1 发布记录](https://github.com/L-Molish/FGO-Capture-Assistant/releases/tag/v2.1.1)
