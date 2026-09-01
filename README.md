# Personal Blog

这是一个使用 Hexo 构建的个人静态博客项目。文章使用 Markdown 编写，Hexo 根据站点配置和 Butterfly 主题生成 HTML、CSS、JavaScript 等静态文件，再由本地服务器或 GitHub Pages 提供访问。

本项目中的代码注释、配置说明和项目文档统一使用简体中文；代码标识符、命令、软件包名称和 API 字段保持原有英文形式。

## 项目状态

- 已完成 Hexo 8 项目的本地初始化。
- 已安装并启用 Butterfly 5.7.0 主题。
- 已建立带简体中文注释的 Butterfly 基础配置。
- 已完成中文站点配置和中文示例文章。
- 已为示例文章添加日期、更新时间、分类、标签和摘要。
- 已创建“分类”“标签”和“关于”独立页面，并完成主要导航配置。
- 已配置自定义头像、页面顶部图片和网站背景。
- 已添加 GitHub Actions 自动构建与 Pages 部署配置。
- 已启用 Butterfly 本地站内搜索。
- 已明确启用不蒜子基础访问统计，包括全站访客数、全站浏览量和文章阅读量。
- 已创建响应式图库页面，并启用 Fancybox 图片放大预览。
- 已创建独立音乐页面，使用 APlayer 播放项目内的本地音频。
- 已验证本地静态文件生成，输出目录为 `public/`。
- 已配置 GitHub 远程仓库 `cgd1029/personal-blog`。
- 已通过 GitHub Pages 正式发布并完成线上访问验证。
- 已按项目站点配置网址 `https://cgd1029.github.io/personal-blog/`。
- `_config.yml` 中的 `deploy.type` 仍为空，当前不能使用 `hexo deploy` 完成一键部署。

## 技术栈

| 技术 | 在项目中的作用 |
| --- | --- |
| Node.js | 运行 Hexo 和相关 JavaScript 工具的基础环境 |
| Hexo 8 | 读取 Markdown、配置和主题，生成静态网站 |
| Markdown | 编写文章正文和项目文档 |
| YAML | 编写 Hexo、主题、pnpm 和 Dependabot 配置 |
| Pug | Butterfly 主题使用的 HTML 模板渲染方式 |
| Stylus | Butterfly 主题使用的 CSS 样式预处理语言 |
| HTML | Hexo 最终生成的网页结构 |
| CSS | 控制网页排版、颜色、字体和响应式布局 |
| JavaScript | 提供主题交互和页面行为 |
| APlayer | 在音乐页面提供音频播放、进度、音量和曲目信息界面 |
| pnpm | 安装、锁定和更新 Node.js 依赖 |
| Git | 记录项目文件的历史版本 |
| GitHub | 保存远程代码仓库并提供协作能力 |
| GitHub Pages | 托管已经生成的静态网页，并通过正式网址提供公开访问 |
| 不蒜子 | 通过第三方脚本提供全站访客数、浏览量和文章阅读量 |
| Dependabot | 在 GitHub 上定期检查依赖版本更新 |

## 运行逻辑

项目的核心数据流如下：

```text
source/_posts/*.md
        │
        │  读取文章和文章头部信息
        ▼
hexo-renderer-marked
        │
        │  Markdown 正文转换为 HTML 片段
        ▼
Hexo + _config.yml + Butterfly 主题
        │
        │  组合站点配置、页面模板和样式
        ▼
public/
        │
        ├── index.html                 博客首页
        ├── archives/                  归档页面
        ├── 年/月/日/文章名/index.html 文章页面
        ├── css/                       生成后的样式
        └── js/                        生成后的脚本
        │
        ├── hexo server                本地预览
        └── GitHub Pages               后续线上发布
```

以当前文章为例：

```text
源文件：source/_posts/hello-world.md
文章标题：你好，世界
链接规则：:year/:month/:day/:title/
生成文件：public/2026/08/28/hello-world/index.html
访问路径：/2026/08/28/hello-world/
```

物理文件名仍为 `hello-world.md`，因此默认链接中的 `:title` 仍使用 `hello-world`；文章页面显示的标题则来自 Markdown 头部的 `title: 你好，世界`。

## 核心依赖

项目的直接依赖记录在 `package.json` 中：

