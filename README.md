<div align="center">
  <img src="https://unpkg.com/npm-graph-bed@latest/img/other/npm-pic.png" alt="npm图床" width="200"/>
  <p><strong>利用 npm 包作为免费、稳定的图床解决方案</strong></p>
  <p>
    <img src="https://img.shields.io/npm/v/npm-graph-bed?style=flat-square" alt="npm version"/>
    <img src="https://img.shields.io/npm/dm/npm-graph-bed?style=flat-square" alt="downloads"/>
    <img src="https://img.shields.io/github/license/cosima/npm-graph-bed?style=flat-square" alt="license"/>
  </p>
</div>

## 📖 简介

本项目利用 npm 的 CDN 分发特性，将图片发布为 npm 包，实现免费、稳定的图床服务。通过 GitHub Actions 自动化发布流程，每次提交图片后自动发布到 npm，无需手动操作。

## ✨ 特性

- 🆓 **完全免费** - 利用 npm 的免费 CDN 服务
- 🚀 **全球加速** - npm CDN 覆盖全球，访问速度快
- 🔄 **自动发布** - GitHub Actions 自动化发布流程
- 📦 **版本管理** - 每次提交自动升级版本号
- 🔒 **稳定可靠** - npm 作为全球最大的包管理平台，稳定性有保障

## 🎯 原理

1. **图片存储**：将图片放在 npm 包的 `images` 目录中
2. **自动发布**：提交代码到 GitHub 后，GitHub Actions 自动将包发布到 npm
3. **CDN 访问**：通过 unpkg、jsdelivr 等 CDN 服务访问图片

### 访问方式

发布后，图片可通过以下 CDN 访问：

```
# unpkg
https://unpkg.com/npm-graph-bed@latest/img/your-image.png

# jsdelivr
https://cdn.jsdelivr.net/npm/npm-graph-bed@latest/img/your-image.png
```

## 🚀 快速开始

### 1. Fork 本项目

点击右上角 **Fork** 按钮，将本项目 Fork 到你的 GitHub 账号下。

### 2. 配置 npm Token

1. 登录 [npmjs.com](https://www.npmjs.com/)
2. 进入 **Access Tokens** 页面
3. 点击 **Generate New Token** → 选择 **Bypass 2FA** 类型 (npm最新规则token最长只能设置90天)
4. 复制生成的 token

### 3. 配置 GitHub Secrets

在你 Fork 的仓库中：

1. 进入 **Settings** → **Secrets and variables** → **Actions**
2. 点击 **New repository secret**
3. 添加以下 Secret：
   - Name: `NPM_TOKEN`
   - Value: 粘贴你的 npm token

### 4. 修改包名

编辑 `package.json`，将包名改为你自己的：

```json
{
  "name": "your-package-name",
  "version": "0.0.1",
  ...
}
```

**注意**：包名必须是 npm 上未被占用的名称。

### 5. 上传图片

1. 将图片放入 `images` 目录
2. 提交代码：
   ```bash
   git add img/
   git commit -m "feat: add new images"
   git push origin master
   ```

3. GitHub Actions 会自动：
   - 提升版本号
   - 发布到 npm
   - 创建版本 tag

### 6. 使用图片

发布成功后，使用以下链接访问图片：

```markdown
![图片描述](https://unpkg.com/npm-graph-bed@latest/img/your-image.png)
```

## 📁 项目结构

```
npm-graph-bed/
├── .github/
│   └── workflows/
│       └── publish.yml      # GitHub Actions 自动发布配置
├── img/                     # 图片存储目录
│   └── other/npm-pic.png
├── index.js                 # 包入口文件
├── package.json            # 包配置文件
└── README.md               # 项目说明
```

## ⚙️ 工作流程

```mermaid
graph LR
    A[上传图片到 img/] --> B[提交到 GitHub]
    B --> C[触发 GitHub Actions]
    C --> D[自动提升版本号]
    D --> E[发布到 npm]
    E --> F[全球 CDN 分发]
    F --> G[通过 CDN 访问图片]
```

## 💡 使用建议

1. **图片优化**：上传前压缩图片，减小包体积
2. **命名规范**：使用有意义的文件名，便于管理
3. **版本控制**：重要图片建议指定具体版本号而非 `@latest`
4. **包大小限制**：npm 包有大小限制，建议单个包不超过 100MB

## 🔧 高级配置

### 使用 Personal Access Token

如果推送遇到权限问题，可以配置 GitHub Personal Access Token：

1. 创建 PAT：https://github.com/settings/tokens
2. 勾选 `repo` 权限
3. 在仓库 Secrets 中添加 `GH_PAT`

### 自定义版本提升策略

编辑 `.github/workflows/publish.yml`：

```yaml
# 补丁版本 (0.0.1 → 0.0.2)
npm version patch

# 次版本 (0.0.1 → 0.1.0)
npm version minor

# 主版本 (0.0.1 → 1.0.0)
npm version major
```

## 📝 注意事项

- ⚠️ **npm 包一旦发布无法删除**，版本号会永久保留
- ⚠️ **不要上传敏感信息**，npm 包是完全公开的
- ⚠️ **遵守 npm 使用条款**，不要滥用 CDN 服务
- ⚠️ **图片版权**，确保你有权使用并分发上传的图片

## 📄 License

ISC

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

---

<div align="center">
  <p>如果这个项目对你有帮助，请给个 ⭐️ Star 支持一下！</p>
</div>
