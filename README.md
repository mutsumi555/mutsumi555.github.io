# mutsumi555.github.io

考研政治「一页纸」学习站点 —— 两个纯前端页面，离线可用，无任何外部依赖。

## 访问地址

| 页面 | 地址 | 内容 |
|---|---|---|
| **刷题** | https://mutsumi555.github.io | 133 道遴选题（9 大解题方法主题） |
| **知识点手册** | https://mutsumi555.github.io/knowledge.html | 121 条知识点 + 86 条解题方法 |

两个页面右上角可互相跳转。

---

## 刷题页（index.html）

- 单选 / 多选，先选后对，边做边记
- 答题卡、进度条、正确率统计
- **导出 / 导入进度**：首页「数据」区可导出 JSON 备份，换设备时导入恢复
- 进度存 localStorage（键 `yzb_quiz_v1`），不上传、不同步
- 自动跟随系统深色 / 浅色模式，手机端适配

## 知识点手册（knowledge.html）

- 121 个知识点：马原 20 / 政经 19 / 国际 2 / 史纲 74 / 其他 6
- 86 条解题方法条目
- 搜索、分类筛选、目录抽屉、字号调节、默认展开、隐藏答案标记
- 设置存 localStorage（键前缀 `yzyz-`）

> 两页的存储键完全隔离，进度互不干扰。

---

## 更新内容

直接替换对应的 HTML 文件，提交后 Pages 会自动重新部署（约 1–2 分钟）。

```powershell
cd "D:\Users\hf\Documents\deepseek-harness\default-workspace\mutsumi555.github.io"
# 替换文件后
git add .
git commit -m "更新内容"
git push
```

| 来源文件 | 目标位置 |
|---|---|
| `考研政治一页纸-刷题.html` | `index.html` |
| `考研政治一页纸-知识点手机版.html` | `knowledge.html` |

---

## 说明

题目、答案、解析、知识点均整理自《2027 这就是一页纸》系列手册，仅供个人学习使用。