| 依赖 | 作用 |
| --- | --- |
| `hexo` | 静态博客生成器核心 |
| `hexo-generator-index` | 生成博客首页 |
| `hexo-generator-archive` | 生成文章归档页 |
| `hexo-generator-category` | 生成分类页 |
| `hexo-generator-tag` | 生成标签页 |
| `hexo-generator-searchdb` | 根据文章标题和正文生成本地搜索索引 |
| `hexo-renderer-marked` | 将 Markdown 转换为 HTML |
| `hexo-renderer-pug` | 渲染 Butterfly 使用的 Pug 页面模板 |
| `hexo-renderer-stylus` | 将 Stylus 样式转换为 CSS |
| `hexo-server` | 启动本地预览服务器 |
| `hexo-theme-butterfly` | 提供当前网站的页面结构、样式和主题交互 |
| `hexo-renderer-ejs` | 为旧 Landscape 主题保留的 EJS 渲染器 |
| `hexo-theme-landscape` | 暂时保留的旧主题，便于必要时回退 |

## 项目结构

```text
personal-blog/
├── .claude/
│   └── learning-journal.md
├── .github/
│   ├── workflows/
│   │   └── pages.yml
│   └── dependabot.yml
├── scaffolds/
│   ├── draft.md
│   ├── page.md
│   └── post.md
├── source/
│   ├── _posts/
│   │   └── hello-world.md
│   ├── about/
│   │   └── index.md
│   ├── categories/
│   │   └── index.md
│   ├── gallery/
│   │   └── index.md
│   ├── music/
│   │   └── index.md
│   ├── audio/
│   │   └── demo-melody.wav
│   ├── img/
│   │   ├── 头像.jpg
│   │   └── 背景.jpg
│   └── tags/
│       └── index.md
├── themes/
│   └── .gitkeep
├── .gitignore
├── _config.butterfly.yml
├── _config.landscape.yml
├── _config.yml
├── package.json
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
└── README.md
```

运行或构建后，本地还会出现 `node_modules/`、`db.json` 和 `public/`。它们不是需要长期手动维护的源文件。

## 各个文件和目录的作用

### `_config.yml`

Hexo 的网站级主配置文件，控制：

- 网站标题、副标题、作者、语言和时区。
- 网站正式网址和文章永久链接格式。
- 源文件目录与静态网页输出目录。
- 新文章命名、草稿、文章资源和外部链接行为。
- 代码高亮、首页排序、分页、分类和标签。
- 当前主题以及后续部署方式。

文件内已经为主要字段添加简体中文注释。修改时必须注意 YAML 缩进，子配置通常比父配置多两个空格。

当前重要配置：

```yaml
title: Laor
author: Laor
language: zh-CN
url: https://cgd1029.github.io/personal-blog
root: /personal-blog/
permalink: :year/:month/:day/:title/
source_dir: source
public_dir: public
theme: butterfly
deploy:
  type: ''
```

### `_config.butterfly.yml`

当前启用的 Butterfly 主题配置文件。它包含基础导航、GitHub 链接、自定义头像和背景、文章目录、站内搜索、访问统计、图库大图预览、评论总开关和中文公告等设置。

当前已配置首页、归档、分类、标签、图库、音乐和关于页面的基础导航，并使用 `source/img/` 中的图片作为头像、顶部图片、网站背景和示例图库内容。站内搜索、基础访问统计、图库和本地音乐播放器均已启用。

图片配置中的 `/img/头像.jpg` 和 `/img/背景.jpg` 是浏览器访问路径，不是本地文件系统路径。生成网站时，Hexo 会把 `source/img/` 中的文件复制到 `public/img/`，因此浏览器最终能够通过 `/img/文件名` 访问它们。

### `_config.landscape.yml`

旧 Landscape 主题的独立覆盖配置文件。当前主题已切换为 Butterfly，因此这个文件暂时不会生效。

保留该文件用于记录旧主题和提供回退入口；只有把 `_config.yml` 改回 `theme: landscape` 时，它才会生效。

### `package.json`

Node.js 项目的依赖清单和命令入口。JSON 语法不允许写注释，因此字段作用在这里说明：

- `name`：项目的软件包名称。
- `version`：项目自身的版本号。
- `private`：设为 `true`，防止误把博客发布成 npm 软件包。
- `scripts`：可通过 npm 或 pnpm 调用的快捷命令。
- `hexo.version`：记录项目使用的 Hexo 版本。
- `dependencies`：运行和生成博客所需的直接依赖。

当前脚本映射：

