# 🚀 三种快速部署方案对比

您遇到的 `bundle` 命令错误意味着系统缺少 Ruby 环境。下面是三种快速解决方案。

---

## 📊 方案对比表

| 方案                              | 难度        | 时间    | 本地预览 | 推荐            |
| --------------------------------- | ----------- | ------- | -------- | --------------- |
| **方案 A：GitHub Pages 自动部署** | ⭐ 最简单   | 5 分钟  | ❌ 否    | ✅ 推荐初学者   |
| **方案 B：安装 Ruby 环境**        | ⭐⭐ 中等   | 20 分钟 | ✅ 是    | ✅ 推荐开发者   |
| **方案 C：使用 Docker 容器**      | ⭐⭐⭐ 较难 | 10 分钟 | ✅ 是    | ✅ 推荐高级用户 |

---

## 🎯 方案 A：GitHub Pages 自动部署（推荐新手）

**优势**：

- ✅ 无需安装任何工具
- ✅ 只需 5 分钟设置
- ✅ 自动部署和更新
- ✅ 完全免费

**劣势**：

- ❌ 无法在本地实时预览
- ❌ 每次推送需等待 1-2 分钟

### 快速步骤

**1. 检查是否有 Gemfile（已有）**

```powershell
ls e:\academic-homepage\Gemfile
```

**2. 初始化 Git（如果还没有）**

```powershell
cd e:\academic-homepage
git init
git add .
git commit -m "Initial academic homepage"
```

**3. 推送到 GitHub**

假设您已有 `academic-homepage` 仓库：

```powershell
git remote add origin https://github.com/BigdogManLuo/academic-homepage.git
git branch -M main
git push -u origin main
```

**4. 在 GitHub 启用 Pages**

- 打开 GitHub 仓库页面
- 进入 **Settings** → **Pages**
- Source 选择 **main** 分支
- 点击 **Save**

**5. 等待部署完成**

网站会自动生成，通常 1-2 分钟后：

```
https://BigdogManLuo.github.io/academic-homepage/
```

**就这么简单！** 🎉

---

## 🔧 方案 B：安装 Ruby 环境（推荐开发者）

**优势**：

- ✅ 本地实时预览更改
- ✅ 快速开发和测试
- ✅ 完整的开发环境
- ✅ 便于调试

**劣势**：

- ❌ 需要安装 Ruby（~500MB）
- ❌ 首次安装较复杂

### 快速步骤

**1. 下载 Ruby**

访问：https://rubyinstaller.org/downloads/

下载 **Ruby+Devkit 3.2.x**（Windows x64）

**2. 安装 Ruby**

- 双击运行安装程序
- 选择 **Add Ruby executables to your PATH**（勾选）
- 安装完成后，会有提示安装 MSYS2
- 按 1 或按 Enter 安装开发工具

**3. 重启电脑**

安装完成后**必须重启**。

**4. 验证安装**

打开新的 PowerShell：

```powershell
ruby --version
gem --version
```

**5. 进入项目目录安装依赖**

```powershell
cd e:\academic-homepage
bundle install
```

**6. 启动本地服务器**

```powershell
bundle exec jekyll serve
```

**7. 打开浏览器**

访问：http://localhost:4000/academic-homepage/

**每次修改文件后会自动重新生成！** ✨

---

## 🐳 方案 C：使用 Docker 容器（推荐高级用户）

**优势**：

- ✅ 无需安装 Ruby
- ✅ 完全隔离的环境
- ✅ 在任何系统上一致
- ✅ 便于团队协作

**劣势**：

- ❌ 需要安装 Docker Desktop（~2GB）
- ❌ 首次运行速度较慢

### 快速步骤

**1. 安装 Docker Desktop**

下载：https://www.docker.com/products/docker-desktop

按默认选项安装，安装完成后重启。

**2. 验证 Docker 安装**

```powershell
docker --version
```

**3. 进入项目目录**

```powershell
cd e:\academic-homepage
```

**4. 创建 Docker Compose 文件（可选）**

在项目根目录创建 `docker-compose.yml`：

```yaml
version: "3"
services:
  jekyll:
    image: jekyll/jekyll:latest
    command: jekyll serve --host 0.0.0.0
    ports:
      - "4000:4000"
    volumes:
      - .:/srv/jekyll
    environment:
      - JEKYLL_ENV=development
```

**5. 运行容器**

```powershell
docker-compose up
```

或者一行命令：

```powershell
docker run --rm -v ${PWD}:/srv/jekyll -p 4000:4000 jekyll/jekyll:latest jekyll serve --host 0.0.0.0
```

**6. 打开浏览器**

访问：http://localhost:4000/

---

## ❓ 我应该选择哪个方案？

### 选择方案 A 如果您：

- 只想快速发布网站
- 不需要在本地预览
- 想要最简单的部署方式
- 是初学者

### 选择方案 B 如果您：

- 想在本地快速测试
- 经常修改网站内容
- 想学习 Jekyll
- 有一些技术背景

### 选择方案 C 如果您：

- 已有 Docker 环境
- 想要一致的开发环境
- 团队协作开发
- 不想污染系统环境

---

## 🎯 我的最终建议

### 对于您的情况（初次搭建）：

**推荐：方案 A + 方案 B**

1. **立即做**：使用**方案 A**推送到 GitHub Pages

   - 只需 5 分钟
   - 网站立即可见
   - 无需任何工具

2. **后续做**：有空时安装**方案 B** Ruby 环境
   - 便于后续修改和调试
   - 更好的开发体验

---

## ✅ 立即执行（方案 A）

如果您现在就要部署，只需这 4 条命令：

```powershell
cd e:\academic-homepage
git init
git add .
git commit -m "Initial academic homepage"
git push origin main
```

然后在 GitHub Settings > Pages 启用 Pages，完成！

---

## 📞 需要帮助？

- **Ruby 安装问题？** → 查看 `ENVIRONMENT_SETUP.md`
- **Git 问题？** → 查看 Git 官方文档
- **网站内容问题？** → 查看 `QUICK_START.md`
- **自定义问题？** → 查看 `WEBSITE_SETUP_GUIDE.md`

---

**选择方案 A（GitHub Pages）只需 5 分钟！** ⏱️

最后更新：2025 年 12 月 10 日
