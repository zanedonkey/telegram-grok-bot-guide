# 02 · 创建 Telegram Bot

[上一步](01-prerequisites.md) · [返回首页](../README.md) · [下一步](03-configure-task-entry.md)

## 第二步：创建自己的机器人

1. 打开官方 [@BotFather](https://t.me/BotFather)。
2. 发送 `/newbot`，按提示设置显示名和机器人用户名。
3. 在自己的设备上安全保存返回的 Token。
4. 打开自己的机器人私聊，后续用于发送 `/start` 和验收消息。

每位使用者创建自己的机器人；不要使用教程作者的机器人或配置。

## 安全配置

在平台支持的安全输入框中配置 Token，或在部署设备上自行编辑受限制的环境文件。没有安全输入方式时，不要把 Token 发到聊天，改为手动配置。

建议字段为 `TELEGRAM_BOT_TOKEN`；具体文件加载方式由生成的程序实现。配置模板：[.env.example](../.env.example)。

Linux 可以对真实配置文件设置 `chmod 600 .env`；Windows 应使用文件访问权限限制，不使用这个 Linux 命令。

## 验证

让程序调用 Telegram `getMe` 并检查返回是否成功。公开报告只写验证结果，不展示请求完整 URL、Token 或异常堆栈中的凭据。

Telegram Token 出现在 API 路径中，HTTP 调试日志尤其需要打码。Token 泄露时，应通过 BotFather 撤销并更新自己的配置。

成功标准：API 认证通过，机器人属于使用者自己。仅创建成功尚不代表桥接完成。

参考：[BotFather 官方说明](https://core.telegram.org/bots/features#botfather)、[getMe](https://core.telegram.org/bots/api#getme)。核对日期：2026-10-12。
