# Tavern Backup Assistant (酒馆备份助手)

**Author:** SenriYuki  
**Version:** 2.2

A simple, "idiot-proof" backup and restore tool designed for SillyTavern.  
专为 SillyTavern 设计的傻瓜式一键备份与还原工具。

> **🛑 CRITICAL INSTALLATION WARNING / 重要安装警告**
>
> **This is a BACKEND plugin.**
> **DO NOT** install this via the SillyTavern interface (Extensions -> Install from URL). **IT WILL NOT WORK.**
> Since this plugin requires system-level permissions (file zip/unzip), you **MUST** install it via the terminal/command line.
>
> **这是一个【后端插件】。**
> **严禁**直接在酒馆网页界面使用“扩展” -> “从 URL 安装”功能，**这会导致插件无法运行！**
> 因为本插件需要系统级权限（读写硬盘、解压文件），您**必须**使用下方的命令行方式进行安装。

---

## ✨ Features (功能特色)

* **一键全备份**：核心数据（角色/对话）、插件、主题美化、配置、密钥。
* **一键还原**：拖拽 ZIP 包即可还原，自动清理临时文件。
* **安全防呆**：实时进度条 + 还原前二次确认。
* **手机/PC 通用**：完美支持 Termux 端酒馆，针对移动端优化的操作流程。

---

## ⚠️ Security & Pre-requisites (安全说明与前置要求)

To make this plugin work (reading/writing backup files), you **MUST** modify `config.yaml`. Please read the risks below.  
为了让插件能够正常读写备份文件，你**必须**修改 `config.yaml` 配置文件。请务必阅读以下风险提示：

> **🔴 Risk Disclosure (风险告知):**
> 1.  **Enable Server Plugins (开启后端插件)**: Gives plugins permission to manage files on your device. **Only install plugins from trusted authors.**
>    (允许插件管理你设备上的文件。请只安装值得信任的作者开发的插件。)
> 2.  **Disable CSRF Protection (关闭 CSRF 保护)**: Necessary for file uploads to work smoothly. **Do not expose your SillyTavern to the public internet without a password.**
>    (为了确保备份文件能顺利上传，需要关闭此项。请勿在无密码的情况下将酒馆暴露到公网，平时使用无需担心。)

---

## ⚙️ Configuration Guide (配置指南)

You must enable specific settings in `config.yaml` for the plugin to function.  
你必须在 `config.yaml` 中开启特定设置，否则插件将无法启动。

### 📱 Android (Termux Users) - 手机端保姆级教程

**Automated Setup (Recommended)**: No need to edit files manually! Just copy and paste the code block below.  
**自动配置（强烈推荐）**：不需要手动编辑文件！直接复制下方代码块并在 Termux 中运行即可。它会自动修改设置，防止手滑出错。

1.  **Stop SillyTavern** (停止酒馆运行):
    Press `Ctrl + C` in Termux to stop the server. (在 Termux 中按 `Ctrl + C` 停止酒馆)

2.  **Run Configuration Command** (运行配置指令):
    **Copy the following lines and paste them into Termux (Long press -> Paste):**
    **复制下面这几行代码，在 Termux 中长按粘贴并回车：**

    ```bash
    cd ~/SillyTavern
    sed -i 's/enableServerPlugins:.*/enableServerPlugins: true/' config.yaml
    sed -i 's/disableCsrfProtection:.*/disableCsrfProtection: true/' config.yaml
    echo "Config Updated! (配置已自动修改完成！)"
    ```

3.  **Restart SillyTavern** (重启酒馆):
    Run `./start.sh` to apply changes. (输入 `./start.sh` 重启)

---

### 💻 PC (Windows/Linux/Mac) - 电脑端教程

1.  Go to your SillyTavern folder. (打开你的酒馆文件夹)
2.  Find `config.yaml` and open it with **Notepad** or any text editor. (找到 `config.yaml` 并用记事本打开)
3.  Find and modify the following two lines (change them to `true`):
    (搜索并修改以下两行，将值改为 `true`)：

    ```yaml
    enableServerPlugins: true      # Allows the plugin to write backup files (允许插件写入文件)
    disableCsrfProtection: true    # Prevents upload errors (防止上传报错)
    ```
4.  Save the file and restart SillyTavern. (保存文件并重启酒馆)

---

## 📦 Installation (安装方法)

**REMINDER: Use the command line below. Do not use the Web UI.** **再次提醒：请使用下方的命令行安装，不要用网页界面安装。**

### 📱 Android (Termux) One-Command Install [推荐]
**只需一步！复制下面的整段指令，在 Termux 中长按粘贴并回车：**

```bash
cd ~/SillyTavern/plugins && git clone https://github.com/JY-s17/TavernBackupAssistant.git && cd TavernBackupAssistant && npm install && echo "Plugin Installed! Please Restart ST. (安装完成，请重启酒馆)"
```

### 💻 PC (Windows/Linux)
**在酒馆目录下打开终端或 CMD：**

```bash
cd plugins
https://github.com/JY-s17/TavernBackupAssistant.git
cd TavernBackupAssistant
npm install
```

> **Note regarding ZIP download (关于手动下载压缩包的说明) **: If you download the source code as a ZIP file manually, you MUST still open a terminal in the plugin folder and run npm install. Otherwise, the plugin will lack dependencies and fail to load. 如果你选择手动下载 ZIP 包解压，解压后必须在插件文件夹内打开终端运行 npm install。否则插件会因为缺少依赖组件而无法运行。

---

## ❓ FAQ (常见问题)
### Q: I installed it but don't see the plugin? (安装了但看不到插件？)
  A: Did you restart SillyTavern? Did you set enableServerPlugins: true in config.yaml?
  (你重启酒馆了吗？你在 config.yaml 里开启服务端插件权限了吗？)
### Q: Upload failed / Network Error? (上传失败/网络错误？)
  A: You likely forgot to set disableCsrfProtection: true.
  (你大概率忘记将 disableCsrfProtection 设为 true 了。)










