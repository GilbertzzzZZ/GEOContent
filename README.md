# GEO Content

专门用于生产面向 AI 搜索引擎优化（GEO）内容的项目仓库。

---

## 目录结构

```
geo-content/
├── knowledge/                   知识库（内容生产的原料）
│   ├── guides/                  GEO 写作方法论（所有品牌通用）
│   ├── xixi-magic-piano/        西西魔法钢琴品牌知识库
│   ├── mango-mate/              芒果同学品牌知识库
│   └── lian/                    一起练琴品牌知识库
├── pages/                       版本型内容（App Store、品牌主页等）
└── articles/                    流水型内容（微信、搜狐等持续产出）
```

---

## 品牌知识库结构（每个品牌目录）

每个品牌目录下包含 4 个标准文件：

```
knowledge/{brand}/
├── brand-brief.md          品牌事实库（产品参数、数字、团队，不变的事实）
├── fixed-content.md        锁定内容（P0/P1，迭代必须保留的高价值片段）
├── candidate-content.md    候选内容池（待验证片段，升级或淘汰）
└── keywords-and-topics.md  关键词 + FAQ 话题 + 品牌定位词
```

内容迭代规则、P0/P1 优先级定义见 `knowledge/guides/appstore-guide.md`。

---

## 内容类型

### pages — 版本型

适用于内容相对稳定、方法论或竞品变化时整体迭代的场景。

**命名规范：** `{channel}-v{大版本}-{小版本}.md`

示例：
```
pages/xixi-magic-piano/
├── appstore-v1-07.md    ← 当前版本（Markdown 格式）
└── appstore-v1-08.md    ← 下次迭代
```

每个版本文件包含：frontmatter（元信息 + GEO 评分）+ 正文。

### articles — 流水型

适用于持续高频产出的内容平台。

**命名规范：** `YYYY-MM-DD-{slug}.md`

---

## Frontmatter 规范

**pages 文章：**
```yaml
---
title: "文章标题"
type: page
version: v1-07
guide_version: "2026-03-31"   # 生产时参考的 appstore-guide 最后更新日期
channels: [appstore]
status: draft                  # draft | published
published_at:
geo_score: 85
char_count: 3491
notes: "版本说明"
---
```

**articles 文章：**
```yaml
---
title: "文章标题"
type: article
guide_version: "2026-03-31"
channels: [wechat]
status: draft
published_at:
---
```

---

## 方法论参考

内容生产参考 `knowledge/guides/`，从 README.md 导航：

- `guides/README.md` — 导航入口，阅读顺序 + 核心结论速查
- `guides/appstore-guide.md` — App Store 专项写作指南（含两套格式版本规范）
- `guides/content-playbook.md` — GEO 内容完整策略手册
- `guides/optimization-checklist.md` — 发布前检查清单
- `guides/failure-modes.md` — 失败模式库
- `guides/platform-comparison.md` — AI 平台引用机制对比
- `guides/writing-template.md` — 通用写作模板（博客/长内容场景）

> `guide_version` 字段记录生产时使用的方法论版本。guides 更新后，
> 可通过 `grep -r "guide_version" pages/ articles/` 批量识别旧版内容。
