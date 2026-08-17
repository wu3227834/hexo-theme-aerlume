# Hexo-Theme-AirCloud

一个简洁轻量的 Hexo 博客主题，专注于阅读体验。

## ✨ 特性

- 🎨 **极简设计** — 卡片式文章列表、圆角代码块、细腻的交互动效
- 📱 **响应式布局** — 桌面/平板/手机自适应，侧边栏可收起
- 🔍 **全局搜索** — 支持关键词搜索与高亮
- 📑 **文章目录** — 自动生成 TOC，阅读进度追踪
- 💬 **评论系统** — 支持 Giscus / Gitment / Disqus / Livere
- 📊 **访问统计** — PV / UV 统计 + 第三方分析（Google / Baidu / Cloudflare 等）
- 🌙 **代码高亮** — Prism.js 支持，一键复制 / 查看源码
- 🔤 **离线字体** — 本地字体文件加载，`font-display` 可配置，无外部字体服务依赖
- ⚡ **性能优化** — 零 jQuery 依赖，CSS/JS 按需加载，资源预连接

## 🚀 快速开始

### 1. 安装

```bash
# 克隆到 themes 目录
cd your-hexo-site/themes
git clone https://github.com/aircloud/hexo-theme-aircloud.git my-aircloud

# 安装搜索插件（可选，用于全局搜索）
cd ../
npm i hexo-generator-search --save
```

### 2. 启用主题

修改 Hexo 根目录的 `_config.yml`：

```yaml
theme: my-aircloud

# 搜索配置
search:
  path: search.json
  field: post
```

### 3. 创建必要页面

```bash
hexo new page tags
hexo new page about
```

然后分别修改：

**tags/index.md**
```yaml
---
layout: "tags"
title: "Tags"
---
```

**about/index.md**
```yaml
---
layout: "about"
title: "About"
date: 2024-01-01 00:00:00
comments: true
---
```

## ⚙️ 配置

### 基础配置

```yaml
# 语言（需匹配主题 languages/ 下的文件名：zh / en / ko）
language: zh

# 日期格式
date_format: YYYY-MM-DD

# 作者名（显示在侧边栏）
author: Your Name

# 副标题（显示在首页顶部）
subtitle: Welcome to my blog

# 头像（放在 source/img/ 下）
sidebar-avatar: avatar.png

# 头像样式
avatar_style:
  radius: true
```

### 离线字体

将字体文件（支持 woff / woff2 / ttf / otf）放入 `source/fonts/` 后配置：

```yaml
font:
  family: AirCloud Local   # @font-face 的 font-family 名称
  file: auto               # auto = 自动加载目录下第一个字体文件，也可指定文件名
  weight: 400              # 字体粗细
  style: normal            # 字体样式（normal / italic / oblique）
  display: swap            # 显示模式（auto / block / fallback / optional / swap）
```

主题通过 `scripts/local-font.js` 生成 `@font-face`，并以 CSS 变量 `--aircloud-local-font` 应用到全站正文。

### 社交链接

```yaml
# GitHub - 点击头像跳转
github_username: your-github

# 以下显示在底部社交栏
twitter_username: your-twitter
zhihu_username: your-zhihu
weibo_username: your-weibo
facebook_username: your-facebook
linkedin_username: your-linkedin
```

> 不想显示某个平台，直接删除或注释掉对应行即可。

### 友情链接

```yaml
friends:
  - title: "友链名称"
    href: "https://example.com"
  - title: "另一个友链"
    href: "https://example2.com"
```

### 评论系统

主题内置 giscus 评论支持。在 [giscus.app](https://giscus.app) 获取配置后：

```yaml
comment:
  type: giscus
  script: |
      <script src="https://giscus.app/client.js"
          data-repo="your-name/your-repo"
          data-repo-id="..."
          data-category="General"
          data-category-id="..."
          data-mapping="title"
          data-reactions-enabled="1"
          data-emit-metadata="0"
          data-input-position="bottom"
          data-theme="light"
          data-lang="zh-CN"
          crossorigin="anonymous"
          async>
      </script>
```

### 站点分析

```yaml
analytics:
  google:
    gtag_id: 'G-XXXXXXXXXX'
  baidu:
    id: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
  cloudflare:
    token: 'your-cloudflare-token'
  umami:
    host: 'https://cloud.umami.is'
    id: 'your-website-id'
```

### 代码风格

```yaml
# 首行缩进（默认开启，设为 0 关闭）
post_style:
  indent: 1
```

### 赞赏功能

```yaml
donate:
  img: img/donate.jpg
  content: 感谢鼓励
```

## 📁 目录结构

```
my-aircloud/
├── languages/             # i18n 语言文件（zh / en / ko）
├── scripts/
│   └── local-font.js      # 离线字体 helper
├── layout/
│   ├── index.ejs          # 首页文章列表
│   ├── post.ejs           # 文章详情页
│   ├── page.ejs           # 普通页面
│   ├── tags.ejs           # 标签聚合页
│   ├── archive.ejs        # 归档页
│   ├── about.ejs          # 关于页
│   ├── 404.ejs            # 404 页面
│   └── _partial/
│       ├── head.ejs       # <head> 标签
│       ├── footer.ejs     # 底部区域
│       ├── nav.ejs        # 侧边导航与搜索
│       ├── toc.ejs        # 文章目录
│       ├── donate.ejs     # 赞赏按钮
│       └── analytics.ejs  # 统计脚本
└── source/
    ├── css/               # aircloud.less 为编译入口，aircloud.css 为编译产物
    ├── fonts/             # 离线字体目录
    ├── js/                # 脚本文件
    │   └── lightbox.js    # 原生图片灯箱
    └── _less/             # Less 源文件
        ├── common.less    # 全局基础样式
        ├── layout.less    # 布局样式
        ├── index.less     # 首页样式
        ├── nav.less       # 导航样式
        ├── post.less      # 文章页样式
        ├── tag.less       # 标签页样式
        ├── toc.less       # 目录样式
        ├── hightlight.less# 代码高亮样式
        └── _partial/
            └── footer.less# 底部样式
```

## 🎨 自定义

### 修改主色调

编辑 `source/_less/variables.less`：

```less
@link-color: #4990E2;  // 链接、hover 主色
```

### 重新编译样式

```bash
# 在主题根目录下执行
npx lessc source/css/aircloud.less source/css/aircloud.css
```

## 📝 注意事项

- 文章不要跳级使用标题（如 h3 下直接 h5），否则目录可能异常
- 代码块自动启用行号和复制按钮，无需额外配置
- 侧边栏默认收起，点击左上角按钮可展开，状态会被记住
- 图片点击放大为原生实现（`js/lightbox.js`），无第三方依赖；主题配置或文章 front-matter 中设置 `fancybox: false` 可关闭

## 许可

MIT
