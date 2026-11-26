# Claude 安全助手 Windows x64 安装与使用指南

这款一键搭建 Claude 安全环境的小工具，经过了两个群里 300 多位群友的测试。感谢大家把安装、配置和使用中遇到的问题反馈给我们，我们根据这些反馈做了一次全面优化和升级。

之前每出一个新版本，群友都得重新下载，再走一遍安装流程。对不太懂技术的朋友来说，每更新一次就要再折腾一遍。这次我们把更新直接做进了小工具里。

之前装过小工具的朋友，可以先退出并删除旧版，再按下面的步骤安装新版「Claude 安全助手」。以后有新版本，在助手里点击「检查更新」，按提示完成更新即可。手动下载、部署和安装，这次走一遍就够了。

## 1. 下载小工具，安装 Docker Desktop

1. 在 Windows「设置」里找到「系统信息」，确认「系统类型」显示 **x64 处理器**。下载安装包 `ClaudeSafeClient-0.5.3-x64.msi`。[下载 Windows x64 v0.5.3](https://github.com/markjizhi/claude-safe-client/releases/download/v0.5.3/ClaudeSafeClient-0.5.3-x64.msi)
2. 下载安装 **Docker Desktop for Windows - x86_64**。按 Docker 官方说明检查这台电脑是否满足系统要求。采用默认的 WSL 2 后端时，如果安装程序提示需要启用或更新 WSL，按官网对应步骤完成，再打开 Docker Desktop 等它启动。已经装好的朋友可以直接打开 Docker Desktop。[Docker 官方安装说明](https://docs.docker.com/desktop/setup/install/windows-install/)
3. 确认 Docker Desktop 使用 **Linux 容器**。可以在 PowerShell 里用下面的命令检查。第一条输出 `linux`，第二条显示 Compose 版本，就可以继续。

   ```powershell
   docker info --format '{{.OSType}}'
   docker compose version
   ```

## 2. 安装并打开助手

双击下载的 `.msi` 文件，跟着 Windows 安装向导完成安装。安装完成后，从「开始」菜单找到 Claude 安全助手并打开。如果安装时弹出 Windows 安全或管理员提示，先核对安装包来自上面的 GitHub 发布页，再由你本人确认提示。

## 3. 完成授权

打开助手后，按授权页面提示填入自己的姓名、手机号和授权码，提交校验。野路子 AI 内部群的群友可以私信我领一个授权码，激活后绑定一台电脑。

## 4. 查看网络检测

授权通过后，看客户端显示的网络状态。**本机代理**是这台 Windows 电脑当前使用的代理。状态未连通时，先检查你平时用的代理软件和系统代理是否已开启。**静态代理**用的是你买到的静态 IP 所对应的 SOCKS5 代理，按下一步配置。

## 5. 用 Codex 提交静态代理

在安装了助手的这台 Windows 电脑上打开 Codex，保持助手运行。

**第一条，安装 Skill。** 新建一个 Codex 聊天，复制下面两行发送。

```text
$skill-installer 请帮我安装这个 Codex Skill：
https://github.com/woshishuiwozaina/configure-claude-static-proxy/tree/main/configure-claude-static-proxy
```

**第二条，发代理信息。** 安装完成后，在同一个聊天里输入 `/skills`，选择「配置 Claude 静态代理」。也可以用 `$` 搜索 `configure-claude-static-proxy`。准备好自己的 SOCKS5 代理，任选下面一种方式发送。

- **发截图**。在服务商页面截同一条代理记录，确认能看到代理主机、端口号、账号和密码。把截图附到自己的 Codex 聊天，再发送下面这句话。

  ```text
  请用这张截图里的代理主机、端口号、账号和密码，帮我配置到这台 Windows 电脑上的 Claude 安全助手。提交后告诉我结果。
  ```

- **发文字**。把四项信息填好，发到自己的 Codex 聊天。

  ```text
  请把下面这条静态 SOCKS5 代理配置到这台 Windows 电脑上的 Claude 安全助手。
  代理主机  【填写】
  端口号    【填写】
  账号      【填写】
  密码      【填写】
  ```

## 6. 确认连通，从助手打开 Claude

Codex 提交配置后，回到助手查看检测。看到 SOCKS5 代理已连接、运行环境已就绪后，再从助手里打开 Claude。某项仍显示红色时，可以把脱敏后的报错截图发给 Codex，说明卡在哪一步。

## 已经装过 Windows 版的朋友

先记下当前版本。v0.5.2 的发布说明写明，当时的 **Windows v0.5.1 用户需手动安装一次 v0.5.2**，该版变更了更新检测地址和签名密钥。[v0.5.2 迁移说明](https://github.com/markjizhi/claude-safe-client/releases/tag/v0.5.2)
