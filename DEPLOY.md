# 部署到 GitHub Pages

## 方式一：网页操作（完全不用命令行）

1. 登录 GitHub，右上角 **+** → **New repository**
2. 仓库名填 `你的用户名.github.io`（例如 `feng-hu.github.io`，用户名必须完全一致）
3. 可见性选 **Public**，**不要**勾选任何初始化文件，点 **Create repository**
4. 在新仓库页面点 **uploading an existing file**，把这个文件夹里的
   `index.html`、`style.css`、`script.js`、`README.md` 全部拖进去
5. 点 **Commit changes**
6. 进入 **Settings** → 左侧 **Pages**
7. Source 选 **Deploy from a branch**，Branch 选 **main**，目录选 **/ (root)**，点 **Save**
8. 等 1–2 分钟，刷新页面，顶部会出现绿色提示和网址
9. 访问 `https://你的用户名.github.io`

> 之后每次改内容，重复第 4–5 步覆盖文件即可，Pages 会自动重新部署。

---

## 方式二：命令行推送（推荐，适合反复更新）

在本文件夹里打开终端（PowerShell），把下面的 `你的用户名` 替换掉后逐行执行：

```powershell
git init
git add .
git commit -m "init site"
git branch -M main
git remote add origin https://github.com/你的用户名/你的用户名.github.io.git
git push -u origin main
```

推送成功后，去仓库 **Settings → Pages** 按方式一的第 6–7 步开启一次即可。

后续每次更新：

```powershell
git add .
git commit -m "更新内容"
git push
```

---

## 方式三：项目站（仓库名不叫 `.github.io`）

如果你想给某个项目单独做一个展示页：

1. 仓库名随意（比如 `my-project`）
2. 同样上传文件，开启 Pages（Settings → Pages → Deploy from a branch → main → / (root)）
3. 访问地址是 `https://你的用户名.github.io/my-project`

⚠️ 项目站如果引用 CSS/JS，用相对路径（本模板已经是 `style.css` 这种相对路径，无需改动）。

---

## 常见问题

| 现象 | 原因 / 解决 |
|---|---|
| 打开是 404 | 文件名不是 `index.html`（必须全小写），或 Pages 还没构建完，等 2 分钟再刷新 |
| 页面没有样式 | `style.css` 没上传成功，或文件名拼写不一致 |
| 改了代码不生效 | 等 Actions 跑完；浏览器按 Ctrl+F5 强刷 |
| Pages 选项灰色 | 仓库是 Private，免费账号需改成 Public |
| 想用自己的域名 | Settings → Pages → Custom domain 填域名；DNS 加 CNAME 记录指向 `你的用户名.github.io`；根目录放一个内容为域名的 `CNAME` 文件 |