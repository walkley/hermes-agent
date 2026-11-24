---
sidebar_position: 15
title: "WeCom 回调（自建应用）"
description: "WeCom 回调模式已从 Hermes 核心移出，改由官方 wecom 插件提供"
---

# WeCom 回调（自建应用）

企业微信（WeCom）自建应用回调平台（`wecom_callback`）已不再是 Hermes 核心的一部分，现与 [WeCom AI Bot](wecom.md) 模式一起由 [NousResearch/hermes-official-plugins](https://github.com/NousResearch/hermes-official-plugins/tree/main/wecom) 中的官方 `wecom` 插件提供，完整的配置指南也在该插件中。

## 安装

`wecom` 是官方默认插件：Hermes 会在每个 profile 上自动安装并启用它。如需手动安装（例如在移除之后）：

```bash
hermes plugins install wecom
```

插件按 profile 安装；为其他 profile 安装请使用 `hermes -p <profile> plugins install wecom`。安装后重启网关即可提供该平台。

所有名称保持不变：`WECOM_CALLBACK_*` 环境变量（`WECOM_CALLBACK_CORP_ID`、`WECOM_CALLBACK_CORP_SECRET`、`WECOM_CALLBACK_AGENT_ID`、`WECOM_CALLBACK_TOKEN`、`WECOM_CALLBACK_ENCODING_AES_KEY`、`WECOM_CALLBACK_HOST`、`WECOM_CALLBACK_PORT`、`WECOM_CALLBACK_ALLOWED_USERS` 等）、`config.yaml` 中的 `platforms.wecom_callback` 配置块（`extra.corp_id`、用于多企业路由的 `extra.apps`、`extra.port` 等）以及 `hermes-wecom-callback` 工具集名称。回调监听端口默认仍为 8645。

:::info 从内置 WeCom 的版本升级
无需任何操作。已在使用 WeCom 回调模式的 profile（`.env` 中有 `WECOM_CALLBACK_CORP_ID` 和 `WECOM_CALLBACK_CORP_SECRET`，或 `config.yaml` 中有 `platforms.wecom_callback.extra.corp_id` / `extra.apps`）会在 `hermes update` 时，或该 profile 首次启动时（遵循 `security.allow_lazy_installs`），自动从插件目录安装该插件。同时使用两种模式的 profile 只会安装一次该插件。如果之后移除了插件（`hermes plugins remove wecom`），它将保持移除状态。
:::
