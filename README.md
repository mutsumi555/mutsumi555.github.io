# 站点名称

用 GitHub Pages 托管的静态网站。

## 本地预览

直接双击 `index.html` 用浏览器打开即可，无需安装任何依赖。

## 功能

- 响应式布局，手机 / 平板 / 桌面自适应
- 自动跟随系统的深色 / 浅色模式
- 零依赖、零构建，纯 HTML + CSS + JS

## 需要改的地方

| 文件 | 位置 | 说明 |
|---|---|---|
| `index.html` | `<title>`、`<h1>`、`.subtitle` | 改成你自己的名字和简介 |
| `index.html` | `.avatar` 里的 `FH` | 换成你的姓名缩写，或改成 `<img src="avatar.jpg">` |
| `index.html` | `#about` | 关于我段落、技能标签 |
| `index.html` | `#projects` 三个 `.card` | 换成你真实的项目 |
| `style.css` | `:root { --accent: ... }` | 换主题色 |

## 部署

见仓库根目录的 [DEPLOY.md](DEPLOY.md)。