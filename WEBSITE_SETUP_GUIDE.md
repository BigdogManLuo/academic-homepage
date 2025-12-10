# 学术网站搭建指南

本文档说明了个性化学术网站的结构和自定义方法。

## 网站结构

网站采用多页面导航结构，包含以下页面：

### 1. **Homepage** (`index.md`)
- **About Me**: 个人简介
- **Research Interests**: 研究兴趣
- **Engineering Skills**: 工程技能
- **Education**: 教育经历（新增）
- **Awards & Honors**: 获奖荣誉

### 2. **Research** (`research.md`)
- **Publications**: 论文发表列表（包含图表摘要、PDF和代码链接）
- **Academic Talks**: 学术报告/会议演讲
- **Research Projects**: 当前研究方向
- **Collaboration Opportunities**: 合作机会

### 3. **Practice** (`practice.md`)
- **Data Science Competitions**: 数据竞赛经历
  - HEFTCom 2024
  - THS Forecasting Hackathon 2025
  - Kaggle 竞赛
- **Open Source Projects**: GitHub 开源项目
  - Wind-ESS Optimization
  - DSP Control Library
  - HEFTCom Implementation
- **Skills & Tools**: 技术栈

### 4. **Blog** (`blog.md`)
- 跳转到博客主页的中转页面

---

## 文件位置和自定义

### 核心文件

```
e:/academic-homepage/
├── index.md                 # 首页内容
├── research.md              # 研究页面内容
├── practice.md              # 实践页面内容
├── blog.md                  # 博客页面内容
├── _config.yml              # 网站配置（个人信息）
├── _layouts/
│   └── homepage.html        # 页面布局（含导航栏）
├── _data/
│   └── publications.yml      # 论文数据（YAML 格式）
├── _includes/
│   └── publications.md       # 论文展示模板
└── assets/
    └── css/
        ├── style.scss       # 样式表（支持深色模式）
        └── style-no-dark-mode.scss  # 样式表（无深色模式）
```

### 配置个人信息 (`_config.yml`)

修改以下字段以个性化您的网站：

```yaml
title: Chuanqing Pu                           # 您的名字
position: Ph.D. Candidate                    # 职位/身份
affiliation: Shanghai Jiao Tong University   # 机构
email: sashabanks@sjtu.edu.cn               # 邮箱

# 社交媒体和专业链接
google_scholar: https://scholar.google.com/...
cv_link: assets/files/curriculum_vitae.pdf
github_link: https://github.com/BigdogManLuo/
linkedin: https://www.linkedin.com/in/...

# 头像和网站图标
avatar: ./assets/img/avatar.jpg
favicon: ./assets/img/favicon.png
favicon_dark: ./assets/img/favicon-dark.png
```

### 添加论文 (`_data/publications.yml`)

编辑 YAML 文件来添加或修改论文信息：

```yaml
main:
  - title: "论文标题"
    authors: <b>Your Name</b>, Co-Author
    conference_short: "期刊缩写"
    conference: "期刊全名"
    pdf: "https://arxiv.org/abs/..."
    code: "https://github.com/..."
    image: "./assets/img/paper-image.png"
    notes: "Accepted"
```

**字段说明：**
- `title`: 论文标题
- `authors`: 作者列表（使用 `<b>Your Name</b>` 加粗自己的名字）
- `conference_short`: 期刊/会议缩写（显示在论文左侧）
- `conference`: 期刊/会议全名
- `pdf`: PDF 或预印本链接
- `code`: 代码仓库链接
- `image`: 图表摘要图像路径
- `notes`: 状态标签（Accepted, Published, Reviewing 等）

---

## 样式定制

### 修改配色

编辑 CSS 文件中的颜色值：

```scss
/* 主要链接颜色 */
color: #0b20e2;

/* 悬停效果 */
&:hover {
  color: #0a1ab5;
}
```

### 修改导航栏

导航栏在 `_layouts/homepage.html` 中定义。修改导航项：

```html
<li>
  <a href="{{ '/your-page.html' | relative_url }}">Your Page</a>
</li>
```

### 支持深色模式

- `style.scss` - 包含深色模式支持（使用 `@media (prefers-color-scheme: dark)` ）
- `style-no-dark-mode.scss` - 无深色模式版本

在 `_config.yml` 中控制深色模式：

```yaml
auto_dark_mode: true   # 启用自动深色模式
```

---

## 内容编辑指南

### 首页 (`index.md`)

修改各个部分的内容：

```markdown
## About Me
您的个人介绍...

## Research Interests
- 研究兴趣1
- 研究兴趣2

## Engineering Skills
您的技能...

## Education
使用 `education-item` 类创建教育经历块...

## Awards & Honors
获奖信息...
```

### 研究页面 (`research.md`)

自动从 `_data/publications.yml` 导入论文列表，手动添加学术报告：

```markdown
### Conference/Event Name

<div class="education-item">
  <h4>演讲标题</h4>
  <p><strong>Event:</strong> ...</p>
  <p><strong>Date:</strong> ...</p>
</div>
```

### 实践页面 (`practice.md`)

添加竞赛和项目信息。使用提供的模板结构。

### 博客页面 (`blog.md`)

修改博客链接：

```markdown
<a href="https://your-blog-url.com/" target="_blank">Visit My Blog</a>
```

---

## 美化建议

### 1. **添加论文图表摘要**
   - 在 `assets/img/` 下存放论文预览图
   - 在 `_data/publications.yml` 中指定 `image` 字段

### 2. **优化排版**
   - 使用适当的间距和缩进
   - 利用 `education-item` 类展示结构化信息
   - 使用 `links` 类显示按钮式链接

### 3. **改进导航**
   - 可以在主页添加快速链接
   - 使用面包屑导航（可选）

### 4. **多语言支持**
   - 创建不同语言的 Markdown 文件（如 `index_zh.md`）
   - 在导航栏中添加语言切换按钮

---

## 本地预览和发布

### 本地运行（需要 Jekyll）

```bash
bundle exec jekyll serve
# 访问 http://localhost:4000
```

### GitHub Pages 发布

1. 推送到 GitHub 仓库
2. 在 Settings > Pages 中启用 GitHub Pages
3. 网站自动生成并发布

---

## 常见问题

### Q: 如何添加新页面？
A: 创建新的 `.md` 文件，设置 `layout: homepage`，添加到导航栏。

### Q: 如何修改导航栏位置？
A: 在 `_layouts/homepage.html` 中查找 `<nav class="nav-menu">` 部分。

### Q: 如何自定义教育经历样式？
A: 修改 `assets/css/style.scss` 中的 `.education-item` 类。

### Q: 可以添加暗黑模式吗？
A: 已经内置支持，通过 `_config.yml` 中的 `auto_dark_mode: true` 启用。

---

## 技术栈

- **静态网站生成器**: Jekyll
- **主题**: Minimal Light
- **标记语言**: Markdown
- **样式**: SCSS
- **托管**: GitHub Pages
- **SEO**: 支持 Google Scholar, Google Analytics

---

## 贡献和反馈

如有任何改进建议，欢迎提交 Issue 或 Pull Request。

---

**最后更新**: 2025年12月10日
