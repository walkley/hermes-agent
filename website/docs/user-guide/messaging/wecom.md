---
sidebar_position: 14
title: "WeCom (Enterprise WeChat)"
description: "WeCom moved out of Hermes core into the official wecom plugin"
---

# WeCom (Enterprise WeChat)

The [WeCom](https://work.weixin.qq.com/) (Enterprise WeChat) gateway platform is no longer part of Hermes core. It ships as the official `wecom` plugin in [NousResearch/hermes-official-plugins](https://github.com/NousResearch/hermes-official-plugins/tree/main/wecom), which carries the full setup guide. The same plugin serves both WeCom modes: the AI Bot WebSocket gateway (this page) and the [self-built app callback](wecom-callback.md).

## Install

The `wecom` plugin is an official default plugin: Hermes installs and enables it on every profile. To install it by hand (for example after removing it):

```bash
hermes plugins install wecom
```

Plugins are installed per profile; use `hermes -p <profile> plugins install wecom` for another profile. Restart the gateway afterwards so it serves the platform.

Every name stays the same: the `WECOM_*` environment variables (`WECOM_BOT_ID`, `WECOM_SECRET`, `WECOM_WEBSOCKET_URL`, `WECOM_ALLOWED_USERS`, `WECOM_HOME_CHANNEL`, `WECOM_DM_POLICY`, `WECOM_GROUP_POLICY`, ...), the `platforms.wecom` block in `config.yaml` (`extra.bot_id`, `extra.secret`, `dm_policy`, `group_policy`, `allow_from`, `groups`, ...) and the `hermes-wecom` toolset name.

:::info Upgrading from a release that bundled WeCom
Nothing to do. Every profile that was already using WeCom (`WECOM_BOT_ID` plus `WECOM_SECRET` in its `.env`, or `platforms.wecom.extra.bot_id` in `config.yaml`) gets the plugin installed automatically from the catalog by `hermes update`, or the first time the profile starts (agent or gateway start; this honours `security.allow_lazy_installs`). This happens once per profile: if you later remove the plugin (`hermes plugins remove wecom`), it stays removed.
:::
