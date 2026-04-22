---
name: knowledge-snapshot
version: 1.1.0
description: 项目知识查阅指引。遇到不确定的实现细节时，按四层上下文体系查找，禁止凭训练记忆编造。Read docs/ first, then external sources.
---

# Knowledge Snapshot

> 核心：AI 不靠记忆靠查阅。训练数据可能过时，项目文档是最准确的。

## 查阅顺序

遇到不确定的细节时：

1. 项目 `docs/` 目录
2. 项目源码（Grep / Read）
3. go.mod 中的依赖版本 → 确认对应版本的 API
4. Context7 查最新文档
5. WebSearch 查官方文档
6. 全部走完仍无结果 → 告知 io-wy「不知道」

## 外部知识查阅

| 知识领域 | 查阅方式 |
|----------|----------|
| Go 标准库 | Context7 / pkg.go.dev |
| 框架用法 | Context7 / 框架官方文档 |
| 第三方库 | Context7 / GitHub README |
| 协议规范 | 官方文档（OpenAI/Anthropic/等） |

## 禁止行为

- 禁止未读项目 docs/ 就回答项目问题
- 禁止凭训练记忆断言框架行为（必须查证）
- 禁止在未确认 Go 版本兼容性的情况下使用新版 API
