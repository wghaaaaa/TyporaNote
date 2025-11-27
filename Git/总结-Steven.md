------

# 一、概念

- Git中有4个区的概念分别是：`工作区`、`暂存区`、`本地仓库区`、`远程仓库区`
- Git使用`git init`✅某一个文件夹进行初始化，如此之后，该文件夹就变成了`工作区`
- Git使用`git add .`✅将文件夹中的文件(修改、新增、删除)，也就是`工作区`的文件转到`暂存区`
- Git使用`git commit -m 更新`✅这个文件夹中的`暂存区`文件存储到`本地仓库区`
- Git使用`git push`✅`本地仓库区`中的文件推送到GitHub或者gitee的`远程仓库`中

------

# 二、常见命令

- `git status`查看当前的文件是否放到了`暂存区`(通常为红色)以及文件是否放到了`本地仓库区`(通常为绿色)但是一般并不能检查是否push到`远程仓库`
- `git log`查看提交历史。显示的是**当前所在分支**的提交历史，按时间倒序排列（最新的提交在最上面）。注意⚠️只有commit到本地仓库的文件提交才会被记录。基本的 `git log` 会显示：
  - 提交的哈希值（唯一ID）
  - 作者信息
  - 提交日期
  - 提交信息

---

# 三、常见开发流程

## 第 1 部分：初始化一个新项目（init → add → commit → push）

### 1. 在本地创建一个项目文件夹

```
mkdir MyProject
cd MyProject
```

------

### 2. 初始化 Git 仓库

```
git init
```

**说明：**
 将当前文件夹变成 Git 仓库（生成 `.git`）。

------

### 3. 检查当前状态（非常常用）

```
git status
```

------

### 4. 添加文件到暂存区（准备提交）

#### 4.1添加所有文件

```
git add .
```

#### 4.2添加指定文件

```
git add 文件名
```

------

### 5. 提交（保存版本）

```
git commit -m "第一次提交：初始化项目"
```

------

### 6. 在 GitHub 上创建一个远程仓库

（比如：https://github.com/你的账号/MyProject）

然后复制 SSH 地址：

```lua
git@github.com:你的用户名/MyProject.git
```

> 注意：这里是先创建仓库在GitHub上面，然后再通过SSH在本地进行🔗

------

### 7. 添加远程仓库地址（绑定 origin）

```lua
git remote add origin git@github.com:你的用户名/MyProject.git
```

> 同上，这些都是在GitHub上面创建仓库后，GitHub直接给出的命令，本地直接复制粘贴即可

------

### 8. 首次推送到 GitHub

```
git push -u origin master
```

**说明：**

- `-u` 建立“上游关系”
- 以后只需要 `git push` 即可自动推送到 master

------

## 📌 到这里：你的本地项目已经成功上传到 GitHub！

## 第 2 部分：日常开发流程（修改 → add → commit → push）

你每天做的事情就是下面 4 步：

### 1. 查看当前状态

```
git status
```

### 2. 将修改加入暂存区

```
git add .
```

### 3. 提交修改

```
git commit -m "描述你这次修改做了什么"
```

### 4. 推送到远程

```
git push
```

> 这 4 条命令是程序员每天最常用的命令组合。

------

------

## 第 3 部分：别人需要从远程仓库获取你的项目（clone → pull）

### 1. 从远程仓库克隆项目（首次获取代码）

```
git clone git@github.com:你的用户名/MyProject.git
```

**说明：**

- 自动下载文件
- 自动配置远程仓库 origin
- 自动切换到 master 分支
- 自动有最新 commit

------

### 2. 进入克隆的项目目录

```
cd MyProject
```

------

### 3. 获取远程最新更新（pull）

```
git pull
```

**说明：**
 将 GitHub 上的新提交拉取到本地并自动合并。

------

------

## 第 4 部分：回到开发流程（继续修改 → add → commit → push）

重复每日开发模式：

```
git status
git add .
git commit -m "xxxx"
git push
```

------

------

## 🌟 最常用命令——全流程精华版（极简总结）

### 创建项目 → 上传到远程

```
git init
git add .
git commit -m "init"
git remote add origin git@github.com:xx/xx.git
git push -u origin master
```

------

### 日常开发

```
git status
git add .
git commit -m "update"
git push
```

------

### 从远程克隆 & 更新

```
git clone git@github.com:xx/xx.git
git pull
```

# 四、Git怎么回滚历史记录！

## 第1部分：回滚暂存区的文件

> (即`git add .`后添加到``暂存区``的文件`回滚`到`工作区`)

~~~html
git restore --staged 文件名
# 这样会将这个文件从暂存区返回到工作区，虽然区的状态改变了，但是你这个文件修改的内容保持不变！
~~~

⚠️：此时文件的内容依旧是修改之后的内容，此命令只是将这个文件从暂存区撤销到了工作区！内容并没有改变！

~~~html
git restore 文件名
# 该命令的作用是将工作区文件的修改丢弃返回到修改之前的状态，如果搭配上一个命令使用能够完美的将文件进行回滚还原！！！
~~~

## 第2部分：回滚本地仓库区的文件

