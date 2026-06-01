# Tangent Page

基于 [KZHomePage](https://github.com/kaygb/KZHomePage) 修改的个人主页，部署为 [sixingwang2025.github.io](https://sixingwang2025.github.io) 的 `/page` 子路径。

## 目录结构

```
Tangent-page/
├── index.html              # 页面主体，个性化内容都在这里改
├── static/
│   ├── bootstrap.min.css   # Bootstrap 4 样式（本地化）
│   ├── style.css           # 页面自定义样式（卡片、按钮、响应式等）
│   ├── fonts.css           # 扩展字体定义（Dancing Script + Noto Serif SC）
│   ├── APlayer-1.10.1/     # 音乐播放器（APlayer + Meting）
│   ├── fontawesome-6.4.0/  # Font Awesome 6.4 图标库（本地化）
│   ├── layer-v3.5.1/       # Layer 弹窗组件
│   ├── main.js             # 页面交互逻辑（按钮导航、一言、播放器初始化）
│   ├── Meting.min.js       # Meting 音乐 API 桥接
│   ├── images/             # 背景图 fbg.jpg、bg.jpeg
│   └── video/              # 背景视频 lty.mp4
└── .github/workflows/      # CI 自动部署
```

## 自定义指南

### 修改个人信息

编辑 `index.html`：

| 位置 | 说明 |
|------|------|
| `<title>` | 浏览器标签页标题 |
| `<meta name="description">` | SEO 描述 |
| `<h1>` | 页面大标题（名字） |
| `<p>` 在 `<h1>` 下方 | 个人简介文字 |
| `.social` 里的 `<li>` | 社交图标链接 |
| `<footer>` | 页脚内容 |

### 修改导航按钮

每个按钮的关键属性：

```html
<button data-href="链接地址"
        data-title="弹窗标题"
        data-window="newtab"   <!-- pop=弹窗 / newtab=新标签页 / current=当前页 -->
        class="kz-nav-btn btn btn-primary col-lg-4">按钮文字</button>
```

### 修改音乐

在 `<head>` 的 `<script>` 块中修改这些变量：

```js
let music_server = "netease";   // netease / kugou / qq
let music_type   = "playlist";  // playlist / song / album
let music_id     = "8362718673";
```

### 关于 fonts.css

`fonts.css` 定义了两种可选字体：

- **Dancing Script** — 英文手写体，适合标题装饰
- **Noto Serif SC** — 中文宋体，适合正文排版

⚠️ **当前这两种字体并未在页面中实际使用。** 如需启用，在 `style.css` 或 `<style>` 中添加：

```css
h1 { font-family: 'Dancing Script', cursive; }
body { font-family: 'Noto Serif SC', serif; }
```

字体文件本身仍从 Google Fonts (`fonts.gstatic.com`) 加载，`fonts.css` 仅做声明。不需要这两种字体的话可以删除 `fonts.css` 并在 `index.html` 中移除对应的 `<link>`。

## 本地预览

直接用浏览器打开 `index.html` 即可，无需构建工具。或者用任意静态文件服务器：

```bash
python3 -m http.server 8080
# 然后访问 http://localhost:8080
```

## 部署

推送到 `main` 分支 → GitHub Actions 将根目录内容部署到 `gh-pages` 分支 → 触发主仓库 `SixingWang2025.github.io` 拉取到 `/page` 路径并部署到 GitHub Pages。
