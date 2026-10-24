# 性格之旅 · GitHub Pages Web 版

一个可直接部署到 GitHub Pages 的 React + Vite 单页网站原型，依据产品需求文档实现：
- 首页与热门目的地卡片
- 15 道性格偏好测试题、进度显示、结果页
- 根据答题偏好生成简化旅行人格与目的地匹配
- 目的地详情与个性化旅行建议
- 收藏夹（保存在当前浏览器 localStorage）
- 响应式布局，适配手机与桌面
- 不需要后端、数据库或 API 密钥

> 说明：人格标签与匹配分数是产品原型的娱乐性参考，不是心理学诊断。当前数据为前端示例数据；收藏只保存在当前浏览器中。

## 本地运行

需要安装 Node.js 18 或更新版本。

```bash
npm install
npm run dev
```

按终端提示打开本地地址。

## 发布到 GitHub Pages

1. 在 GitHub 新建一个仓库，例如 `personality-travel-web`。
2. 解压 ZIP，把里面 `personality-travel-web` 文件夹中的所有内容上传到仓库根目录。仓库根目录应直接看到 `index.html`、`package.json`、`vite.config.js`、`src/` 和 `.github/`；不要把整个项目文件夹再套一层上传，也不要只上传 ZIP。
3. 打开仓库 **Settings → Pages**。
4. 在 **Build and deployment → Source** 中选择 **GitHub Actions**，不要选择 `Deploy from a branch`。
5. 确认工作流文件路径是 `.github/workflows/deploy.yml`，并且仓库默认分支名为 `main`。
6. 点击 **Actions**，打开最新的 `Deploy to GitHub Pages` 工作流，确认 Build 和 Deploy 都成功。成功后从 **Settings → Pages** 打开网站地址。

### 常见问题
- **网页显示 404**：检查 Pages 是否选择 GitHub Actions，并确认部署任务成功。
- **Actions 没有自动运行**：确认你推送到了 `main` 分支；如果默认分支叫 `master`，把 `deploy.yml` 中的 `branches: [main]` 改成 `branches: [master]`。
- **页面空白**：打开 Actions 查看 `Build` 日志；不要用 GitHub 仓库里的 `index.html` 直接预览 React 源码，必须由 Vite 构建并部署 `dist`。

如果你的默认分支不是 `main`，请修改 workflow 中的分支名称。

## 主要目录

```text
src/
  main.jsx       页面、问卷、推荐算法与交互
  styles.css     响应式样式
.github/
  workflows/
    deploy.yml   GitHub Pages 自动部署
```

## 后续升级建议

要上线真实用户系统、云端同步收藏、AI 自动生成攻略或真实旅游数据，需再接入后端/API；不要把私密 API Key 写在前端代码中。
