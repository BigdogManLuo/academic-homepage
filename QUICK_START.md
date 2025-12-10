# 快速开始指南

## 🎯 网站已搭建完成！

您的英文学术网站框架已完全搭建。下面是快速开始步骤。

---

## 📋 立即行动的事项

### 1️⃣ 更新个人信息

编辑 `_config.yml` 文件：

```yaml
title: 您的名字 # 改成您的名字
position: 您的职位 # 如 "Ph.D. Candidate"
affiliation: 您的机构 # 如 "Your University"
email: 您的邮箱 # 联系邮箱

# 重要链接
google_scholar: 您的链接 # Google Scholar profile
cv_link: assets/files/curriculum_vitae.pdf # 简历PDF
github_link: https://github.com/您的用户名/
linkedin: https://www.linkedin.com/in/您的链接/
```

### 2️⃣ 更新头像

将您的个人照片放在 `assets/img/avatar.jpg`

### 3️⃣ 添加论文信息

编辑 `_data/publications.yml`，按以下格式添加论文：

```yaml
main:
  - title: "您的论文标题"
    authors: <b>您的名字</b>, 其他作者
    conference_short: "期刊缩写"
    conference: "期刊或会议全名"
    pdf: "https://arxiv.org/abs/xxxx"
    code: "https://github.com/您的代码"
    image: "./assets/img/your-paper.png"
    notes: "Accepted"
```

### 4️⃣ 更新首页内容

编辑 `index.md` 的以下部分：

- **About Me**: 个人简介
- **Research Interests**: 研究兴趣
- **Engineering Skills**: 技能
- **Education**: 教育经历
- **Awards & Honors**: 获奖

### 5️⃣ 更新研究页面

编辑 `research.md`：

- 论文列表会自动从 `_data/publications.yml` 导入
- 手动添加 "Academic Talks" 部分的报告信息

### 6️⃣ 更新实践页面

编辑 `practice.md`：

- 添加您的竞赛信息
- 添加 GitHub 项目描述

### 7️⃣ 更新博客链接

编辑 `blog.md`：

修改博客链接（目前指向示例博客）：

```markdown
<a href="https://您的博客网址/" target="_blank">
  Visit My Blog
</a>
```

---

## 🎨 网站结构

```
导航栏：
├── Homepage      → 首页（个人简介、教育、获奖）
├── Research      → 研究（论文、学术报告）
├── Practice      → 实践（竞赛、开源项目）
└── Blog          → 博客（外链）
```

---

## 🔧 自定义样式

所有样式都在 `assets/css/` 目录：

- `style.scss` - 主样式（支持深色模式）
- `style-no-dark-mode.scss` - 无深色模式

修改这些文件来改变：

- 颜色配置
- 字体
- 间距
- 导航栏样式

---

## 📂 文件快速参考

| 文件                                | 用途         | 优先级  |
| ----------------------------------- | ------------ | ------- |
| `_config.yml`                       | 个人信息配置 | 🔴 必改 |
| `index.md`                          | 首页内容     | 🔴 必改 |
| `_data/publications.yml`            | 论文列表     | 🔴 必改 |
| `assets/img/avatar.jpg`             | 头像         | 🔴 必改 |
| `research.md`                       | 研究页面     | 🟡 应改 |
| `practice.md`                       | 实践页面     | 🟡 应改 |
| `blog.md`                           | 博客链接     | 🟡 应改 |
| `assets/files/curriculum_vitae.pdf` | 简历         | 🟡 应改 |

---

## 🚀 部署方案

网站部署有多种方式，根据您的情况选择：

### 🟢 **方案 1：GitHub Pages 自动部署（推荐）**

最简单快速的方式，只需 5 分钟：

```powershell
cd e:\academic-homepage
git add .
git commit -m "Initial commit"
git push origin main
```

然后在 GitHub > Settings > Pages 启用，网站自动发布！

✅ **优点**：无需安装任何工具，自动部署  
❌ **缺点**：无法本地实时预览

