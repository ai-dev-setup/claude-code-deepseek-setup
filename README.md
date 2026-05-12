# Claude Code + DeepSeek 配置指南

在你的电脑上安装 Claude Code 并接入 DeepSeek API。

> ⚠️ **网络要求：** Claude Code 启动时需要连接 Anthropic 服务器进行认证，在中国大陆网络环境下需要能够访问外网才能正常使用。请确保你的网络环境可以访问 `api.anthropic.com`。

点击展开你的操作系统对应的指南：

---

<details>
<summary><b>🍎 macOS 用户点这里</b></summary>

<br>

**Terminal（终端）是什么？**
Terminal 是 Mac 自带的命令行工具，可以通过输入文字命令来操作电脑。打开方式：按 `Command + 空格`，输入 `Terminal`，回车即可打开。

---

### 第一步：安装 Node.js

> 如果你之前装过 Node.js，可以跳过这一步。

打开 Terminal，把下面的命令**逐行**复制粘贴进去，每行粘贴后按回车执行，等上一行执行完再粘贴下一行：

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

```bash
. "$HOME/.nvm/nvm.sh"
```

```bash
nvm install 24
```

安装完成后，验证是否成功（看到版本号说明成功）：

```bash
node -v
```

---

### 第二步：安装 Git

> 如果你之前装过 Git，可以跳过这一步。

访问官方安装指南按指引安装：https://git-scm.com/install/mac

---

### 第三步：安装 Claude Code

在 Terminal 中执行：

```bash
npm install -g @anthropic-ai/claude-code
```

---

### 第四步：注册 DeepSeek 并获取 API Key

