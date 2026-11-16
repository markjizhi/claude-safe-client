# 给 Codex 的 Claude 安全客户端安装说明

这份说明适用于用户正在操作的 Mac。用户提出安装请求，并随请求提供了本文档的附件或链接时，请接手安装，在本机完成能操作的步骤。做到客户端打开、静态 IP 配置校验通过、运行环境显示已启动。

## 1. 检查并准备 Docker

- 确认你能操作用户这台 Mac，识别它的芯片和 macOS 版本。
- 先检查本机 Docker。用 `docker info` 确认本地 Docker 引擎可用，用 `docker compose version` 确认 Compose 可用。两项都通过就复用已有安装。当前 Docker 上下文如果指向远程主机，先确认客户端可以使用本机引擎，再启动运行环境。
- 已安装 Docker Desktop 但还没运行时，先启动它，等引擎就绪后再检查。需要全新安装时，从 Docker 官方页面选择与芯片匹配、支持这台 Mac 的 Docker Desktop，按官方步骤安装并启动。[Docker Desktop 的 Mac 安装说明](https://docs.docker.com/desktop/setup/install/mac-install/)
- Docker Desktop 已运行但终端找不到 `docker` 时，先检查 Docker Desktop 的 CLI 工具设置和命令路径。
- 遇到 Docker 首次使用协议或系统权限确认，把对应窗口留给用户操作。用户完成后接着检查引擎和 Compose。

## 2. 下载并打开客户端

- 本机已经装有客户端时，先检查版本和状态。已有版本可以使用就直接打开，保留原有配置。发现需要替换现有版本时，先确认用户是否希望升级。
- 从项目的 GitHub 发布页下载最新版 Mac ZIP。用 `unzip -t` 检查 ZIP，解压到临时目录，确认应用名称为「Claude安全客户端.app」，用 `codesign --verify --deep --strict` 检查签名完整性，再安装到「应用程序」并打开。[下载最新版 Mac 客户端](https://github.com/markjizhi/claude-safe-client/releases/latest/download/Claude-Safe-Client-macOS.zip)
- 如果 macOS 弹出首次打开的安全提示，告诉用户现在卡在哪个窗口，请用户在本机确认后继续操作。手动打开的步骤见[手动安装教程](https://github.com/markjizhi/claude-safe-client/blob/main/docs/install-manual.md#1-首次打开工具)。

## 3. 帮用户配置已有的静态 IP

- 打开客户端的授权或代理配置界面。如果能操作桌面，直接带用户到相应字段。只有终端可用时，先启动应用，再告诉用户接下来需要在界面上完成哪一步。
- 姓名栏可填写内部群昵称。手机号、工具验证码和代理密码等信息请用户在客户端界面填写。内部群友还没拿到工具验证码时，可以私信极致先生领取。
- 使用用户已准备好的 SOCKS5 静态 IP。拿到完整 SOCKS5 链接，可以在「快速填写完整 SOCKS5 链接」中粘贴。也可以分别填写代理主机、端口、用户名和密码。已有配置可用时，检查并复用它。请用户本人在客户端粘贴带凭据的链接，避免把密码、验证码或完整代理链接写入聊天和日志。
- 填好后点击「校验并进入客户端」。遇到配置错误，先看客户端的实际提示，再说明需要核对哪一项。

## 4. 启动运行环境并回报结果

- 点击「启动运行环境」，等待初始化和首次镜像下载完成。以客户端显示的「运行环境已启动」和「SOCKS5 已连接」为准。如果用户知道预期的出口，可在本机对照确认。首次登录 Claude 时，由用户在 Claude 窗口里完成。
- 最后告诉用户安装了哪个版本、Docker 是否可用、客户端是否已打开，以及静态 IP 和运行环境是否验证通过。仍需用户操作时，只说明下一步做什么，完成后接着处理。
