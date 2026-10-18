# 市场脉搏 · Market Pulse（可安装 PWA）

一个五合一的行情看板：布伦特原油、A股恐贪指数、沪深300股权风险溢价、沪深300、COMEX黄金。
本目录是一个 **PWA（渐进式 Web 应用）**：部署到 HTTPS 静态托管后，可以在手机上“添加到主屏幕”，像原生 App 一样全屏打开、有图标。

## 目录结构

```
app/
├─ index.html            主页面（全部样式和逻辑都在这一个文件里）
├─ manifest.webmanifest  应用清单（名称、图标、全屏模式）
├─ sw.js                 Service Worker（缓存应用外壳，行情数据仍走实时接口）
├─ icons/                应用图标（192 / 512 / maskable）
└─ README.md
```

## 如何部署（推荐 GitHub Pages，免费、HTTPS）

1. 注册并登录 GitHub，新建一个仓库（例如 `market-pulse`）。
2. 把本 `app` 目录里的 **全部文件**（`index.html`、`manifest.webmanifest`、`sw.js`、`icons/`）上传到仓库根目录。
3. 打开仓库 `Settings → Pages`：
   - `Source` 选择 `Deploy from a branch`；
   - `Branch` 选择 `main`，目录选 `/ (root)`，点 Save。
4. 几分钟后得到地址：`https://你的用户名.github.io/market-pulse/`。

> 用 GitHub Desktop 或网页端 “Add file → Upload files” 都能完成第 2 步，不需要命令行。

## 手机安装到主屏幕

- **Android（Chrome）**：打开上面的网址 → 右上角菜单 → “添加到主屏幕 / 安装应用”。
- **iPhone（Safari）**：打开网址 → 底部“分享”按钮 → “添加到主屏幕”。

安装后点图标就是全屏 App。行情数据来自公开接口，需要联网；应用外壳会缓存，离线也能打开页面框架（数据会显示为快照或等待连接）。

## 本地预览

```
python -m http.server 8000 --bind 0.0.0.0
```

手机和电脑在同一 Wi-Fi 时，用 `http://电脑IP:8000/` 访问（注意：本地 HTTP 无法触发“安装到主屏幕”，部署到 GitHub Pages 后才有完整 PWA 安装能力）。

## 数据与免责声明

行情来自腾讯财经、新浪财经等公开接口；情绪指数来自百分位（baifenwei.com）；股权风险溢价来自 QuantPal（quantpal.cn）；“今日一句”来自《高性价比人生指南》（cdyforever.github.io/how-to-live-better）。页面仅供研究参考，不构成投资、医疗或法律建议。
