# bbchannel·witch 发布包

这个仓库只放打包好的程序（zip）和更新日志，**源码不在这里**。

## 下载

打开 [Releases](../../releases)，选最新版本，下载 `BBchannelWitch-<版本>-win64.zip`（约 1.3 GB）。
不想看到候选版就把 `Pre-release` 的跳过，正式版会标 `Latest`。

## 运行

1. 解压到可写的位置，例如 `D:\BBchannelWitch`。不要放 `C:\Program Files`，程序会在自己的文件夹里保存设置和数据。
2. 双击 `BBchannelWitch\BBchannelWitch.exe`。
3. 程序没有数字签名，第一次运行 Windows 可能提示“Windows 已保护你的电脑”，点“更多信息 → 仍要运行”即可。

## 校验

每个 zip 旁边有 `.sha256` 文件，可以自己核对：

```
certutil -hashfile BBchannelWitch-<版本>-win64.zip SHA256
```

## 升级

把新版本解压到新文件夹，然后把旧文件夹里的 `config`、`settings`、`strategy`、`wave`、`assets\assist`、`assets\equipmaker` 复制过去。0.1.2 之前的版本目录叫 `BBchannel`、程序叫 `BBchannel.exe`，目录内容一样。