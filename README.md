# GEO Content

专门用于生产面向 AI 搜索引擎优化（GEO）内容的项目仓库。

---

## 目录结构

```
geo-content/
├── docs/guides/       方法论文档（只读参考）
├── assets/            素材原料（关键词、竞品分析、研究数据）
├── versioned/         版本型内容（App Store、Wikipedia、品牌主页等）
└── stream/            流水型内容（微信、搜狐、LinkedIn 等持续产出）
```

---

## 内容类型

### versioned — 版本型

适用于内容相对稳定、方法论更新时整体迭代的场景。

- 命名规范：`{topic}/v{N}.md`，如 `appstore-description/v2.md`
- 触发更新：guides 方法论升级、竞品变化、平台规则变化

### stream — 流水型

适用于持续高频产出的内容平台。

- 命名规范：`YYYY-MM-DD-{slug}.md`，如 `2026-04-01-why-brand-missing-ai.md`

---

## Frontmatter 规范

**stream 文章：**
```yaml
---
title: "文章标题"
type: stream
guide_version: "2026-03-23"   # 生产时参考的 guides 版本（文档最后修改日期）
channels: [wechat, sohu]       # 目标发布渠道，可多个
status: draft                  # draft | published
published_at:                  # 发布后填写，格式 YYYY-MM-DD
---
```

**versioned 文章：**
```yaml
---
title: "文章标题"
type: versioned
version: v2
guide_version: "2026-03-23"
channels: [appstore-cn, appstore-us]
status: draft
published_at:
notes: "与上版的主要差异说明"
---
```

---

## 方法论参考

所有内容生产参考 `docs/guides/` 中的文档：

| 文档 | 用途 |
|------|------|
| `geo-content-playbook.md` | 完整 GEO 内容策略手册 |
| `geo-writing-template.md` | 文章写作模板（直接复用） |
| `geo-seo-rewrite-guide.md` | SEO 文章改写为 GEO 的操作指南 |
| `geo-optimization-checklist.md` | 发布前质量检查清单 |
| `geo-platform-comparison.md` | 各 AI 平台引用机制对比 |
| `geo-failure-modes-and-trends.md` | 失败模式分析与趋势预测 |
| `geo-action-plan-90d.md` | 30-60-90 天行动计划 |

> `guide_version` 字段记录内容生产时使用的方法论版本。guides 更新后，
> 可通过 `grep guide_version stream/*.md versioned/**/*.md` 批量识别旧版内容。
