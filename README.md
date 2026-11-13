# FGO抓包助手 v2.2.1

Windows 单文件程序，可在 MuMu 安卓 15 ROOT 实例上为国服、日服生成游戏数据快照，查看抽卡统计和迦勒底报告，也支持打开已有的本地数据文件。

[下载 Windows 程序](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.1/FGO-v2.2.1.exe) · [使用说明](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.1/instructions.txt) · [文件校验](https://github.com/L-Molish/FGO-Capture-Assistant/releases/download/v2.2.1/SHA256SUMS.txt)

## 这个版本保存什么

- 新快照只保留生成统计和报告所需的游戏数据，包括卡池抽数、从者图鉴、技能、羁绊、关卡和资源。快照中的从者实例编号只用于关联本文件内的记录。
- 程序在内存中筛选数据。磁盘文件和剪贴板得到相同的统计快照；失败时只显示错误类别。新版不生成完整登录响应、解码副本或失败响应转储。
- 快照不包含账号 ID、好友码、御主名或签名。导入旧文件时，这些字段的显示取决于旧文件自身。

## 开始使用

1. 将 EXE 放在可写文件夹，无需安装 Python。升级时可放回原程序目录，沿用已有设置、公开统计资料和本机证书。
2. 选择区服和 MuMu 实例，点击“初始化环境”，再点“检查环境”。公开版使用内置 mitmproxy，无需下载 Reqable。初始化会自动检查并开启所选实例的 ROOT，必要时自动重启并等待就绪。首次初始化会自动把本机公开 CA 安装到设备的系统与 Conscrypt 证书库并立即核验，无需手动导入证书或操作 KernelSU；ROOT 已可用且证书已匹配时不会重复安装或重启。证书使用运行时挂载，模拟器重启后需再次初始化。
3. 点击“开始抓包”，按游戏提示正常登录。使用模拟器内加速器时，先让游戏进入标题画面。抓取成功后，国服快照保存在 `results/`，日服保存在 `results/JP/`。
4. 在“统计”页读取最新文件，或选择已有的本地文件。可查看抽数、五星数、UP 出货率和报告，并导出 PNG 长图。移动带有 `.origin` 的文件时请一起移动区服标记。

## 文件兼容性

新版快照用于本助手。Chaldea 的“HTTPS 抓包导入”要求完整数据中含有成功登录记录；新版文件省略了该记录，不能直接用于这个入口。过去保留的原始文件仍可按旧方式使用。[Chaldea 导入器源码](https://github.com/chaldea-center/chaldea/blob/ba81b31307ad48f531d09828916abc15ea13815c/lib/app/modules/import_data/import_https_page.dart#L1004)

旧版程序和说明仍在各自的发布页。[v2.1.1 发布记录](https://github.com/L-Molish/FGO-Capture-Assistant/releases/tag/v2.1.1)
