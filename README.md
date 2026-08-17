# Dororo 发布包

Dororo 桌宠的下载与版本信息。**本仓库不含源码。**

## 下载

到 [Releases](https://github.com/ckzzzgo/dororo-release/releases/latest) 下载最新的
`Dororo_v<版本>_win.zip`，解压后运行 `dororo.exe` 即可。

无需安装 .NET 或 VC++ 运行库，运行库已内置在包里。仅支持 Windows 64 位。

聊天功能需要自己填写 API Key（设置 → 聊天）。接口地址、模型名与人设都已内置。

## version.json

`version.json` 供桌宠内的「检查更新」读取，固定地址：

```
https://raw.githubusercontent.com/ckzzzgo/dororo-release/main/version.json
```

字段说明：

| 字段 | 用途 |
| --- | --- |
| `version` | 最新版本号，与源码里 `project.godot` 的 `config/version` 一致 |
| `released` | 发布日期 |
| `notes_url` | 该版本的更新说明页 |
| `package.name` | 安装包文件名 |
| `package.url` | 安装包直链，供自动更新下载 |
| `package.size` | 字节数，用于显示下载进度 |
| `package.sha256` | 校验值，下载后必须比对，避免用到损坏或被篡改的包 |

之所以用 raw 地址而不是 GitHub API：raw 没有 API 那样的每小时 60 次匿名限流，
对「每天检查一次」这种用法更稳，也不需要任何凭据。

发版时由源码仓库的 `tools/build_release.ps1` 生成新的 `version.json`，
连同安装包一起发布到这里。
