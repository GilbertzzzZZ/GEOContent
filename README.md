# GEO Content

专门用于生产面向 AI 搜索引擎优化（GEO）内容的项目仓库。

---

## 目录结构

```
geo-content/
├── knowledge/                   知识库（内容生产的原料）
│   ├── guides/                  GEO 写作方法论（所有品牌通用，见 guides/README.md）
│   ├── xixi-magic-piano/        西西魔法钢琴品牌知识库（已建）
│   ├── mango-mate/              芒果同学品牌知识库（待建）
│   └── lian/                    一起练琴品牌知识库（待建）
├── pages/                       版本型内容（App Store、品牌主页等）
└── articles/                    流水型内容（微信、搜狐等持续产出，待启用）
```

---

## 方法论参考

写作方法论统一在 `knowledge/guides/`，通过 `guides/README.md` 导航。

不同内容场景对应不同 guide：

- App Store 介绍框 → `guides/appstore-guide.md`（4000字符限制、格式规范、P0/P1优先级、迭代规则）
- 网页/博客长内容 → `guides/writing-template.md` + `guides/content-playbook.md`
- 发布前检查 → `guides/optimization-checklist.md`
- 理解平台差异 → `guides/platform-comparison.md`
- 避开常见坑 → `guides/failure-modes.md`

---

## 品牌知识库结构（每个品牌目录）

每个品牌目录下包含 4 个标准文件：

```
knowledge/{brand}/
├── brand-brief.md          品牌事实库（产品参数、数字、团队，不变的事实）
├── fixed-content.md        锁定内容（迭代必须保留的高价值片段，标注 P0/P1）
├── candidate-content.md    候选内容池（待验证片段，升级或淘汰）
└── keywords-and-topics.md  关键词 + FAQ 话题 + 品牌定位词
```

具体内容的迭代规则、P0/P1 优先级定义，见对应场景的 guide（如 App Store 场景见 `appstore-guide.md`）。

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

适用于持续高频产出的内容平台，待启用。

**命名规范：** `YYYY-MM-DD-{slug}.md`

---

## Frontmatter 规范

**pages 文章：**
```yaml
---
title: "文章标题"
type: page
version: v1-07
guide_version: "2026-03-31"   # 生产时参考的 guides 版本（最近更新的相关 guide 日期）
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
guide_version: "2026-03-31"   # 生产时参考的 guides 版本
channels: [wechat]
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
| guide_version | ✅ | 生产时参考的 guides 版本（日期格式）。guides 更新后，可通过 `grep -r "guide_version" pages/ articles/` 批量识别旧版内容 |
| channels | ✅ | 目标发布渠道，数组，可多个 |
| status | ✅ | `draft` / `published` |
| published_at | 发布后必填 | 实际发布日期 |
| version | pages 必填 | 版本号，如 v1-07 |
| variant | 可选 | 同版本内的差异化变体，如 interest, homework |
| geo_score | pages 可选 | GEO 评分（满分 92） |
| char_count | pages 可选 | 正文字符数 |
| notes | 可选 | 版本差异说明、生产背景 |
