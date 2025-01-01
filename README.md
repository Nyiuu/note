# 仅供自己参考的readme

## 用于obsidian的笔记管理

## git操作
### 配置 Git 用户信息（只需在每台新机器上做一次）

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

### 克隆仓库到本地

```bash
git clone git@github.com:Nyiuu/note.git
```

### 查看仓库状态

```bash
git status
```

### 拉取远程仓库更新（同步到本地）

```bash
git pull origin main  # 或者 master，取决于你的默认分支
```

### 创建并切换到新分支

```bash
git checkout -b new-feature
```

### 切换到已有分支

```bash
git checkout existing-branch
```

### 提交更改

```bash
git add .  # 添加所有更改的文件
git commit -m "Your commit message"
```

### 推送本地更改到远程仓库

```bash
git push origin main  # 或者 master，取决于你的默认分支
```

### 查看分支列表

```bash
git branch -a  # 查看所有分支，包括远程和本地
```

### 查看提交历史

```bash
git log  # 查看详细的提交历史
git log --oneline  # 查看简洁的提交历史
```

### 回退到某个提交

```bash
git checkout <commit-hash>  # 临时查看或修改某个提交
git reset --hard <commit-hash>  # 回退并丢弃所有更改
```

### 删除本地分支

```bash
git branch -d branch-name  # 删除本地分支
```

### 查看远程仓库 URL

```bash
git remote -v
```

### 更改远程仓库 URL

```bash
git remote set-url origin git@github.com:Nyiuu/note.git
```

### 获取远程仓库的更改（但不合并）

```bash
git fetch origin
```

### 清理本地未追踪的文件

```bash
git clean -fd  # 删除未追踪的文件和目录
```

### 查看当前的 Git 配置信息

```bash
git config --list
```


