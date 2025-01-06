---
project: heimdallr
stars: 587
description: 一个非常轻量的通知网关，可以聚合各种推送渠道，使用 Serverless 部署，几乎零成本运行。
url: https://github.com/LeslieLeung/heimdallr
---

Heimdallr
=========

> 🔧该项目已经重构至新版本，API、配置项 等与原v1.x版本不兼容。若需要用旧版，请查看 legacy 分支 。

交流群：Telegram

简介
==

Heimdallr 是一个非常轻量的通知网关，可以聚合各种推送渠道，使用 Serverless 部署，几乎零成本运行。

特性
==

-   等同于免费、开源、可自建的 新版Server酱，没有任何限制，痛快推送
-   支持各种常见的推送渠道，如Bark、企业微信等
-   支持 Apprise，从此再也不缺通知渠道（完全列表见链接）
-   完全兼容 Bark 的路由，任意支持 Bark 的地方，都可以使用 Heimdallr 同时发送到更多渠道
-   提供兼容 message-pusher、PushDeer 的路由。
-   支持发送图片（仅 Apprise）
-   支持多通知渠道和分组配置
-   支持 Serverless 部署，几乎零成本运行
-   解决因为群晖DSM奇怪的 webhook 设置方式而无法接入一些推送渠道的问题
-   提供 配置生成器

目前支持的通知方式
---------

-   Bark
-   企业微信应用消息
-   企业微信机器人webhook
-   PushDeer
-   Chanify \[未测试\]
-   Pushover \[未测试\]
-   Email
-   Discord(webhook)
-   Telegram Bot
-   ntfy
-   飞书/Lark
-   钉钉自定义机器人
-   Apprise
-   PushMe

> 如果有需要的通知方式，请提交 issue

部署方式
====

配置项见 示例。也可以使用配置生成器。

具体配置，见 配置文档

第三方服务
-----

### Vercel

### Zeabur

> 配置方式参考 文档，在编辑原始环境变量处粘贴 `.env` 的内容即可。

Serverless
----------

-   腾讯云Serverless
-   阿里云Serverless

Docker
------

见 Docker （支持 `arm64`、`amd64`架构）

接口文档
====

见 接口文档 。

兼容接口
----

Heimdallr 提供与 Bark 完全兼容的接口以及与 message-pusher 兼容的接口，在支持 Bark 或 message-pusher 的服务上，将服务链接换成 Heimdallr 的链接即可把信息通过 Heimdallr 发送。

### Bark 兼容接口

只需要把 Bark 的服务链接换成 Heimdallr 的服务链接即可。

### message-pusher 兼容接口

message-pusher 的接口形如 `https://<domain>/push/<username>`，替换成 `https://<domain>/competable/message-pusher/push` 即可，token 填 Heimdallr 分组的 token。

### PushDeer 兼容接口

PushDeer 的接口形如 `https://<domain>/message/push`，替换成 `https://<domain>/competable/pushdeer/message/push` 即可，pushkey 填 PushDeer 的 token。

Markdown 支持
-----------

在一些支持 Markdown 的服务上，格式化的文本可以以 Markdown 格式呈现。在请求时，通过 query 参数或 json 传入 `msg_type = markdown` 即可。

示例：

# GET
curl 'http://<HOST>/<TOKEN>/\*Hello\*/\_\_World\_\_?msg\_type=markdown'
# POST
curl -X POST 'http://<HOST>/push' --data-raw '{
    "key": "<TOKEN>",
    "title": "\*Hello\*",
    "body": "\_\_World\_\_",
    "msg\_type": "markdown"
}'

> 注意，支持 Markdown 的服务中，并非所有服务都采用相同的语法。在不支持 Markdown 的服务，内容将以纯文本展示。
> 
> 当前支持 Markdown 的服务及其支持的语法如下：
> 
> -   企业微信
> -   Discord
> -   Telegram

示例应用
====

-   使用 Heimdallr 接收群晖DSM推送
-   使用 Heimdallr 接收威联通推送
-   使用 Heimdallr 接收 GitHub star webhook
-   使用 Heimdallr 接收 RSS 推送

更新日志
====

见 更新日志

Stargazers over time
====================
