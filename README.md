# Adrian Punk · 提示词画廊

> 中文字体 AI 提示词博物馆，来自 [@AdrianPunk115](https://x.com/AdrianPunk115) 的 X 原创内容。

**Live:** [https://violin86318.github.io/adrian-punk-gallery/](https://violin86318.github.io/adrian-punk-gallery/) · [https://adrian.beyondmotion.net/](https://adrian.beyondmotion.net/)

---

## 关于

本画廊收录 @AdrianPunk115 发布的全部 AI 字体设计提示词，每条提示词均附 GPT Image 2 实测结果。

核心特点：
- 每条提示词 **独立详情页**，含完整 prompt + 测试图
- 双引擎对比：GPT Image 2（原图）+ Gemini Flash（参考图）
- 支持分类过滤（26 个字体/设计分类）

---

## 目录结构

```
adrian-punk-site/
├── index.html                  # 首页画廊
├── prompt/                    # 详情页（adrian-{N}-{标题}.html）
├── assets/
│   └── tests/
│       ├── adrian_bizyair_*.png   # GPT Image 2 测试图
│       └── adrian_gcli_*.jpg      # Gemini Flash 参考图
└── README.md
```

提示词源数据：`../prompt-gallery/data/adrian_prompts.json`

---

## 自动更新

定时任务每天 10:01（北京时间）自动运行：

1. 抓取 @AdrianPunk115 最新推文
2. 对比 `adrian_prompts.json` 去重
3. 新提示词追加 JSON + 生成详情页 + 更新首页
4. gcli（本地免费）+ bizyair（GPT Image 2）双引擎生成测试图
5. 推送 GitHub，自动触发 GitHub Pages 部署

---

## 技术栈

| 模块 | 方案 |
|------|------|
| 提示词抓取 | fxtwitter API / opencli |
| GPT Image 2 | BizyAir（`bza-image-o2-base`） |
| 参考图生成 | 本地 gcli2api（`gemini-3.1-flash-image`） |
| 托管 | GitHub Pages + Cloudflare Workers（自定义域名） |
| CI/CD | GitHub Actions（`pages-build-deployment`） |

---

## 相关项目

- **小小东提示词画廊** — 另一套独立站点，同一技术架构
- **prompt-gallery** — 本地开发目录（含通用批生成脚本、跟踪器）
