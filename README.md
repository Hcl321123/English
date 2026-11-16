# 大学英语四级作文 · 好词好句背诵手册（GitHub Pages 版）

单文件静态站点，零外部依赖，直接在手机 / 微信内置浏览器中打开。

## 内容

- 第一模块：6 类通用功能句型 × 5 句 = 30 句（先搭框架）
- 第二模块：7 类高频话题 ×（10 个核心好词 + 5 个高分好句）= 70 词 + 35 句（再填内容）
- 每条好句统一为「原句 / 中文翻译 / 句式·模板」三项，模板挖空可直接套用
- 吸顶导航（10 个入口）、锚点翻页、回到顶部、浅色/深色自适应

## 文件说明

| 文件 | 作用 |
| --- | --- |
| `index.html` | 站点唯一页面，内容与样式脚本全部内联，46 KB 左右 |
| `.nojekyll` | 空文件，要求 GitHub Pages 跳过 Jekyll 构建（保留隐藏文件、加快部署） |

> 上传时注意：`.nojekyll` 以点开头，网页端上传需要手动勾选「显示隐藏文件」，或用命令行 `git add -A` 才能带上。少了它站点也能打开，只是会多走一遍 Jekyll 构建。

## 发布方式一：网页上传（不用装 git）

1. 新建仓库：<https://github.com/new> → 名称填 `cet4-handbook` → 可见性选 **Public** → Create
2. 进入仓库 → **Add file → Upload files** → 把本目录的 `index.html`、`.nojekyll` 一起拖进去 → Commit changes
3. 仓库 **Settings → Pages** → Source 选 **Deploy from a branch** → Branch 选 `main`、目录选 `/ (root)` → Save
4. 等 1～2 分钟刷新该页面，顶部会显示站点地址：

```
https://<你的用户名>.github.io/cet4-handbook/
```

## 发布方式二：命令行

```bash
# 首次使用需配置提交身份（只需一次）
git config --global user.name  "你的名字"
git config --global user.email "你的邮箱"

cd github-pages
git init -b main
git add -A
git commit -m "feat: CET-4 作文好词好句背诵手册"
git remote add origin https://github.com/<你的用户名>/cet4-handbook.git
git push -u origin main
```

推送需要凭据：推荐用 [Personal Access Token](https://github.com/settings/tokens)（勾 `repo` 权限）当密码，或让 Git Credential Manager 弹窗登录。

推送完成后，同样到 **Settings → Pages** 选择 `main` / `/ (root)` 并保存。

## 发布后建议补两处

1. **canonical 地址**：`index.html` 第 20 行附近有一行被注释掉的

   ```html
   <!-- <link rel="canonical" href="https://<用户名>.github.io/<仓库名>/"> -->
   ```

   把尖括号换成真实地址并去掉注释，有利于搜索引擎识别正式页面。

2. **分享预览**：`og:title` / `og:description` 已填好；若想要缩略图，再加一张 1200×630 的图片到仓库，并补一行
   `<meta property="og:image" content="./cover.png">`。

## 深链可以直接分享

锚点跳转全部在前端完成，带 hash 的地址可以单独发出去，打开即定位：

```
https://<你的用户名>.github.io/cet4-handbook/#t6      → 生活方式
https://<你的用户名>.github.io/cet4-handbook/#m2      → 功能句型
https://<你的用户名>.github.io/cet4-handbook/#resources → 学习资源
```

## 关于访问稳定性（如实说明）

- `*.github.io` 在中国大陆的连通性不稳定，实测经常出现间歇性打不开或很慢；**微信里点开可能白屏或转圈**，这不是页面本身的问题。
- 如果主要给国内同学用，建议二选一作为主入口：
  - **Cloudflare Pages** / **Vercel**：免费、同样支持直接拖文件夹部署，国内连通性通常好于 github.io
  - **Gitee Pages**：国内速度快，但需要实名认证，且 Pages 服务对仓库内容有审核，公开前需确认其当前政策
- GitHub Pages 强制 HTTPS，且不支持服务端重定向，因此本目录没有放 `404.html`——单页站点用不到，放了反而容易在「用户页 / 项目页」两种路径下算错地址。

## 可选：同时提供 Word / PDF 下载

把 `../stage3/大学英语四级作文好词好句背诵手册.docx` 与 `.pdf` 复制进本目录并改成英文名（如 `cet4-handbook.docx`），再在 `index.html` 里加一段下载链接即可。中文文件名在 URL 中会被百分号编码，能用但不利于长按复制。
