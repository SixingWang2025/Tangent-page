# Tangent Page

个人主页，基于 [KZHomePage](https://github.com/kaygb/KZHomePage) 修改，上线地址：[**sixingwang2025.github.io/page/**](https://sixingwang2025.github.io/page/) 。

## 功能特性

- 🎯 导航按钮（新标签页 / 弹窗 / 当前页三种打开方式）
- 🎵 APlayer + Meting 音乐播放器（支持网易云、QQ、酷狗）
- 💬 一言 API 随机句子
- 🎨 Layer 弹窗组件
- 📱 Bootstrap 4 响应式布局

## 目录结构

```
Tangent-page/
├── index.html              # ★ 页面主体
├── static/
│   ├── bootstrap.min.css   # Bootstrap 4（本地化）
│   ├── style.css           # 自定义样式（卡片、按钮、响应式）
│   ├── fonts.css           # 扩展字体声明（Dancing Script + Noto Serif SC）
│   ├── main.js             # 交互逻辑（按钮导航、一言、播放器初始化）
│   ├── Meting.min.js       # Meting 音乐 API 桥接
│   ├── layer.js            # Layer 弹窗
│   ├── APlayer-1.10.1/     # 音乐播放器
│   ├── fontawesome-6.4.0/  # Font Awesome 6.4 图标库
│   ├── layer-v3.5.1/       # Layer 弹窗样式
│   ├── images/             # 背景图（fbg.jpg、bg.jpeg）
│   └── video/              # 背景视频（lty.mp4）
└── .github/workflows/      # CI 自动部署
```

## 自定义指南

### 个人信息

编辑 `index.html`：

| 位置 | 内容 |
|------|------|
| `<title>` | 浏览器标签页标题 |
| `<meta name="description">` | SEO 描述 |
| `<h1>` | 你的名字 |
| `<h1>` 下方 `<p>` | 个人简介 |
| `.social` 的 `<li>` | 社交图标链接 |
| `<footer>` | 页脚 |

### 导航按钮

```html
<button data-href="链接地址"
        data-title="弹窗标题"
        data-window="newtab"   <!-- pop/弹窗  newtab/新标签  current/当前页 -->
        class="kz-nav-btn btn btn-primary col-lg-4">
    按钮文字
</button>
```

### 音乐播放器

在 `<head>` 的 `<script>` 块中修改：

```js
let music_server = "netease";   // netease / kugou / qq
let music_type   = "playlist";  // playlist / song / album
let music_id     = "8362718673";
```

### 自定义字体

`fonts.css` 声明了两种字体（当前未实际使用）：

- **Dancing Script** — 英文手写体
- **Noto Serif SC** — 中文宋体

如需启用，在 `style.css` 中指定：

```css
h1 { font-family: 'Dancing Script', cursive; }
body { font-family: 'Noto Serif SC', serif; }
```

## 本地预览

直接浏览器打开 `index.html`，或用静态服务器：

```bash
python3 -m http.server 8080
# 访问 http://localhost:8080
```

## 部署

推送 `main` → GitHub Actions 部署到 `gh-pages` 分支 → 主仓库 `SixingWang2025.github.io` 拉取到 `/page/`。
