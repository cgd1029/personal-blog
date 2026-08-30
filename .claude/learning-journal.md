# Personal Blog 学习日志

<!-- setup_done: true -->

## 学习目标

- 理解 Hexo 博客从 Markdown 源文件到浏览器网页的完整运行逻辑。
- 理解项目中每个自有文件和目录的作用，知道哪些应当修改、哪些不应手动修改。
- 能独立完成新增文章、本地预览、生成网页，并为后续 GitHub Pages 发布打基础。

## 当前基础

- 已理解 Markdown 文章需要经过 Hexo 转换为 HTML。
- 已理解 Git/GitHub 用于记录和同步项目文件，GitHub Pages 用于对外提供网页。
- 已理解 Pages 必须读取包含新版网页的正确来源。
- 已接触 GitHub 仓库，但不熟悉 Git 命令和网站部署。

## 当前项目

- 项目位置：`/Users/Admin/项目/personal-blog`
- 框架：Hexo 8
- 主题：Landscape
- 包管理相关文件：`package.json`、`pnpm-lock.yaml`、`pnpm-workspace.yaml`

## 待学习模块

- [x] 整体运行链路：Markdown → Hexo → 主题渲染 → `public/` → 本地服务器
- [x] `package.json` 中脚本和依赖的作用
- [ ] `_config.yml` 与主题配置的作用
- [ ] `source/`、`scaffolds/` 中内容文件的作用
- [ ] `public/`、`db.json`、`node_modules/` 等生成内容的作用
- [ ] `.gitignore`、`.github/dependabot.yml` 等 GitHub 辅助配置
- [ ] 从修改一篇文章到本地预览的完整操作

## 学习方式

- 以 `source/_posts/hello-world.md` 为真实案例追踪数据流。
- 每次聚焦一个模块，先判断文件在链路中的位置，再阅读关键代码。
- 跳过形式化认证，以项目推进和实际操作为主。

## 2026-08-30

- 用户希望系统理解项目逻辑以及各个文件和代码的作用。
- 本轮从整体运行链路开始，后续依次讲解配置、内容、生成目录和发布辅助文件。
- 已能判断文章内容应该修改 `source/_posts/hello-world.md`，而不是修改生成后的 `public/index.html`。
- 已理解 `npm run <名称>` 会读取 `package.json` 的 `scripts`，并执行右侧对应的 Hexo 命令。
- 已理解 `package.json` 的 `dependencies` 是博客运行所需的软件依赖清单，而不是文章内容。
- 已能判断缺少 `hexo-renderer-marked` 会使 Markdown 正文无法正常转换为 HTML。