| 项目命令 | 实际命令 | 作用 |
| --- | --- | --- |
| `npm run server` | `hexo server` | 启动本地预览服务器 |
| `npm run build` | `hexo generate` | 生成静态网站 |
| `npm run clean` | `hexo clean` | 删除旧的输出文件和缓存 |
| `npm run deploy` | `hexo deploy` | 按部署配置发布网站 |

### `pnpm-lock.yaml`

pnpm 自动生成的依赖锁定文件，用于记录：

- `lockfileVersion`：锁定文件格式版本。
- `settings`：依赖解析设置。
- `importers`：项目直接依赖及其实际版本。
- `packages`：直接和间接依赖的版本、校验值与运行要求。
- `snapshots`：最终依赖组合关系。

不要手动编辑此文件。使用 `pnpm install`、`pnpm add` 或 `pnpm update` 时，pnpm 会自动维护它。

### `pnpm-workspace.yaml`

pnpm 的工作区级配置。当前主要用于控制哪些依赖可以在安装过程中运行自身的构建脚本。

当前已经在 `allowBuilds` 中允许 `hexo-util` 运行安装构建脚本。如果以后出现新的 `ERR_PNPM_IGNORED_BUILDS`，应先审查报错中列出的依赖，再通过 `pnpm approve-builds` 或手动配置 `allowBuilds` 明确允许或拒绝；不要直接允许所有依赖执行脚本。

### `source/`

博客源内容目录，是日常写作时最常修改的目录。

`source/_posts/` 保存正式文章。每篇文章通常由两部分组成：

```markdown
---
title: 文章标题
date: 2026-08-31 20:00:00
categories:
  - 学习记录
tags:
  - Hexo
  - 博客
---

这里开始编写 Markdown 正文。
```

两个 `---` 之间称为 Front-matter，用于保存文章标题、日期、分类和标签等元数据；第二个 `---` 后面才是文章正文。

### `source/_posts/hello-world.md`

当前项目的第一篇示例文章，标题为“你好，世界”。它介绍了创建文章、本地预览、生成静态文件和部署等 Hexo 基础命令。

它的 Front-matter 还提供了以下文章信息：

- `date`：文章的首次创建或发布日期。
- `updated`：文章最近一次修改的日期。
- `categories`：文章所属的内容分类，当前为“学习记录”。
- `tags`：描述文章主题的关键词，当前为“Hexo”和“博客搭建”。
- `description`：文章内容的简短摘要。

### `source/categories/index.md`

Butterfly 的分类索引页。它不是某一篇文章，而是用于汇总和展示各个文章分类的独立页面。

Front-matter 中的 `type: categories` 用于告诉 Butterfly：这个页面应当按照分类索引页的形式渲染。导航中的“分类”链接会访问 `/categories/`。

### `source/tags/index.md`

Butterfly 的标签索引页，用于汇总文章使用过的全部标签。当前示例文章会提供“Hexo”和“博客搭建”两个标签。

Front-matter 中的 `type: tags` 用于告诉 Butterfly：这个页面应当按照标签索引页的形式渲染。导航中的“标签”链接会访问 `/tags/`。

### `source/about/index.md`

网站的“关于”独立页面，用于说明博客的用途、主要内容和当前建设状态。它会生成 `/about/index.html`，访问地址为 `/about/`。

这个页面是普通独立页面，因此不需要设置特殊的 `type`。后续可以把其中的占位介绍替换为真实的个人介绍、学习方向和联系方式。

### `source/img/`

网站自定义图片的源文件目录。目前包含：

- `头像.jpg`：Butterfly 侧栏作者卡片和移动端侧栏使用的头像。
- `背景.jpg`：页面顶部横幅和网站整体背景使用的图片。

执行 Hexo 构建后，这些图片会被复制到 `public/img/`。主题配置应填写 `/img/文件名` 形式的浏览器访问路径，不要填写电脑上的绝对路径，也不要把 `source` 写入访问路径。

### `scaffolds/`

Hexo 新建内容时使用的模板目录：

- `scaffolds/post.md`：普通文章模板，对应 `hexo new post`。
- `scaffolds/page.md`：独立页面模板，对应 `hexo new page`。
- `scaffolds/draft.md`：草稿模板，对应 `hexo new draft`。

模板中的 `{{ title }}` 和 `{{ date }}` 会在创建内容时由 Hexo 自动替换。

### `themes/.gitkeep`

`.gitkeep` 用于让 Git 保留空的 `themes/` 目录。当前 Butterfly 和旧 Landscape 主题都通过 `package.json` 安装到 `node_modules/`，因此这里暂时没有主题源码。

