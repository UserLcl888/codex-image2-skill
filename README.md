# codex-image2

## 功能

- 使用 OpenAI 兼容的图片接口调用 `gpt-image-2`。
- 支持文生图和图片编辑。
- 支持单图、多图以及 PNG Mask 局部编辑。
- 支持 JSONL 批量任务和并发处理。
- 支持 Base64 与 URL 两种图片响应格式。
- 自动重试网络超时、429、5xx 和 524 错误。
- 提供 Windows x64、Windows ARM64、macOS Intel 和 macOS Apple Silicon 可执行文件。
- 支持输出文件覆盖保护，API Key 不写入技能文件或日志。

## 安装

### 通过 Codex 安装

将本仓库地址提供给 Codex，请求安装此技能：

```text
请安装这个 Skill：
https://github.com/UserLcl888/codex-image2-skill
```

### 手动安装

Windows PowerShell：

```powershell
git clone https://github.com/UserLcl888/codex-image2-skill.git
Copy-Item codex-image2-skill\codex-image2 "$HOME\.codex\skills\codex-image2" -Recurse
```

macOS / Linux：

```bash
git clone https://github.com/UserLcl888/codex-image2-skill.git
cp -R codex-image2-skill/codex-image2 ~/.codex/skills/codex-image2
```

### 配置环境变量

PowerShell：

```powershell
[Environment]::SetEnvironmentVariable("CODEX_API_URL", "你的API地址", "User")
[Environment]::SetEnvironmentVariable("CODEX_API_KEY", "你的API密钥", "User")
```

macOS / Linux：

```bash
export CODEX_API_URL="你的API地址"
export CODEX_API_KEY="你的API密钥"
```

配置后完全退出并重新启动 Codex。

## 基本使用

在 Codex 请求中指定 `$codex-image2`：

```text
使用 $codex-image2 生成一张图片：
一只戴着宇航员头盔的橘猫站在月球表面。
```

编辑图片：

```text
使用 $codex-image2 修改这张图片：
只替换背景，保留主体、姿势和构图。
```

命令行也可以直接调用对应平台的可执行文件：

```powershell
& "codex-image2/bin/codex-image2-windows-amd64.exe" generate `
  --prompt "A blue nebula inside a glass bottle" `
  --quality auto `
  --out "output/imagegen/nebula.png"
```

详细参数和批量任务格式请参阅 [`codex-image2/SKILL.md`](codex-image2/SKILL.md) 与 [`codex-image2/references/batch-format.md`](codex-image2/references/batch-format.md)。
