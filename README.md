# smallyu的AI文章（blog-ai）

仅发布中文 AI 文章的独立 Hexo 站点，域名 `ai.smallyu.net`，静态产物在 `docs/`。所有文章作为正常文章发布，首页、标签、分类、sitemap、Atom 和 RSS 均正常收录。

## 本地构建

```sh
npm ci --ignore-scripts
npm run build
npm run serve
```

## 写作和迁移

使用普通 `post` scaffold，不设置 `collection: ai`。主题自动给文章标题增加 AI 徽标并对正文应用 `.ai-content`。正文标题只调整视觉字号和装饰，不改动 Markdown 或 HTML 标题层级。RSS 阅读器使用自身样式。

首次迁入 66 篇文章（blog 22、blog-en 20、blog-b 6、blog-crazy 18），保留原日期、语言和正文。2026-11-13 按要求删除其中 20 篇英文文章，当前保留 46 篇中文文章。`migration-manifest.json` 保存当前保留文章的来源、正文校验值及资源清单；它不是文章或订阅源的一部分。文章按来源分目录，公开路径统一为日期和文件名。旧站删除文章和文章库页面，不保留跳转或兼容逻辑。

## 主题维护

四个原站的 `themes/yinplus` 是干净公共基线，站点差异仅放在各自主题 `_config.yml`。本项目维护独立派生主题 `themes/yinplus-ai`。

相对公共基线，本主题定制文件为：

- `_config.yml`：本站导航和配置。
- `layout/layout.pug`：加载 AI 徽标和正文样式，保留文章自身的语言标记。
- `layout/post.pug`：文章标题徽标和正文容器。
- `layout/index.pug`、`layout/tag.pug`、`layout/category.pug`：文章列表徽标（含系列内文章）。
- `source/css/ai-badge.css`、`source/css/ai-content.css`：AI 专属样式。

其余文件沿用公共基线。同步公共修复时，其余文件可直接同步；上述文件需要人工合并。不要把 AI 展示规则加回原站，也不要使用旧的文章库过滤脚本。

## 发布

将本目录作为独立仓库，托管 `docs/`（例如 GitHub Pages 的 main 分支 /docs）。设置自定义域名 `ai.smallyu.net`、对应 DNS 和 HTTPS。`source/CNAME` 已配置域名。修改域名时同时更新 `_config.yml`、CNAME、robots.txt 和 llms.txt，然后重新构建。

- Atom：`https://ai.smallyu.net/atom.xml`
- RSS 2.0：`https://ai.smallyu.net/rss.xml`

blog-feed 的来源列表保持不变，不接入本项目。本项目不配置通知 blog-feed 的工作流。分析统计默认关闭，配置本站统计 ID 后再开启。

## 本次迁移验证

2026-11-13 本地验证：五站静态构建成功；66 篇迁移正文和 6 张图片的校验值保持一致；新站首页、Atom、RSS 和 sitemap 完整收录 66 篇；20 篇英文文章保留 `lang=en`；四个原站的普通文章及资源未修改，AI 文章页面、文章库页面及专属 CSS 均已移除，无跳转页。blog-feed 工作区未修改。此记录不表示已提交、推送或上线。

2026-11-13 后续调整：站点标题改为“smallyu的AI文章”，删除 20 篇英文文章及其静态页面，首页和订阅源保留 46 篇中文文章。