### `.gitignore`

告诉 Git 哪些文件不需要进入版本记录。目前忽略：

- 操作系统生成的临时文件。
- Hexo 缓存 `db.json`。
- 日志文件。
- 第三方依赖目录 `node_modules/`。
- 静态网站输出目录 `public/`。
- Hexo 部署和多配置产生的临时文件。

### `.github/dependabot.yml`

GitHub Dependabot 配置文件。它会定期检查根目录中的 Node.js 依赖，并在发现可更新版本时创建更新请求。

Dependabot 创建的更新不能直接视为安全可用，仍需检查版本变化并重新运行构建验证。

### `.claude/learning-journal.md`

本地代码库学习日志，用于记录已经理解的模块、待学习内容和学习进度。它不参与 Hexo 构建，也不会影响最终网站。

### `README.md`

当前项目说明文档，用于帮助维护者和仓库访问者理解项目结构、运行逻辑和使用方法。

### `node_modules/`

pnpm 安装的第三方依赖目录。它可以根据 `package.json` 和 `pnpm-lock.yaml` 重新安装，不应手动修改，也不提交到 Git。

### `db.json`

Hexo 自动生成的本地缓存数据库，用于提高后续处理速度。执行 `hexo clean` 时会被删除，之后可以重新生成。

### `public/`

Hexo 生成的最终静态网站目录，包含 HTML、CSS、JavaScript 和图片等浏览器可访问文件。

不要长期手动修改 `public/`，因为再次运行 Hexo 后，这些修改可能被重新生成的文件覆盖。正确做法是修改 `source/`、`_config.yml` 或主题配置，然后重新生成。

## 使用说明

### 1. 环境要求

- Node.js：`>= 20.19.0`
- pnpm：用于安装和更新依赖
- Git：用于版本管理和同步 GitHub 仓库

当前已经验证的本地环境：

```text
Node.js 26.0.0
pnpm 11.19.0
Hexo 8.1.2
Hexo CLI 4.3.2
```

### 2. 获取项目

```bash
git clone https://github.com/cgd1029/personal-blog.git
cd personal-blog
```

### 3. 安装依赖

```bash
pnpm install
```

如果 pnpm 提示某些依赖的构建脚本被忽略，先阅读依赖名称和风险，再运行：

```bash
pnpm approve-builds
```

只批准经过确认的依赖，然后重新执行 `pnpm install`。

### 4. 启动本地预览

```bash
npm run server
```

默认访问地址：

```text
http://localhost:4000
```

停止服务器时，在运行命令的终端中按 `Control + C`。

如果 `4000` 端口已被占用，可以直接使用 Hexo 本地程序指定其他端口：

```bash
./node_modules/.bin/hexo server --port 4001
```

然后访问 `http://localhost:4001`。

### 5. 创建新文章

```bash
./node_modules/.bin/hexo new post "文章文件名"
```

Hexo 会根据 `scaffolds/post.md` 创建：

```text
source/_posts/文章文件名.md
```

建议文章文件名使用简短的英文、数字和连字符，以获得更稳定、易分享的网址；页面显示的中文标题写在文章 Front-matter 的 `title` 中。

### 6. 编辑文章

打开 `source/_posts/` 中对应的 Markdown 文件，修改 Front-matter 和正文。保存后，本地预览服务器通常会自动检测变化并重新生成页面。

不要直接修改 `public/index.html` 或文章目录中的 `index.html`。

### 7. 清理并重新生成网站

```bash
npm run clean
npm run build
```

两条命令分别执行：

```text
hexo clean     删除 public/ 和 db.json
hexo generate  根据最新源文件重新生成 public/
```

### 8. 检查生成结果

构建成功后，重点检查：

- `public/index.html` 是否存在。
- 新文章对应的 `public/年/月/日/文章名/index.html` 是否存在。
- 本地首页是否显示新文章。
- 文章标题、图片、链接和代码块是否正常。

### 9. 提交到 GitHub

```bash
git status
git add .
git commit -m "更新博客内容"
git push
```

提交前先用 `git status` 确认文件范围，避免提交密钥、临时文件或无关内容。

### 10. GitHub Pages 发布说明

本项目已经创建 `.github/workflows/pages.yml`，用于在 `main` 分支收到新提交后自动构建并部署网站。仓库的 **Settings → Pages → Source** 已选择 **GitHub Actions**，首次部署和线上访问均已验证成功。

