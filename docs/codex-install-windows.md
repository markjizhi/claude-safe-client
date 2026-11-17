# 给 Codex 的 Claude 安全客户端安装说明（Windows x64）

用户提出安装请求并提供本文链接时，请在用户正在操作的 Windows 电脑上完成安装和配置。开始前，确认能操作本机，并核对 Windows 版本与系统架构。

## 1. 检查 Docker

- 用 PowerShell 运行 `docker info` 和 `docker compose version`。确认本机 Docker 引擎可用且运行的是 Linux 容器。已有环境可用就直接使用。
- Docker Desktop 已安装但还未运行时，先启动它，等容器引擎就绪后再检查。需要安装时，从 Docker 官网下载 Windows x86_64 版，按官网步骤安装。采用默认的 WSL 2 后端时，按官方说明核对本机的 WSL 和系统要求。[Docker Desktop 的 Windows 安装说明](https://docs.docker.com/desktop/setup/install/windows-install/)
- 遇到首次使用协议、管理员确认或需要重启的提示，告诉用户接下来要确认什么。用户完成后再继续检查 Docker。

## 2. 安装并打开客户端

- 已经安装客户端时，先检查现有版本并打开，保留已有配置。需要覆盖安装时，先确认用户是否要升级。
- 初次安装请下载 GitHub 发布页的 Windows x64 EXE。下载后可用 PowerShell 的 `Get-FileHash -Algorithm SHA256` 核对文件，当前发布包的 SHA-256 为 `a70f8a42551f4c65c691545d9bf8c6d368a1d43a3f48a74c0ad02d6d61dd2676`。[下载 Windows x64 安装包](https://github.com/markjizhi/claude-safe-client/releases/download/v0.3.0/Claude-Safe-Client-Windows-x64.exe)
- 打开 EXE，按安装程序界面完成安装。遇到 SmartScreen 或 UAC 提示时，请用户在本机查看并确认。安装完成后，从开始菜单打开「Claude安全客户端」。

## 3. 配置静态 IP 并验证

- 打开客户端的激活或代理配置界面。使用用户已准备好的 SOCKS5 静态 IP，按界面提供的方式填写代理信息。请用户在客户端里输入激活码和代理密码，或粘贴带凭据的 SOCKS5 链接。
- 配置完成后启动运行环境，以客户端实际显示的运行和连接状态为准。用户已有预期出口时，在本机核对。最后告诉用户 Docker、客户端、代理和运行环境分别是否通过检查。需要用户操作时，指出具体窗口和下一步。
