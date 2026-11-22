# GitHub 配置完成情况

本机 Git 环境已全部配置好，**只差最后一步：把 SSH 公钥添加到你的 GitHub 账号**。

---

## 已完成

| 项目 | 状态 |
|---|---|
| Git 版本 | ✅ 2.49.0 |
| user.name | ✅ `mutsumi555`（全局 + 仓库级） |
| user.email | ✅ `2913539100@qq.com`（全局 + 仓库级） |
| credential.helper | ✅ `manager`（GCM 2.6.1 已安装并启用） |
| init.defaultBranch | ✅ `main` |
| core.autocrlf | ✅ `true`（Windows 换行） |
| SSH 密钥 | ✅ 已生成 `~/.ssh/id_ed25519_github`（ed25519） |
| 私钥权限 | ✅ 已收紧为仅当前用户可读 |
| SSH config | ✅ 已添加 `github.com` 主机条目 |
| known_hosts | ✅ 已记录 github.com |
| remote | ✅ `git@github.com:mutsumi555/mutsumi555.github.io.git` |
| 网络连通性 | ✅ SSH 22 端口已连通（`Connection established`） |

---

## 现在要做的：添加公钥（1 分钟）

复制下面整行公钥：

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIC0te2yGhP/0d2JyjRymh6msvLjkDBSD7LKSC40BGo3A 2913539100@qq.com
```

然后：

1. 打开 https://github.com/settings/ssh/new
2. **Title** 随便填，比如 `Windows-PC`
3. **Key type** 选 `Authentication Key`
4. **Key** 粘贴上面那一整行
5. 点 **Add SSH key**

---

## 然后创建仓库并推送

### 1. 创建仓库

打开 https://github.com/new

- **Repository name** 填 `mutsumi555.github.io`（必须完全一致）
- 选 **Public**
- **不要**勾选 README / .gitignore / license
- 点 **Create repository**

### 2. 推送

在你的 PowerShell 窗口里执行：

```powershell
cd "D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io"
git push -u origin main
```

成功的话会看到：
```
To github.com:mutsumi555/mutsumi555.github.io.git
 * [new branch]      main -> main
```

### 3. 开启 Pages

1. 仓库页 → **Settings** → 左侧 **Pages**
2. **Source** 选 `Deploy from a branch`
3. **Branch** 选 `main` + `/ (root)`
4. 点 **Save**
5. 等 1–2 分钟，刷新页面，顶部出现绿色提示

### 4. 访问

**https://mutsumi555.github.io**

---

## 验证配置是否成功

```powershell
ssh -T git@github.com
```

看到 `Hi mutsumi555! You've successfully authenticated...` 就说明配置完全正确。

---

## 之后更新题库

```powershell
cd "D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io"
copy "D:\Users\hf\Downloads\政治\考研政治一页纸-刷题.html" index.html
git add .
git commit -m "更新题库"
git push
```

---

## 常见问题

| 现象 | 原因 / 解决 |
|---|---|
| `Permission denied (publickey)` | 公钥还没加到 GitHub，或加错了账号 |
| `Could not resolve hostname` | 网络问题，检查代理是否开启 |
| `Repository not found` | 仓库还没在 GitHub 上创建，或仓库名拼错 |
| `Host key verification failed` | 执行 `ssh-keygen -R github.com` 后重试 |
| `schannel: SEC_E_NO_CREDENTIALS` | 在 DSH 沙箱内运行了；换到自己的 PowerShell 窗口 |
| 打开网站 404 | Pages 还没构建完，等 2 分钟；或仓库名不是 `mutsumi555.github.io` |

---

## 备用方案：HTTPS + Token

如果 SSH 不行，也可以走 HTTPS：

```powershell
git remote set-url origin https://github.com/mutsumi555/mutsumi555.github.io.git
git push -u origin main
```

会弹 GCM 登录窗口，选 **Sign in with your browser** 授权即可。