# WTTao Blog 搭建说明

本博客基于 [CuteLeaf/Firefly](https://github.com/CuteLeaf/Firefly) 初始化，站点域名已配置为：

```txt
https://wttao.xyz
```

## 本地运行

```bash
corepack enable
corepack prepare pnpm@9.14.4 --activate
pnpm install
pnpm dev
```

访问：<http://localhost:4321>

## 构建

```bash
pnpm build
```

构建产物位于 `dist/`。

## GitHub Pages 部署

仓库已包含 `.github/workflows/deploy.yml`，推送到 `master` 后会自动构建并发布到 `pages` 分支。

GitHub 仓库设置建议：

1. Settings → Pages → Build and deployment
2. Source 选择 `Deploy from a branch`
3. Branch 选择 `pages`，目录选择 `/root`
4. Custom domain 填写 `wttao.xyz`
5. 勾选 `Enforce HTTPS`

## DNS 配置

如果使用根域名 `wttao.xyz` 指向 GitHub Pages，请在域名 DNS 服务商处添加：

```txt
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
CNAME www   <你的 GitHub 用户名>.github.io
```

如果你部署到 Vercel/Netlify/Cloudflare Pages，则应改用对应平台提供的 CNAME 或 A 记录。

## 已修改的关键文件

- `src/config/siteConfig.ts`：站点标题、描述、URL、页面开关
- `src/config/profileConfig.ts`：个人资料与链接
- `src/content/spec/about.md`：关于页面
- `src/content/posts/welcome/index.md`：首篇文章
- `public/CNAME`：GitHub Pages 自定义域名

