# GitHub Pages 部署指南（中文）

## 部署到 `https://zheng977.github.io/MutiAgent4Fraud/`

### 前置条件
- 已安装 Node.js 24 或更高版本
- 已安装 Git
- 拥有 GitHub 账号
- 已有 `zheng977.github.io` 仓库

### 当前配置
- **部署路径**: `https://zheng977.github.io/MutiAgent4Fraud/`
- **Base 路径**: `/MutiAgent4Fraud/`（已在 `astro.config.ts` 中配置）

### 方式一：将项目复制到 zheng977.github.io 仓库（推荐）

如果你希望将项目作为 `zheng977.github.io` 仓库的一部分：

1. **将项目文件复制到 zheng977.github.io 仓库**
   ```bash
   # 假设你在 academic-project-astro-template 目录
   cd ..
   git clone https://github.com/zheng977/zheng977.github.io.git
   # 或者如果已经克隆，直接进入目录
   cd zheng977.github.io
   
   # 复制项目文件到 MutiAgent4Fraud 目录
   cp -r ../academic-project-astro-template ./MutiAgent4Fraud
   ```

2. **更新 GitHub Actions 工作流**
   
   在 `zheng977.github.io/.github/workflows/` 目录下创建或更新工作流文件，参考现有的 `deploy-mutiagent4fraud.yml` 配置。

3. **提交并推送**
   ```bash
   cd zheng977.github.io
   git add .
   git commit -m "添加 MutiAgent4Fraud 项目页面"
   git push
   ```

### 方式二：作为独立仓库部署

如果你想保持项目独立，但部署到子路径：

1. **确保 astro.config.ts 配置正确**
   ```typescript
   site: 'https://zheng977.github.io',
   base: '/MutiAgent4Fraud/',
   ```

2. **配置 GitHub Pages**
   - 在项目仓库的 Settings > Pages
   - Source 选择：**GitHub Actions**
   - 部署后访问：`https://zheng977.github.io/MutiAgent4Fraud/`

3. **提交并推送代码**
   ```bash
   git add .
   git commit -m "配置部署到 /MutiAgent4Fraud/ 路径"
   git push
   ```

### 步骤：启用 GitHub Pages

1. 在 GitHub 仓库页面，点击 **Settings**（设置）标签
2. 在左侧侧边栏找到 **Pages**（在 "Code and automation" 部分下）
3. 在 **Build and deployment**（构建与部署）部分：
   - **Source**（来源）选择：**GitHub Actions**
4. 保存设置

### 等待自动部署

- GitHub Actions 会自动开始构建和部署
- 你可以在仓库的 **Actions** 标签页查看部署进度
- 部署完成后，你的网站将在 `https://zheng977.github.io/MutiAgent4Fraud/` 上线
- 通常需要 1-3 分钟完成首次部署

### 后续更新

每次你修改代码并推送到 `main` 分支时，GitHub Actions 会自动重新构建和部署：

```bash
git add .
git commit -m "更新内容"
git push
```

---

## 常见问题

### 部署失败怎么办？

1. 检查 **Actions** 标签页中的错误信息
2. 确保 Node.js 版本兼容（GitHub Actions 使用 Node 20）
3. 检查 `astro.config.ts` 中的 `base` 路径是否正确

### 网站显示 404？

- 首次部署可能需要等待几分钟
- 检查 GitHub Pages 设置中的 Source 是否选择了 "GitHub Actions"
- 确认仓库是 Public（公开）的

### 如何查看部署日志？

在仓库的 **Actions** 标签页中，点击最新的工作流运行，可以查看详细的构建日志。

