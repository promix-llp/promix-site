# Promix 个人博客

一个零依赖、零构建的静态博客。纯 HTML + CSS，直接放上 GitHub Pages 就能跑。
绑定域名：**promix.cloud**

---

## 📁 文件结构

```
promix-site/
├── index.html              ← 首页（文章列表）
├── about.html              ← 关于页
├── 404.html                ← 找不到页面时显示
├── CNAME                   ← 自定义域名（promix.cloud），别删
├── assets/
│   └── style.css           ← 所有样式都在这里
└── posts/
    ├── _template.html      ← 写新文章用的模板（复制它）
    ├── hello-world.html
    ├── optical-interconnect.html
    └── on-investing.html
```

---

## ✍️ 怎么写一篇新文章

1. 进入 `posts/` 文件夹，**复制 `_template.html`**，改个英文文件名，比如 `posts/my-new-post.html`
   （文件名建议用英文/数字/连字符，不要用中文，避免网址乱码）
2. 用记事本或任意编辑器打开它，按里面的中文注释提示，改三处：
   - `<title>` 里的标题
   - `<h1>` 里的标题
   - `class="prose"` 区域里的正文（每段用 `<p>...</p>` 包住）
3. 回到 `index.html`，在文章列表里照着已有的样子，**新增一段**指向你的新文章：

```html
<li class="post-item">
  <a href="posts/my-new-post.html">
    <span class="date">2026-06-01</span>
    <div>
      <h3>你的新标题</h3>
      <p class="excerpt">一句话摘要。</p>
      <span class="tag">分类</span>
    </div>
  </a>
</li>
```

4. 保存，提交到 GitHub（见下），几分钟后网站自动更新。

> 正文里常用写法：加粗 `<strong>字</strong>`、斜体 `<em>字</em>`、
> 链接 `<a href="网址">字</a>`、小标题 `<h2>标题</h2>`、引用 `<blockquote>话</blockquote>`、
> 列表 `<ul><li>项</li></ul>`。

---

## 🚀 怎么发布到 GitHub Pages（首次）

1. 在 GitHub 新建一个仓库（建议名字就叫 `promix-site` 或直接用你已有的 `llp`）。
2. 把这个文件夹里的**所有文件**上传上去（网页端 "Add file → Upload files" 拖进去即可）。
3. 仓库 **Settings → Pages**：
   - Source 选 **Deploy from a branch**
   - Branch 选 **main** / **`/ (root)`** → Save
4. 同一个 Pages 设置页，**Custom domain** 填 `promix.cloud` → Save
   （仓库里的 `CNAME` 文件已经替你写好了这个域名）

---

## 🌐 怎么把域名 promix.cloud 接上（DNS 设置）

到你买域名的服务商后台（阿里云/腾讯云/Cloudflare/GoDaddy 等），添加 DNS 记录：

**根域名 promix.cloud —— 加 4 条 A 记录，指向 GitHub：**

| 类型 | 主机记录 | 记录值 |
|------|---------|--------------------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

**带 www 的 www.promix.cloud —— 加 1 条 CNAME：**

| 类型 | 主机记录 | 记录值 |
|------|---------|--------------------------|
| CNAME | www | `你的GitHub用户名.github.io` |

> 例如用户名是 promix-llp，就填 `promix-llp.github.io`

设置后通常 10 分钟～几小时生效。生效后回到 GitHub Pages 设置页，
勾选 **Enforce HTTPS**，网站就有了免费的 https 证书。

---

## 🔍 本地预览（可选）

双击任意 `.html` 文件就能在浏览器里看大概效果。
想看得更准（含路径），可在这个文件夹里跑：

```bash
python3 -m http.server 8000
```

然后浏览器打开 http://localhost:8000

---

有任何要改的（配色、字体、加栏目、加配图），告诉我即可。
