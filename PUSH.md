# 推送到 GitHub 的两种方式（选一种）

本地仓库已经建好、也已提交，**只差最后一步推送**。
仓库位置：`D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io`

---

## 方式 A：网页上传（最省事，无需任何凭据）

1. 打开 https://github.com/new
2. **Repository name** 填 `mutsumi555.github.io`
3. 可见性选 **Public**（免费账号的 Pages 必须公开）
4. **不要**勾选 README / .gitignore / license 任何初始化选项
5. 点 **Create repository**
6. 在新页面点 **uploading an existing file** 链接
7. 打开本地文件夹 `mutsumi555.github.io`，把里面的
   **`index.html`**、**`README.md`**、**`.gitignore`** 拖进上传框
   （`.gitignore` 是隐藏文件，看不见的话在资源管理器「查看」里勾选「隐藏的项目」）
8. 点 **Commit changes**
9. 进入 **Settings** → 左侧 **Pages**
10. **Source** 选 `Deploy from a branch`，**Branch** 选 `main` + `/ (root)`，点 **Save**
11. 等 1–2 分钟，刷新页面，顶部出现绿色提示
12. 打开 **https://mutsumi555.github.io** 开始刷题

---

## 方式 B：命令行推送（需要你自己执行，因为需要登录凭据）

在 PowerShell 里执行：

```powershell
cd "D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io"
git push -u origin main
```

会弹窗要求登录 GitHub（浏览器授权或输入用户名 + Personal Access Token）。
**注意：这一步必须在你自己的终端里运行**，在 DSH 沙箱内会因禁止命名管道而失败
（`sh.exe: couldn't create signal pipe, Win32 error 5`）。

推送成功后，同样去 **Settings → Pages** 开启一次（方式 A 的第 9–11 步）。

---

## 之后更新题库

方式 A：网页上重新上传覆盖 `index.html` 即可。
方式 B：

```powershell
cd "D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io"
copy "D:\Users\hf\Downloads\政治\考研政治一页纸-刷题.html" index.html
git add .
git commit -m "更新题库"
git push
```

Pages 会自动重新部署，约 1 分钟后生效。

---

## 排错

| 现象 | 原因 / 解决 |
|---|---|
| 打开是 404 | 仓库名不是 `mutsumi555.github.io`；或 Pages 还没构建完，等 2 分钟 |
| 显示的是 README 而不是刷题页 | `index.html` 没上传成功，检查仓库根目录是否有这个文件 |
| Pages 选项灰色 | 仓库是 Private，改成 Public |
| 推送报 `Authentication failed` | 密码已不可用，需用 Personal Access Token 代替密码 |
| 推送报 `couldn't create signal pipe` | 在 DSH 沙箱内执行了，换到你自己的 PowerShell 窗口运行 |