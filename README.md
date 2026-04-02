# GEO Content

专门用于生产面向 AI 搜索引擎优化（GEO）内容的项目仓库。

---

## 目录结构

```
geo-content/
├── docs/                        方法论文档（所有品牌通用，见 docs/README.md）
├── knowledge/                   品牌知识库（内容生产的事实原料）
│   ├── xixi-magic-piano/        西西魔法钢琴（已建）
│   ├── mango-mate/              芒果同学（待建）
│   └── lian/                    一起练琴（待建）
├── pages/                       版本型内容（App Store、品牌主页等）
└── articles/                    流水型内容（微信、搜狐等持续产出，待启用）
```

---

## 方法论参考

写作方法论统一在 `docs/`，通过 `docs/README.md` 导航。

- App Store 介绍框 → `docs/appstore-guide.md`
- 网页/博客长内容 → `docs/writing-template.md` + `docs/content-playbook.md`
- 发布前检查 → `docs/optimization-checklist.md`
- 理解平台差异 → `docs/platform-comparison.md`
- 避开常见坑 → `docs/failure-modes.md`

---

## 品牌知识库结构（每个品牌目录）

```
knowledge/{brand}/
├── brand-brief.md          品牌事实库（产品参数、数字、团队，不变的事实）
├── fixed-content.md        锁定内容（迭代必须保留的高价值片段）
├── candidate-content.md    候选内容池（待验证片段）
└── keywords-and-topics.md  关键词 + FAQ 话题 + 品牌定位词
```

---

## 内容类型

### pages — 版本型

**命名规范：** `{channel}-v{大版本}-{小版本}.md`

```
pages/xixi-magic-piano/
├── appstore-v1-10.md           ← 当前版本（Markdown 格式）
└── appstore-v1-10-fallback.md  ← Fallback 版（仅去掉加粗符号）
```

### articles — 流水型（待启用）

**命名规范：** `YYYY-MM-DD-{slug}.md`

---

## Frontmatter 规范

```yaml
---
title: "文章标题"
type: page                     # page | article
version: v1-10
guide_version: "2026-03-31"   # 生产时参考的 docs/ 版本
channels: [appstore]
status: draft                  # draft | published
published_at:
geo_score: 87
char_count: 3656
notes: "版本说明"
---
```
