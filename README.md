# 房昊成 作品集网站

个人作品集网站，已配置可直接部署到 GitHub Pages 或 Cloudflare Pages。

## 📁 文件结构

```
deploy/
├── index.html          # 主页面
├── 404.html            # SPA路由兜底页（index.html的副本，Cloudflare Pages自动处理）
├── .gitignore
├── README.md           # 本文件
├── assets/
│   ├── index-DOZskezo.js   # React应用主JS
│   └── index-B58ziSA7.css  # 样式表
└── manus-storage/      # 所有图片资源
```

## 🚀 部署方法（推荐 Cloudflare Pages）

### 第1步：上传代码到 GitHub

1. 登录 [GitHub](https://github.com)（无账号先注册）
2. 点击右上角 **+** → **New repository**
3. 填写仓库名称（如 `portfolio-website`），选择 **Public**，点击 **Create repository**
4. 下载并安装 [Git](https://git-scm.com/downloads)
5. 打开 Git Bash，执行：

```bash
cd "deploy文件夹的完整路径"
git init
git add .
git commit -m "初始提交：房昊成作品集网站"
git branch -M main
git remote add origin https://github.com/你的用户名/你的仓库名.git
git push -u origin main
```

或者直接双击 `一键部署到GitHub.bat` 自动完成（脚本在 deploy 文件夹的同级目录）。

### 第2步：在 Cloudflare Pages 部署

1. 打开 [Cloudflare Pages](https://pages.cloudflare.com/)，免费注册
2. 点击 **Create a project** → **Connect to Git**
3. 授权 GitHub，选择刚创建的仓库
4. 部署设置（**关键步骤**）：
   - **Project name**: 你的项目名（决定网址）
   - **Production branch**: `main`
   - **Framework preset**: 选 `None`
   - **Build command**: **留空**
   - **Build output directory**: **/**（斜杠）
5. 点击 **Save and Deploy**
6. 等待 1-2 分钟，部署完成
7. 获得公开网址：`https://你的项目名.pages.dev`

### 第3步：让别人访问

把网址发给任何人，他们就能打开了！

## ❗ 常见问题

### 问题1：部署时上传文件很小（如0.33 KiB）

**原因**：通常是 Git 推送时某些大文件被 Git LFS 限制或 .gitignore 过滤了。
**解决**：检查 .gitignore 文件，不要把 manus-storage/ 目录排除。

### 问题2：_redirects 报错"无限循环"

**原因**：`/* /index.html 200` 会让 `/index.html` 也匹配 `/*` 规则形成死循环。
**解决**：本项目**不使用 _redirects**，改用 404.html 兜底（Cloudflare Pages 原生支持）。

### 问题3：作品详情页打不开

**原因**：SPA 路由需要服务器把所有未匹配路径返回 index.html。
**解决**：本项目已配置 `404.html` 作为兜底，Cloudflare Pages 会自动处理 SPA 路由。

## 🔧 自定义域名（可选）

1. 在 Cloudflare Pages 项目页面，点击 **Custom domains** → **Set up a custom domain**
2. 输入你的域名，按提示配置 DNS
3. 等待 DNS 生效（5-30分钟）

## 📝 后续更新

修改 `assets/index-DOZskezo.js` 中的内容后：
```bash
git add .
git commit -m "更新内容"
git push
```
Cloudflare Pages 会**自动重新部署**。

## ✅ 网站功能

- 中英文双语切换（右上角 EN/中 按钮）
- 首页打字机动画
- 个人简介 + 实习经历 + 工具链
- 5个作品详情页
- 联系方式展示
- 响应式设计
