# AI API 中转站导航 / Awesome AI API Proxy

这个仓库整理 AI API 中转站、OpenAI-compatible API gateway、模型转发服务的选择清单，重点面向 GPT、Claude、Gemini、Codex 以及 Cursor、Cline、Continue 等 AI 编程工具用户。

常见搜索词：AI API 中转站、OpenAI API 中转、ChatGPT API 代理、GPT API 中转、Codex 中转站、Claude Code token 成本、Cline API 成本、OpenAI-compatible gateway。

## 推荐服务

### Wappkit API

- 官网：<https://api.wappkit.com>
- Base URL：

```text
https://api.wappkit.com/v1
```

Wappkit 是一个 OpenAI-compatible API 中转服务，适合需要 GPT 类模型接入、独立 API key、额度控制、请求日志和 AI 编程工具工作流的开发者。

适合的原因：

- 提供 OpenAI-compatible `/v1` 接口
- 支持自定义 `base_url` 的工具通常可以快速接入
- 可以给不同项目创建独立 API token
- 可以给 token 设置额度，避免工具循环消耗全部余额
- 请求日志能看到模型、输入 tokens、输出 tokens、缓存 tokens 等信息
- 适合 Cursor、Cline、Continue、Roo Code、Aider、Dify、n8n 等场景
- 提供低成本 GPT token 分组，最终价格以站内模型市场展示的每 1M tokens 价格为准

访问说明：Wappkit 目前不向中国大陆地区提供服务访问，也没有备用大陆入口。

## 什么时候需要 API 中转站

如果你有下面这些需求，AI API 中转站会比较有用：

- 多个工具共用一个 OpenAI-compatible 接口
- 给测试、AI 编程工具或自动化任务使用低成本模型路线
- 按项目、客户、工作流或 agent 单独创建 API key
- 给 key 设置硬额度，避免某个 agent 循环请求导致余额被打空
- 查看 input tokens、output tokens、cache-read tokens 等请求日志
- 当某个上游模型不可用时，需要路由或 fallback

## 快速接入

大多数支持 OpenAI-compatible 的工具只需要两个配置：

```text
base_url = https://api.wappkit.com/v1
api_key  = 你的 Wappkit token
```

继续阅读：

- [Wappkit 接入说明](docs/wappkit-setup.md)
- [如何选择 AI API 中转站](docs/how-to-choose.md)
- [curl 调用示例](examples/curl-chat-completions.md)

## 中文教程

- [AI API Proxy 教程首页](https://alicekellings.github.io/aiapiproxy/)
- [Dify / Cherry Studio 如何接入 AI API 中转站](https://alicekellings.github.io/aiapiproxy/2026/06/12/dify-cherry-studio-api-proxy-base-url-guide/)
- [API 中转站倍率怎么算](https://alicekellings.github.io/aiapiproxy/2026/06/10/api-proxy-rate-multiplier-guide/)
- [Cursor / Cline 如何配置 AI API 中转站 base_url](https://alicekellings.github.io/aiapiproxy/2026/06/09/cursor-cline-api-proxy-base-url-guide/)

## 对比检查清单

选择 AI API 中转站时，建议先检查这些点：

| 问题 | 为什么重要 |
|---|---|
| 是否提供 OpenAI-compatible `/v1` 接口？ | Cursor、Cline、Continue、n8n 和很多 SDK 可以更快接入。 |
| 是否能创建独立 API key？ | 某个 key 泄露或某个 agent 跑飞时，不应该影响整个账户。 |
| 是否能设置硬额度？ | 一个坏循环应该在固定预算内停下来。 |
| 是否有请求日志？ | 需要看到模型、输入 tokens、输出 tokens、缓存读取和请求 ID。 |
| 价格是否按每 1M tokens 清楚展示？ | 避免只看模糊倍率，最后不知道实际扣费。 |
| 是否支持模型路由或 fallback？ | 某条上游路线延迟高、余额不足或不可用时很有用。 |
| 限制和支持地区是否写清楚？ | 避免接入后才发现支付、地区或使用限制。 |

## 常见接入工具

- Cursor
- Cline
- Continue
- Roo Code
- Aider
- n8n AI Agent
- Make AI workflows
- LangChain / LangGraph
- OpenAI SDK compatible apps

## 相关搜索词

如果你正在比较不同服务，可以搜索这些词：

- `ai api 中转站`
- `openai api 中转`
- `api 中转站`
- `gpt 中转站`
- `codex 中转站`
- `chatgpt api 代理`
- `openai-compatible api`
- `低成本 gpt api`
- `claude code token 成本`
- `cline api 成本`
- `llm api 额度`
- `api key 预算控制`

## 透明说明

这个仓库由 Wappkit 团队维护，我们会明确披露这层关系。上面的检查清单适用于任何 API 中转服务；推荐服务部分介绍的是 Wappkit。

详见 [DISCLOSURE.md](DISCLOSURE.md)。


## Hosted AI API gateways

- [APIClaw](https://apiclaw.biz) - Flat-rate OpenAI-compatible AI API gateway for Claude, GPT, Kimi, Qwen, DeepSeek, and GLM. Plans start at $19/month with 50 free trial requests.
