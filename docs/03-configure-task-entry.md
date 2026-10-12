# 03 · 配置任务入口

[上一步](02-create-telegram-bot.md) · [返回首页](../README.md) · [下一步](04-forward-and-reply.md)

## 第三步：核实并创建 Routine

在自己的 Grok Bot 中检查是否提供 Webhook 触发的 Routine。若支持：
1. 选择负责处理任务的 Bot。
2. 创建仅用于 Telegram 接入的任务入口。
3. 从当前平台界面或官方说明确认鉴权方式、请求格式、状态码与运行限制。
4. 安全配置地址和鉴权材料。
5. 使用 [Routine 提示词](../prompts/routine-prompt.md)设置执行和回传规则。
6. 使用无副作用输入测试，检查运行记录。

这里不提供未经验证的应用深层链接或固定面板路径。无法找到入口时，向当前平台确认能力，不猜测端点。

## 配置与请求约定

模板中的 `GROK_BOT_WEBHOOK_URL` 和 `GROK_BOT_WEBHOOK_KEY` 是建议配置名。只有平台明确要求 Bearer 鉴权时，才使用 `Authorization: Bearer <KEY>`，否则按平台协议配置。

建议转发程序和 Routine 约定以下字段；这不是官方协议：
- `update_id`：任务去重标识。
- `message_id`：原消息标识。
- `chat_id` 和 `from_id`：已由可信程序核验的数字身份。
- `text`：外部任务文本，仍视为不可信输入。

Routine 不能仅凭请求正文的“已授权”声明放行。入口鉴权、身份验证和来源限制必须由可信程序或平台机制完成。

## 三类结果

| 状态 | 证据 |
| --- | --- |
| 请求已接受 | 入口按照协议确认接收 |
| 任务已完成 | 执行结果和可检查的任务状态 |
| 回复已送达 | Telegram 发送成功结果 |

异步入口返回 HTTP 2xx，不代表任务完成。没有执行证据时不要回复“已完成”。

官方 [Routine 说明](https://docs.x.ai/grok-bot/skills-routines-and-automations)已核对（2026-10-12）；本教程所需的完整 Webhook 协议与账号可用性仍待部署者核实。
