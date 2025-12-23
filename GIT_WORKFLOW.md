# Git 代码维护工作流程指南

## 当前状态
- ✅ 已成功克隆原作者的代码仓库
- ✅ 当前远程仓库 `origin` 指向：`git@github.com:EZreal-zhangxing/rk_ffmpeg.git`

---

## 步骤 1：在 GitHub/GitLab/Gitee 创建自己的新仓库

### 操作步骤：
1. 登录您的 GitHub/GitLab/Gitee 账号
2. 点击 "New repository" 或 "新建仓库"
3. 填写仓库名称（例如：`my_rk_ffmpeg`）
4. **不要**初始化 README、.gitignore 或 license（因为我们已经有了代码）
5. 创建仓库

### 意义：
- 创建您自己的代码仓库，用于独立维护您的修改
- 这个仓库完全属于您，可以自由推送和修改

---

## 步骤 2：将远程仓库地址改为您自己的仓库

### 操作命令：
```bash
git remote set-url origin git@github.com:您的用户名/您的仓库名.git
```

### 意义：
- 将 `origin`（默认远程仓库）指向您自己的仓库
- 之后所有的 `git push` 都会推送到您的仓库，而不是原作者的仓库
- 这样您就可以在自己的仓库中独立维护代码

---

## 步骤 3：推送代码到您自己的仓库

### 操作命令：
```bash
git push -u origin main
```

### 意义：
- `-u` 参数会设置上游分支，之后可以直接使用 `git push`
- 将当前所有代码和历史记录推送到您的仓库
- 完成后，您的 GitHub/GitLab 上就能看到完整的代码了

---

## 步骤 4：后续日常维护流程

### 4.1 查看修改状态
```bash
git status
```
**意义**：查看哪些文件被修改了，哪些文件已添加到暂存区

### 4.2 查看具体修改内容
```bash
git diff
```
**意义**：查看文件的具体修改内容，确认修改是否正确

### 4.3 添加修改到暂存区
```bash
# 添加所有修改的文件
git add .

# 或添加特定文件
git add src/文件名.cpp
```
**意义**：将修改的文件标记为"准备提交"，暂存区是提交前的缓冲区

### 4.4 提交修改
```bash
git commit -m "修改说明：描述您做了什么修改"
```
**意义**：
- 创建一个新的提交记录，保存当前的修改
- 提交信息要清晰描述修改内容，方便以后查看历史

### 4.5 推送到远程仓库
```bash
git push
```
**意义**：将本地的提交推送到您的远程仓库（GitHub/GitLab），让代码同步到云端

---

## 完整工作流程示例

假设您修改了 `src/push_stream_with_control_keyboard_and_mouse.cpp` 文件：

```bash
# 1. 查看修改状态
git status

# 2. 查看具体修改了什么
git diff src/push_stream_with_control_keyboard_and_mouse.cpp

# 3. 确认无误后，添加到暂存区
git add src/push_stream_with_control_keyboard_and_mouse.cpp

# 4. 提交修改
git commit -m "修复键盘鼠标控制功能的bug"

# 5. 推送到您的仓库
git push
```

---

## 常用 Git 命令速查

| 命令 | 作用 |
|------|------|
| `git status` | 查看当前状态 |
| `git diff` | 查看未暂存的修改 |
| `git diff --staged` | 查看已暂存的修改 |
| `git log` | 查看提交历史 |
| `git log --oneline` | 简洁版提交历史 |
| `git add .` | 添加所有修改 |
| `git commit -m "消息"` | 提交修改 |
| `git push` | 推送到远程仓库 |
| `git pull` | 从远程仓库拉取更新（如果有多台电脑） |

---

## 注意事项

1. **提交信息要清晰**：好的提交信息能帮助您以后快速了解每次修改的目的
2. **经常提交**：不要积累太多修改才提交，建议完成一个小功能就提交一次
3. **推送前检查**：推送前用 `git status` 和 `git diff` 确认修改无误
4. **备份重要修改**：重要修改建议先备份，再推送

