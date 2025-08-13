> [!NOTE]
> If you need English, please click [here](https://github.com/EverythingSuckz/TG-FileStreamBot)
> / 你想查看 英文 文档 或者原仓库？ 请[点我](https://github.com/EverythingSuckz/TG-FileStreamBot)

<h1 align="center">Telegram File Stream Bot Chinese / Telegram 文件直链机器人中文版</h1>
<p align="center">
  </a>
  <p align="center">
    <a herf="https://github.com/yanjie233/TG-FileStreamBot">
        <img src="https://telegra.ph/file/a8bb3f6b334ad1200ddb4.png" height="100" width="100" alt="File Stream Bot Logo">
    </a>
</p>
  <p align="center">
    一个Telegram机器人 <b>将文件转换为直链</b>
    <br />
  </p>
</p>

<hr>

> [!NOTE]
> 如果你感兴趣，可以查看原作者的[python 分支](https://github.com/EverythingSuckz/TG-FileStreamBot/tree/python)

> [!NOTE]
> 汉化仅限Go语言(Docker不算) 可在Releases获得二进制文件进行安装。

<hr>

<details open="open">
  <summary>目录</summary>
  <ol>
    <li>
      <a href="#how-to-make-your-own">如何自建</a>
      <ul>
        <li><a href="#deploy-to-koyeb">部署到 Koyeb</a></li>
        <li><a href="#deploy-to-heroku">部署到 Heroku</a></li>
      </ul>
      <ul>
        <li><a href="#download-from-releases">下载并运行</a></li>
        <li><a href="#run-using-docker-compose">Docker compose 运行</a></li>
        <li><a href="#run-using-docker">Docker 运行</a></li>
        <li><a href="#build-from-source">源码编译运行</a>
          <ul>
            <li><a href="#ubuntu">Ubuntu</a></li>
            <li><a href="#windows">Windows</a></li>
          </ul>
        </li>
      </ul>
    </li>
    <li>
      <a href="#setting-up-things">环境配置</a>
      <ul>
        <li><a href="#required-vars">必需环境变量</a></li>
        <li><a href="#optional-vars">可选环境变量</a></li>
        <li><a href="#use-multiple-bots-to-speed-up">多机器人加速</a></li>
        <li><a href="#use-multiple-bots-to-speed-up">使用用户会话自动添加机器人</a>
          <ul>
            <li><a href="#what-it-does">功能说明</a></li>
            <li><a href="#how-to-generate-a-session-string">如何生成会话字符串</a></li>
          </ul>
        </li>
      </ul>
    </li>
    <li><a href="#contributing">贡献</a></li>
    <li><a href="#contact-me">联系方式</a></li>
    <li><a href="#credits">致谢</a></li>
  </ol>
</details>



## How to make your own

### Deploy to Koyeb

> [!IMPORTANT]
> 部署前请展开“环境变量和文件”部分并填写相关变量。

> [!NOTE]
> 此方式部署的是最新 docker 发行版而非最新提交。使用预构建容器，部署速度更快。

[![一键部署到 Koyeb](https://www.koyeb.com/static/images/deploy/button.svg)](https://app.koyeb.com/deploy?type=docker&name=file-stream-bot&image=ghcr.io/everythingsuckz/fsb:latest&env%5BAPI_HASH%5D=&env%5BAPI_ID%5D=&env%5BAPI_HASH%5D=&env%5BAPI_ID%5D=&env%5BBOT_TOKEN%5D=&env%5BHOST%5D=https%3A%2F%2F%7B%7B+KOYEB_PUBLIC_DOMAIN+%7D%7D&env%5BLOG_CHANNEL%5D=&env%5BPORT%5D=8038&ports=8038%3Bhttp%3B%2F&hc_protocol%5B8038%5D=tcp&hc_grace_period%5B8038%5D=5&hc_interval%5B8038%5D=30&hc_restart_limit%5B8038%5D=3&hc_timeout%5B8038%5D=5&hc_path%5B8038%5D=%2F&hc_method%5B8038%5D=get)

### Deploy to Heroku

> [!NOTE]
> You'll have to [fork](https://github.com/EverythingSuckz/TG-FileStreamBot/fork) this repository to deploy to Heroku.

Press the below button to fast deploy to Heroku

[![Deploy To Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

[Click Here](https://devcenter.heroku.com/articles/config-vars#using-the-heroku-dashboard) to know how to add / edit [environment variables](#required-vars) in Heroku.

<hr>

### Download from releases

<hr>
### 部署到 Heroku

> [!NOTE]
> 部署前需先 fork 本仓库。

点击下方按钮一键部署到 Heroku

[![一键部署到 Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

[如何在 Heroku 添加/编辑环境变量](https://devcenter.heroku.com/articles/config-vars#using-the-heroku-dashboard)

<hr>

### 下载并运行
- 前往 [releases](https://github.com/EverythingSuckz/TG-FileStreamBot/releases) 下载适合你平台的预发布版本。
- 解压到文件夹。
- 新建 `fsb.env` 文件，添加所有变量（参考 `fsb.sample.env`）。
- 给可执行文件加权限（Windows 不需要）。
- 运行 `./fsb run`（Windows 用 `./fsb.exe run`）。

<hr>

### Docker compose 运行

- 克隆仓库
```sh
git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
```

- 新建 `fsb.env` 文件，添加所有变量（参考 `fsb.sample.env`）。
```sh
nano fsb.env
```

- 构建并运行 docker-compose：
```sh
docker-compose up -d
```
或
```sh
docker compose up -d
```

<hr>

### Docker 运行

```sh
docker run --env-file fsb.env ghcr.io/everythingsuckz/fsb:latest
```
`fsb.env` 为环境变量文件。

<hr>

### 源码编译运行

#### Ubuntu

> [!NOTE]
> 需安装 go 1.21 及以上版本。
> 参考 https://stackoverflow.com/a/17566846/15807350

```sh
git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
go build ./cmd/fsb/
chmod +x fsb
mv fsb.sample.env fsb.env
nano fsb.env
# 添加环境变量，详见下节
./fsb run
```

停止程序：按 <kbd>CTRL</kbd>+<kbd>C</kbd>

#### Windows

> [!NOTE]
> 需安装 go 1.21 及以上版本。

```powershell
git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
go build ./cmd/fsb/
Rename-Item -LiteralPath ".\fsb.sample.env" -NewName ".\fsb.env"
notepad fsb.env
# 添加环境变量，详见下节
.\fsb run
```

停止程序：按 <kbd>CTRL</kbd>+<kbd>C</kbd>

## 环境配置

本地部署时，在根目录新建 `fsb.env` 文件，添加所有变量。可参考 `fsb.sample.env`。

示例：

```sh
API_ID=你的API_ID
API_HASH=你的API_HASH
BOT_TOKEN=你的机器人Token
LOG_CHANNEL=你的频道ID
PORT=8080
HOST=http://你的服务器IP
# (如需设置多个机器人)
MULTI_TOKEN1=工作机器人Token1
MULTI_TOKEN2=工作机器人Token2
```

### 必需环境变量
在运行机器人前，你需要设置以下必填变量：

- `API_ID`：你的 Telegram 账号的 API ID，可在 my.telegram.org 获取。
- `API_HASH`：你的 Telegram 账号的 API Hash，同样在 my.telegram.org 获取。
- `BOT_TOKEN`：Telegram 直链机器人 Token，可在 [@BotFather](https://telegram.dog/BotFather) 获取。
- `LOG_CHANNEL`：日志频道 ID，机器人会将媒体消息转发到此频道并存储文件以生成直链。获取方法：新建频道，发消息，转发到 [@missrose_bot](https://telegram.dog/MissRose_bot)，回复 /id 获取频道 ID。

### 可选环境变量
除了必填变量，还可以设置以下可选变量：

- `PORT`：Web 服务监听端口，默认 8080。
- `HOST`：域名或服务器 IP（如 `https://example.com` 或 `http://your_vps_ip:8080`）。
- `HASH_LENGTH`：直链 hash 长度，范围 6-32，默认 6。
- `USE_SESSION_FILE`：是否使用 session 文件加速 worker 启动，默认 false。
- `USER_SESSION`：用户机器人 session 字符串，用于自动添加 worker 到 LOG_CHANNEL，默认 null。
- `ALLOWED_USERS`：允许使用的用户 ID 列表，逗号分隔，默认 null。

<hr>

### 多机器人加速

> [!NOTE]
> **什么是多客户端功能？有什么作用？**<br>
> 该功能可将 Telegram API 请求分配给多个 worker 机器人，提高下载速度，避免 Telegram 限流。<br>

> [!NOTE]
> 最多可添加 50 个机器人，因为频道最多可设置 50 个管理员。

启用多客户端时，生成新的机器人 Token，并在 `fsb.env` 文件中按如下命名添加：

`MULTI_TOKEN1`：第一个 worker 机器人 Token
`MULTI_TOKEN2`：第二个 worker 机器人 Token
可继续添加，最多 50 个，如 `MULTI_TOKEN3`、`MULTI_TOKEN4` 等。

> [!WARNING]
> 请务必将所有 worker 机器人加入 LOG_CHANNEL（日志群组），否则无法正常工作。


### 使用用户会话自动添加机器人

> [!WARNING]
> 此功能可能导致账号被限制或封禁，仅新注册账号易受影响。

如需使用此功能，请为你的用户账号生成 pyrogram session 字符串，并将其添加到 `fsb.env` 文件的 `USER_SESSION` 变量。

#### 功能说明

该功能可在 worker 启动时自动将其添加到 LOG_CHANNEL，适合有大量 worker 机器人时无需手动添加。

#### 如何生成会话字符串

最简单的生成方式如下：

```sh
./fsb session --api-id <你的API_ID> --api-hash <你的API_HASH>
```

<img src="https://github.com/EverythingSuckz/TG-FileStreamBot/assets/65120517/b5bd2b88-0e1f-4dbc-ad9a-faa6d5a17320" height=300>

<br><br>

此命令会通过二维码认证为你的用户账号生成 session 字符串。暂不支持手机号认证，后续会添加。

## Contributing

## 贡献

如果你有任何新的想法，欢迎为本项目贡献力量。

## Contact me

## 联系方式（原作者）

[![原作者Telegram 频道](https://img.shields.io/static/v1?label=加入&message=Telegram%20频道&color=blueviolet&style=for-the-badge&logo=telegram&logoColor=violet)](https://xn--r1a.click/wrench_labs)
[![原作者Telegram 群组](https://img.shields.io/static/v1?label=加入&message=Telegram%20群组&color=blueviolet&style=for-the-badge&logo=telegram&logoColor=violet)](https://xn--r1a.click/AlteredVoid)

你可以通过 [原作者Telegram 群组](https://xn--r1a.click/AlteredVoid) 联系原作者，或直接私信 [@EverythingSuckz](https://xn--r1a.click/EverythingSuckz)


## Credits

## 致谢

- [@celestix](https://github.com/celestix) 提供了 [gotgproto](https://github.com/celestix/gotgproto)
- [@divyam234](https://github.com/divyam234/teldrive) 贡献了 [Teldrive](https://github.com/divyam234/teldrive) 项目
- [@karu](https://github.com/krau) 添加了图片支持
- [@yanjie233](https://github.com/yanjie233) 进行汉化

## Copyright

## 版权声明

版权所有 (C) 2023 [EverythingSuckz](https://github.com/EverythingSuckz)，遵循 [GNU Affero 通用公共许可证](https://www.gnu.org/licenses/agpl-3.0.en.html)。

TG-FileStreamBot 是自由软件：你可以自由使用、学习、分享和改进它。
你可以根据 [GNU Affero 通用公共许可证](https://www.gnu.org/licenses/agpl-3.0.en.html) 的条款，重新分发和/或修改本项目，
该许可证由自由软件基金会发布，可以选择第3版或更高版本。
请注意，所有本仓库的分支（fork）必须保持开源，并且必须采用相同的许可证。