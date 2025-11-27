------

## 1. 基本设置（只需做一次）

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

**说明：**
 设置提交记录中的作者信息，用于团队协作识别身份。

------

## 2. 查看仓库状态

```bash
git status
```

**说明：**
 查看修改、暂存区、未跟踪文件，是使用频率最高的命令。

------

## 3. 添加到暂存区（Staging Area）

### 添加指定文件

```bash
git add 文件名
```

### 添加全部文件

```bash
git add .
```

**说明：**
 将修改加入暂存区，为下一次提交做准备。

------

## 4. 提交（Commit）

```bash
git commit -m "提交说明"
```

**说明：**
 将暂存区内容保存为一个版本快照。

------

## 5. 查看提交历史

### 完整历史

```bash
git log
```

### 一行简化历史

```bash
git log --oneline
```

### 图形化历史（强烈推荐）

```bash
git log --oneline --graph --all
```

------

## 6. 撤销已暂存（取消 add）

```bash
git restore --staged 文件名
```

**说明：**
 取消 `git add` 操作，保留文件内容，但移出暂存区。

------

## 7. 撤销工作区修改（恢复文件）

```bash
git restore 文件名
```

**说明：**
 恢复为上一次 commit 的内容。

------

## 8. 重写历史（未 push 时使用）

### 回退但保留改动（修改在“绿色”）

```bash
git reset --soft HEAD~1
```

### 回退但保留改动（修改在“红色”）

```bash
git reset HEAD~1
```

### 回退并丢弃所有改动（危险）

```bash
git reset --hard HEAD~1
```

------

## 9. 安全回滚（已 push 使用，不改历史）

```bash
git revert <commit-hash>
```

**说明：**
 生成一个反向 commit，用于撤销之前的提交，历史保持安全。

------

## 10. 分支（Branch）

### 查看分支

```bash
git branch
```

### 创建分支

```bash
git branch 分支名
```

### 切换分支

```bash
git checkout 分支名
```

### 创建并切换

```bash
git checkout -b 分支名
```

------

## 11. 合并分支（Merge）

```bash
git merge 分支名
```

------

## 12. 远程仓库（GitHub）

### 添加远程地址

```bash
git remote add origin <URL>
```

### 查看远程列表

```bash
git remote -v
```

### 首次推送（设置上游）

```bash
git push -u origin master
```

### 普通推送

```bash
git push
```

### 拉取远程更新

```bash
git pull
```

------

## 13. 克隆仓库

```bash
git clone <URL>
```

------

## 14. 查看 HEAD 操作历史（超重要，可救命）

```bash
git reflog
```

**说明：**
 可找回被 `reset --hard` 删除的提交，是 Git 的“后悔药”。

------

## 15. 常用流程（工作日常）

```bash
git status
git add .
git commit -m "message"
git push
```

------

## 16. 撤销常用操作总结

### 只撤销 add（保留修改）

```bash
git restore --staged 文件
```

### 丢弃文件修改并恢复上次版本

```bash
git restore 文件
```

### 回退 commit（未 push）

```bash
git reset --soft HEAD~1
```

### 回退 commit（已 push）

```bash
git revert <hash>
```

------

## 17. Git 状态颜色说明

- **红色（modified）**：文件修改但未暂存
- **绿色（staged）**：已暂存，等待 commit
- **白色（untracked）**：新文件，未被 Git 跟踪
- **clean**：工作区与上次 commit 一致

------

## 18. 最重要的 10 条命令（精炼版）

```bash
git status
git add .
git commit -m "xxx"
git push
git pull
git log --oneline
git restore 文件
git restore --staged 文件
git reset --soft HEAD~1
git revert <hash>
```

------

