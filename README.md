# GEO Content

专门用于生产面向 AI 搜索引擎优化（GEO）内容的项目仓库。

---

## 目录结构

```
geo-content/
├── knowledge/         知识库（方法论 + 各品牌素材，内容生产的原料）
│   ├── guides/        GEO 写作方法论（只读参考）
│   ├── keywords/      关键词研究
│   ├── competitors/   竞品分析
│   ├── research/      数据与研究素材
│   ├── xixi-magic-piano/   西西魔法钢琴品牌知识
│   ├── mango-mate/         芒果同学品牌知识
│   └── lian/               一起练琴品牌知识
├── pages/             版本型内容（App Store、Wikipedia、品牌主页等）
└── articles/          流水型内容（微信、搜狐、LinkedIn 等持续产出）
```

---

## 内容类型

### pages — 版本型

适用于内容相对稳定、方法论或竞品变化时整体迭代的场景。

**命名规范：** `{channel}-{version}-{variant}.md`

| 部分 | 说明 | 示例 |
|------|------|------|
| `channel` | 目标平台 | `appstore`, `wikipedia` |
| `version` | 版本号 | `v1`, `v2` |
| `variant` | 可选，同版本内的差异化变体 | `interest`, `homework` |

示例：
```
pages/
├── mango-mate/
│   ├── appstore-v1-interest.md    ← 兴趣课版本
│   └── appstore-v1-homework.md    ← 作业辅导版本
├── lian/
│   └── appstore-v1.md
└── xixi-magic-piano/
    └── appstore-v1.md
```

### articles — 流水型

适用于持续高频产出的内容平台。

**命名规范：** `YYYY-MM-DD-{slug}.md`

示例：
```
articles/
├── 2026-04-01-why-brand-missing-ai.md
└── 2026-04-02-geo-vs-seo-difference.md
```

---

## Frontmatter 规范

**pages 文章：**
```yaml
---
title: "文章标题"
type: page
version: v1
variant: interest          # 可选，同版本内的变体标识
guide_version: "2026-03-23"   # 生产时参考的 guides 版本（文档最后修改日期）
channels: [appstore]           # 目标发布渠道，可多个
status: draft                  # draft | published
published_at:                  # 发布后填写，格式 YYYY-MM-DD
notes: "版本说明"
---
```

**articles 文章：**
```yaml
---
title: "文章标题"
type: article
guide_version: "2026-03-23"
channels: [wechat, sohu]
status: draft
published_at:
---
```

---

## 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| title | ✅ | 文章标题 |
| type | ✅ | `page` 或 `article` |
| guide_version | ✅ | 生产时参考的 guides 版本（日期格式） |
| channels | ✅ | 目标发布渠道，数组，可多个 |
| status | ✅ | `draft` / `published` |
| published_at | 发布后必填 | 实际发布日期 |
| version | pages 必填 | 版本号，如 v1, v2 |
| variant | 可选 | 同版本内的差异化变体，如 interest, homework |
| notes | 可选 | 版本差异说明、生产背景 |

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
> 可通过 `grep -r "guide_version" pages/ articles/` 批量识别旧版内容。