当前发布配置如下：

- 正式网址：`https://cgd1029.github.io/personal-blog/`
- 网站路径前缀：`/personal-blog/`
- 源代码分支：`main`
- Hexo 输出目录：`public/`
- Pages 来源：GitHub Actions 构建产物

每次更新后的自动发布过程是：

1. 在本地修改文章或配置并完成预览。
2. 把修改提交并推送到 GitHub 的 `main` 分支。
3. GitHub Actions 自动安装依赖并运行 Hexo。
4. 自动上传 `public/` 并部署到 GitHub Pages。
5. 检查 Actions 状态和线上网页是否已更新。

如果使用 GitHub Actions，通常由自动任务执行以下链路：

```text
读取仓库中的 Markdown
        ↓
安装 Node.js 和项目依赖
        ↓
运行 Hexo 生成静态网页
        ↓
上传 public/ 中的构建产物
        ↓
部署到 GitHub Pages
```

当前不要直接运行 `npm run deploy` 并期待网站上线，因为 `_config.yml` 的 `deploy.type` 仍为空。

### 11. 访问统计说明

Butterfly 会根据 `_config.butterfly.yml` 中的 `busuanzi` 配置，在网页中生成统计数字的显示位置并加载不蒜子脚本。Hexo 本身不会记录访客，也不会计算浏览量；访问者打开网页后，浏览器中的第三方脚本才会请求统计数据并把数字填入页面。

当前显示三类数据：

- `site_uv`：全站访客数，用于近似表示访问过网站的不同访客数量，不等同于注册用户数或绝对精确的人数。
- `site_pv`：全站页面浏览量，同一访客打开多个页面或多次访问时可以累计多次。
- `page_pv`：单篇文章的页面浏览量，在文章页面中显示为阅读次数。

访问统计依赖外部网络和第三方服务。如果浏览器拦截统计脚本、第三方服务暂时不可用，数字可能不显示，但不会影响文章正文和页面本身。判断统计功能是否正常时，应以 GitHub Pages 正式网址为准，不要把本地预览地址中的数字当成真实博客访问数据。

不蒜子属于第三方服务，可能处理访问记录以完成统计。在正式长期运营网站前，应阅读其隐私说明，并在博客隐私说明中告知访问者所使用的统计服务。

### 12. 图库使用说明

图库源文件是 `source/gallery/index.md`。其中使用 Butterfly 内置的 `gallery` 标签读取多行 Markdown 图片语法，再由主题中的 JavaScript 把图片排列成会随屏幕宽度调整的图库。该页面设置了 `aside: false`，因此只在图库中隐藏右侧信息栏，为照片留出更宽的展示区域。

当前图库写法如下：

```markdown
{% gallery false,10,10 %}
![博客头像](/personal-blog/img/头像.jpg "博客头像")
![博客背景](/personal-blog/img/背景.jpg "博客背景")
{% endgallery %}
```

`gallery false,10,10` 中三个参数的作用：

- `false`：不显示“加载更多”按钮，直接加载当前图库中的图片。
- 第一个 `10`：分批加载时，每一批最多加载 10 张图片。
- 第二个 `10`：第一次最多加载 10 张图片。

以后添加照片时：

1. 在 `source/img/` 中创建 `gallery/` 文件夹。
2. 把照片放入 `source/img/gallery/`。
3. 在 `source/gallery/index.md` 的 `gallery` 标签内部增加图片，例如：

```markdown
![照片说明](/personal-blog/img/gallery/照片文件名.jpg "照片标题")
```

4. 运行 `npm run server`，打开 `/personal-blog/gallery/` 检查排版和点击放大效果。
5. 确认无误后构建、提交并推送，GitHub Actions 会自动发布新版。

图片地址必须包含项目站点前缀 `/personal-blog/`。如果只写 `/img/gallery/照片.jpg`，浏览器会从 GitHub 用户站点的根路径查找图片，可能产生 404。图片文件名建议简短、含义明确，并避免使用空格。

### 13. 音乐播放器说明

音乐页面源文件是 `source/music/index.md`，示例音频位于 `source/audio/demo-melody.wav`。生成网站时，Hexo 会把音频原样复制到 `public/audio/`，GitHub Pages 再把它作为普通静态文件提供给浏览器。

音乐播放链路如下：

