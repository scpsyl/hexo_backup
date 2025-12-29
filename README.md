# Hexo Blog

基于 Hexo 的个人博客，使用 Next 主题，部署到阿里云 OSS。

>关于环境的配置请参考相关教程，默认完成完整运行环境配置（Node.js、Hexo、Git 等）

## 首次配置（新机器）

### 1. 安装依赖
```bash
npm install
```

### 2. 配置敏感信息
创建 `_config.local.yml` 文件：

```yaml
deploy:
  type: ali-oss
  region: oss-ap-southeast-1
  accessKeyId: YOUR_ACCESS_KEY_ID
  accessKeySecret: YOUR_ACCESS_KEY_SECRET
  bucket: YOUR_BUCKET_NAME
```

将 `YOUR_ACCESS_KEY_ID` ,`YOUR_ACCESS_KEY_SECRET`和`YOUR_BUCKET_NAME`替换为实际的阿里云 OSS 凭证。

实际使用时需手动添加deploy信息到`_config.yml`中。

## 日常使用

### 创建新文章
```bash
hexo new "文章标题"
```

文章会创建在 `source/_posts/` 目录，同时会创建同名文件夹用于存放图片等资源。

### 本地预览
```bash
npm run server
```

访问 http://localhost:4000 查看效果。

### 生成静态文件
```bash
npm run build
```

### 部署到线上
```bash
npm run deploy
```

### 清理缓存
```bash
npm run clean
```

## 完整工作流程

```bash
# 1. 创建新文章
hexo new "我的新文章"

# 2. 编辑文章
# 编辑 source/_posts/我的新文章.md

# 3. 本地预览
npm run server

# 4. 生成并部署
npm run build && npm run deploy
```

## 项目结构

```
.
├── _config.yml              # 主配置文件
├── _config.local.yml        # 本地配置（包含敏感信息，不提交到 git）
├── source/
│   └── _posts/              # 博客文章目录
├── themes/
│   └── next/                # Next 主题
└── public/                  # 生成的静态文件（不提交到 git）
```

## 注意事项

- `_config.local.yml` 包含敏感信息，已添加到 `.gitignore`，不会提交到 git
- 每次在新机器上克隆项目后，需要手动创建 `_config.local.yml` 并填入凭证
- 文章资源文件夹功能已启用（`post_asset_folder: true`），图片等资源放在与文章同名的文件夹中
