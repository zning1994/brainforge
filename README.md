<div align="center">

# brainforge

> 一个锻造 Claude Code 技能的工坊。

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Marketplace-blueviolet)](https://claude.ai/code)
[![Plugins](https://img.shields.io/badge/plugins-3-green)](#里面有什么)
[![Status](https://img.shields.io/badge/status-v0.1.0-orange)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

brainforge 是一个 Claude Code plugin marketplace。
聚合一些我自己写的、也确实在用的 skill/plugin，让别人可以一行命令装上用。

[安装](#安装) · [里面有什么](#里面有什么) · [贡献 / 反馈](#贡献--反馈)

</div>

---

## 这是什么

brainforge 不是一个单独的 skill，而是一个**清单仓库**。它只包含一份 `marketplace.json`，里面列出每个插件的独立 GitHub repo。Claude Code 读到这份清单后，会去各自的源仓库拉对应的 skill。

每个 skill 都有自己独立的 repo，可以单独 clone、单独 issue、单独迭代。brainforge 只是把它们收纳到同一个货架上。

---

## 安装

### 加 marketplace

```bash
/plugin marketplace add zning1994/brainforge
```

### 装某个插件

```bash
/plugin install cooking-skill@brainforge
/plugin install docs-organization@brainforge
/plugin install brainforge-autoresearch@brainforge
```

### 更新到最新

```bash
/plugin marketplace update brainforge
/reload-plugins
```

---

## 里面有什么

### cooking-skill

帮你决定今晚吃啥、怎么做、技法怎么救场。默认中式家常菜，先问两句关键条件，再给能下锅的推荐。

- 仓库：[zning1994/cooking-skill](https://github.com/zning1994/cooking-skill)
- 适用场景：`今晚吃啥`、`冰箱里有 X 能做啥`、`牛肉怎么炒嫩`

### docs-organization

整理项目文档。按大小、受众、新鲜度来组织，瘦身臃肿的 CLAUDE.md/AGENTS.md，决定每份 doc 该放在哪。

- 仓库：[zning1994/docs-organization](https://github.com/zning1994/docs-organization)
- 适用场景：新项目建文档骨架、CLAUDE.md 超过 250 行、文档散乱要重构

### brainforge-autoresearch

自动化优化 skill prompt。基于 Karpathy autoresearch 的思路：定义 binary eval → 让 agent 跑实验 → 自动 mutate prompt → 留下更好的版本。

- 仓库：[zning1994/brainforge-autoresearch](https://github.com/zning1994/brainforge-autoresearch)（前身 `openclaw-autoresearch`）
- 适用场景：某个 skill 效果一般想系统性调优 prompt、想对比多个 prompt 变体的效果

---

## 项目结构

```text
brainforge/
├── .claude-plugin/
│   └── marketplace.json    # 插件清单（指向各个独立 skill repo）
├── README.md
└── LICENSE
```

marketplace.json 的每条 plugin 都用 `source.url` 指向独立 repo，所以 brainforge 本身很轻，skill 更新只需要 push 到各自 repo，brainforge 不用动。

只有新增/下架 skill、调整清单元信息时才需要改 brainforge。

---

## 设计原则

- **一个 skill 一个 repo**：独立版本、独立 issue、独立迭代
- **brainforge 只是目录**：不复制内容，只做聚合
- **OpenClaw / ClawHub 可共存**：同一份 skill 可以同时在两边发布
- **改一处只影响一处**：marketplace.json 改 URL 不会动 skill 本身

---

## 贡献 / 反馈

- 某个 skill 有问题 → 去对应 skill 的 repo 提 issue
- 整个 marketplace 的问题（清单错了、少了什么）→ 在本 repo 提 issue
- 想把自己的 skill 加进来 → 目前只收录我自己写的 skill，欢迎 fork 出你自己的 marketplace

---

## License

MIT