```text
source/audio/demo-melody.wav
        ↓ Hexo 复制静态文件
public/audio/demo-melody.wav
        ↓ GitHub Pages 返回音频
浏览器加载音频
        ↓
APlayer 提供播放、暂停、进度和音量界面
```

当前没有使用 Meting 在线歌单接口，原因是在线歌单还依赖额外的音乐平台和第三方 API，可能受到登录、版权、地区限制或服务可用性的影响。本地音频方案更适合作为第一版博客的稳定实现。

播放器设置中的关键字段：

- `container`：指定播放器要显示在哪个 HTML 元素中。
- `autoplay: false`：禁止页面打开后自动播放，必须由访问者主动点击。
- `preload: 'metadata'`：先读取音频时长等信息，不立即下载完整音频。
- `volume: 0.5`：第一次打开时使用 50% 音量；用户调整后，播放器可能记住新设置。
- `audio`：曲目清单，每一项包含名称、作者、音频地址和封面地址。

以后替换成自己的音乐时：

1. 确认自己拥有公开传播音频的权利。
2. 把 MP3、WAV 或其他浏览器支持的音频放入 `source/audio/`。
3. 修改 `source/music/index.md` 中 `audio` 数组里的 `name`、`artist`、`url` 和 `cover`。
4. 多首歌曲可以在 `audio` 数组中继续增加对象，每个对象代表一首曲目。
5. 使用 `npm run server` 本地检查播放、暂停、进度条和手机端布局，然后再提交发布。

APlayer 的资源版本固定为 `1.10.1`，并且只在音乐页面加载。即使播放器资源暂时加载失败，文章、搜索、图库和其他页面仍可继续访问。

## 日常更新流程

```text
1. 在 source/_posts/ 中新增或修改 Markdown
2. 保存文件
3. 使用 npm run server 本地预览
4. 检查标题、正文、图片和链接
5. 使用 npm run clean 和 npm run build 重新生成
6. 使用 git status 检查改动
7. 提交并推送到 GitHub
8. 发布配置完成后，检查 GitHub Actions 和 Pages 状态
9. 打开线上网址验证新版内容
```

## 常见问题

### 修改文章后页面仍然是旧版

依次检查：

1. 修改的是 `source/_posts/` 中的 Markdown，而不是 `public/` 中的 HTML。
2. 文件已经保存。
3. Hexo 构建没有报错。
4. 新版内容已经提交并推送到 GitHub。
5. GitHub Pages 正在读取包含新版网页的正确来源。
6. 浏览器没有显示旧缓存。

### `pnpm run build` 出现 `ERR_PNPM_IGNORED_BUILDS`

这是 pnpm 对依赖构建脚本的安全限制，不等于 `_config.yml` 写错。审查被拦截的依赖后，可以使用：

```bash
pnpm approve-builds
```

在当前已安装依赖的环境中，也可以直接验证 Hexo：

```bash
./node_modules/.bin/hexo clean
./node_modules/.bin/hexo generate
```

### 为什么不能给 `package.json` 添加中文注释

`package.json` 使用严格 JSON 格式，JSON 语法不支持注释。直接加入 `//` 或 `#` 会导致包管理器无法解析，因此相关字段统一在本 README 中解释。

### 为什么不提交 `public/`

当前 `.gitignore` 把 `public/` 视为可重复生成的构建产物。后续如果选择“直接从仓库目录发布”的 GitHub Pages 方案，需要同步调整输出目录和 `.gitignore`；如果使用 GitHub Actions，则可以保持由自动任务生成并部署构建产物。

## 维护原则

- 文章内容只修改 `source/`，不要长期修改 `public/`。
- 网站级配置修改 `_config.yml`。
- 当前主题配置修改 `_config.butterfly.yml`。
- 依赖通过 pnpm 命令维护，不手动修改 `pnpm-lock.yaml`。
- 不修改 `node_modules/` 中的第三方代码。
- 所有代码注释使用简体中文。
- 每次修改后先本地预览，再构建、提交和发布。
- 不在代码、文档或 Git 历史中保存密码、Token、Cookie 等敏感信息。

## 参考资料

- [Hexo 官方文档](https://hexo.io/docs/)
- [Hexo 配置说明](https://hexo.io/docs/configuration)
- [Hexo 写作说明](https://hexo.io/docs/writing)
- [GitHub Pages 文档](https://docs.github.com/pages)
- [不蒜子官网](https://www.busuanzi.cc/)
- [pnpm 官方文档](https://pnpm.io/)
