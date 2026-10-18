# bbchannel·witch 发布包

这个仓库只放打包好的程序（zip）和更新日志，**源码不在这里**。

## 下载

打开发布页，选标着 `Latest` 的那一版：

- `BBchannelWitch-<版本>-win64.zip`（约 1.3 GB）：完整包，**第一次安装用这个**。
- `BBchannelWitch-<版本>-update-win64.zip`（约 148 MB）：增量包，只含程序本体，给已经装好的版本升级用。
- 同名的 `.sha256` 是校验文件。

候选版（Pre-release）不会出现在程序的更新提示里，用正式版就行。

## 运行

1. 解压到可写的位置，例如 `D:\BBchannelWitch`。不要放在 `C:\Program Files` 下：程序会在自己的文件夹里保存设置和数据。
2. 双击 `BBchannelWitch\BBchannelWitch.exe`。
3. 程序没有数字签名，第一次运行 Windows 可能提示“Windows 已保护你的电脑”，点“更多信息 → 仍要运行”即可。
4. 需要 Windows 10 / 11（64 位）和一个安卓模拟器（MuMu、雷电等）。界面使用系统自带的 WebView2；没有它时会在默认浏览器里打开，功能不变。

## 校验

每个 zip 旁边都有 `.sha256` 文件，可以自己核对：

```
certutil -hashfile BBchannelWitch-<版本>-win64.zip SHA256
```

## 升级

**自动更新（0.1.4 起）**

打开程序左侧的“版本更新”，有新版本时点“下载并更新”：

1. 只下载增量包（约 148 MB，程序本体），页面上显示进度；
2. 下载完自动核对 SHA-256；
3. 点“重启并更新”，程序关闭、替换 `BBchannelWitch.exe` 和 `_internal\`，然后自动重新打开。

`config`、`settings`、`strategy`、`wave`、`assets`、`data` 全程不动，设置、编队、自定义提示音、下载过的立绘都保留。
新版本如果启动失败，会自动回滚到旧版本，过程写在 `config\update\apply.log`。

## 手动升级

自动更新失败（网络、杀毒软件拦截、程序里没有更新提示等）时，两种包都可以手动用。

**用增量包**（`BBchannelWitch-<版本>-update-win64.zip`，约 148 MB）：推荐，和程序自己做的更新是同一件事。

1. 退出程序（右键任务栏图标退出，确认任务管理器里没有 `BBchannelWitch.exe`）；
2. 把这个 zip 解压到**现有的** `BBchannelWitch` 文件夹里——就是有 `BBchannelWitch.exe` 的那一层；
3. 提示同名文件时选“覆盖”；
4. 重新打开 `BBchannelWitch.exe`。

它只会替换 `BBchannelWitch.exe`、`BBchannelWitch.exe.config`、`README.txt` 和整个 `_internal\`，
`config`、`settings`、`strategy`、`wave`、`assets`、`data` 都不会被动到。

**用完整包**（约 1.3 GB）：换一个干净的安装，或者增量包用不了时用。

1. 解压到一个新文件夹；
2. 把旧文件夹里的 `config`、`settings`、`strategy`、`wave`、`assets\assist`、`assets\equipmaker` 复制过去；
3. 打开新文件夹里的 `BBchannelWitch.exe`，确认没问题后再删掉旧文件夹。

`0.1.3` 是第一个公开发布的版本，它本身没有增量包可下，只能用手动方式（完整包或以后版本的增量包）升级。

## 数据在哪里

设置、编队、日志和下载的数据都保存在程序自己的文件夹里（`config`、`settings`、`data`、`assets`），
换文件夹或重装时记得一起带走。
