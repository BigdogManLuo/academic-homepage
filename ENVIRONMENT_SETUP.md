# 本地开发环境配置指南

## 问题

运行 `bundle install` 时出现错误：

```
'bundle' 不是内部或外部命令
```

这表示系统还没有安装 Ruby 和 Bundler。

---

## 解决方案

### 方法 1：安装 Ruby + Bundler（推荐）

#### Windows 用户

**第 1 步：下载并安装 Ruby**

1. 访问 https://rubyinstaller.org/downloads/
2. 下载 **Ruby+Devkit 版本**（推荐 3.2.x 或更新版本）
3. 运行安装程序，按默认选项安装
4. 在安装最后，勾选 "Run 'ridk install'" 来安装开发工具包
5. 完成后重启系统

**第 2 步：验证 Ruby 安装**

打开 PowerShell 并运行：

```powershell
ruby --version
gem --version
```

应该看到版本信息，如：

```
ruby 3.2.0 (2022-12-25 revision a528908271) [x64-mingw32]
gem 3.4.3
```

**第 3 步：安装 Bundler**

```powershell
gem install bundler
```

**第 4 步：验证 Bundler**

```powershell
bundle --version
```

---

### 方法 2：使用 Windows Subsystem for Linux (WSL2)（高级用户）

如果您已安装 WSL2 和 Ubuntu，可以在 Linux 中安装：

```bash
sudo apt-get update
sudo apt-get install ruby-full build-essential
gem install bundler
```

---

### 方法 3：使用 Docker（容器化方案）

如果您已安装 Docker Desktop，可以使用容器：

```powershell
# 进入项目目录
cd e:\academic-homepage

# 使用 Docker 构建
docker run --rm -v ${PWD}:/site -w /site ruby:3.2 bash -c "bundle install && bundle exec jekyll serve --host 0.0.0.0"
```

---

## 完整的快速开始流程

### 假设您已安装 Ruby 和 Bundler

**第 1 步：进入项目目录**

```powershell
cd e:\academic-homepage
```

**第 2 步：安装依赖**

```powershell
bundle install
```

这会安装 Gemfile 中列出的所有包（Jekyll、Minimal Light 主题等）。

**第 3 步：本地运行网站**

```powershell
bundle exec jekyll serve
```

输出示例：

```
Configuration file: e:\academic-homepage\_config.yml
            Source: e:\academic-homepage
       Destination: e:\academic-homepage\_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 1.234 seconds.
 Auto-regeneration: enabled for 'e:\academic-homepage'
    Server address: http://127.0.0.1:4000
  Server running...
  Press Ctrl-C to stop.
```

**第 4 步：在浏览器中打开**

访问：**http://localhost:4000/academic-homepage/**

---

## 如果 Bundler 安装有问题

### 错误：无法访问 gem 源

**解决方案**：使用国内镜像源

```powershell
# 配置国内镜像（清华大学）
bundle config set mirror.https://rubygems.org https://mirrors.tuna.tsinghua.edu.cn/rubygems

# 然后重新安装
bundle install
```

### 错误：缺少开发工具

**解决方案**（Windows）：

```powershell
# 安装 MSYS2 开发工具
ridk install
```

然后选择选项 3（MSYS2 and MINGW development toolchain）。

---

## 不安装本地开发环境的替代方案

如果您**不想在本地安装 Ruby**，可以考虑以下方案：

### 方案 A：直接推送到 GitHub 让 GitHub Pages 自动构建

1. 将代码推送到 GitHub：

   ```powershell
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. 在 GitHub 仓库设置中启用 GitHub Pages
3. 网站会自动构建并发布（不需要本地 Jekyll）
4. 访问：`https://你的用户名.github.io/academic-homepage/`

**优点**：

- 无需安装任何工具
- 自动构建和部署
- 简单快捷

**缺点**：

- 无法在本地实时预览
- 每次推送后需等待 1-2 分钟才能看到更新

### 方案 B：使用在线 Markdown 编辑器

直接在 GitHub 网页上编辑 Markdown 文件，无需本地工具。

---

## 我的建议

根据您的需求选择：

| 场景                         | 推荐方案                      |
| ---------------------------- | ----------------------------- |
| 我想在本地快速测试和预览     | 安装 Ruby + Bundler（方法 1） |
| 我只是想修改内容，不在乎预览 | 直接推送到 GitHub（方案 A）   |
| 我已有 Docker 环境           | 使用 Docker（方法 3）         |
| 我的 Ruby 环境有问题         | 检查国内镜像源                |

---

## ✅ 快速检查清单

安装完成后，运行这些命令验证：

```powershell
# 检查 Ruby
ruby --version

# 检查 Gem
gem --version

# 检查 Bundler
bundle --version

# 进入项目目录
cd e:\academic-homepage

# 查看 Gemfile（依赖列表）
cat Gemfile

# 安装依赖
bundle install

# 运行 Jekyll
bundle exec jekyll serve
```

---

## 需要帮助？

如果安装时遇到问题，请：

1. **检查 Ruby 是否正确安装**：

   ```powershell
   ruby --version
   ```

2. **检查 gem 源是否可访问**：

   ```powershell
   gem sources
   ```

3. **查看 Bundler 日志**：

   ```powershell
   bundle install --verbose
   ```

4. **清空缓存重新安装**：
   ```powershell
   bundle clean --force
   bundle install
   ```

---

**最后更新**：2025 年 12 月 10 日