👉 **[查看详细说明 →](./DEPLOYMENT_OPTIONS.md#-方案-agithub-pages-自动部署推荐新手)**

---

### 🟡 **方案 2：本地 Jekyll 预览**

需要安装 Ruby（~20 分钟）：

```powershell
# 1. 安装 Ruby（从 https://rubyinstaller.org/ 下载）
# 2. 重启电脑
# 3. 运行以下命令：

cd e:\academic-homepage
bundle install
bundle exec jekyll serve

# 4. 打开浏览器：http://localhost:4000/academic-homepage/
```

✅ **优点**：本地实时预览，快速开发  
❌ **缺点**：需要安装 Ruby

👉 **[查看详细说明 →](./DEPLOYMENT_OPTIONS.md#-方案-b安装-ruby-环境推荐开发者)**

---

### 🔵 **方案 3：Docker 容器运行**

适合已有 Docker 环境的用户：

```powershell
docker run --rm -v ${PWD}:/srv/jekyll -p 4000:4000 jekyll/jekyll:latest jekyll serve --host 0.0.0.0
```

✅ **优点**：无需安装 Ruby，环境隔离  
❌ **缺点**：需要安装 Docker

👉 **[查看详细说明 →](./DEPLOYMENT_OPTIONS.md#-方案-c使用-docker-容器推荐高级用户)**

---

### 📋 快速对比

| 方案          | 难度        | 时间    | 本地预览 | 推荐度     |
| ------------- | ----------- | ------- | -------- | ---------- |
| GitHub Pages  | ⭐ 最简单   | 5 分钟  | ❌       | ⭐⭐⭐⭐⭐ |
| Ruby + Jekyll | ⭐⭐ 中等   | 20 分钟 | ✅       | ⭐⭐⭐⭐   |
| Docker        | ⭐⭐⭐ 较难 | 10 分钟 | ✅       | ⭐⭐⭐     |

👉 **[查看三种方案详细对比 →](./DEPLOYMENT_OPTIONS.md)**

---

## ✨ 推荐的美化方案

### 1. 论文展示优化

- 添加论文预览图（位于 `assets/img/papers/`）
- 为每篇论文添加简短描述
- 使用 `image` 字段显示 graphical abstract

### 2. 排版优化

- 使用 Education Item 组件展示教育经历
- 使用 Links 组件展示 PDF/Code 按钮
- 保持各部分间距一致

### 3. 内容补充

- 添加研究项目的详细描述
- 列出主要技能和工具
- 添加合作机会部分

### 4. 互动功能

- 考虑添加邮件订阅
- 添加社交媒体分享按钮
- 考虑添加评论功能（可选）

---

## ❓ 常见问题

**Q: 我需要 HTML 知识吗？**
A: 不需要！所有内容用 Markdown 编写，框架已搭建完毕。

**Q: 如何添加新页面？**
A: 创建新的 `.md` 文件，设置 `layout: homepage`，在 `homepage.html` 导航中添加链接。

**Q: 支持多语言吗？**
A: 支持！复制 `.md` 文件为 `filename_zh.md`，然后在导航栏中添加语言切换链接。

**Q: 如何修改颜色？**
A: 编辑 `assets/css/style.scss`，查找 `#0b20e2`（蓝色）并替换为您喜欢的颜色。

**Q: 可以添加自定义 JavaScript 吗？**
A: 可以。将 JS 文件放在 `assets/js/`，在 `homepage.html` 的 `<script>` 标签中引入。

---

## 📞 需要帮助？

1. 查看 `WEBSITE_SETUP_GUIDE.md` 获取详细文档
2. 检查 Jekyll 官方文档: https://jekyllrb.com/
3. 查看 Minimal Light 主题文档

---

## ✅ 检查清单

在部署前，确保完成以下事项：

- [ ] 更新了 `_config.yml` 中的个人信息
- [ ] 添加了头像图片
- [ ] 填充了论文列表和信息
- [ ] 编辑了首页内容
- [ ] 编辑了研究和实践页面
- [ ] 更新了博客链接
- [ ] 本地测试所有链接
- [ ] 检查了拼写和语法
- [ ] 测试了深色/浅色模式
- [ ] 在 GitHub 上完成部署

---

**祝贺！您的学术网站已准备好展示给世界了！** 🎉

最后更新: 2025 年 12 月 10 日