1. 访问 [platform.deepseek.com](https://platform.deepseek.com)，注册账号并登录
2. 左侧导航栏点击 **API Keys**
3. 点击 **Create new API key**，给它起个名字（随意），点确认
4. 复制生成的 API Key（一串字母数字）— **注意：这个 Key 只会显示一次，请立即粘贴到记事本保存好**

---

### 第五步：配置环境变量

这一步是告诉 Claude Code 去用 DeepSeek 的模型而不是 Anthropic 的模型。

**先准备好替换好的内容：**

把下面这段文字复制到记事本，然后把 `<你的DeepSeek API key>` 替换成第四步保存的 API Key（直接替换整段文字，包括尖括号一起删掉）：

```
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=<你的DeepSeek API key>
export ANTHROPIC_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_OPUS_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_SONNET_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_HAIKU_MODEL=deepseek-v4-flash
export CLAUDE_CODE_SUBAGENT_MODEL=deepseek-v4-flash
export CLAUDE_CODE_EFFORT_LEVEL=max
```

**替换好之后，打开 Terminal，执行以下命令将内容写入配置文件：**

把下面这整段复制粘贴进 Terminal（注意先替换 API key），一次性回车执行：

```bash
cat >> ~/.zshrc << 'EOF'
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=<你的DeepSeek API key>
export ANTHROPIC_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_OPUS_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_SONNET_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_HAIKU_MODEL=deepseek-v4-flash
export CLAUDE_CODE_SUBAGENT_MODEL=deepseek-v4-flash
export CLAUDE_CODE_EFFORT_LEVEL=max
EOF
```

> ⚠️ 注意：执行前务必把 `<你的DeepSeek API key>` 替换为实际的 key，否则配置无效。

然后让配置生效：

```bash
source ~/.zshrc
```

---

### 第六步：启动 Claude Code

**重新打开一个 Terminal 窗口**（关掉旧的，重新打开），然后切换到你想要工作的文件夹路径。

例如切换到桌面：

```bash
cd ~/Desktop
```

然后执行：

```bash
claude
```

**首次启动会遇到两个提示：**

1. 出现 **Quick safety check** 时，输入 `1` 回车，选择 **Yes, I trust this folder**
2. Mac 可能弹出系统权限窗口提示 **"Terminal" would like to access files on a network volume**，点击 **Allow（允许）**

完成后即可进入 Claude Code 交互界面。

---

### 第七步：充值 DeepSeek 账号（开始实际使用前）

> DeepSeek 按使用量计费，费用较低，充值 10 元可以用很久。

1. 登录 [platform.deepseek.com](https://platform.deepseek.com)
2. 左侧导航栏点击 **Top Up（充值）**
3. 完成实名认证
4. 选择充值金额，完成支付

充值完成后即可正常使用 Claude Code。

</details>

---

<details>
<summary><b>🪟 Windows 用户点这里</b></summary>

<br>

**PowerShell 是什么？**
PowerShell 是 Windows 自带的命令行工具。打开方式：按 `Win + S`，输入 `PowerShell`，点击打开。

---

### 第一步：安装 Node.js

> 如果你之前装过 Node.js，可以跳过这一步。

1. 访问 [nodejs.org/zh-cn/download](https://nodejs.org/zh-cn/download)
2. 页面往下滑，找到并点击绿色的 **Windows 安装程序（.msi）** 按钮下载安装包
3. 双击下载好的 `.msi` 文件，一路点 **Next**，保持所有默认选项，完成安装
4. 安装完成后，打开 PowerShell，验证是否成功（看到版本号说明成功）：

```powershell
node -v
```

---

### 第二步：安装 Git

> 如果你之前装过 Git，可以跳过这一步。

1. 访问 [git-scm.com/download/win](https://git-scm.com/download/win)，下载安装包
2. 双击安装包，一路点 **Next** 完成安装（所有选项保持默认即可）

---

### 第三步：安装 Claude Code

打开 PowerShell，执行：

```powershell
npm install -g @anthropic-ai/claude-code
```

等待安装完成，看到命令行重新出现 `>` 符号说明安装成功。

---

### 第四步：注册 DeepSeek 并获取 API Key

1. 访问 [platform.deepseek.com](https://platform.deepseek.com)，注册账号并登录
2. 左侧导航栏点击 **API Keys**
3. 点击 **Create new API key**，给它起个名字（随意），点确认
4. 复制生成的 API Key（一串字母数字）— **注意：这个 Key 只会显示一次，请立即粘贴到记事本保存好**

---

### 第五步：配置环境变量

这一步是告诉 Claude Code 去用 DeepSeek 的模型而不是 Anthropic 的模型。

在 PowerShell 中逐行执行以下命令（把 `<你的DeepSeek API key>` 替换为第四步保存的 key，包括尖括号一起删掉）：

```powershell
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_BASE_URL", "https://api.deepseek.com/anthropic", "User")
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_AUTH_TOKEN", "<你的DeepSeek API key>", "User")
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_MODEL", "deepseek-v4-pro[1m]", "User")
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_DEFAULT_OPUS_MODEL", "deepseek-v4-pro[1m]", "User")
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_DEFAULT_SONNET_MODEL", "deepseek-v4-pro[1m]", "User")
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_DEFAULT_HAIKU_MODEL", "deepseek-v4-flash", "User")
[System.Environment]::SetEnvironmentVariable("CLAUDE_CODE_SUBAGENT_MODEL", "deepseek-v4-flash", "User")
[System.Environment]::SetEnvironmentVariable("CLAUDE_CODE_EFFORT_LEVEL", "max", "User")
```

> ⚠️ 注意：执行前务必把 `<你的DeepSeek API key>` 替换为实际的 key，否则配置无效。

---

### 第六步：启动 Claude Code

**重新打开一个 PowerShell 窗口**（关掉旧的，重新打开，这样环境变量才会生效），然后切换到你想要工作的文件夹路径。

例如切换到桌面：

```powershell
cd $HOME\Desktop
```

然后执行：

```powershell
claude
```

**首次启动会出现安全提示 Quick safety check**，输入 `1` 回车，选择 **Yes, I trust this folder**，即可进入 Claude Code 交互界面。

---

### 第七步：充值 DeepSeek 账号（开始实际使用前）

> DeepSeek 按使用量计费，费用较低，充值 10 元可以用很久。

1. 登录 [platform.deepseek.com](https://platform.deepseek.com)
2. 左侧导航栏点击 **Top Up（充值）**
3. 完成实名认证
4. 选择充值金额，完成支付

充值完成后即可正常使用 Claude Code。

</details>
